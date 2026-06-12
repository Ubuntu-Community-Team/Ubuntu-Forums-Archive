---
title: "Install + dodgy harddrive = ?"
date: 2009-09-15
forum: Installation &amp; Upgrades
---

### Post by timbledum on 2009-09-15
Okay so here goes.

I have dabbled with a bit of linux on virtual machines and live cds before, and have finally gotten a hold of one of my buddies ageing laptop to... experiment on. Initially my mandate was purely to wipe the password on xp that he had forgotten, however this was quickly accomplished with the help of "Offline NT Password & Registry Editor". I quickly realised that the laptop was only marginally capable of xp and needed a good linux distro on it to get it flying. The plan was to set up a duel boot, get my mate to try both, and wait for him to revert to ubuntu when xp slows right down.

A good plan, with a fatal flaw.

The facts:
Compaq Presario V2000
224 ram
Average condition.
Capable CPU, however in XP the graphics card in devices came up with an error. Shouldnt be a problem methinks.
40 g ntfs harddrive with about 6g full. (model st94019a)

--------------
Ive just read through this and its a bit wordy so Ill quickly summarise the next few paragraphs
Tried installing with ubuntu, puppy linux and finally xubuntu, seems to freeze/stall just after loading the partition editor without actually entering. Determined that this is because the installer cannot mount the internal harddrive for whatever reason. Xp runs fine.
--------------

I began with trying vanilla ubuntu as I already had a cd lying around, however it took aaaaaages to get around. Obviously there wasn't enough ram to run the live cd so I quickly gave up on the idea when parts of the interface started shutting down.

Second go, an old version of puppy linux. Bad idea. This distro was clearly not designed to be installed on harddrives and thus the install, while well explained, was a tad more complicated than I was prepared for. It was here where I found my first glimmer of an error. For some reason the partition part of the installer would not open. After trying for a while to get the partitioner to open, I gave up and decided on xubuntu.

I downloaded the live cd of xubuntu, burnt to disk (old laptop wont boot off a usb, sad times) and same problem as before. It was a little better than ubuntu however and several times I got (without loading into the full live environment) right up to when it loads the partition program, loads it all up, and then freezes. I restarted the install about 5 times, then gave up, putting it down to the slow speed of the computer and determining to download the alternate installer.

The alternate installer was a lot better for this kind of computer, and as far as I've experienced it is highly recommended! Actually very easy to understand, and I love the keyboard test. Great idea. Anyways, back to the problem. I began to smell a serious rat when the installer got to exactly the same place as the live cd version, right after it loads the partitioner. Right after that I got a full light blue blank screen. Obviously it wasn't the speed of the computer that did it this time! I was shocked! 

I tried another 5 times before getting up the courage to try the option which is repair installation or something. I tried to (i think) manually partition the drive or something, and you need to mount a file system. It tried to mount the harddrive and failed! This was the message it gave:
"An error occurred while mounting the device you entered for your root file system"

 After this I tried again and after it failed i pressed control alt delete and it gave me an error about the drive being read only or something. "read only file system" ?

Okay I'm really suspicious at this point so I load up the bios and do a full hard drive test. It comes back 1- #7 fail, which a quick google search shows could be a number of things, from a dodgy drive to dodgy controllers. I even tried taking the harddrive out and putting it back again! So somethings dodgy hardware wise, but I'm not forking out NZ$140 for a PATA harddrive for my mates old crappy laptop.

----------------------------

So I guess my final two questions are
1 - Even if the harddrive is slightly dodgy why can't linux (not just ubuntu, puppy didn't work either) mount the drive when xp runs it completely fine and
2 - Is there any way, any boot parameter or anything that I could use to get around this problem without replacing the harddrive (which would hurt my pocket and might not work, plus I dont have access to a copy of xp)

Of course there may be a simple widely known explanation for all of this, but I been banging my head against this thing for a while now without any relief. And I was so excited when it first booted up. :(

And guys, thanks for any help, Ive got a feeling this isn't an issue that will be able to be resolved, but I've come to the end I can do so I'm chucking it out there and seeing what will happen. Sorry for the long post but meh. I figure more info is better than less.

Peace out

---

### Post by earthpigg on 2009-09-15
hi,

a bad hard drive is a bad hard drive and should not be relied upon. perhaps there is something going on in the Master Boot Record of the hard drive that lets it be read, but not written to? that would stop the Ubuntu install because it needs to over***write*** that MBR... that was just one example.

i have good news for you. **your laptop does not require a functional hard drive to run Ubuntu.**

take the hard drive out[COLOR="Green"]*[/COLOR], put a thumb drive in, boot from the LiveCD, and install Ubuntu onto that thumb drive as if it where a hard drive. set the BIOS of the laptop to boot from thumb drive, of course.

when you want to run ubuntu, pop the thumb drive in and turn the computer on. ubuntu will be able to read the contents of the windows C:\ drive.

if you want to install ubuntu without taking up to much of that thumb drive space, the Ubuntu remix in my sig takes up about half as much space: about 1gb instead of just over 2gb.

the other option is a [WUBI install]("http://en.wikipedia.org/wiki/Wubi_%28installer%29"), which i do not advise on a questionable hard drive.




[COLOR="Green"]*in this case, you are taking the hard drive out to prevent Ubuntu from trying to install the bootloader ([grub]("http://en.wikipedia.org/wiki/GNU_GRUB")) there, and maybe to help prevent you from making any windows-killing mistakes. i idiot-proof myself from myself in the same way.[/COLOR]

---

### Post by timbledum on 2009-09-15
Wow yeah that would make a lot of sense! Thanks a lot!

I do like the idea of booting from the usb, especially because it makes that clicking sound that suggests that the drive is going to fail any second now! However the bios does not have an option for booting from usb. I am currently on a quest to find a bios update.

---

### Post by earthpigg on 2009-09-15
linux has a solution for that, too, though it may be a bit awkward:

[http://www.supergrubdisk.org/w/index.php5?title=USB_Boot](http://www.supergrubdisk.org/w/index.php5?title=USB_Boot)

---

### Post by johnk73 on 2009-09-23
> **timbledum said:**
> Wow yeah that would make a lot of sense! Thanks a lot!

I do like the idea of booting from the usb, especially because it makes that clicking sound that suggests that the drive is going to fail any second now! However the bios does not have an option for booting from usb. I am currently on a quest to find a bios update.

I have a Compaq V2000 and the BIOS does boot from USB flash drive, but it's hidden.  Expand "Hard Drives" in the boot order list and you should see it.

---

