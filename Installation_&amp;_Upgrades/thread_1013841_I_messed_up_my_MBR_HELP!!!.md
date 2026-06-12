---
title: "I messed up my MBR HELP!!!"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by rockie12 on 2008-12-17
Hi I hope someone can help me.  I have a toshiba notebook which was dual booting fine into Ubuntu 7.10 and windows XP.  I have an external notebook usb harddrive caddy and wanted to install 8.10 on it.  So I did and when it came time to tell it where to put the MBR, I did not click advanced... so it put it somewhere.  Then when it was done, I removed the usb drive and my dualboot notebook gave me a grub error 21.  Then it dawned on me that I did not tell it to put GRUB in the external drive and not mess with my internal drive, but now it is too late.  

I tried the install again and told it to put the GRUB loader on the external drive, that did not work... then I did the install again and said to put it on the internal drive... and now I can only boot this box if I have the external drive and the usb flash drive that I installed ubuntu 8.10 from in their appropriate usb ports.

How can I fix the MBR on the internal drive to only show the windows and ubuntu 7.10 like I had before starting this mess?

Thanks in advance
Dean-O

---

### Post by lovelyvik293 on 2008-12-17
To install the MBR again put the windows cd and go to the recovery consol and use the commands
```

fixmbr
fixboot

```
And then install the GRUB with live cd.

---

### Post by lovelyvik293 on 2008-12-17
After installing the MBR your grub does not woks so you have to install the grub again.

---

### Post by caljohnsmith on 2008-12-17
If you don't have your Windows Install CD, you can restore a Windows MBR to your Windows drive from the Ubuntu Live CD. If you boot your Live CD, open a terminal (Applications > Accessories > Terminal) and run:
```
sudo lilo -M  /dev/sda mbr
```
That will write a Windows equivalent MBR to your sda drive. After that, you should be able to boot straight into Windows again if you boot your Windows drive on start up. To boot Ubuntu you will have to change your BIOS to boot your external USB drive first. That should work assuming you have Grub properly installed to the MBR of the USB drive. Let us know how it goes or if you run into problems.

---

### Post by rockie12 on 2008-12-17
Hi all

Thanks for the replies... my goal is to get my dual booting working again... not to just boot into windows.  I had dual booting working on the notebook before I went to install 8.10 on an external usb drive... that is when things went south...

So if I want to get my notebook back to being able to dual boot windows and ubuntu 7.10... how do I do that?  I do not want to boot the usb drive on this notebook.

If that was already stated and I missed it... I please restate it... I am a newbie here and love my dual boot world... I miss it terribly :)

Thanks
Dean-O

---

### Post by caljohnsmith on 2008-12-17
In order to get a clearer picture of your setup, how about downloading the attached "boot_info9.txt" file to your desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo sh ~/Desktop/boot_info9.txt
```
That will create a "BootInfo.txt" file on your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup in order to know what might be the best way to set up your dual boot.

---

### Post by rockie12 on 2008-12-17
Hi I tried your boot_info9.txt file and I get the following error

 80: arith: syntax error: "i+1"

---

### Post by caljohnsmith on 2008-12-17
That's strange, the script has never had a problem like that before. How about trying again with the newly attached "boot_info9_modified.txt" file:
```
sudo sh ~/Desktop/boot_info9_modified.txt
```

---

### Post by rockie12 on 2008-12-17
That worked, but it created an empty file

---

### Post by caljohnsmith on 2008-12-17
OK, how about instead posting the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo xxd  -l  2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
So replace "sda" above with each of your drives. Note "-l" is a lowercase L, not a one. And finally, for each command above that returns "eb48", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
And replace sda with the drives that previously returned "eb48". That will help clarify what your setup is like.

---

### Post by rockie12 on 2008-12-17
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf932f932

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   103137299    51568618+   7  HPFS/NTFS
/dev/sda2       103137300   153999089    25430895   83  Linux
/dev/sda3       153999090   156296384     1148647+   5  Extended
/dev/sda5       153999153   156296384     1148616   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x97509750

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    74846834    37423386   83  Linux
/dev/sdb2        74846835    78140159     1646662+   5  Extended
/dev/sdb5        74846898    78140159     1646631   82  Linux swap / Solaris

Disk /dev/sdc: 2038 MB, 2038431744 bytes
251 heads, 62 sectors/track, 255 cylinders, total 3981312 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          62     1478389      739164    6  FAT16
/dev/sdc2         1478390     3968309     1244960   83  Linux

---

### Post by rockie12 on 2008-12-17
sudo xxd -l 2 -p /dev/sda
eb48

sudo xxd -l 2 -p /dev/sdb
33c0


sudo xxd -l 2 -p /dev/sdc
faeb

---

### Post by rockie12 on 2008-12-17
sudo xxd -s 1049 -l 2 -p /dev/sda
0082

---

### Post by caljohnsmith on 2008-12-17
OK, first to restore your dual boot between Windows and 7.10, and also to install Grub to your 8.10 drive, try the following:
```
sudo grub
grub> root (hd0,1)
grub> setup (hd0)
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
Please post the output of all the above commands, reboot, and you should get your old 7.10 Grub menu allowing you to boot Windows/7.10. Then if you can set your BIOS to boot your 8.10 drive, you should be able to boot 8.10. Let me know how it goes or if you run into problems.

---

### Post by rockie12 on 2008-12-17
ok I entered those commands and they seemed to work... meaning I did not get any errors.  So now I should be able to shutdown my notebook.  Disconnect any external drives... cross my fingers and it should book like it id before with the windows/7.10?

Then if I shutdown and attach my external drive with 8.10 on it, start up the notebook go to the menu to choose which HDD to boot from, I should be able to boot from the external drive?

Just checking before I shutdown and disconnect stuff.

---

### Post by caljohnsmith on 2008-12-17
> **rockie12 said:**
> ok I entered those commands and they seemed to work... meaning I did not get any errors.  So now I should be able to shutdown my notebook.  Disconnect any external drives... cross my fingers and it should book like it id before with the windows/7.10?

Then if I shutdown and attach my external drive with 8.10 on it, start up the notebook go to the menu to choose which HDD to boot from, I should be able to boot from the external drive?

Just checking before I shutdown and disconnect stuff.
Yes to all your questions; let me know how it goes. :)

---

### Post by rockie12 on 2008-12-17
:guitar:

Dude!!!! You Rock!!!!  Take the rest of the day off with pay :)

Thanks Big time!!!

---

### Post by meierfra. on 2008-12-17
rockie12:  I'm the person who wrote the script "boot_info9.sh". Since I have no idea why it did not work for you, could you help me debugging it?

Could you run  both scripts again and  then  post the output of

```
ls -l /tmp
cat /tmp/BootFiles0/Error_Log
cat /tmp/BootFiles/Error_Log
```

Thanks

---

### Post by caljohnsmith on 2008-12-17
> **rockie12 said:**
> :guitar:

Dude!!!! You Rock!!!!  Take the rest of the day off with pay :)

Thanks Big time!!!
Glad to hear that did the trick; if you have a little time, it would be great if you could help out both meierfra and me by posting the info that meierfra asked for, because we both would like to know why the script failed to run on your setup. If you don't have time though, that's fine. :)

---

### Post by rockie12 on 2008-12-18
Sure thing... how do I do that?  Where is the URL to do that?

Dean-O

---

### Post by caljohnsmith on 2008-12-18
Thanks for helping us out, how about first trying meierfra's latest script by doing:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo sh ./boot_info_script.txt
```
And post the contents of the boot_info_results.txt file on your desktop if the script above works. If you get an error again, please let us know what it is and also post:
```
ls -l /tmp /tmp/Boot*
cat /tmp/Boot*/Error_Log
```
And I'm sure meierfra will be around soon to ask for any additional info he needs for troubleshooting the script.

---

### Post by rockie12 on 2008-12-18
The second script that was attached to the thread was able to run and allowed me to create the files.  I then pasted the contents of those files into this thread... then I was instructed to do the steps listed above to set up grub on hd0 and hd1

That is what fixed it.

---

### Post by meierfra. on 2008-12-18
rockie 12,  I figured out why the script was not working for you. The command "sh" behaves differently in Ubuntu 8.10 than in some of the earlier versions of  Ubuntu.   To succesfully run the scripts you downloaded one has   to use "bash" instead of "sh.

Thanks for you input.

---

### Post by rockie12 on 2008-12-19
I was able to run the second script with sh just fine... no error on the math line 80 where it had x + 1 line

---

