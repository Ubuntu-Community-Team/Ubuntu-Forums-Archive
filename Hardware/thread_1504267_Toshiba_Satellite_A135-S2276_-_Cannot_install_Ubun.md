---
title: "Toshiba Satellite A135-S2276 - Cannot install Ubuntu"
date: 2010-06-07
forum: Hardware
---

### Post by dirtydave on 2010-06-07
I have tried Ubuntu 10.4, 9.10 and Linux Mint 8, all of them hang after detecting keyboard.  This actually is the part where Ubuntu is looking for the hard drive.  Is there an incompatability with the ATI Express 200M chipset?  If so are there any workarounds?

---

### Post by dirtydave on 2010-06-09
Anyone?

---

### Post by WanderingAlbatross on 2010-11-28
Same problem.  Toshiba Satellite A135-S2356.

---

### Post by WanderingAlbatross on 2010-12-15
I ended up making my LiveCD from the windows XP partition on the Toshiba and it worked fine after that.  I didn't like the CD I made on my Dell.

---

### Post by crashbang on 2011-01-25
I am having the same problem with a satellite a105-s2236. It will not boot at all from usb and always acts like it disconnects the dvd drive when reading the HDD. I am stuck on what to do. It will install iDeneb v1.6 and windoze but will not even do a basic text install of debian without freezing. I put a brand new HDD in this craptop and checked it for errors and passed with flying colors. What do I do? This isn't my laptop and I need to get it back to its owner.

---

### Post by IWantFroyo on 2011-01-26
Try the boot options (acpi=off). I have a Toshiba T235D S360 and I had to do that. Esc while livecd/usb is loading, and f6 (boot options) and acpi=off. If you get a menu that lists stuff like: Linux Kernel Generic 2.6.5.1.1, go to the first one (generic) e to edit, and type acpi=off anywhere in there.

---

### Post by crashbang on 2011-01-26
> **IWantFroyo said:**
> Try the boot options (acpi=off). I have a Toshiba T235D S360 and I had to do that. Esc while livecd/usb is loading, and f6 (boot options) and acpi=off. If you get a menu that lists stuff like: Linux Kernel Generic 2.6.5.1.1, go to the first one (generic) e to edit, and type acpi=off anywhere in there.

Thanks but I have tried that, pci=noapci, command only, still nothing

---

### Post by davidmohammed on 2011-01-26
common boot options that you can try are [here]("https://help.ubuntu.com/community/BootOptions").

I don't have your particular model (satellite pro A30) - for my part I have to boot with 'noapic'.

---

### Post by crashbang on 2011-01-27
> **davidmohammed said:**
> common boot options that you can try are [here]("https://help.ubuntu.com/community/BootOptions").

I don't have your particular model (satellite pro A30) - for my part I have to boot with 'noapic'.

Well I had to dig back to 9.10 and was able to get it with noapci plus quiet splash. Thanks all for your help. I guess the newer distros are too heavy for this older machine? :confused::confused:

---

### Post by sidzen on 2011-01-27
1.60Ghz CPU
512MB RAM
A marginal system to begin with, therefore must recommend lubuntu over ubuntu
-----------------------------------------------------------------
A sign of inherent issues re: linux drivers --
[http://www.petitiononline.com/x200MLin/petition.html](http://www.petitiononline.com/x200MLin/petition.html)
[URL="http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide"]
http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide[/URL]
-----------------------------------------------------------------
or, this series of commands worked for one user --

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) 
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

it allowed him to be able to change video resolutions.

---

### Post by crashbang on 2011-01-27
> **sidzen said:**
> 1.60Ghz CPU
512MB RAM
A marginal system to begin with, therefore must recommend lubuntu over ubuntu
-----------------------------------------------------------------
A sign of inherent issues re: linux drivers --
[http://www.petitiononline.com/x200MLin/petition.html](http://www.petitiononline.com/x200MLin/petition.html)
[URL="http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide"]
http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide[/URL]
-----------------------------------------------------------------
or, this series of commands worked for one user --

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) 
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

it allowed him to be able to change video resolutions.

Thanks, but that is the op's system. The one I'm messing with is a satellite a105-s2236.
Intel celeron m 1.6 ghz
2 gigs ram
5400 rpm wd scorpio blue 320 g HDD
Ati something chipset
Booting live looks great with noapci and safe graphics but at reboot is when things get tricky. Freezing on ubuntu logo or freezing after boot up. I'm about to gut this thing or something.

---

### Post by crashbang on 2011-01-28
So after trying openSUSE vesa mode told me that I should try pnpbios=off. Tried that and it then told me there was a problem with the bios. Got the bios update from toshibas site, installed it, and now things seem to be going much better. Will let you guys know if this solves my issues. Hopefully it will save others my headaches lol

---

### Post by crashbang on 2011-01-28
Yes the BIOS update did the trick for this craptop.  It is currently running Ubuntu 10.10 desktop edition with no problems.  I do not really understand what the problem with the BIOS was but it definitely did have a problem with every version of Linux that I tried.  Thanks all for your help.  I hope this thread saves someone the problems that I had.  I am not the OP so I cannot mark this thread as solved.

---

### Post by TrombaMarina on 2012-07-27
I have a Toshiba Satellite A135-S2356 and had to use both acpi=off and noapic in order to boot a Live CD - thanks for the tips!

I also found that the Atheros AR242x / AR542x Wireless Network Adapter works out of the box with 32-bit Ubuntu 12.04, but might not have a driver at all for 64-bit (as of 2012-07-27).  The rest of the system seems to work fine with 64-bit, but since it can't support more than 2GB memory, 32-bit is probably more appropriate anyway.

The word, "Craptop" made me smile.  I'm hoping a solid state drive will help, and that encrypting my home folder won't hurt.  We'll see...

---

### Post by wildmanne39 on 2012-07-28
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

