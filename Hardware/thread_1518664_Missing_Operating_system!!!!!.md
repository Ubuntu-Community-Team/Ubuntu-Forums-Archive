---
title: "Missing Operating system!!!!!"
date: 2010-06-26
forum: Hardware
---

### Post by b3crack on 2010-06-26
Hi,

I had Ubuntu 9.04 wubi-installed in Windows 7. I tried to format my pen drive using fdisk command in Ubuntu. After executing this command, I restarted my system to see "Missing operating System" message. I can't even boot from CD or Flash drive. I tried with "unetbootin" with no avail. I have recover my entire data.

Please help!!!

Laptop details:
-----------------------
Sony Vaio VGN-N320E
2 GB RAM
Don't have a Windows disk.

---

### Post by garvinrick4 on 2010-06-26
> **b3crack said:**
> Hi,

I had Ubuntu 9.04 wubi-installed in Windows 7. I tried to format my pen drive using fdisk command in Ubuntu. After executing this command, I restarted my system to see "Missing operating System" message. I can't even boot from CD or Flash drive. I tried with "unetbootin" with no avail. I have recover my entire data.

Please help!!!

Laptop details:
-----------------------
Sony Vaio VGN-N320E
2 GB RAM
Don't have a Windows disk.
Start your computer and get into BIOS before it boots and set your CD drive to boot first in order.
Take your Ubuntu Cd and go into TRY mode or Live CD as it would and let it boot up and then open a terminal and do this:
  	 	 	 	 	 	  Restore basic windows boot loader - universe enabled
```
sudo apt-get install lilo
```
```
sudo lilo -M /dev/sda mbr
```
May show error messages about the rest of lilo missing, ignore, we just want MBR



Now reboot take out your Ubuntu CD and let it boot into Windows hopefully and then see
what kind of mess you made of Ubuntu. I am interested in what has happened report back in this thread.

---

### Post by wilee-nilee on 2010-06-26
Post the bootscript in my signature, in code tags as described. Use a linux Live cd to run the script, I wouldn't run any commands or load another bootloader until we see the script.

---

### Post by garvinrick4 on 2010-06-26
He is in a WUBI there wilee I was just trying to get his Windows running. He can worry about the ubuntu after he gets his machine running aqain. 
 Going to watch a movie b3crack, wilee-nilee can help you from here. Good luck, I will check back later to see how she worked out.

---

### Post by b3crack on 2010-06-26
Thats where the problem is!
I can't boot with Ubuntu CD even though I set optical drive as the first boot option.

I created Ubuntu CD by burning Ubuntu ISO as an image. I don't know whether I need to do anything to make it bootable!


Anyways, Thanks for the promptly reply

---

### Post by wilee-nilee on 2010-06-26
> **b3crack said:**
> Thats where the problem is!
I can't boot with Ubuntu CD even though I set optical drive as the first boot option.

I created Ubuntu CD by burning Ubuntu ISO as an image. I don't know whether I need to do anything to make it bootable!


Anyways, Thanks for the promptly reply

I realize your using wubi, your computer needs a key prompt to get to the boot from menu on mine it is f12. Do you know what I'm talking about and do you know the key prompt. 

It is highly unlikely that we can't get the cd to boot if it has worked before.

---

### Post by b3crack on 2010-06-26
I'm unable to use any function key other than F2(BIOS).

However, F8 is for boot menu options on my system.

Laptop Details:
===============

Sony Vaio VGN-N320E
About 3 yrs old.
OS: Windows 7 32-bit

---

### Post by wilee-nilee on 2010-06-26
> **b3crack said:**
> I'm unable to use any function key other than F2(BIOS).

However, F8 is for boot menu options on my system.

Laptop Details:
===============

Sony Vaio VGN-N320E
About 3 yrs old.
OS: Windows 7 32-bit
 The fix suggested may be what is used but it needs a cd to boot to run it. f8 is usually for a windows choice of safe boot and other options. There is another key prompt that is for a menu outside of the bios that is a boot menu. Does this make sense, it may be that the computer uses f8 but seems unlikely. try esc, and all the f keys to see if you get to a boot from menu that would be the HD, floppy,cd...etc, if you get to it use the arrow key to boot from a cd that you know will boot.

---

### Post by wilee-nilee on 2010-06-26
Okay I found the manual online it is the f11 key I believe, here is a link to the manual for your future needs.
[http://www.manualnguide.com/manual-get/8102/](http://www.manualnguide.com/manual-get/8102/)

---

### Post by b3crack on 2010-06-27
Thank you so much for correcting me.

Yes, It's the ESC key which got me to boot menu.
I inserted Ubuntu CD and started the system pressing ESC key, I got 2 options CD and HD. I selected CD and entered, it still shows "Missing OS"...

These are the contents in my CD at root:

*.disk, casper, dists, install, isolinux, pics, pool, preseed, autorun.inf, md5sum.txt, README.diskdefines, ubuntu, wubi.exe*

Hope the ISO I am using is correct one!

---

### Post by wilee-nilee on 2010-06-27
> **b3crack said:**
> Thank you so much for correcting me.

Yes, It's the ESC key which got me to boot menu.
I inserted Ubuntu CD and started the system pressing ESC key, I got 2 options CD and HD. I selected CD and entered, it still shows "Missing OS"...

These are the contents in my CD at root:

*.disk, casper, dists, install, isolinux, pics, pool, preseed, autorun.inf, md5sum.txt, README.diskdefines, ubuntu, wubi.exe*

Hope the ISO I am using is correct one!

Any Live Ubuntu cd will work is this one that you have used before to boot with? And I believe you were trying to load a thumb. Do you have another computer around that will confirm the cd boots or that you can get another ISO if needed and burn a cd at the slowest speed or load a thumb with unetbootin?

Funny The manual says f11 for a floppy boot maybe it's just for a floppy alone.

---

### Post by b3crack on 2010-06-27
Can you please suggest me any ISO image link. So that I burn iso freshly.

Also, when I try with unetbootin procedure with thumb drive I got 3rd boot menu option and if I select that I get this message

[I]Remove disks or other media
Press any key to restart[/I]

The message is still showing doing nothing!

---

### Post by wilee-nilee on 2010-06-27
> **b3crack said:**
> Can you please suggest me any ISO image link. So that I burn iso freshly.

Also, when I try with unetbootin procedure with thumb drive I got 3rd boot menu option and if I select that I get this message

[I]Remove disks or other media
Press any key to restart[/I]

The message is still showing doing nothing!

Here is a link to the Lucid download, just be sure to burn the cd as an image and at a slow speed 4x if possible. 
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Download the 32 or 64 bit whichever your computer is running.

Also did you pre-format the pendrive before loading with unetbootin?

---

### Post by wilee-nilee on 2010-06-27
Here is the Jaunty and lucid download as well.
[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

I'm just trying to give you multiple download options, I'm not sure if the 2 Lucid's are from the same sever probably not. I believe the Lucid's are the same basic downloads http address.

---

### Post by b3crack on 2010-06-27
I previously used to have Ubuntu 9.04 can I try with 10.04 now.
can I recover my data using new OS version?. Does root.disk in wubi has any issues with OS version?

Yes! I tried unetbootin with pre-formatted thumb drive.

---

### Post by wilee-nilee on 2010-06-27
> **b3crack said:**
> I previously used to have Ubuntu 9.04 can I try with 10.04 now.
can I recover my data using new OS version?. Does root.disk in wubi has any issues with OS version?

Yes! I tried unetbootin with pre-formatted thumb drive.

Either disc will work for lilo if that is needed, and the boot script. Also give me a link to the fdisk  method you were using, and the command. This makes me wonder if you haven't wiped the HD or repartitioned it accidentally. That is why I wanted to see what is still there with the bootscript. If there has been a corruption that will need a recovery other then from a live cd installing lilo to get in could have caused more problems, possibly. It is smarter to know the whole setup before just trying a method that may work in the best of circumstances.

If the data is still there yes you will be able to recover with the Live cd, either one as far as I know.

---

### Post by b3crack on 2010-06-27
Problem started when my thumb drive (I have 2) showing as write protected.
So I tried to format it with with gparted but could not format it.

Then i tried this:

sudo fdisk /dev/sdb1

I remember this as the last step I did.

---

### Post by wilee-nilee on 2010-06-27
> **b3crack said:**
> Problem started when my thumb drive (I have 2) showing as write protected.
So I tried to format it with with gparted but could not format it.

Then i tried this:

sudo fdisk /dev/sdb1

I remember this as the last step I did.

Alright thanks, just for future use maybe even in this process we will see, here is a W7 recovery disc link as well.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by b3crack on 2010-06-27
Hi,

I tried to boot with fresh Ubuntu CD (burnt at slowest possible speed) and with unetbootin thumb drive. But, still can't boot my system.

Do I need to add any boot files to Ubuntu ISO image to make it bootable?

I think problem is with ISO directly burning on CD.

---

### Post by wilee-nilee on 2010-06-27
> **b3crack said:**
> Hi,

I tried to boot with fresh Ubuntu CD (burnt at slowest possible speed) and with unetbootin thumb drive. But, still can't boot my system.

Do I need to add any boot files to Ubuntu ISO image to make it bootable?

I think problem is with ISO directly burning on CD.
 
The ISO is an image and is used all the time as it is. Maybe you need to try a cd that is made by another manufacturer, on occasion we see posts about one type not working, you need a cd-r for sure.

Check the ISO and the cd with a md5sum.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

As far as I know you have 3 choices here one boot with an linux cd to get in, two run the recovery with a key prompt as this computer probably has a recovery partition which will over write everything, three get the oem disc set which will overwrite everything. 

I'm not sure why the boot from a cd is not working. What OS are you using to burn the cd and what program?

Have you checked on the computer your downloading with if the cd boots there. You also might just call the manufacturer helpline and see if there is something missing, in the process to boot a cd.

The problem here is that your the one that has been using the computer, and has first hand knowledge of whats been done with it. On the forum we can only suggest a standard protocol. Unless the bios has been messed up or you have a hardware issue, a boot from a cd should happen. If you can take your computer to where you bought it or get somebody to look at it, in other words somebody that can get it to boot a cd, getting it fixed or getting stuff out is more difficult and will need somebody who can get in another way,  or knows how to instruct you how to.

---

### Post by b3crack on 2010-06-27
I installed and ran winMd5Sum...gave Ubuntu iso file location in the filename and gave 66fa77789c7b8ff63130e5d5a272d67b(source: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)) in the compare text box...Hit compare. It says "MD5 check Sums are Same"

Is this the right procedure to check ISO?

---

### Post by wilee-nilee on 2010-06-27
> **b3crack said:**
> I installed and ran winMd5Sum...gave Ubuntu iso file location in the filename and gave 66fa77789c7b8ff63130e5d5a272d67b(source: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)) in the compare text box...Hit compare. It says "MD5 check Sums are Same"

Is this the right procedure to check ISO?

I believe so if you look at the original link you can check the cd as well I believe. I wonder if it is the cd type or brand or this is a hardware or another issue.

---

### Post by wilee-nilee on 2010-06-27
> **b3crack said:**
> I installed and ran winMd5Sum...gave Ubuntu iso file location in the filename and gave 66fa77789c7b8ff63130e5d5a272d67b(source: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)) in the compare text box...Hit compare. It says "MD5 check Sums are Same"

Is this the right procedure to check ISO?

I believe so if you look at the original link you can check the cd as well I believe. I wonder if it is the cd type or brand or this is a hardware or another issue.

---

### Post by b3crack on 2010-06-27
I tried to mount Ubuntu iso and Win 7 repair disc iso in Daemon Tools Lite software to test the iso images. Well, I could get a pop-up window once I mount Win 7 (i.e, Win 7 iso is bootable) but its not the case with Ubuntu iso (i.e, its not bootable).

My conclusion is Ubuntu iso image is not bootable!
Where can I get a bootable Ubuntu iso file?

---

