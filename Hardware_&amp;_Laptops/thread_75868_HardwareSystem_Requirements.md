---
title: "Hardware/System Requirements"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by enjoythefall on 2005-10-14
I looked on the Ubuntu Website but I cant seem to find it. I am looking to install Ubuntu on a older computer, and I was just wondering what would be the idea system requirements. Thank you.

---

### Post by farmer on 2005-10-14
Well, what's in this system? We can tell you if it'll fit the bill or not. Linux will run on mostly everything. You may have to use a special install option, however.

---

### Post by dbott67 on 2005-10-14
I'm running on a P2-300 Toshiba Tecra laptop with 256 MB RAM... it's a bit on the sluggish side, but definitely usable.  I know of others that have only 128 MB RAM, but choose to run other Desktop Environments, such as XFCE (or Xubuntu).  After installing Ubuntu, you can download other Window Managers such as IceWM, Blackbox/Fluxbox, enlightenment, etc. and use them instead.

-Dave

---

### Post by Xentex on 2005-10-17
[QUOTE=enjoythefall]I looked on the Ubuntu Website but I cant seem to find it. I am looking to install Ubuntu on a older computer, and I was just wondering what would be the idea system requirements. Thank you.[/QUOTE]

Sorry to sort-of encourage jumping ship - but have a look at Gentoo. The reason I say this, is becuase I had an old 233MHz MMX/128MB/5GB machine, which was needing a new lease of life.

I tried several distros - Debian-based, Slackware, and Redhat-based too.  All of them were too "demanding" for the old system.

I won't rant and rave about how good Gentoo is, as it's down to personal opinion - but no-one can argue against the fact that an optimised OS is better than a *generic* installation on older hardware - enter Gentoo.

I installed Gentoo 2005.0, following Bob P's NPTL tutorial ([http://jackass.homelinux.org)](http://jackass.homelinux.org)), with the downloaded ISO for Pentium MMX.

After several *days* of compiling (Couldn't be bothered to set-up distcc, and thought several days of work would test the system for stability ;-) XFCE4 was up and running - along with an old Creative Soundblaster 5.1 card. The speed of the little beast was impressive to say the least - I opted for the highest-optimisation level.

I donated the little beast, along with other bits of hardware I had lying around (printer, SCSI scanner, cd-rw etc) to a local kids-club, who are happily using it to this day :-)

---

### Post by stlshawn on 2005-10-18
Well, i'm jumping in head first.  Tomorrow while travelling, I'm going to try and install on a 233 Mhz machine with 48 megs ram and a 2 gig drive (Old Panasonic Toughbook covered with stickers, paint, and other accumulated decoration).

I should have an answer (and probably some new questions) tomorrow.

Thanks,
Shawn

---

### Post by Hamman on 2005-10-18
I've ran XFCE and Slackware 10.0 on a 300mhz with 64mb RAM, and it worked pretty nicely. Tips:
* Don't use Gnome or KDE, but something a bit more lightweight such as XFCE, or Fluxbox if you feel like editing a lot of config files
* Don't use Mozilla/Firefox, but something lighter like Dillo
* Don't even think about starting OpenOffice, or your harddrive will die out of the effort ;). Use AbiWord and Gnucash instead.
As for a lightweight filemanager, Rox is really nice, albeit not as good as nautilus or Konqueror (*personal opinion*)
the xubuntu-desktop package might be worth looking into. 
A good way of freeing up resources is to disable system services that you do not need (cups for example, if you wont be using a printer). 

Oh, and don't use Gentoo. Apart from the painfully long compiletimes, Portage requires quite a bit of harddrive space.

---

### Post by SickTwist on 2005-10-18
[QUOTE=stlshawn]Well, i'm jumping in head first.  Tomorrow while travelling, I'm going to try and install on a 233 Mhz machine with 48 megs ram and a 2 gig drive (Old Panasonic Toughbook covered with stickers, paint, and other accumulated decoration).

I should have an answer (and probably some new questions) tomorrow.

Thanks,
Shawn[/QUOTE]

If it is at all possible for you to upgrade the RAM I would highly recommend it. Also, be sure to create a swap partition that is 1-2 times the size of your RAM installed.

A regular Ubuntu installed could squeeze on your 2 GB drive but it will be a tight fit. You may want to consider doing a server install (type "server" without quotes on the install CD boot prompt and press Enter) which will install a minimum of packages. If you do this, be warned that you will log in on a terminal for the first boot (and until you install more packages). After your first log-in, you could run **sudo apt-get install xubuntu-desktop** if you want to install the XFCE desktop and its dependencies. XFCE is a lightweight alternative to GNOME and KDE.

---

### Post by az on 2005-10-18
You can install the full ubuntu desktop on a 300 MHz computer with at least 128 megs of ram.  It is a personal preference, but anything less is just too slow.

If you find that too slow, you can install a lighter desktop like icewm or xfce4 (use synaptic and log out then log into your new session)

You need more than two gigs of HDD space.

If you have too small a hard dirve, you can install the base system (server) and just install what you need.

sudo apt-get install x-window-system-core gdm synaptic mozilla-firefox xfce4

That should take up less than one gig....

---

### Post by Alacrity on 2005-10-23
Ok....harder challenge for the forum...

I have an HP Omnibook 800CT 166Mhz MMX 80MB RAM.  Will any of the combos you mention so far work on this PC?

I am using Windows 2000 with services.msc trimmed via blackviper.com of unused processes.  Not too bad and very stable compared to windows 98. But am wondering if a trimmed Ubuntu would work even better.  I am using Ubuntu on my high end machine and am very satisfied ...  seems faster and crisper than XP.

But for the Omnibook...what do you all think?  

Thanks in advance for any suggestions.

No CD boot on this machine by the way.  Floppy and HDD boot only.  But, I did put in a 20GB HDD....so plenty of space.

---

### Post by bugmenot on 2005-11-07
[http://archive.ubuntu.com/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/](http://archive.ubuntu.com/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/)

---

### Post by daigorobr on 2005-11-07
If you install it with the 'server' option in boot time and, after the initial install is done, install the xubuntu-desktop, maybe you get a nice surprise. I put it running in a K6 233 with 64 megs of RAM.

And if you get to write a sentence with so many 'install's, I will forever respect you.

---

### Post by themoomin on 2006-07-11
Ok. how bout p1 120mhz 24mb ram, cd and floppy, 1gb HD.

:)

or 

p3 666mhz, 256mb ram, cd dvd floppy, 20gb hd, graphics card, sound card.

---

### Post by passonno on 2006-07-11
Regarding XFCE:

I have a Sony Vaio Desktop. with 32 or 64 mb ram, I don't remember, and a 200mhz processor.

I just installed Breezy Server, and would now love to install Xfce, but I do not have a net connection at home.

So my question, then is: could I download the xubuntu-desktop packages with my laptop, burn them to a cd, then install?

Is there a sure way to figure out dependencies without the connection?

---

### Post by az on 2006-07-11
> **themoomin said:**
> Ok. how bout p1 120mhz 24mb ram, cd and floppy, 1gb HD.

:).

No.  The alternate installer needs 64 megs of ram.  The Desktop cd needs 256.

> **themoomin said:**
> 
or 

p3 666mhz, 256mb ram, cd dvd floppy, 20gb hd, graphics card, sound card.

Yes.

---

### Post by Ptero-4 on 2006-07-11
> Ok. how bout p1 120mhz 24mb ram, cd and floppy, 1gb HD.


For that one you need to use Damn Small Linux.

---

### Post by themoomin on 2006-07-12
where can i get a live cd for that?

---

### Post by reynal_sf on 2007-07-04
These are the Ubuntu System Requirements...

[Minimum requirements]

- 300 MHz x86 processor 

- 64 MB of system memory (RAM) 

- At least 2 GB of disk space (for full installation and swap space) 

- VGA graphics card capable of 640x480 resolution 

- CD-ROM drive 

> If your system has less than 192 MB of system memory, use the Alternate Installation CD.




[Recommended minimum requirements]

- 500 MHz x86 processor 

- 192 MB of system memory (RAM) 

- 8 GB of disk space 

- Graphics card capable of 1024x768 resolution 

- Sound card 

- A network or Internet connection 

> Note: All 64-bit (x86-64) PCs should be able to run Ubuntu. Use the 64-bit installation CD for a 64-bit-optimised installation.



By the way... I can't run Ubuntu... I have an HP Pavilion -- Windows XP (32bit) 2.70GHz of Processor, 512MB of RAM, and Video 256BM.

And my brother can actualy run it... and this is his PC specifications -- Windows XP (32bit) 2.0GHz of Processor, 256MB of RAM, and Video 64MB (Shared memory)

This is the error I get when I click "Start or Intall Ubuntu"

[IMG]http://i82.photobucket.com/albums/j264/Airforce_sf/UbuntuError.jpg[/IMG]

---

### Post by jacob106106 on 2007-11-28
[FONT="Arial"]I ran on a article at: [http://linuxreviews.org/software/desktops/]("http://linuxreviews.org/software/desktops/")

Look for: 4. ***Hardware requirements***
It's not about Ubuntu but hardware requirements for KDE, Gnome, XFCE, ...
Make sure that you read it all !!! These values are general rules of thumb. KDE will start on computer systems who should have been moved to museums long ago, but it will run horribly slow.

Take a look, it's interesting.

Hope it helps ![/FONT]

---

### Post by rpsf on 2007-12-24
I've just completed my first install of Linux on a 7 year old Dell XPST 600. Ubuntu 7.10 installed easily but with only 128MB RAM it is not very useful beyond basic browsing. Lots of disk space- 30GB is wasted when I am unable to work with Open Office or Gimp. Both slow the system to a crawl. 

I suspect 2 total freezes had to do with insufficient memory to even let me switch to the console. ALT F1.  I gave up waiting and rebooted. Could not get to the shell, mouse dead.

Other than that, I like what I see and will upgrade the memory as soon as I can find some cheap old chips.

Lots to like over Windows behavior.

---

