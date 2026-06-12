---
title: "Bios Smart, OS Install Stupid."
date: 2010-03-04
forum: Hardware
---

### Post by reyak on 2010-03-04
I have a gateway laptop with no operating system. I tried installing windows, and it says the hard drive is not there. (even though the BIOS plainly sees it.)

I tried deleting than creating a new partition with Dparted. worked just fine, no issues at all. I ran a couple of tests (memory and what not) and got no issues, everything's fine and dandy.

I decided to install Ubuntu since I was getting used to it on the other computer. Now remember, the hard drive is clean/wiped with a brandy dandy new partition. The CD loaded for a few seconds until I got the following error:

disk error 80, ax = 4200, drive 9f boot failed, press enter to reboot

I rebooted of course, and the same thing came up again. Since I'm a little slow on the uptake I followed the directions a number of times (I was paying attention to a TV show) before I realized it was a dead end.

Now, I HAVE gotten the Ubuntu CD working just fine on the other computer. However, I did not boot directly through the disk, I ran the installer through windows. All other bootable CDs work just fine on the laoptop, but nothing whatsoever will install an operating system onto it, saying there is not hard drive.

Mind you, like I said earlier, the BIOS sees the drive just fine, and all of the windows installers I have used (ME, 2K, XP, Vista And W7) say it does not exist.

Would someone please give me a hand with this? I've been at it for months now, and I've posted in other forums. A few of which I had no answers at all, and some I had 2 or 3, but none of them did me any good.

Reyak

---

### Post by akand074 on 2010-03-04
Did you do an automatic install? If so I'd recommend you choose manually select partitions. I personally like to mount /home on another partition, but either way delete the whole drive (unless its already all as unallocated space) and reformat it as ext4 with mount point "/" without the quotations and install. If it does not work, and windows thinks there is no hard drive, there's a chance its a faulty hard drive. So if it doesn't work I'd try installing it on another hard drive.

EDIT: Oh yeah don't forget to make a swap partition (allocate some space, only about 1024MB is necessary though some people like to put the same amount of swap as in their RAM for when RAM is pretty full and your putting your computer to sleep). Anyways format that as SWAP. That is necessary. Should not have missed that!

---

### Post by pricetech on 2010-03-04
What exactly does your BIOS find ??  It should give you enough information to know, or at least determine, what's there.

Is SMART monitoring turned on the BIOS ??  If it's off, you may be missing the problem because the BIOS is not detecting, or even testing for, a problem.

If it was on my bench, I'd clear the BIOS, go back in and turn SMART on, and go from there.

Keep us posted.

---

### Post by oldfred on 2010-03-04
Even though the CD spun for a minute are you sure you are booting from the CD or perhaps is the CD not working correctly and then it tries to boot from the hard drive which of course will not work?

Can you boot from USB (or floppy)?

---

### Post by reyak on 2010-03-04
> Did you do an automatic install? If so I'd recommend you choose manually select partitions

Sounds great, but I never get that far, the disk loads, but errors out before the installer loads.

> delete the whole drive and reformat it as ext4 with mount point "/" and install.

I created 2 partitions, one ext4 and one extended, not that I have a clue what the difference is. what exactly is "mount point /"? I've never even heard of that, nor would I know how.

> don't forget to make a swap partition

That is not even an option in G-Parted. What can I use to do that?

> What exactly does your BIOS find
In reference to what? It lists a hard drive as WD######### (Western Digital)

> Is SMART monitoring turned on the BIOS ?
I haven't a clue, nor would I know how to turn it on. This bios is very limited, showing me some information, but not letting me alter very much.

> I'd clear the BIOS
.....ok, I'll try anything....how?

> are you sure you are booting from the CD?
Yes, I am certain. I recognize the boot msgs.

---

### Post by Maheriano on 2010-03-04
There's 2 ways to clear the BIOS. there might be an option in the BIOS itself to return to factory defaults but a fool-proof way is to move the jumper on the motherboard. Move the reset jumper, restart the computer, turn computer off, move jumper back, restart computer. It's how you remove BIOS passwords if someone sets one as a joke.

---

### Post by pricetech on 2010-03-04
Clearing the BIOS is done either by removing, or moving, a jumper or by removing the CMOS battery.  This probably won't clear the BIOS password, but that doesn't appear to be your problem.

You should have an option to turn SMART on in the BIOS.  Most computers will have such an option.

The message you quoted shows that the BIOS did indeed find a Western Digital hard drive.  The model number can be deciphered to determine what size if you don't already know.

Give us all the details you can about your computer.  There seems to be something missing and the more information you can give us the better.

---

### Post by reyak on 2010-03-04
ok, Thank you all for your help. I downloaded the desktop version of Ubuntu and was able to install it just fine for whatever reason.

I did find out something rather quickly though. As soon as the installer was finished and the OS boot up, I got a msg telling me there are "disk has many bad sectors". The system seems to run just fine so far, but I would not count on it for very long.

Does anyone know a good program that will fix me up? I know it's not a permenant solution, but I can't buy a new drive....or lunch, lol. I know windows/dos had Check Disk, that basically locks out the bad sectors. Anything like that for Linux?

---

### Post by akand074 on 2010-03-04
> **reyak said:**
> ok, Thank you all for your help. I downloaded the desktop version of Ubuntu and was able to install it just fine for whatever reason.

I did find out something rather quickly though. As soon as the installer was finished and the OS boot up, I got a msg telling me there are "disk has many bad sectors". The system seems to run just fine so far, but I would not count on it for very long.

Does anyone know a good program that will fix me up? I know it's not a permenant solution, but I can't buy a new drive....or lunch, lol. I know windows/dos had Check Disk, that basically locks out the bad sectors. Anything like that for Linux?

umm you can use "fsck" in ubuntu, in the terminal type "man fsck" without quotations to learn more about it, also "ckfs" is the linux equivalent of window's chkdsk though I don't really know much about them myself.

---

### Post by reyak on 2010-03-04
fsck works, but doesn't seem to do anything, or it least I have no clue what it is doing. I don't use man, I use sudo, since it keeps telling me I don't have the privilage.

ckfs does nothing at all since Terminal says the command doesn't exist....Isn't there a proggie I can download for this?....perhaps with a graphical interface, for the more "simple" among us? lmao;)

---

### Post by pricetech on 2010-03-04
> **reyak said:**
> I don't use man, I use sudo,

man is the command to invoke the manual pages.  Try  man man  for a complete explanation.

---

### Post by reyak on 2010-03-04
I did try manual...which is why I'm not using manual, lol. I got completely perplexed, it simply didn't make any sense. either way, it looks as though fsck is for the file system, and ckfs is for the physical disk, that is what I need for bad sectors, yes?

---

### Post by akand074 on 2010-03-05
> **reyak said:**
> I did try manual...which is why I'm not using manual, lol. I got completely perplexed, it simply didn't make any sense. either way, it looks as though fsck is for the file system, and ckfs is for the physical disk, that is what I need for bad sectors, yes?

The manual tells you information about it (it doesn't actually execute the command) it opens up the manual about that command and tells you everything about it. Put man before any command and it will tell you all about it so you can learn more about it.

---

