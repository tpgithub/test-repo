# test-repo

adding more lines to repo...
Building RPM Packages

Main things to know while creating the RPM package in Linux(fedora) is

1. how to create RPM package
2. how to create SPEC file

Steps to to achive this:

First, ready your system to do this,

In order to create RPM packages in Fedora you need to setup development tools and core components and set up user accounts you will use.
	#yum install @development-tools
	#yum install fedora-packager
Create a dummy user to create RPM packages so that build process gone wrong can't trash your file and send you keys to whole world.
   Note: Don't create RPM package as a root user

So create a Dummy user to just create the package manager
	lets create new user name makerpm and add user to “mock” group and set password and login as that user. Below are the steps to do it.
	#/usr/sbin/useradd makerpm
	#usermod -a -G mock makerpm <== this will add makerpm to group mock.
	#passwd makerpm
   
Now login as makerpm
	Now create the required directory structure in makerpm home directory by executing the command below
	#rpmdev-setuptree – this command will build the following directory structure as below
	 /rpmbuild
	     |
	     /BUILD  /RPMS /SOURCES  /SPECS  /SRPMS
	specs and build are the main directories used to build rpm packages. Also note that .rpmmacros file has been created in makerpm(dummy user) home directory, which will be used to set various options.

Basics of building RPM Packages

Create a .SPEC text file – this contains information abour software being packaged. Once this .spec file is created then run rpmbuild command on spec file which will go thru series of steps in spec file to produce RPM Package.

How to place your files
- Original sources such as .tar or .gz files should be placed in /rpmbuild/sources directory
- .spec file should be placed in /rpmbuild/specs directory and name it “NAME.spec”
					Where NAME is base name of package.
