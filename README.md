# OpenAudible
A cross-platform desktop application for downloading and managing your Audible audiobooks.

![build status badge](https://codebuild.ap-southeast-2.amazonaws.com/badges?uuid=eyJlbmNyeXB0ZWREYXRhIjoiaWs2Q2pIaGFJcWNwb284RkpWVjhPTmpUMEc0T0lhUFpYb3Z2cmlnbDdSdzFyU2t1WjZhYTI0TDM2Rit4MWJrR0VmZEZvR0dCMEtFQ2VVWDF1aXI5VVh3PSIsIml2UGFyYW1ldGVyU3BlYyI6InUycndQMjYrK21STCthVmYiLCJtYXRlcmlhbFNldFNlcmlhbCI6MX0%3D&branch=development)

## Latest Binary Release

[Download](https://openaudible.org) installers for Windows, Mac and Linux. (64bit)

More information is available at the project home page [openaudible.org](http://openaudible.org).

## Features
- Import audible books from your account
- Convert to mp3 with all tags
- Import (or Drag and drop) aax files directly into the app
- Display all your books in searchable UI
- Export web page/javascript file with all your books

## Note
This open source version 1.1.8 is not the latest available as a binary version. 
You can still build this version from scratch, but it will not be the latest version available. 
You can also run the latest version using Java debugger using these instructions, and the source can be decompiled.

## Building version 1.1.8
OpenAudible is a java application that uses Maven for building.

### Prerequisites
Java 8, Maven, and git. Windows, Mac or Linux Desktop, 64 bit Intel/AMD architectures only.

Clone the [git repo](https://github.com/openaudible/openaudible)

```
git clone https://github.com/openaudible/openaudible.git
```

#### Build using Intellij
Import Project: <br />
Select the openaudible/pom.xml file <br />
Click through all of the defaults

#### Build using Eclipse
Import... Maven Project<br />
Select the openaudible directory<br />

#### Build from command line (requires maven, java 8 SDK)

```
cd openaudible
mvn compile
mvn package
```
## Running/Debugging

Your IDE should link the platform specific SWT library via the maven profile.
SWT is the eclipse widget library, used by Eclipse IDE and other apps. It has a
jar file for each platform mac, win64, and linux.


#### IntelliJ
Select menu Run: Debug...  <br />
Select Edit Configurations... <br />
Add Application <br />
Name: OpenAudible <br />
Main Class: org.openaudible.desktop.Application <br />
VM options: -ea -Dfile.encoding=UTF-8 <br />
Mac VM options: -XstartOnFirstThread <br />
Then Run or Debug <br />

#### Windows Command Line
```
java -Dfile.encoding=UTF-8 -ea -cp "target\openaudible-jar-with-dependencies.jar;swt\org.eclipse.swt.win32.win32.x86_64-4.6.jar" org.openaudible.desktop.Application
```

#### Mac Command Line
```
java -XstartOnFirstThread -Dfile.encoding=UTF-8 -ea -cp "./target/openaudible-jar-with-dependencies.jar:./swt/org.eclipse.swt.cocoa.macosx.x86_64-4.6.jar" org.openaudible.desktop.Application
```
Notice on Mac, the -XstartOnFirstThread is required to run SWT apps.

#### Linux Command Line
```
java -Dfile.encoding=UTF-8 -ea -cp "target/openaudible-jar-with-dependencies.jar:swt/org.eclipse.swt.gtk.linux.x86_64-4.6.jar" org.openaudible.desktop.Application
```

#### Notes

Running with -ea to alert you of assertion failures is recommended for debugging. We use "asserts" to help identify problems.

Enter that into the VM Arguments on your debugger/run dialog if using an IDE.

You should see the user interface. You may see an error, or a warning about where you can go to preferences and enter your audible account details.

Open the Preferences from the Edit Menu. <br />
Enter your audible user name (email) and password. <br />
Before logging in with the application, go to the Controls: Browser menu and log into your audible account. <br />
This is only required if logging in fails or if the browser cookies expire. <br />

The application will use cookies to expedite logging in-- and bypassing some of the "are you a human" checks.

Errors are logged to the console window, under the File menu.

Some effort was made to separate the SWT GUI from the core code, which can be used in other projects or using another front end. Maybe someone wants to port the app to Swing or Electron.

## Built With

- [Eclipse SWT](http://www.eclipse.org/swt/) - Standard Widget Toolkit
- [HTML Unit](https://htmlunit.sourceforge.net/) - HTML web page scraping
- [InAudible-NG](https://github.com/inAudible-NG/) - Decode

## Contributing

While stable, OpenAudible is always looking for improvements, testing and bug reporting for all platforms. Community support of all kinds is essential and greatly appreciated. 

- Donation of an [Open Source code signing certificate](https://www.certum.eu/certum/cert,offer_en_open_source_cs.xml) would be nice.
- Exporting to a podcast format is being considered
- Testing and feedback with regions outside of the US/UK is needed
- Exporting to a format that supports the best mobile and linux audio book players is the goal.
- Are chapters, artwork, and meta data working well in your favorite audio book player?
- UI improvement ideas welcome, especially for Linux.
- The in-app [help documentation](https://github.com/openaudible/openaudible/tree/master/src/main/help) is not great and ugly.  
- Support for multiple audible accounts would be nice


Please feel free to submit issues and pull requests.



## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/openaudible/openaudible/tags).

Rebased on 1/26/2018 with version 0.9.2

## Authors

See the list of [contributors](https://github.com/openaudible/openaudible/contributors) who participated in this project.

## License

This project is licensed under the Apache 2.0 License - see the [LICENSE.md](LICENSE.md) file for details, but may uses code licensed by other licenses.

Please use responsibly on content you are legally authorized to access.
