---
title: "Installing Maple 8 on Ubuntu Hoary Hedgehog 5.04 with Sun Java j2sdk1.5"
date: 2006-02-02
forum: Installation &amp; Upgrades
---

### Post by synthespian on 2006-02-02
Hi --

 This is for those of us that haven't yet the cash for a new Maple license, and are sticking to their old guns. 
 I'm putting this down here for the record.

  If you don't do this, you get the following error upon installation:
 
me@outerspace:/tmp/maple $ sudo ./installMapleLinuxSU
/tmp/maple/Linux/Linux/resource/jre/bin/i386/native_threads/java: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

 *HEY! NO GARANTEES* Your software crashes because of my instructions, it's your problem. I also assume you have your very licensed official Maple CD-ROM, not warez.
 In case you've downloaded Sun j2sdk1.5 here's what you do:

 In humanspeak:
 1) You've got to download and install Java. Read up on how to do it using Ubuntu's methods (recommended).
 2) You've got to copy the contents of the CD-ROM to a temporary folder.
 3) Then, you've got to alter two lines on the LinuxInstaller.bin script that deal with the kernel.
 4) Then make Maple use your new Java (instead of what's on the CD)
 5) Install, run.

 In Unixspeak (I'm not dealing with the Java installation part, it's thoroughly documented on the net by other people):

me@outerspace:/tmp $ sudo mkdir /tmp/maple/

me@outerspace:/ $ sudo cp -r /cdrom/* /tmp/.

me@outerspace:cd to /tmp/maple/Linux/Linux

me@outerspace: sudo emacs LinuxInstaller.bin 

then uncomment lines 1331 and 1332 that refer to LD_ASSUME_KERNEL variable.

C-x C-s on emacs and Exit

cd to /tmp/maple/Linux/Linux/resource/jre/bin

mv java java.bak

me@outerspace:/tmp/maple/Linux/Linux/resource/jre/bin $ \
> sudo ln -s /usr/lib/j2sdk1.5-sun/bin/java java

me@outerspace:/tmp/maple/Linux/Linux/resource $ cd ../../../

me@outerspace:/tmp/maple $ sudo ./installMapleLinuxSU &

me@outerspace:/usr/local/maple8/bin $ ./xmaple&

I don't know why you can't use GNOME's Application launcher, but I don't really care. You might want to read Zukhov's solution: [http://ubuntuforums.org/showthread.php?t=38126&highlight=Maple](http://ubuntuforums.org/showthread.php?t=38126&highlight=Maple)

The uncommenting the 2 lines bit I took from Maplesoft's FAQ:
[http://www.maplesoft.com/support/faqs/Maple8/Installation/10.aspx](http://www.maplesoft.com/support/faqs/Maple8/Installation/10.aspx)

---

