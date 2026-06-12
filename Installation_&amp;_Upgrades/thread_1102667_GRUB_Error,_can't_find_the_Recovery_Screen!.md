---
title: "GRUB Error, can't find the Recovery Screen!"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by boothruwindow on 2009-03-21
I know there are lots of posts on this already, but I need more help with the one by Kipper, which should work for *if I could just find my way to a Recovery screen*! Maybe Xubuntu works different. Anyway, I have GRUB blocking my hard drive after I did an installation just to my Sandisk pen drive! So, I have that error when I try to boot my hard disk, doesn't matter whether my CD is in the drive. There is no opportunity to type in anything like "Recovery" at any prompt, just the error message. When I F12 and select my CD to boot into, I get the following menu:
[CENTER]Try Ubuntu...
Install Ubuntu
Check CD for defects
Test Memory
Boot from first hard disk
[/CENTER]I checked the F4 and F6 options for each of these, and saw nothing on recovery. So, I need more details on how to actually access that screen with recovery options.  I've seen such a screen before with a recovery option when I had a dual-boot system (Ubuntu Ibex and Vista), but I only knew how to access it from the hard disk, and GRUB won't let me near it now. The directions I've seen so far aren't helping me, if it makes any difference I'm using 8.10 - please help!

---

### Post by Pumalite on 2009-03-21
Do you see Grub or you get an error message? If error message; post it exactly as it appears.

---

### Post by cholericfun on 2009-03-21
wild guess:
(happens to the best of us)

HD not recognised

boot from CD Live and check if you can access your HD
properly.
if not:
install gpartet
reboot.

run the check/fix on all partitions

if that doesnt work there is some magic boot file manager out there that wil help you rewrite the boot part and enable you to access all the OSs that you have installed. ...  unfortuatly i happen to have forgotten the name... googel is your frined... something with S

---

### Post by boothruwindow on 2009-03-21
> **Pumalite said:**
> Do you see Grub or you get an error message? If error message; post it exactly as it appears.

What I see is GRUB, with an error - not always the same number, so far I've seen 23, 25, 21.

---

### Post by boothruwindow on 2009-03-21
> **cholericfun said:**
> wild guess:
(happens to the best of us)

HD not recognised

boot from CD Live and check if you can access your HD
properly.

I tried that, and can't - xubuntu doesn't see that hard drive, in the File Browser, but the partitioning window seems to understand something's there. 
> if not:
install gpartet
reboot.

What should I install it on? Can a burned CD take the program, or will I have to use my flash drive (can't access the HD)?

Well, maybe I shouldn't expect to see in the Xbuntu file browser what I saw in Ubuntu, but the /media folder is empty!

> run the check/fix on all partitions

if that doesnt work there is some magic boot file manager out there that wil help you rewrite the boot part and enable you to access all the OSs that you have installed. ...  unfortuatly i happen to have forgotten the name... googel is your frined... something with S

---

### Post by cholericfun on 2009-03-22
do the fix/check option from the LiveCD 
gparted should be in the system-admin menu

---

### Post by cholericfun on 2009-03-22
[QUOTE=cholericfun;6935134]

            boot from CD Live and check if you can access your HD
            properly.
            if not:
            install gpartet
            reboot.

            run the check/fix on all partitions


ok, that was a stupid comment...
obviously doesnt work while in Live Cd mode...

-cross out the reboot part above

---

### Post by cholericfun on 2009-03-22
PS:
rereading your original post again...

what are you actually doing?

no CDs in the drive / USB attached - booting up?

what do you get?

---

### Post by boothruwindow on 2009-03-22
> **cholericfun said:**
> do the fix/check option from the LiveCD 
gparted should be in the system-admin menu

Oh, there was something where I would least expect it! The bad news is that when I tried running System>Partition>Check (that's how it's set up in Xbuntu) it crashed with an error when it checked my system drive. I tried this on both my system , and my extended Fat32 drive, and neither are accessible for that now.
 
I just tried the umount -a command, which has fixed problems before. Xubuntu failed to do this, said that all the drives are "busy" - other than busy stealing the user's time, what?

Is there a program available which I may be able to run from USB?

---

### Post by cholericfun on 2009-03-22
ok, i got little knowledge, especially bout Xubuntu,

in the LiveCD after a fresh restart / terminal
type 
sudo fdisk -l

post the output here
to see if it catches anything of your HD

might be worth to open up your box and plug in your HD in somewhere else (had to do that myself once)

not sure if Xubuntu uses gparted, try installing it in the Live, and run it - at least to see it IT can see any of your HD

---

### Post by boothruwindow on 2009-03-22
It's been enough of a puzzle to sort out what wasn't doing what, but now I can see that the GRUB error is blocking the hard drive-installed menu which contains the Recovery functions. It is only when I booted, without pressing any bypass keys, and with the same Sandisk which will likely cost me another week of my life, that I was able to access that screen, but never figured that out until I tried the Check and Fix (for my hard drive partitions, which seem to be damaged by the creation of that Sandisk bootable), which failed. When I finally got in, through the DOS screen menu and Recovery, I did a couple of things, including ..Check.., but there were lots of errors, and there were no results. 

I can still burn a CD through my laptop, anybody know of a downloadable which is better known to fix these problems?

---

### Post by cholericfun on 2009-03-25
Hi,

did you manage to solve your problem?
just back from trying to install a dual boot at a friends (impossible and not funny!)

for HD problems, gparted did a pretty good job when i had to use it, although initially it didnt see anything, 
finally worked after fresh boot into LiveCD and imediatly running gparted/check.

for GRUB problems
one thing that should be of help is a program called Supergrubdisk
which might come across as somewhat more user friendly as using grub commands.
you can install (or should be able to...) this in a liveCD session and run it from there.
in the end your MBR should be able to point to all sortrs of OSs and recovery options.
oh and one more thing... not really sure how your computer is set up (sounds like single OS) from the posts above but one thing that surprised me earlyer:
in a dualboot: MBR just points to the grub on the Linux partition. it is from there that you can choose between different OSs.
hope this helps.

any news on whether you solved your problem migh help others!

---

