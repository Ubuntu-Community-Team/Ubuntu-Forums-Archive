---
title: "Yet another NOOB with problems."
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by Scott Mayham on 2009-04-20
While I'm an experienced Windows IT guy, I'm a total newbie to Ubuntu.  So, I thought I'd install it on an old PC and play with it in order to learn. 

However, I ran into a bit of a problem.

The target box is an older HP desktop PC with a 1.6 ghz Celeron, 512 mb ram, 120 gb hard drive, and a CDROM drive. Video, network and sound hardware are all on the MoBo, and all *WERE* working fine under Windows XP.  The moitor is a generic Plug-and-Play SVGA.

Using another PC (the one I'm typing on now) I downloaded the <ubuntu-8.10-desktop-i386.iso> distro from the Ubuntu website, confirmed a good MD5, burned a CD, booted it on the target, ran the self-check of the CD (it was fine), and then installed Ubuntu by selecting all defaults.  For example, I chose to wipe the existing WindowsXP partition and let the Ubuntu installer do whatever it thought best.

After some time, the system rebooted, and the monitor would only display colorful "snow" - nothing intelligible.  Apparently, the installer is somehow confused with regard to video settings.

So, my questions are as follows:

1. Is there reasonably straightforward way to analyze this problem?  If not, see #2 below.
2. It seems that I've read of a text-based, more detailed way of installing Ubuntu.  Would such a technique give me a chance to guide the installer with respect to video settings?  Finally, would such a technique be possible using the distro I already have (ubuntu-8.10-desktop-i386.iso), or do I need to download another one, and if so, which one?

Thanks in advance,
Scott

---

### Post by abn91c on 2009-04-20
you can try booting to recovery mode the run the **xfix** command, see if that helps.  I found better to run the live cd first, that way you can test all the hardware then install from the desktop icon.
some people just boot from the cd and immediately select install instead of "try ubunbtu..." option and run into problems
you acn also try from the command prompt **[COLOR="Red"]sudo dpkg --reconfigure xserver-xorg[/COLOR]**

---

### Post by Scott Mayham on 2009-04-20
"you can try booting to recovery mode the run the xfix command"

Um, just how, exactly, does one do that?

---

### Post by Bucky Ball on 2009-04-20
So, when you restart and reboot, you don't get the grub menu, you just get snow?

If so, try pressing escape right after the boot and that might get you to a grub menu before boots into snow. If you can get to the grub menu, there is an option second down to run the recovery. Try that and see if you get any help there. If you can get that far, the monitor problem is probably diagnosable and possibly fixable. Get to the grub menu and hit F1. That should take you to a command line where you will be able to get a better picture (no pun) of what's going wrong.

Always give your posts a descriptive title. :)

---

### Post by Scott Mayham on 2009-04-20
Ok, I've pretty much determined that the "snow" problem was bogus - somehow the monitor and PC confused each other.  power-cycling both fixed that problem - AND - revealed that Windows was still installed on the hard drive.

So, the current issue is why Ubuntu did not install itself on the hard drive?  

I rebooted off the Ubuntu CD, got the usual startup screen, hit  F4 and selected "safe graphics mode", hoping it would not "confuse" the monitor this time.  I than selected "Install Ubuntu" off the menu and watched carefully.

Over the next several minutes, a number of progress messages scrolled by, saying things like "*Setting <something>" or "*Starting <something else>", which I presume is just as expected.  However, after the message "*Starting Ubiquity", there was a long pause, the screen went blank, there was some CD activity, and then everything stopped cold.  The machine appeared to be hung.  Just to be sure, I waited about 30 minutes, but nothing else happened.  So, I removed the Ubuntu CD and then rebooted - to Windows again!

The machine has only one hard drive, a 120gb Maxtor PATA IDE drive with only one NTFS partition, with Windows XP on it.  I DO NOT want a dual-boot arrangement, I want Ubuntu to completely replace Windows.  I'm guessing that Ubiquity was attempting to do this when it hung.

Any thoughts / ideas / suggestions ????

Thanks,
ScottM

---

### Post by megamania on 2009-04-20
> **Scott Mayham said:**
> 
Any thoughts / ideas / suggestions ????
Try running Ubuntu from the Live CD and see what happens, then let us know.

---

### Post by Bucky Ball on 2009-04-21
> **megamania said:**
> Try running Ubuntu from the Live CD and see what happens, then let us know.

I think that might be what's happening.

When you boot from your cd, you get a list of options? One of them is install Ubuntu? Install straight from the menu that appears when you boot from the CD, not from the Live desktop (try Ubuntu version).

---

### Post by megamania on 2009-04-21
> **Scott Mayham said:**
> I rebooted off the Ubuntu CD, got the usual startup screen, hit  F4 and selected "safe graphics mode", hoping it would not "confuse" the monitor this time.  **I than selected "Install Ubuntu" off the menu and watched carefully.**
> **megamania said:**
> **Try running Ubuntu from the Live CD** and see what happens, then let us know.
> **Bucky Ball said:**
> I think that might be what's happening.

When you boot from your cd, you get a list of options? One of them is install Ubuntu? **Install straight from the menu** that appears when you boot from the CD, not from the Live desktop (try Ubuntu version).
From what I see, he *is* installing straight frome the menu. My advice was to use the live version to see if it starts properly.

But I may be mistaken.

---

### Post by Scott Mayham on 2009-04-21
Ok, folks, thanks for all the input and suggestions.  I'll attempt to address them in order.

First of all, when running the CD as a "live" session, everything is fine. And this makes sense, since in that context, the system's hard drive is explicitly NOT a player.

And no, I'm not trying to install from within that live session.  I'm booting from the Distro CD, and selecting "Install" from that first, very simple menu which comes up (Orange background, other options are things like Memory test, check integrity of CD, etc.).  So, I'm doing what I *think* is the right thing.  

The problem is, that the install process only gets so far, and then hangs.  No error message is displayed, so it is difficult to tell what the problem is.  And, since the hard drive has not yet been touched, there is no error log or other trace to see for verification.

So, I'll back to one of my original questions - Isn't there another Distro with which you can sort of "hand fly" the process one step at a time?  What I'd like to do is step through the process step by step to determine just what is failing, and hopefully get some kind of indication of just what's wrong.  

For example, the last message I get is "*Starting Ubiquity".  Isn't Ubiquity the thingy which sets up the partitions for Ubuntu?  Since my hard drive has only one partition which occupies the entire disk, it would appear the Ubiquity (or some other program) must delete that partition and then create the partitions needed by Ubuntu.  However, it seems to be stalling at this point.  Am I supposed to delete the partition "by hand" before installing Ubuntu, or is Ubuntu supposed to be able to do that without much help from me?  You see, part of my problem is that I'm so new to Ubuntu that I do not yet know what to expect, and so I don't know what looks "abnormal."  

Any advice on how to analyze and correct this situation would be much appreciated.  

Thanks,
ScottM

---

### Post by abn91c on 2009-04-21
installing from the live session is the best way, make sure everything works, like the network, desired screen resolution, sound. in the partitoning screen i found it ideal to use the Guided "use entire disk" option. In my current installation that is the optionthat I used,  and kubuntu "remembered" all my live session settings when it was done.

---

### Post by lisati on 2009-04-21
Don't forget to take the CD out once you've installed Ubuntu, and keep an eye open for things like recovery partitions that you might want to keep "just in case".

---

### Post by Bucky Ball on 2009-04-21
You can try the alternate install rather than the desktop. That sometimes works where the other doesn't. So you are not getting to the partitioner I take it.

You have checked the cd for defects (the most reliable way to download the ISO is by torrent - the torrent files can be found on the download page)?

---

### Post by Scott Mayham on 2009-04-22
"in the partitoning screen i found it ideal to use the Guided "use entire disk" option."

Gee.  I guess I didn't make it clear enough.  It never gets that far.  I'd love to use the "use entire disk" option, but the installation stalls before offering me that option.

Will somebody please answer definitively - is "Ubiquity" the program which handles disk partitioning?  I ask because this program seems to be the one that is hanging - and hanging without gving me any messages, menus or nice options like "use...".  It just stops.

How does one go about analyzing such a problem?  

Thanks again,

ScottM

---

### Post by redb on 2009-04-22
> **Scott Mayham said:**
> "in the partitoning screen i found it ideal to use the Guided "use entire disk" option."

Gee.  I guess I didn't make it clear enough.  It never gets that far.  I'd love to use the "use entire disk" option, but the installation stalls before offering me that option.

Will somebody please answer definitively - is "Ubiquity" the program which handles disk partitioning?  I ask because this program seems to be the one that is hanging - and hanging without gving me any messages, menus or nice options like "use...".  It just stops.

How does one go about analyzing such a problem?  

Thanks again,

ScottM

If I remember right I had problems with my install.  After several attempts I looked at the installation options offered on the live cd using the f-keys.  I think it was f4 that allowed me to finally install in safe graphics mode.  

Before you hit "enter" on install ubuntu I would try safe graphics mode.

Mike

---

### Post by cariboo on 2009-04-22
Ubiquity is the installer program, if it is hanging there, there must be a problem with the disk. I haven't closely reasd the entire thread, but when I do a complete install, I always use the try first option to get to the desktop, then double click the install icon. I then open Firefox and read the forums while the installation runs in the background. As some of the other posters have said, It might been an idea to try the Alternate install CD. It is a text based installer, so you will have to use the keyboard instead of the mouse to do the navigation.

---

### Post by curly_nostrill on 2009-04-22
Ubiquity is the graphical installer environment, I guess ... [HTML]http://www.google.com/search?hl=en&q=ubiquity+ubuntu&btnG=Search[/HTML]

Also, I would check in the BIOS (usually "del" key at boot) to see if there are any onboard so called "raid controllers" or other odd bios settings.  I've found that sometimes setting the "Plug and Play OS" bios setting one way or the other can have an effect on linux dist installers.

Also, if you don't have anything on that machine you need, try just setting the bios to default settings a few times and see what happens...

Hang in there, I do, it's worth it.

---

### Post by Bucky Ball on 2009-04-22
You go about analysing the problem by trying the alternate install. It is text based, not disco GUI, and will probably give you a better idea of why it is crashing with error messages (and as I say, may not crash at all). Try it.

---

### Post by Scott Mayham on 2009-04-24
Kind folks,

I appreciate the torrent of suggestions.  Many are already addressed in the thread - for example, YES, I downloaded the distro using BitTorrent, and YES, I already checked the quality of the CD I burned using the option the CD gives you when you boot it up.  And, NO, there is no weird RAID or anything funky - it is a very simple single-partition NTFS IDE drive which has nothing on it I want saved - I simply want to blow away what is there, and install Ubuntu.  I looked over the BIOS and saw nothing weird or strange.  Oh, and YES, I already used the F4 option "Safe Video Mode", thinking that there was possibly some weird video issue.  All to no avail.

I will no look into downloading the "alternate" Distro, with the text-based installer.  Perhaps it will work fine, or failing that, give somevisibility into what the problem is.

Thanks again to all,
ScottM

</EndOfThread>
ScottM

---

### Post by curly_nostrill on 2009-04-24
addendum: I've had issues with optical drives.  I strongly suggest trying another CD/DVD (whatever) drive since the cheaper ones can easily go bad.  And it's not always outwardly evident i.e. the drive will spin up and play some cd's but will balk on some Linux install cd's.  I guess sometimes the compression methods used on some cd's is just too much for some drives to deal with gracefully.

If you have the bandwidth (and the temerity) you might also try the Debian Lenny (5.0) net install CD.  I've also had good times with Sidux (based on Debian Sid) and other distros;  I mean, just to get **something** on there.

Another thing, you might try deleting all the partitions on the drive first... even using an XP install disk or a KNOPPIx CD or, maybe even better, using 'disk partioner' under the 'adminitration' menu on the live Ubuntu CD. Often those store bought HP's, etc. have 'hidden' partitions which might be read only, hidden or something and might be thwarting the linux installer.

---

### Post by Bucky Ball on 2009-04-26
> **Scott Mayham said:**
> 
I will no look into downloading the "alternate" Distro, with the text-based installer.  Perhaps it will work fine, or failing that, give somevisibility into what the problem is.

Let us know how you go with that ...

---

