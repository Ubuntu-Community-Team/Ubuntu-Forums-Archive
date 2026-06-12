---
title: "install x3270 in 8.04 for all users?"
date: 2008-07-28
forum: General Help
---

### Post by support on 2008-07-28
I have found quite a bit of good documentation on how to install the x3270 packages for yourself and have successfully launched the emmulator for my own account. The problem is that I am working in a remote-mounted networked environment and want every user who logs on to be able to launch x3270 and have found no information to this end.

I attempted an install procedure with failed in the following way: When I launch the program in a terminal with the "x3270 &" command, I get a "x3270: Command not found." error... 

My NON-FUNCTIONAL installation attempt follows.

Any ideas what I may be doing wrong?


#####
# Download the required packages for x3270.
wget -c [http://archive.ubuntu.com/ubuntu/pool/universe/i/ibm-3270/ibm-3270_3.3.4p6.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/universe/i/ibm-3270/ibm-3270_3.3.4p6.orig.tar.gz)

# Extract the zipped archive to prepare for installation.
sudo tar -C /opt -zxvf ibm-3270_3.3.4p6.orig.tar.gz

# Make the "x3270" launcher command available
# to all users.
sudo ln -s /opt/3270-3.3.4p6.orig/x3270 /usr/bin/x3270

# Launch in a terminal via the following command.
x3270 &

---

### Post by mixmaster on 2008-07-28
The obvious first check is that the file you are linking to has the correct execute permissions etc.

Try running
/opt/3270-3.3.4p6.orig/x3270
and see if that works.  If it doesn't fix the permissions.

---

### Post by support on 2008-07-28
Apparently there is more to it than I thought...


I set the permissions via the following commands:

sudo chmod -R o+x /opt/3270-3.3.4p6.orig/
sudo chmod -R o+r /opt/3270-3.3.4p6.orig/


Setting the permissions did not resolve the problem.


Also, running the following command give the same command not found error --likley because x3270 is a directory:

/opt/3270-3.3.4p6.orig/x3270


After digging around the /opt/3270-3.3.4p6.orig/x3270 directory a little more, I tried running the install-sh script via the following command:

sudo ./opt/3270-3.3.4p6.orig/x3270/install-sh


This returns the following error:

sudo : ./opt/3270-3.3.4p6.orig/x3270/install-sh: command not found


Also, running the install script via following command:

sudo ./opt/3270-3.3.4p6.orig/x3270/install-sh


Yields the following error:

install: no input file specified


I'm out of ideas again... Any of you know what I'm missing?

---

### Post by mixmaster on 2008-07-29
sudo ./opt/3270-3.3.4p6.orig/x3270/install-sh

The . at the beginning means look for a directory called opt in the current directory.  This command would only work if you are in the / directory.

sudo /opt/3270-3.3.4p6.orig/x3270/install-sh 
should work if install-sh specifies a valid shell.

My original suggestion assumed that the x3270 was the executable.  It would appear that you have symlinked a directory into /usr/bin, which you can do but that will not give you access via an executable name without changing your path.

Looking back to your original post, you seem to have done the following:

1. Extracted the contents of the tar archive into a subdirectory of /opt
2. Linked a subdirectory of that extraction into /usr/bin
3. Assumed this will give you access to the x3270 executable.

There are a lot of misconceptions there.  I assume you are a linux newbie?

I would do the following (I'm guessing a bit as I don't have access to your package definitions):
Remove the stuff in /opt (it is not where you keep installation temp files)
   sudo rm -rf /opt/3270-3.3.4p6.orig/x3270
Remove the symlink
   sudo rm -f /usr/bin/x3270
Unpack the archive into a temporary file
   sudo tar -C /tmp -zxvf ibm-3270_3.3.4p6.orig.tar.gz
go to the directory with the install-sh file
   cd /tmp/3270-3.3.4p6.orig/x3270
run the install script
   sudo ./install-sh

what you have to do next really depends on how sophisticated the install-sh script is.  It may ask if you want to install for all users (say yes) or it may do something which you need to tidy up afterwards.
It may well be sufficient to provide a symlink from /usr/bin to the x3270 executable (wherever the installer puts it).

---

### Post by pgte3 on 2008-07-29
I am also looking at x3270. I see that it is a package offered through the Ubuntu repositories. Will I have to compile this package? If so, why are the binaries not included?

---

### Post by pgte3 on 2008-07-29
I was able to get a x3270 session running by downloading the x3270 and co-requisites (mainframe term) packages through synaptic and running /usr/bin/x3270.

---

### Post by mixmaster on 2008-07-31
I had assumed you had some reason for not using the version in the repositories.  Generally, that is the simplest way to install software.

---

### Post by support on 2008-08-04
Apparently I was experiencing inconsistant behavior. When I attempted to install via apt-get the first time, it only worked if you had sudo access. When I attempted again, everything worked fine for all users. The commands I used which were successful follow:


# Download and install the required packages for x3270

sudo apt-get install x3270
sudo apt-get install x3270-common
sudo apt-get install libc6
sudo apt-get install libice6
sudo apt-get install libsm6
sudo apt-get install libssl0.9.8
sudo apt-get install libx11-6
sudo apt-get install libxaw7
sudo apt-get install libxext6
sudo apt-get install libxmu6
sudo apt-get install libxt6
sudo apt-get install pr3287
sudo apt-get install xfonts-x3270-misc

# Launch in a terminal via the following command:
x3270 &

---

### Post by ManofPatience on 2008-09-19
Help, I'm still at a loss here on this topic.  From the last msg, I followed the "Download and install the required packages for x3270"

i.e., 
sudo apt-get install x3270
sudo apt-get install x3270-common
sudo apt-get install libc6
sudo apt-get install libice6
sudo apt-get install libsm6
sudo apt-get install libssl0.9.8
sudo apt-get install libx11-6
sudo apt-get install libxaw7
sudo apt-get install libxext6
sudo apt-get install libxmu6
sudo apt-get install libxt6
sudo apt-get install pr3287
sudo apt-get install xfonts-x3270-misc

I was up to date on all except the first one, which ran fine:
  The x3270-common, however, gives an error : 
$ sudo apt-get install x3270-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package x3270-common

$ echo $?
100

What does this mean?  and How can I get x3270 to work?

---

### Post by jt6806 on 2008-10-02
The package name is '3270-common' without the leading 'x.'

---

### Post by stans on 2008-11-12
Documentation ? I'd love to find it myself. 

The package seems to be the only option for Linux - too bad the presentation size is so small. After working with full screen all day...

---

