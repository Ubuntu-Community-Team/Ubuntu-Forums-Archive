---
title: "no grub installed"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by kevein on 2009-05-26
Hi every body,

I have a computer included windows xp, and Fedora core 10, I have removed fedora and installed ubuntu 9.04 the last version on my internal HDD and after installation comploted it seems that there is no grub installed, I tried many times to delete my partions and reinstall ubuntu but it's same problem happens each time.
while I am trying to grub-install /dev/hda using live CD it shows me an error message each time.
and i got a grub error message
GRUB> while starting up, so I can't access any operatin system.

Hope to solve my problem and thanks for every body

---

### Post by Lampi on 2009-05-26
> **kevein said:**
> 
while I am trying to grub-install /dev/hda using live CD it shows me an error message each time.
are you sure it is hda? mine is always sda, I guess it depends how old this drive is (pata or sata connector)

you can check this with cat /proc/partitons - this should show you the recognized partitions, so you get the "name" of your disk like that.

---

### Post by ronparent on 2009-05-26
From a live cd session use the terminal to enter **sudo grun**. From the grub prompt enter **>find /boot/grub/stage1**. The ouput of this last command should give you the location of grub in grub terms (ie (hd1,0) ). Ther will be more than one if more than one installation is found. Pick the one you want to boot to and enter **>root (hdx,y)** (x and y being numbers). Then enter **setup (hdx)**. Grub should now be written properly to the mbr and you shold be able to boot to grub with your chosen installation of ubuntu being your first boot choice. If that doesn't do it then something else is amiss that will have to be chasen down. Good luck.

---

### Post by kevein on 2009-05-26
Hi every body,
Thank you **[COLOR=Red]Lampi[/COLOR]** to try to help my in this.

[COLOR=Red]**ronparent**[/COLOR] I did every thing you said and every thing was successful but no grub installed.
I don't know what is going on, there is some thing wrong, Thanks dear.

---

### Post by ronparent on 2009-05-26
Run the script from the following site:

[http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055)

Hopefully it will give us a better picture of what is at work here.

---

### Post by kevein on 2009-05-27
I will do it after going home
thanks

---

### Post by kevein on 2009-05-27
It's not ok any didn't fixed the problem
thanks
---------------------------------------------------------------
When I am using sudo gurb command I got this >

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,4)
grub> root (hd0,4)
root (hd0,4)
grub> setup (hd0,4)
setup (hd0,4)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,4)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,4)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,4) /boot/grub/stage2 p /boot/grub/menu.lst "... succeeded
Done.
grub> quit
quit

---

### Post by zubin71 on 2009-05-27
do you get the grub at boot time?
is that when you select an O.S. it refuses to boot up?
Currently which are the O.S.`s in your system?

please try the following:-

$ sudo dd of=/dev/sda if=/dev/zero bs=1 count=448

what this command does is write the first 448 bytes of your harddisk with zero`s. in effect, the existing grub is removed. then try the above procedure again. this should work.
if it does not please explain what`s happening in detail.

---

### Post by ronparent on 2009-05-27
I should have said post the output of the script here. It won't fix anything, only tell whomever read the script what your setup is and hopefully how to fix your boot problems.

---

### Post by kevein on 2009-05-28
Hello every body,
I am thanking every body was trying to help me.

Actually problem was in the internal IDE HDD if I remove it it and keep SATA HDD it works O.k. with the Grub installed by default, so I did that.

Thanks again.

---

### Post by presence1960 on 2009-05-28
> **kevein said:**
> Hello every body,
I am thanking every body was trying to help me.

Actually problem was in the internal IDE HDD if I remove it it and keep SATA HDD it works O.k. with the Grub installed by default, so I did that.

Thanks again.

You probably dont need to remove your IDE drive, sounds like if you go into BIOS and set your SATA drive as first to boot in the device boot order you will be fine. If you had posted the results file of the script ronparent asked you to post we would have seen you have 2 HDDs and probably got it to work without opening your box and removing any hardware.

---

### Post by kevein on 2009-05-29
Hi presence1960,
Just it was a test because I got headache from the problem I have removed it, Start my machine and got grub which it was installed by default the shut it down the reconnect the hard disk without any configuration and got fine result.

Thanking you and every body.

---

