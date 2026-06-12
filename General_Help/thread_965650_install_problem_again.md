---
title: "install problem again"
date: 2008-10-31
forum: General Help
---

### Post by cmay on 2008-10-31
i cant use ubuntu no more..
```
he installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.
```since 7.4.0 the installer did this to me. i upgraded from the net last time since all my cd will do this. last time a release went out i spend 7 cd to burn it and i bought a copy from a online store that sells ubuntu cd but same result. i can burn open-solaris and debian and netbesd and whatever whitout problems but not ubuntu. so i have to quit now. i have no more possible way of using ubuntu until this installer is fixed. it has got to be the installer after all logic . this time i already used two cd but i cant afford this. i know from last time it is not the burned cd that is wrong. it also runs fine live. is is really annoying and i have no launch pad account so i can simply file bug report about. the problem. 

have any others the same problems.???

---

### Post by Idefix82 on 2008-10-31
You could try installing Ubuntu from a USB drive.

To get a Launchpad account will take you five minutes, so it's not a good reason not to file a bug.

---

### Post by cmay on 2008-10-31
thanks for the reply. how do i go about this usb install. i would hate not having uibuntu no more.
i have had it since 6.8.0 i think. i use debian and all other nix but i use ubuntu for my internet usage mostly and its good at finding printers whitout a problem. so i would love to have this fixed somehow. i am going to try to take screenshot and post this as bugreport somehow. maybe it is the mirrors in denmark that are messed up both of them but to happen with two releases i do not think is likely. 
is it a known problem whit the installer i just not read about.

---

### Post by Idefix82 on 2008-11-01
Here is a guide for installing from usb:
[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

I have not heard about this problem but it does sound annoying!

---

### Post by cmay on 2008-11-01
thanks. i am trying one more time just trying to download the alternative installer right now. i may quit using ubuntu if it does not work. i use debian also so its no biggie but i will really really miss ubuntu .

---

### Post by dci-Japan on 2008-11-05
Installing Ubuntu 8.10 [Errno 5] My Success Story

My solution to [Errno 5] on Ubuntu install was to remove some RAM modules.

I had great trouble installing 8.10 to my computer (model: HP d330). It took me three days and countless hours researching around the internet. Here is my success story.

I downloaded the ISO and attempted to install from the Live CD. The following error appeared at about 24% of install process:

[Errno 5] Input/output error

This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.

1. Attempted reburn CD-R at slower speed. Same error.
2. Attempted install with "Alternate CD". Same problem (it froze up somewhere in "copy files to disk" process).
3. Attempted boot from Live CD and double click "Install". NO GO. Wouldn't even start process.
4. Repeated all the above in various ways. Same results.
5. Tried changing the various choices under F6 on boot-up. Freeze or same error. 
6. Live CD then begin to hang on boot from CD. Couldn't get anything to do anything.
7. Attempted to install from Flash card (using separate PC to set it up). Booted fine, but same error on install.
8. Attempted many solutions offered on various forums online. Still no luck.
9. Tried noapic options and others to no avail.
10. Tried repartitioning hard drive, and wiping hard drive and etc. etc. etc.
11.Gave up and installed Windows XP. Hated it (as usual). Waited several hours. Kept repeating all the above plus anything I could think of. Redownload ISO. Burn at slower speeds. Try Alternate CD. Try Flash card again. NO LUCK. Fiddle with various settings again.

And then I used the little grey cells in my head (as Poirot would say in an Agatha Christie novel). I remembered someone somewhere suggested RAM error as the culprit. I ran the memory test without a problem (that took many hours!), but still I was supicious about the memory. My PC has four memory slots but with 3 actually memory sticks. 256Mb (original memory stick that came with computer) + 1Gb (cheap no brand stick added later) + 1GB (another added no brand stick). I simply took out the two 1Gb stick and left only the original 256Mb stick and attempted an install. Bang! It worked. No error. No problem (except it was as slow as molassis to install...). After the successful install, I replaced the 2Gb of memory and rebooted. Everything worked out. RAM modules might be faulty but everything seems fine.

I'm not sure if this solution will help everyone. The cause of [Errno 5] might be different for each machine, and sometimes just trying a million attempts leads to an eventual success. But in my case, removing most of the RAM solved the problem. 

Finally I can get on with enjoying Ubuntu 8.10.

---

### Post by cmay on 2008-11-08
woohooo
i got it installed.
i find it very hard to believe that all the images i downloaded was corrupt since i checked it and burned it on media that was ok quality but this time i had four disk that did not work before i  got a disk that worked. i used a mirror other than denmark and it solved it. hehe.
8.10 is by far the most cool ubuntu version i have had up to now. 
and i got the desktop cube also :)
oh joy, oh great happiness.
its feels great to be a ubuntu user.

@dci-Japan
oh and thanks for the tips

---

