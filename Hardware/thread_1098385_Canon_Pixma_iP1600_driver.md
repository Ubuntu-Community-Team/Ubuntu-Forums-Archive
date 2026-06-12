---
title: "Canon Pixma iP1600 driver"
date: 2009-03-17
forum: Hardware
---

### Post by tanusgreystar on 2009-03-17
Hi. I'm going crazy! I'm new to Linux. I installed Ubuntu, and it recognizes my printer in System/admin/printing. It's there, but it won't print. I downloaded a driver, not the exact one but one that supposedly works, but I'm having a hard time installing it. I have it on my desktop. It's a rpm file and I had to install 7zip to be able to open it, but I don't know what else to do. I tried to use the terminal but it says the file doesn't exist. Any help would be appreciated. Thanks!

---

### Post by rsambuca on 2009-03-17
You need to install the canon ip2200 driver.  It will not work on a 64-bit system, though.

---

### Post by tanusgreystar on 2009-03-18
I do have the driver file on my desktop. The folder is called ip2200_Linux_260.tar.gz   Inside the folder are :

cnijfilter-common-2.60-1.i386.rpm
cnijfilter-common-2.60-1.src.rpm
cnijfilter-ip2200-2.60-1.i386.rpm
cnijfilter-ip2200-lprng-2.60-1.i386.rpm

not sure what to type in terminal to install. I typed in something I found online but it didn't work. Please help!:guitar:

---

### Post by rsambuca on 2009-03-18
Try the instructions in this post here.  If that doesn't work, let us know and we can probably figure it out.

[http://ubuntuforums.org/showpost.php?p=6276893&postcount=1](http://ubuntuforums.org/showpost.php?p=6276893&postcount=1)

---

### Post by tanusgreystar on 2009-03-18
Thanks I'll try it.:popcorn:

---

### Post by tanusgreystar on 2009-03-20
Everything works until I enter this command:

sudo /etc/init.d/cupsys restart

it keeps saying Command Not Found. Everything else went through provided I don't mispell anything!

---

### Post by rsambuca on 2009-03-22
> **tanusgreystar said:**
> Everything works until I enter this command:

sudo /etc/init.d/cupsys restart

it keeps saying Command Not Found. Everything else went through provided I don't mispell anything!

Very strange.  Are you running Ubuntu or Kubuntu, and which version?

---

### Post by Matsukaze on 2009-03-22
> **tanusgreystar said:**
> Everything works until I enter this command:

sudo /etc/init.d/cupsys restart

Try cups restart instead of cupsys. Apparently this command has been changed in Ubuntu 8.10.

---

### Post by tanusgreystar on 2009-03-23
> **rsambuca said:**
> Very strange.  Are you running Ubuntu or Kubuntu, and which version?

Ubuntu 8.10

---

### Post by tanusgreystar on 2009-03-23
> **Matsukaze said:**
> Try cups restart instead of cupsys. Apparently this command has been changed in Ubuntu 8.10.

ok I'll try that

---

### Post by tanusgreystar on 2009-03-24
The cups command worked, but the printer still doesn't work. I got a message when I typed: sudo alien cnijfilter-ip2200-2.60-1.i386.rpm
It said:
 Warning: skipping conversion of scripts in  package cnijfilter-ip2200: post inst p ostrm

Warning: use the --scripts parameter to include the scripts

---

### Post by mocoloco on 2009-03-24
Cups will also restart if you just reboot, if that's any easier.

---

### Post by tanusgreystar on 2009-03-24
> **mocoloco said:**
> Cups will also restart if you just reboot, if that's any easier.

cups worked but still no printer

---

### Post by rsambuca on 2009-03-24
The script error from the rpm to deb conversion is likely the problem.  Are you using 32 bit or 64 bit Ubuntu?

---

### Post by tanusgreystar on 2009-03-24
> **rsambuca said:**
> The script error from the rpm to deb conversion is likely the problem.  Are you using 32 bit or 64 bit Ubuntu?

32 bit

---

### Post by tanusgreystar on 2009-03-28
How do I fix this??

---

### Post by tanusgreystar on 2009-04-01
??

---

### Post by mocoloco on 2009-04-02
Now that the driver is installed, can you set up a new printer and select that driver?  What happens when you do that?

---

### Post by rsambuca on 2009-04-02
Hey tanus, I don't have Ubuntu on my PC with the Canon printer right now, but if you can wait until after the weekend, I'll install Ubuntu on an empty partition and figure out the printer stuff.

---

### Post by tanusgreystar on 2009-04-02
> **mocoloco said:**
> Now that the driver is installed, can you set up a new printer and select that driver?  What happens when you do that?

it installs, but when you go to print test page it doesn't do anything. I did the troubleshooting thing and it said it couldn't help me. I have the log it created on my desktop. Also I was messing around with wine and attempted to launch ip1600xp190dejz.exe and it started to install, but I got a message saying there was something wrong with the print spooler??

---

### Post by lowell112 on 2009-04-14
I followed all the instructions above and everything went fine, except i also can not print still.  The debugger showed nothing, but the first time i tried to print I got this message:

"pstocanonij write error"

I can't get that message to come up again though, tried doing some research but got nothing.  Pls and ty for any help?  Also, if I were running 64 bit would this be any easier?

---

