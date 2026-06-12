---
title: "Copy install from 16gig USB to 2gig USB"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by balddogger on 2009-04-15
Long story, but I had to install Ubuntu MID on a 16gig thumb drive to compile a few drivers (i.e. Nvidia Graphics Driver).  Now that everything works on the 16gig thumb drive, i need to copy/install on a 2gig thumb drive.

I have tired a few things, but nothing seems to work.

1) liveusb - wants to be running from a livecd image (the 16gig is persistent with a ramdisk - as it shoud be :-) )
2) i don't think dd will work since i am going from a 16gig to a 2gig.

Any ideas?  What's the best way to do this?

Thanks in advance for the help!

---

### Post by tamas305 on 2009-04-15
From what I have noticed Ubuntu needs a little more than 2gb just to run. I have 8gb USB drive that is partitioned in this way...

  - 2gb fat32 (for windows)
  - 5gb ext3 (for Ubuntu)
  - .5gb swap (for Ubuntu)

However when I look at how much space is left on the 5gb portion it only shows 3.2 gb (when just barebones install, only applications that came packaged with Ubuntu). And since you want it to be persistent, I am expecting that you want to save files from Ubuntu. I would go with 4gb as the bare minimum. Use a slimmer OS such as Puppy Linux or Arch Linux.

-tamas

---

### Post by balddogger on 2009-04-15
Thanks for the reply, keep in mind that this is Ubuntu MID (Mobile Internet Device).

With all the "extra" packages I installed to build my drivers from source, I right @ 2gig.  

Guess what I'm saying is trimming down the install with MID to less than 2 gig will not be a problem :-).  THe problem is getting the complete install from the 6gig device to the onboard / built-in 2gig device.

---

### Post by tamas305 on 2009-04-15
I am not sure if just dragging and dropping would work in this situation but if Ubuntu recognises your 2gb as an external device you might be able to get it to do a full manual install onto that drive. I have tried to install Ubuntu onto 2gb flash drive before and it would not let me do it. If you are not able to free up more space I'll keep my recommendation for a slimmer Linux. I think I remember the installer saying the minimum amount of space you can achieve a successful full install on is 4gb. Other choice, if your MID has a SD slot than get a 8gb or larger one =D

-tamas

---

### Post by tamas305 on 2009-04-15
> **balddogger said:**
> Thanks for the reply, keep in mind that this is Ubuntu MID (Mobile Internet Device).

With all the "extra" packages I installed to build my drivers from source, I right @ 2gig.  

Guess what I'm saying is trimming down the install with MID to less than 2 gig will not be a problem :-).  THe problem is getting the complete install from the 6gig device to the onboard / built-in 2gig device.

I am kind of confused by your procedure. Since it is a mobile internet device after all could you not just install Ubuntu and then download the drivers using the MID?

-tamas

---

### Post by sgosnell on 2009-04-15
dd should work, as long as the size of the files on the 16GB drive is less than 2GB.  Of course, if you have more than 2GB of data on the larger drive, you're SOL.

---

### Post by balddogger on 2009-04-15
Ok, let's start over.  Thanks again for all the replies!!!

2 drives on the system.
/dev/sda -> 2gig -> on board, USB Flash
/dev/sdb -> 16gig -> usb thumb drive pluged into my usb port.

1) Installed Ubuntu MID on a 16gig thumb drive.
2) Downloaded & Built restricted drivers w/ nvidia installer.  
3) With all the build files needed for the nvidia installer, this pushed the install over 2gig - this is way I couldn't justs build / install on the 2 gig of onboard USB flash (/dev/sda)
[COLOR="Red"]4) Now, I just need to get the standard Ubuntu MID install w/ the built nvidia drivers onto the onboard 2gig of flash.[/COLOR]

I guess there are two approches.
1) Copy the needed files from the Nvidia graphics driver built for MID.
2) Install MID into the onboard 2gig flash.
3) Copy the files saved in step 1 onto the onboard 2gig flash.

The other approach
1) Trim current install on 16gig thumb drive down to less than 2gig.
2) Copy the files from 16gig to onboard 2gig drive.
3) Install bootloader/grub into mbr for /dev/sda.

Questions for approach 1.
1) What files are actually needed for Nvidia graphics driver.  I guess I would find this out with any package manger and see what files get installed???

Question for approach 2.
1) dd didn't work.  I didn't try puting a limit on it.  Just copied /dev/sdb to /dev/sda. 
2) can I just use a cc -R?  I can boot from a 3rd USB Live Image, then cp from 16gig to 2gig???

Any other ideas?  Looked into creating my own live image, or my own linux distro.  Looks like there are some restrictions since I need to include the Nvidia drivers.

Again, thanks for all the help!!!

---

### Post by balddogger on 2009-04-15
> **sgosnell said:**
> dd should work, as long as the size of the files on the 16GB drive is less than 2GB.  Of course, if you have more than 2GB of data on the larger drive, you're SOL.

it's under 2gig, but from what i understand, dd is a byte copy.  starting @ byte 0, going to byte 16gig.  There is no guarantee that the 16gig is contiguous

---

### Post by balddogger on 2009-04-15
> **tamas305 said:**
> I am kind of confused by your procedure. Since it is a mobile internet device after all could you not just install Ubuntu and then download the drivers using the MID?

-tamas

I could not find prebuilt restricted drivers (nvidia) for MID.  Uname returns something like "lapd".  So, if you added the restricted modules, apt-get looks for a folder like lapd and can't find it....

If you know have any other ideas, let me know!!!! - - I'm new @ this :-)

---

### Post by balddogger on 2009-04-15
> **tamas305 said:**
> I am not sure if just dragging and dropping would work in this situation but if Ubuntu recognises your 2gb as an external device you might be able to get it to do a full manual install onto that drive. I have tried to install Ubuntu onto 2gb flash drive before and it would not let me do it. If you are not able to free up more space I'll keep my recommendation for a slimmer Linux. I think I remember the installer saying the minimum amount of space you can achieve a successful full install on is 4gb. Other choice, if your MID has a SD slot than get a 8gb or larger one =D

-tamas

draging and droping between the two drives would work (i.e. manual install).  but what files do I need?  I don't even know where to start!!!!

---

### Post by tamas305 on 2009-04-15
I have never used the MID version of Ubuntu but I assume that it is marginally different than the desktop edition I am currently using. As for the 1st option, I believe the package manager will show what the needed drivers are so you can copy them as for 2nd option you would need "/" (it is can be found under Places within the File Browser on the left side). This is where everything that Ubuntu uses is located so I believe that it is safe to assume that it will work once you have copied those files. Those Nvidia drivers are most likely in there also.

Good luck,
-tamas

Just curious what MID is it?

---

### Post by balddogger on 2009-04-15
> **tamas305 said:**
> I have never used the MID version of Ubuntu but I assume that it is marginally different than the desktop edition I am currently using. As for the 1st option, I believe the package manager will show what the needed drivers are so you can copy them as for 2nd option you would need "/" (it is can be found under Places within the File Browser on the left side). This is where everything that Ubuntu uses is located so I believe that it is safe to assume that it will work once you have copied those files. Those Nvidia drivers are most likely in there also.

Good luck,
-tamas

Just curious what MID is it?

Yeah, I am assuming that there is extra stuff under root ("/") that I do not need.  (for example, tmp, usr/src, etc).  

As for MID, it's just a stripped down version of Ubuntu Desktop Edition w/ a different window manager.

Thanks again for you input!!!
[http://www.ubuntu.com/products/mobile](http://www.ubuntu.com/products/mobile)

---

### Post by tamas305 on 2009-04-15
> **balddogger said:**
> Yeah, I am assuming that there is extra stuff under root ("/") that I do not need.  (for example, tmp, usr/src, etc).  

As for MID, it's just a stripped down version of Ubuntu Desktop Edition w/ a different window manager.

Thanks again for you input!!!
[http://www.ubuntu.com/products/mobile](http://www.ubuntu.com/products/mobile)

Your Welcome!

However, I would be extremely careful when deleting things from the "/" as many of Ubuntu's files are spread across multiple files. I would try to delete useless programs first (Applications --> Add/Remove...) but if you are that limited on space I would ask someone who is experienced in mobile Linux before deleting it. Also I was wondering what device not operating system. lol

-tamas

---

### Post by balddogger on 2009-04-15
> **tamas305 said:**
> Your Welcome!

However, I would be extremely careful when deleting things from the "/" as many of Ubuntu's files are spread across multiple files. I would try to delete useless programs first (Applications --> Add/Remove...) but if you are that limited on space I would ask someone who is experienced in mobile Linux before deleting it. Also I was wondering what device not operating system. lol

-tamas

Yeah, I would use the package manager to remove files.  No worries there, just haven't done it yet.  

Mobile device - - LOL, It's some custom hardware.  Intel Core 2 Duo, 4 GB DDR2, Nvidia G73M, 40+watts, not really mobile! I'm using it to demo some custom software that uses the Nvidia G73M GPU for some number crunching.  It would be nice if I didn't have that thumb drive sticking out for my demo :-)

---

### Post by tamas305 on 2009-04-15
> **balddogger said:**
> Yeah, I would use the package manager to remove files.  No worries there, just haven't done it yet.  

Mobile device - - LOL, It's some custom hardware.  Intel Core 2 Duo, 4 GB DDR2, Nvidia G73M, 40+watts, not really mobile! I'm using it to demo some custom software that uses the Nvidia G73M GPU for some number crunching.  It would be nice if I didn't have that thumb drive sticking out for my demo :-)

True, very true. Doesn't exactly sound like a mobile device...so why the thumb drive? Or do you not have enough space for a hard drive?

-tamas

---

### Post by balddogger on 2009-04-15
> **tamas305 said:**
> True, very true. Doesn't exactly sound like a mobile device...so why the thumb drive? Or do you not have enough space for a hard drive?

-tamas

Just trying to make it as small as possible.  I am using the 16gig thumb drive as a temp work-a-round.  The 2gig is actaully on the board itself  (soldered down).

I do have a SATA port, but then I would have to put it outside of my chassis. This would be my last resort.  The 16gig thumb drive w/ a RAM disk running on the 1.5GHz Dual Core2 Duo is more than fast enough :-)

---

### Post by tamas305 on 2009-04-15
If you are adamant about using only those 2 gb than I recommend a slimmer disto. For example puppy linux because it is absolutely tiny and arch linux because it is small and extremely customisable. However, the drawback of arch linux is that it has a steep learning curve, which I have yet to reach. Recommending other distros on an ubuntu forum is heresy but 2gb can be considered heresy also =D Is there a specific reason you are so attached to Ubuntu?

-tamas

---

### Post by balddogger on 2009-04-15
> **tamas305 said:**
> If you are adamant about using only those 2 gb than I recommend a slimmer disto. For example puppy linux because it is absolutely tiny and arch linux because it is small and extremely customisable. However, the drawback of arch linux is that it has a steep learning curve, which I have yet to reach. Recommending other distros on an ubuntu forum is heresy but 2gb can be considered heresy also =D Is there a specific reason you are so attached to Ubuntu?

-tamas

The software I need to demo was devleped on Ubuntu Desktop 8.10.  So, I'm sticking with that :-)

MID is the right size, just needed to complie the nvidia drivers.

---

### Post by tamas305 on 2009-04-15
Makes since, so good luck with your demo 

-tamas

---

