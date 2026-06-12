---
title: "Installing 4 light distros in old PC"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by PabloBS on 2009-10-05
Hello everybody:

I'm writing this thread looking for advice and sharing information about other experiences on a new linux adventure I want to begin.

I have been using Ubuntu for almost a year now (currently on Jaunty), and I have an old PC built from scratch that I want to use to surf the Web, and some light stuff, like using OpenOffice, checking mail, etc.  I was lookin for light distros based on Ubuntu, since most of my experience is on it (I began with Puppy).

Anyway, the old PC is a Pentium II 450 MHz, with 256 Mbytes RAM (formerly 128 Mbytes), 2 USB ports, **1 serial port - to use with a serial port mouse (it works!), PS/2 port - for the keyboard**, and 1 CD-ROM drive. I will install on it a Wi-Fi card, remove the floppy disk drive, and install a 80 Gbytes disk on it.

I was checking for the best distros, and after long considerations, I decided to install 4(!) of them at the same time:  moonOS 3.0, gOS, Vector Linux, and MacPup.  Most of all, because I want to try Enlightment desktops, and eyecandy stuff.  Besides, it's going to be a surfing-the-web-desktop (I have to set up an objective for this experience).

The procedure to install the four of them and get them to work without problems is what gives me most of my concerns. I will try this: 

1.  Installing moonOS on the first 20 Gbytes partition. Configure Swap to 512 Mbytes or 1 Gbyte.  Use this partition to place GRUB.
2.  Installing gOS on the second 15 Gbytes partition.  Add this to the moonOS GRUB and try.
3.  Installing MacPuP on the third 15 Gbytes partition.  Add this to the GRUB and try it.  
4.  Installing Vector Linux (I must try this Slackware!) on the remaining space.  Add this to the GRUB and try.

I can also look for a 19-1-20-20-20 configuration.

I will try every distro with it's own /home, because not all of them are Ubuntu based, and could be problems with only one /home.
I will love everyone to comment about this.

Also, there is the Issue on how to edit GRUB after each installation procedure. I don't want to mess up.

The serial port mouse is a concern, beacause it doesn't work out of the box in some distros.  With Puppy was a piece of cake, with Xubuntu and Fluxbuntu not so much, but it worked at last. No experience with this issue with Slackware or with Enlightment desktop.

Finally, and in order to keep the "eyecandy" objective on sight, and after 4 distros succesfully installed and working, replacing the GRUB with GRUB 2 (The graphical GRUB).

Does anybody have similar experience on this?

My intention is to have an optimized-good-looking experience in this desktop.  And of course, to let my experience in this written for everyone every step in the way. I want the answers of the problems I must face written for the future.  I will detail the steps I will take.

I will start tomorrow.  Wish me luck.

---

### Post by i.r.id10t on 2009-10-05
Umm... thats not an old PC.. 

FWIW, I have 10 kiosks around campus, all P2-450s and P3-500s with 384mb of ram running Ubuntu 9.04

An old PC is a Pentium or 486...

---

### Post by tuahaa on 2009-10-05
Well good "look" then!

I've never tried this before, it looks interesting...

Tell us what happens,:popcorn:

and good look once again!:)

---

### Post by PabloBS on 2009-10-13
Ok..I'm giving the first update on this post.

After a lot of delays because of my job, I finally was able to put hands on work.  I got the four LiveCD's ready (already tested on a DELL Latitude D800) and started the process with moonOS 3.0.

moonOS ran almost perfectly on the Pentium (a little bit slow).  The Enlightenment Desktop showed really nice, and, as I expected, the mouse wasn't running (remember: is a serial port mouse).  For half an hour I tried to get up the mouse with the recipes I learned at a previous Xubuntu installation.  Editing xorg.conf didn't worked, nor dpkg-reconfigure xserver-xorg (no mouse menu to pick!!), nor inputattach.  moonOS is hard to work without a mouse, and finally, after another half an hour trying to install without mouse, didn't find the way to get started.  I try a reboot, and moonOS didn't pass through bootsplash.

So, I tried gOS, the next option.  At this stage, I expected at least to have a partition table up.  But the evening wasn't good to me and gOS refused to load, not one but 3 times.  I didn't expect this.  Same problem as the second boot in moonOS.  Written down.

Next.  Open the CD tray and Load the Vector Linux 6.0 LiveCD. It looked good, until the same thing happen with it.  No progress after the initial loading screens.  At this point, I noticed, like in gOS and second moonOS boot, the screen freezes in the same drivers loading notifications.  IRQ 10 and 11 recognition succesfull.  These IRQ's, according to BIOS belong to the USB ports behind the PC.  Another 2 shots.  No progress.

At this point, I was very sad.  I prepared everything to make this work at least with minimum problems.  So, I didn't expected so much when I put the MacPup disk inside the CD tray. 

And it worked.  Silky smooth!!  The MacPup live CD even recognized the serial port mouse.  So, the PC was full operative.  Serial mouse working, Ethernet card working.  At least this minimum.  To finish this work, I ran Gparted.  Create a primary partition to install Macpup, a swap (1.2 Gbytes) and an extended partition for the rest.  Inside the extended partition, create 3 logical ones.  I had problems to create one of them, but I left it without a file system configuration.

I installed MacPup.  It loaded everything from HD.  Recognized the Serial port mouse, and the Ethernet card.  Working nice.  But I have a bad taste in my mouth.  I will re-burn moonOS, gOS and Vector.  It has to be a problem there.  I discarded a reading problem in the CD tray, since MacPup succesfully load.

There are questions to Answer:
1.  How to begin an installation process in moonOS using the terminal?
2.  How to build a partition table in moonOS using terminal?

I will check out.  But, Can anybody give any feedback?

Thanks a lot.

---

### Post by PabloBS on 2009-10-20
Ok.. Next update on this issue.

I regret to say I'm making no progress at all.  I reburn the ISO images of the CD's, test them on other PC's (even my main PC), and finally, trying to install them on the "test subject".  Still making no progress.  moonOS 3.0 don't load at all.  I tried moonOS 2, and it does pass through bootsplah, but doesn't go further.  

I realize there was some hardware failure and try to boot an old Debian CD I have.  Same results. I noticed the same error.  I have a LFS disk in my stock, so I tried to boot with it.  No progress, but I got isolated the hardware error I was noticing.  I took pictures with the details.  

Does somebody know what is it about?  Why Puppy and MacPup don't get this error during boot and uploading from LiveCD?

I'm rethinking the experiment.  I can build another PC from scratch (different motherboard) so I can go further, and maybe, bypass this problem.  I wiil decide tomorrow.

---

### Post by dabl on 2009-10-20
Since you're interested in the E desktop, you might want to give Elive a try.  It has excellent good hardware detection (but I haven't tried it with an old serial mouse), and is very light.

Since they try to hit you up for a donation on the "stable" version, try downloading the "Development" ISO.  ;)

---

### Post by PabloBS on 2009-10-20
> **dabl said:**
> Since you're interested in the E desktop, you might want to give Elive a try.  It has excellent good hardware detection (but I haven't tried it with an old serial mouse), and is very light.

Since they try to hit you up for a donation on the "stable" version, try downloading the "Development" ISO.  ;)

And what about the hardware problem, if it is a hardware or a driver problem? And why it is not giving problems with MacPup?
Not that I'm solving a critical problem, but I would like to know the answer, just the "why"

I also downloaded Elive and OpenGEU, but I don't see Elive more atractive than moonOS (it's a matter of tastes).  At this point, I should give it a try, and I will.  OpenGEU seems to be a heavy distro for the equipment I'm using for this experiment.  I have still to solve the problem for the other distros.  Thanks for the advice.  I will replace moonOS or gOS for Elive and see what happens.

---

### Post by PabloBS on 2009-10-26
Short Update:

As suggested, I try ELive on the subject PC, but I got the same results.  I try the 2 Failsafe modes. The recurring error seems to be the same I posted before, with the photos.  I will try the second solution.

Not all bad news.  Using a virtual PC, I wrote down keyboard commands to navigate through Elive, moonOS, Vector Linux and gOS menus.  So, If I can't get the mouse to work, I still could initiate the OS installation process, and then, make a proper mouse installation.

---

