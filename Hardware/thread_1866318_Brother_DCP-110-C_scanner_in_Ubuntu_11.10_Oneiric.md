---
title: "Brother DCP-110-C scanner in Ubuntu 11.10 Oneiric"
date: 2011-10-21
forum: Hardware
---

### Post by lhuppe on 2011-10-21
First of all, credit to the following for providing the information I needed to put together this procedure:

[http://ubuntuforums.org/showthread.php?t=1340908](http://ubuntuforums.org/showthread.php?t=1340908)

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101)

1) Install these two packages from Synaptic along with all dependencies:

	brother-lpr-drivers-extra 
	brother-cups-wrapper-extra

2) Download and install these two packages from the Brother web site

	brscan2
	brscan-skey

3) Edit two files 

	sudo gedit /lib/udev/rules.d/40-libsane.rules 

	add the following two lines at the bottom ...

	# Brother scanners 
	ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes" 

	next ...

	sudo gedit /lib/udev/rules.d/50-udev-default.rules 

	edit the line ... 
	
	SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", ... , MODE="0664" 

	to this...

	SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", ... , MODE="0666" 
 
4) Copy the following files

	from /usr/lib64/ to /usr/lib/ ...

	libbrscandec2.so.1.0.0 
	libbrcolm2.so.1.0.1 
	libbrcolm2.so 
	libbrscandec2.so.1 
	libbrscandec2.so 
	lib64/libbrcolm2.so.1 

	from /usr/lib64/sane/ to /usr/lib/sane/ ...

	libsane-brother2.so.1.0.7 
	libsane-brother2.so.1 
	libsane-brother2.so 

5) Reboot

Hope that helps :)

---

### Post by yetanothersteve on 2011-10-28
Good post. 
I can confirm your steps also work for a Brother MFC-7820N.

---

### Post by yetanothersteve on 2012-05-18
Also required in Ubuntu 12.04 Precise.

Copying the files from /usr/lib64 to /usr/lib is not necessary, you can simply make symbolic links, like so via sudo or as root

ln -s /usr/lib64/libbrcolm2.so /usr/lib/libbrcolm2.so
ln -s /usr/lib64/libbrcolm2.so.1 /usr/lib/libbrcolm2.so.1
ln -s /usr/lib64/libbrcolm2.so.1.0.1 /usr/lib/libbrcolm2.so.1.0.1
ln -s /usr/lib64/libbrscandec2.so /usr/lib/libbrscandec2.so
ln -s /usr/lib64/libbrscandec2.so.1 /usr/lib/libbrscandec2.so.1
ln -s /usr/lib64/libbrscandec2.so.1.0.0 /usr/lib/libbrscandec2.so.1.0.0
ln -s /usr/lib64/sane/libsane-brother2.so /usr/lib/sane/libsane-brother2.so
ln -s /usr/lib64/sane/libsane-brother2.so.1 /usr/lib/sane/libsane-brother2.so.1
ln -s /usr/lib64/sane/libsane-brother2.so.1.0.7 /usr/lib/sane/libsane-brother2.so.1.0.7

---

### Post by newb85 on 2012-06-02
I had used this procedure after doing a fresh install of Precise, and it worked great.  Today I found that my scanner was no longer detected.  It seems an update had purged the files copied from lib64 to lib.  Looks like I'll be creating a script to create those links in case it happens again in the future.

---

### Post by newb85 on 2012-06-02
Here's a shell script of the commands given by yetanothersteve to create symbolic links (instead of lhuppe's step 4).

Ensure the script is executable on your machine (right-click->Properties, Permissions, Allow executing file as a program).

Then run the script in a terminal (Double-click, Run in Terminal).

In the future, if your computer fails to detect the scanner, run the script again.

---

### Post by yetanothersteve on 2012-10-20
Thanks newb85.

I installed 12.10 today and the manual intervention documented here was still required.

I used your script of the commands I provided after installing 
brscan2-0.2.5-1.amd64.deb

Scanner now working, no issues.

---

