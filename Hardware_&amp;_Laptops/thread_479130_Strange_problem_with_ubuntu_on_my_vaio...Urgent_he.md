---
title: "Strange problem with ubuntu on my vaio...Urgent help needed"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by technomaniac on 2007-06-20
My laptop is a Sony Vaio c15 :1.66 Ghz core 2 duo, 1GB ram, 80 GB sata seagate HDD, Geforce  go 7400

I once installed ubuntu 6.06 on my vaio and it installed well. But now none of the versions are getting installed. While ubuntu 6.06 and 6.10 live cd stops at "Setting up locales.... 

The problem with 7.04 is much more strange

The last few lines of the error message are

Loading manual drivers...
Checking File systems
logsave:tzfile.c:344:__tzfile_read:assertion 'num_types==1' failed. Aborted file system check        failed
a log is being saved in /var/log/fsck/checkfs if that location is writable.

Please repair the file system manually

After this I get a maintainence shell.

On pressing Ctrl+D the boot continues and finally stops again at

Starting system log daemon ....

Here it stops for an eternity.

I have tried restoring my laptop to factory installed state and I tried again but the problem is same.


With 6.10 and 6.06 I also get the following error message

[4294669.437000]PCI:failed to allocate memory resource #6:20000@c0000000 for 0000:01:00.0


Can anybody tell me what the problem is?

Also I checked the 7.04 CD and it says I file is corrupted.

Only ubuntu causes this problem. Even opensuse, fedora, xp and vista are installing. 

Please help

---

### Post by ukripper on 2007-06-20
Post your DMESG here

---

### Post by technomaniac on 2007-06-22
[SIZE="5"][4294669.437000]PCI:failed to allocate memory resource #6:20000@c0000000 for 0000:01:00.0[/SIZE]

What does this message mean?

I got this with Ubuntu as well as Fedora Core? 

I have installed FC now.But once again I get this message after which some services start. Then I get

Starting System Logger:

and FC booting stops. No further progress. Can anyone please help? I am still able to run windows perfectly.

---

### Post by technomaniac on 2007-06-22
[4294669.437000]PCI:failed to allocate memory resource #6:20000@c0000000 for 0000:01:00.0

What does this message mean?

I got this with Ubuntu as well as Fedora Core?

I have installed FC now.But once again I get this message after which some services start. Then I get

Starting System Logger:

and FC booting stops. No further progress. Can anyone please help? I am still able to run windows perfectly.

Earlier I had OpenSuse. I cant even boot from the ubuntu live CD.  But someone pls tell me what the above message means....

Is my HDD bad or is my ram damaged.That shouldn't be coz windows runs perfectly. Also I have hardly ever had improper shut downs with windows.

You can find more info about my problem here

[http://ubuntuforums.org/showthread.php?t=479130](http://ubuntuforums.org/showthread.php?t=479130)

---

### Post by tgalati4 on 2007-06-22
You might have a disk problem in the partition that you are trying to install to.  Why don't you wipe the partition and start again.  Make sure the Live CD that you use will pass the CD check.  Remember, your CD reader needs to be able to read the entire disk, otherwise you will get a problematic install.

Turn off the suspend-to-disk option in the BIOS.  It could be that the Windows suspend-to-disk is clobbering your installs.

---

### Post by technomaniac on 2007-06-22
okay i try out all these.

But I formatted the whole HDD twice and tried, but the same problem occurs

---

### Post by technomaniac on 2007-06-23
I have found out a bit more about the problem. This time I selected the option "Install updated driver CD". Then it asks me to insert the updated driver CD and press enter. I dont change the CD and just press enter. It searches for driver updates from the ubuntu installation CD after which I am again asked to re-insert the Ubuntu installation CD and press enter. I press enter and finally after several minutes of waiting I get the GNOME desktop. But when I click the install icon, the installation app crashes. The installation app is called ubiquity and I tried running it from the terminal and I got the following error message

python:tzfile.c:344:__tzfile_read:Assertion 'num_types==1' failed

 What does this mean?  I am also going to replace the RAM modules on my laptop and try again. If the problem doesn't occur, it will mean my RAM was defective. But I dont think RAM is the problem. Windows,OpenSuse and well as games like NFS Carbon, Hitman, UT are running fine.

---

### Post by bapoumba on 2007-06-23
@ technomaniac: merged your other thread in here.

---

### Post by technomaniac on 2007-06-23
Well now I have finally installed Ubuntu but it still refuses to boot up. The boot process starts and goes on for ever. I dont know what to do. Downloading Ubuntu 7.04 again. Can anyone help?  I guess I will do a LFS thing, make my own distro

---

### Post by tgalati4 on 2007-06-24
Ubiquity is the Ubuntu installer application.  Ubiquity means the quality of being everywhere as in ubiquitous.

The CD driver may be needed to get the CD to read the ISO image properly--it's probably a work-around or patch that is needed to work with Sony CD drives.  It could be as simple as suppressing copy protection that some CD readers have built-in.

If you went through the installation properly, then the black screen on bootup could be a graphics driver problem.  This is quite common.

Try booting into single-user-mode (rescue) from the Grub menu.  See if the system boots then run dmesg to look at the bootup messages and see if anything looks unusual.

For graphics display help, search the forums for your model of graphics chip.

---

### Post by technomaniac on 2007-06-24
Well.. I ran memtest and it showed no errors. I have checked the RAM and they are not faulty. I tried logging in through the rescue option as mentioned in the above thread and this is what I get

[ 17.836000] ipw3945:Radio Frequency kill switch is on:
*Setting up console font and keymap:confused:

init:rcS-sulogin main process(4471) killed by quit signal

I am unable to login even under rescue mode.

Someone help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!1

---

### Post by ukripper on 2007-06-24
> **technomaniac said:**
> Well.. I ran memtest and it showed no errors. I have checked the RAM and they are not faulty. I tried logging in through the rescue option as mentioned in the above thread and this is what I get

[ 17.836000] ipw3945:Radio Frequency kill switch is on:
*Setting up console font and keymap:confused:

init:rcS-sulogin main process(4471) killed by quit signal

I am unable to login even under rescue mode.

Someone help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!1

Killing switch problem is refrred here - 
[http://ubuntuforums.org/showthread.php?t=246074&page=2](http://ubuntuforums.org/showthread.php?t=246074&page=2)

---

### Post by prasinos on 2007-10-26
OP: The error message usually means that there is a problem in your "time" setup. 
In the maintenance shell try to delete the file /etc/localtime. You will have to mount your root partition read/write:
mount -o remount,rw /dev/<root> 

If you boot successfully, you have to set up timezone information with "sudo tzconfig".

Hope this helps.

---

