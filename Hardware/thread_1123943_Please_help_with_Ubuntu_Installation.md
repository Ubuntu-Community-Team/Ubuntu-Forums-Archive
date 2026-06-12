---
title: "Please help with Ubuntu Installation"
date: 2009-04-12
forum: Hardware
---

### Post by haaagmatthew on 2009-04-12
Please help me,

I'm running on a 64 bit Vista Sony Vaio VGN-FW290 Laptop.

I have made numerous installation disks, and they all boot up fine...
The problem is that it doesn't run or install,
the screen becomes multicolored and then doesn't do anything.

The discs I have made are all 64 bit.

I HAVE NOT installed any drivers.
Sorry Really new to Linux.

Please help...Thanks

---

### Post by taurus on 2009-04-12
1.  Did you run the checksum to check the integrity of the ISO image after you've downloaded it?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2.  Did you burn it at a slow speed like 4x if possible?

3.  Did you run the check cd for defects at the initial screen when you boot from the CD?

4.  Press F4 to boot with safe graphics mode after you have check the cd for defects.

---

### Post by haaagmatthew on 2009-04-12
> **taurus said:**
> 1.  Did you run the checksum to check the integrity of the ISO image after you've downloaded it?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2.  Did you burn it at a slow speed like 4x if possible?

3.  Did you run the check cd for defects at the initial screen when you boot from the CD?

4.  Press F4 to boot with safe graphics mode after you have check the cd for defects.

I booted with F4 and now it is working!!!
Can I install now, and when I'm installing, I need help with partitioning. :-D

---

### Post by nathansoz on 2009-04-12
When you partition are you going to want to keep vista? If not, there should be an option to just wipe the whole drive and use it all for ubuntu. If you want to keep vista I think that there is an option to have them run side by side and you can resize..... but I don't remember because I just chose the first option. No vista for me! ;)

---

### Post by taurus on 2009-04-12
Do you have a separate partition/space to install Ubuntu on?  Or do you plan to resize your harddrive during the installing process?

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by haaagmatthew on 2009-04-12
> **taurus said:**
> Do you have a separate partition/space to install Ubuntu on?  Or do you plan to resize your harddrive during the installing process?

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

I want to Dual Boot.

When I pick guided, it allows me to go forward, but then the next step doesn't work.  Sorry I'm annoying you guys but I'm very new to Linux.  Basically the Partitioning isn't working.
Please give me specific directions if possible.

Also, since I'm booting in Safe Mode, after I install, will it work normally?

---

### Post by raymondh on 2009-04-12
> **haaagmatthew said:**
> I need help with partitioning. :-D

What are your intentions?

You can dual boot where you choose guided resize and allocate space for ubuntu.

You can have solely ubuntu where you choose "use entire disk"

As a sub-choice, you can also have / separate from /home (where you have your home partition -aka documents in windows- separate from the OS.  That way you can re-do/change/rework the OS whilst having your files intact.  If that is the case, you can choose Manual.

There are a lot of reads.  I used this a lot.  Hope it helps.  Good luck and enjoy the learnings.

[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

Raymond

I forgot :  try to make a back-up before touching your hard disk.

---

### Post by Agent.Logic_ on 2009-04-12
Hi haaagmatthew,

You might want to check out [this article](http://www.psychocats.net/ubuntu/partitioning) which explains different strategies for partitioning your hard drive. It is very down to earth and does not contain a lot of mumbo jumbo. ;)

---

### Post by raymondh on 2009-04-12
> **haaagmatthew said:**
> I want to Dual Boot.

When I pick guided, it allows me to go forward, but then the next step doesn't work.  Sorry I'm annoying you guys but I'm very new to Linux.  Basically the Partitioning isn't working.
Please give me specific directions if possible.

Also, since I'm booting in Safe Mode, after I install, will it work normally?

Is the CD with NO DEFECTS?

There was a time when I had problems installing Ubuntu (guided resize).  One forum member asked me to stop installation for a minute, boot into vista and defrag twice.  After that, I then backed-up all my Vista files then tried the installation again which went well .... of course CD had no defects and I burned the iso at 4x ....  Since then, all my installs with windows dual boots involve a defrag.

Nevertheless, are you able to use the liveCD and post a screenshot?  If so, can you boot into live CD then go system > administrative > partition editor.  That will pull up gparted and show your actual hard disk.  Then, go to applications > accessories > take a screenshot.  That will allow you to post that screenshot here so we may see what your disk looks like.
I say this because maybe you have 3 partitions already and ubuntu requires 2.  There is a 4 primary partition limit....so if this is tru, we may have to do manual.  Let's see what the screenshot shows.

---

### Post by haaagmatthew on 2009-04-12
> **raymondhenson said:**
> Is the CD with NO DEFECTS?

There was a time when I had problems installing Ubuntu (guided resize).  One forum member asked me to stop installation for a minute, boot into vista and defrag twice.  After that, I then backed-up all my Vista files then tried the installation again which went well .... of course CD had no defects and I burned the iso at 4x ....  Since then, all my installs with windows dual boots involve a defrag.

Nevertheless, are you able to use the liveCD and post a screenshot?  If so, can you boot into live CD then go system > administrative > partition editor.  That will pull up gparted and show your actual hard disk.  Then, go to applications > accessories > take a screenshot.  That will allow you to post that screenshot here so we may see what your disk looks like.
I say this because maybe you have 3 partitions already and ubuntu requires 2.  There is a 4 primary partition limit....so if this is tru, we may have to do manual.  Let's see what the screenshot shows.


The disk has no deffects, I've checked almost everything.
I'm Defragmenting now.
I'm not sure how this is going to work, because I still can't boot up without being in safe mode.
If I don't go into safe mode, after Ubuntu is done loading and everything after I click install or try running off disk, it just becomes multicolored and turns white.
For the record though, I can hear the load up music.

PLEASE HELP.

---

### Post by haaagmatthew on 2009-04-12
Bump....
My installation and booting problem has not gone away.

---

### Post by raymondh on 2009-04-13
> **haaagmatthew said:**
> Bump....
My installation and booting problem has not gone away.

Look at this thread ... are you having a similar problem?

[http://ubuntuforums.org/showthread.php?t=1122624&page=2](http://ubuntuforums.org/showthread.php?t=1122624&page=2)

---

### Post by haaagmatthew on 2009-04-13
> **raymondhenson said:**
> Look at this thread ... are you having a similar problem?

[http://ubuntuforums.org/showthread.php?t=1122624&page=2](http://ubuntuforums.org/showthread.php?t=1122624&page=2)

No, I'm still having trouble getting to that screen itself.
I can only boot up in safe mode.
But if I boot up using a VM, it works fine.

---

### Post by raymondh on 2009-04-13
Sorry for the delay.  had to get sleep for an early work today.

Haagmathew, I googled you're dilemna and found some interesting ubuntu threads with regards to Ubuntu and Sony.  Have a read while we research some more as I am stumped, but not giving up :

[http://ubuntuforums.org/showthread.php?t=481577&highlight=Sony+VIAO+VGN](http://ubuntuforums.org/showthread.php?t=481577&highlight=Sony+VIAO+VGN)
[http://ubuntuforums.org/showthread.php?t=687482&page=2](http://ubuntuforums.org/showthread.php?t=687482&page=2)
[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/sony-says-sony-viao-laptops-cant-dual-boot-is-that-really-true-706330/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/sony-says-sony-viao-laptops-cant-dual-boot-is-that-really-true-706330/)

A fiend of mine suggested to try an alternate install (this is the TEXT only install).  I've never done it as all my installs and re-installs (about 11 total) have been auto or manual from the live CD.  You may want to investigate this.

Is there any way we can take a peek at your HDD partitions?  If you can't use the Ubuntu liveCD, you can use Vista's disk manager .... controlpanel>administartive>security>partition hard drive.  Maybe you can take a picture and post here or, copy down exactly what you see.

If you click manual (in partitioning), do you have the option to go FORWARD?  Don't worry, you may quit the install anytime before the final "apply".  Likewise, in "use full disk"?  If I understand your posts, is it only on "guided resize" that you can't go "forward"????

Raymond

---

