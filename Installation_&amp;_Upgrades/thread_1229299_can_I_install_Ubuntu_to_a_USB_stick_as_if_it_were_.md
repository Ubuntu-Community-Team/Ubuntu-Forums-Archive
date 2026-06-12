---
title: "can I install Ubuntu to a USB stick as if it were a hard drive?"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by KinKiac on 2009-08-01
Hello.  I am writing this to ask if anyone out there knows of any reason why I would not be able to install Ubuntu to a USB stick as if it were my HDD.  What I want to do is have a working OS, that can use pretty much any hardware(at least those supported by ubuntu) using a 16 or 32gig thumb drive.  

I am NOT looking to do this for any illegal reasons as Ive heard mentioned in another thread regarding this same topic.  I just think it would be cool(there's the geek in me talking again, lol) to have a working OS that I can bring over to my friends houses, or parents place/aunt and uncles or whatever, where I can showcase my OS as well as some of the software I have.  

Id really love to get compiz to work off of a thumb drive, although Im pretty sure Id have to somehow work out how I would install the video drivers on the fly.  Im thinking I could maybe have as many drivers as I can sitting in a folder on the thumb drive, and just have my system install the proper one at startup automatically.  

The compiz thing may be pushing it a bit, but Id like to try anyway for the fun of it.  

Anyway, I have found a tutorial(many actually) that shows how to install Ubuntu on a thumb drive and they all seem to utilize a casper -rw loop file to save changes.  Here's the link:

[http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)

There is others on this site depending on how you want to install it.  The only problem I have with this approach is the need for the casper file.  Why cant I just treat my thumb drive as if it were an HDD?  

The reason I have a problem with this is that this approach seems to only allocate 1-4gb for saving changes.  I want to get this going on a 16 or 32gig thumb drive which could hold almost all of my files.  Currently Im using a 20gig partition on my HDD at home for my Ubuntu which seems to be plenty for the OS itself(I store music and other files on another drive).  Why cant I use a 32gig thumb drive for the same thing?  Why is there a need for the casper file to save changes?  cant I just install to a pre-formatted thumb drive in the same way I installed to my HDD?  If not, why?

I realize I may be asking a bit much here, but any answers at all would be greatly appreciated.

Thanks
Kin'

---

### Post by Mighty_Joe on 2009-08-02
See my post [in this thread]("http://ubuntuforums.org/showthread.php?t=1193680") for some links to instructions for doing a full install to a USB drive.  I'm typing from one right now 8)

---

### Post by Herman on 2009-08-02
I always just install Ubuntu to USB flsh memory sticks as if the USB flash memory stick was a normal hard disk drive. All the newer version of Ubuntu will set up their x server automatically on boot-up like a live CD so they'll boot fine and show a good display in almost any computer.

You can take some anti-wear measures later if you want.
A few anti wear measures may give you a little speed boost, that's the only reason I bother with them. I like to have a swap area but set the swappiness to 10. I found that with no swap area my systems were slow. WIth swappiness set to 10 the system will prefer to use the RAM but it can still use the swap if it really needs to. 
I like to use either reiserfs or ext4 file systems for their speed.
I use noatime in fstab and also set the noop ioscheduler as a kernel option in GRUB.
Those tweaks are optional and only if you feel like doing some extra work.
I have lots of old USB flash memory sticks that have had many installs of Ubuntu in them and none of mine have worn out yet. I have only recently started trying out some of those tweks for extra speed, not as anti wear measures. I only use the USB installations occasionally though, I don't use them as my main operating system.
I also have an EeePC with a 4 GB flash SSD drive that I leave on 24/7 and it's still fine after a year.
Details about how I set my flash OSes up at the bottom of this page, [Ubuntu Karmic Koala Encrypted Flash Memory Installation]("http://members.iinet.net/%7Eherman546/p19.html"). (I don't recommend Karmic to new users yet, most people should probably use Jaunty or earlier).

Anyway, when USB3 comes out in a few more months you'll want to upgrade to a USB3 flash memory stick after a while when the price comes down, so why worry about flash memory wear? Just install Ubuntu and enjoy it.

That's my 2 cents worth anyway.
Regards, Herman :D

---

### Post by ArmenianLeader4 on 2009-08-02
Yeah, you can start it up from a USB. When you see your loading screen when you first turn on your computer, click F2 or F12 or whichever the option is for you. Go down to your BIOS setup in the screen and de-select all booting options other than your USB, which should already have Ubuntu on it. be careful when install ubuntu onto an external memory card, disc, or HDD, because you could end up with a glitch like I did here:
[http://ubuntuforums.org/showthread.php?t=1229760](http://ubuntuforums.org/showthread.php?t=1229760)
Otherwise, if you can get it to work without it glitching, you can just pop your USBB into any normal slot on your computer, de-select all other booting discs except for the USB, and just go. Everything should work like normal.

---

### Post by KinKiac on 2009-08-05
Cool, thanks guys!  Well, so far I have been successful in booting to a USB drive, although I keep messing it up, lol.  Here's a description of my experience for anyone out there who might come across this thread looking to do the same.

The first time i tried was actually onto a 4gig SD card from my cellphone.  I installed a full version in the same way as i did my initial install.  I just booted to a live CD, selected install, then partitioned and formatted my SD card(it came with a usb card reader that is about the size of a thumbnail, which seems to work just like a thumb drive) and installed like normal.  The only problem I had with the SD card is lack of space for a full install.  I set aside 1 gig for swap and ended up with only maybe a gig or so left after the install.  

You have to be careful though when installing that 1, you install to the right drive and dont overwrite your Ubuntu or windows and 2, that you dont overwrite your MBR or grub on your internal drives.  So, I had to make sure when I got to the last step before starting the install that I selected advanced and told the boot loader to install on the SD card.  After the install it booted up perfectly.  The one thing I noticed though was that updating and installing was a bit slow, however downloading and browsing the web was almost as quick as on a HDD.  So, after being successful on my first attempt, I decided that I wanted a bit more room and went out and bought a 16gig thumb drive(w/lifetime warranty so if it wears out Ill just return and replace).  

Immediately I ran into another problem and had to do some research to get it boot properly.  Apparently(I say this just because I didnt know this previously) my BIOS and most other BIOS's can only read the first 1024mb or so of a disk for the kernel and boot loader on older disks(and apparently thumb drives) the first 8gig on newer drives, or so Ive read.  What that means is that if the /boot directory does not fall within the first gig of that drive, that you cant boot properly.  I ended up after a few tries just creating a boot partition as my first partition on the thumb drive and assigned 1gig for just that, then 14gig of ext3, and another gig for swap.  This time it booted properly.

Then came the crash, lol.  I had been using my roommates laptop to install as he was using my TV at the time I started(my LCD TV is my only monitor for my PC ATM) and we didnt have a plug for it near where we had our router, so I was running off of battery power when trying to download and install updates.  It was taking a long time as there was a lot of updates that needed to be installed(my live disk version ends in 11, the newest version of jaunty ends in 14) and the thumb drive seemed to take a long time to apply the updates.  The battery was holding up fine at first, but them my roommate came by and hooked up his iphone to the laptop for charging.  By this time I had started using my PC for other stuff while I waited for the laptop to finish.  I didnt notice that when he plugged in the iPhone it totally drained the laptop battery and the laptop shut down in the middle of updating my thumb drive.  Needless to say the installation is now corrupt and I am going to have to re-install, no biggie since it is just my thumb drive, its just time consuming.  

On the bright side i think i am going to try using ext4 to try to speed it up a bit and may look into the other suggestions as well.  

Thanks again for the responses guys, its greatly appreciated.

---

### Post by Mighty_Joe on 2009-08-06
If you have enough memory (1Gig+ for web browsing, using Open Office, listening to music, etc.) do not create a swap partition.  First, USB is slow so swapping will slow down your system.  Second, flash drives can wear out, so the fewer writes you do (reads don't count), the better.  
See the link in my post above for more configuration hints, like moving logging to /tmp.

---

### Post by KinKiac on 2009-08-08
> **Mighty_Joe said:**
> If you have enough memory (1Gig+ for web browsing, using Open Office, listening to music, etc.) do not create a swap partition.  First, USB is slow so swapping will slow down your system.  Second, flash drives can wear out, so the fewer writes you do (reads don't count), the better.  
See the link in my post above for more configuration hints, like moving logging to /tmp.

Actually Im not sure what PC('s) I may be using it on so Id like to keep the swap space just in case.  What Im going to do though is set swappiness to 10, like Herman said, so that the system will prefer RAM, but will swap when needed.  Also, Im not worried about the wear and tear.  This installation is not going to carry anything that isnt already on my home PC, it will act more like a portable extension, so if it ends up dying someday, I wont be losing anything.  Also, I paid extra for the thumb drive (100$ total for a 16gig drive) to get a lifetime warranty from the manufacturer as well as I get a 3 years extended warranty from the store I bought it at, they will replace it no questions asked for three years if it dies due to wear and tear.  By that time USB 3.0 will be out and Ill have bought a new thumb drive to use.  From what Ive read so far a full install is what I want and need, not a persistent Live boot.  Thanks for the suggestions though.

---

### Post by dE_logics on 2009-08-09
> What I want to do is have a working OS, that can use pretty much any hardware(at least those supported by ubuntu) using a 16 or 32gig thumb drive.

No, the Ubuntu that you install on 1 PC does not necessarily work on all.

The main bummer is the graphs chip.

> to have a working OS that I can bring over to my friends houses, or parents place/aunt and uncles or whatever, where I can showcase my OS as well as some of the software I have.

No...you have to use the live CD for that...or I think installing all possible video drivers will help.

If you want to do illeagle stuff, why not try backtrack?...the live CD is fantastic...ok not illeagle (:P) but generally. It looks great too with it's KDE interface.

---

### Post by Herman on 2009-08-09
> No, the Ubuntu that you install on 1 PC does not necessarily work on all.
The main bummer is the graphs chip.
:) What you're saying was true before Hardy Heron came out. Before Hardy Heron we used to need to run 'sudo dpkg-reconfigure xserver-xorg' after booting in a computer with different hardware. Advances in the X-server technology that came in with Ubuntu Hardy Heron changed all that.
Hardy Heron uses [Xorg 7.3]("http://www.ubuntu.com/getubuntu/releasenotes/804overview#head-34da8c8d2432823a293ea6a0639fe8b9a24c0f77")  Xwindow system from [X.Org Foundation]("http://www.x.org/wiki/"), Intrepid Ibex uses  the latest [X.Org 7.4]("http://www.x.org/wiki/Releases/7.4"), Xwindow system from [X.Org Foundation]("http://www.x.org/wiki/") and Jaunty Jackalope was using  [X.Org]("http://www.x.org/") server, version 1.6, the last time I checked.
You should be able to easily boot a normal installation of Ubuntu in a USB flash memory stick in just about any computer now and it'll be fine. Try it!  :)

---

### Post by drbin on 2009-08-09
YES! Absolutely. I first tried it using 8.04. Since i'm a very scared admin, running any possible os for many decades, I introduced myself to the following practice :
1. get a laptop and remove the internal disk (its only 2 screws anyway)
2. get a usb case, and place in it an HD - sata or ide - both work
3. plug the usb and boot from live cd. The only available drive is your USB
4. run the installer, cant fail. actually never failed.

When I bought a new laptop, I used the same usb to boot. Worked better with the new (and improved) h/w

I also used the external drive, to replace the internal after some time. Had no glitch whatsoever. If that's what you want to do, make sure that the usb drive is the same typelike ide or sata.

Lately I dd my usb ide to sata cause the new laptop had sata as internal disk. I didnt expect any error and got no errors either.

For some reason, ubuntu works too good with any configuration. Maybe I'm lucky but besides winmodems I had no problems with h/w. and I also do this for a living.

ps: after the introduction of the utility (the ubuntu built in, under Administration, to install directly from ubuntu to usb, I'm not using cd's anymore for new installations. its much faster just to boot from the stick and install the system. Prerequisite : the pc must be able to boot from usb, like 3-4 year old systems.

hope this helps

---

### Post by rubie on 2009-08-24
> **KinKiac said:**
> Immediately I ran into another problem and had to do some research to get it boot properly.  Apparently(I say this just because I didnt know this previously) my BIOS and most other BIOS's can only read the first 1024mb or so of a disk for the kernel and boot loader on older disks(and apparently thumb drives) the first 8gig on newer drives, or so Ive read.  What that means is that if the /boot directory does not fall within the first gig of that drive, that you cant boot properly.  I ended up after a few tries just creating a boot partition as my first partition on the thumb drive and assigned 1gig for just that, then 14gig of ext3, and another gig for swap.  This time it booted properly.

Hi KinKiac. Did you use the installer to do this? Can you please describe in more detail the installation steps?

---

### Post by Mighty_Joe on 2009-08-25
> **rubie said:**
> Hi KinKiac. Did you use the installer to do this? Can you please describe in more detail the installation steps?

In the partition step of the installer you are given the choice to use a default configuration, to reformat the drive and use it exclusively for Ubuntu or to manually configure the partitions.  Choose to manually configure.  Have a look at: [HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

---

