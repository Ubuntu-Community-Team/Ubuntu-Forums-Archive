---
title: "hplip installation problems"
date: 2011-08-01
forum: Hardware
---

### Post by johnmill on 2011-08-01
Iam running UBUNTU 10.4 and  have just bought new HP printer and needed to install hplip 3.11.7 as its not on 3.10.2 list and followed instructions on web site . Installation failed to install dependencies libusb-dev and libsane-dev with errors 100

I tried rerunning after restarting the machine (old windows trick) and got the following 

warning: HPLIP removal failed. The previous install may have been installed using a tarball or this installer.
warning: Continuing to run installer - this installation should overwrite the previous one.
hplip-install[1454]: info: :
hplip-install[1454]: info: :
hplip-install[1454]: info: :[01mRUNNING POST-PACKAGE COMMANDS[0m
hplip-install[1454]: info: :[01m-----------------------------[0m
hplip-install[1454]: info: :OK
hplip-install[1454]: info: :
hplip-install[1454]: info: :
hplip-install[1454]: info: :[01mRE-CHECKING DEPENDENCIES[0m
hplip-install[1454]: info: :[01m------------------------[0m
scheduler is running 

error: A required dependency 'libusb (libusb - USB library)' is still missing.
error: Installation cannot continue without this dependency.
error: Please manually install this dependency and re-run this installer.


I am a beginner and not sure how to go about installing manually or why it failed with error 100

Any help gratefully received  John

---

### Post by Metaxa on 2011-08-01
I had this same issue and followed the following guide with success. 


[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)


Hope this helps.


Metaxa

---

### Post by johnmill on 2011-08-02
Thanks for suggestion but I have tried that and still get

Running 'sudo apt-get install --assume-yes libusb-dev'
Please wait, this may take several minutes
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ?

Retry gets the same error so I am stuck

---

### Post by johnmill on 2011-08-02
I have tried to install libusb-dev manually as suggested and got the following 


john@john-mill:~$ sudo apt-get install libusb-dev
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libusb-dev: Depends: libusb-0.1-4 (= 2:0.1.12-14) but 2:0.1.12-14ubuntu0.2 is to be installed
E: Broken packages
john@john-mill:~$ 

Can someone please explain what I do about the unmet dependencies? 

Does this mean my software needs updating?

I use the machine to run EmC2 and don't want to do anything to upset production - just trying to use new printer!

---

### Post by johnmill on 2011-08-03
Have managed to get there by ignoring automatic option and then selecting a subset of options ignoring network and scanner options. It has then loaded usb-dev, I am pleased but very puzzled as to what is going on.

---

