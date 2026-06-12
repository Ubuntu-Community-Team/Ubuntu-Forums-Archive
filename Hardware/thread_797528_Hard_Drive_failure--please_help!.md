---
title: "Hard Drive failure--please help!"
date: 2008-05-17
forum: Hardware
---

### Post by tamirtoad on 2008-05-17
Okay so here is the story.

I have an 80gb hard drive which always spins up on startup and which has a single ext3 partition on it. Maybe a month or two back, when my laptop (a sony vaio vgn-fs550) would start to boot up, it would give me the 'Operating System Not Found' error. I could solve this by simply pressing the power button, shutting down the laptop, and starting it back up. Doing this a few times would eventually get it to load GRUB, and I'd get into ubuntu. Now, the same thing happened yesterday, except that turning it on and off for like two hours did nothing for me. 

Here are the things that I have tried:

1) A friend of mine told me that if i changed my hdd to 'compatibility mode' in the bios then it would work again. No such option in the BIOS.

2) Gutsy and Hardy LiveCDs both do not recognize the hard drive. (im actually running off of a Hardy liveCD right now) As such, any recovery software that works through ubuntu does not work, HOWEVER, i did try them through knoppix, as i've detailed below.

3) Knoppix does recognize the Hard drive, but cannot mount it (this means that its not completely dead...). Running dd_rescue through knoppix gives me a bunch of i/o errors. Running testdisk through knoppix recognizes the disk, but does not give me any partitions to work with. (i remember it had an option to overwrite the MBR... think its worth it?) Photorec does not work because it recognizes no partitions.

4) Windows XP installation disk tells me that it cannot continue because it did not find a hard drive.

5) Windows Vista installation disk tells me that it detects my hard drive, but that it has nothing on it.

6) gParted liveCD tells me that there is a hard drive there, but that its all unallocated space. 

7) Ubuntu Heron installation tells me that there is no hard drive there.


Right now, I've found some tools that work on windows like Stellar Pheonix Linux Recovery. My next step is to get XP installed on the external hard drive, boot into XP, and then see what I can do through there. Another option is getting a 2.5" hard drive enclosure so that I could just plug in my hard drive into another computer and see what I can do to fix it, or even if it recognizes it.


All i want to do right now is recover my files from the hard drive. After that, I could go into gParted and wipe it and then I think that the Heron installation will recognize it.

Any ideas?

---

### Post by EXCiD3 on 2008-05-18
If your drive is really going bad, you wont be able to format it. You should give the System Rescue CD a shot and see if you can do anything with your drive. [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) At most you will be able to backup some of the drive, but you will probably have to replace the drive in the laptop if it truly is going bad. You should also check the S.M.A.R.T. status of the drive, if possible. The smartmontools is available for linux and you could install it in a live copy of linux such as ubuntu, if there is a /dev/sdX for you drive. [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)


Hopefully you can get something to work! You never know when a drive might fail. Always back up important info!

---

