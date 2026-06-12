---
title: "2G surf eeepc/low power systems OS install"
date: 2011-03-31
forum: Hardware
---

### Post by rvndmnmt on 2011-03-31
To begin the story, I bought a 2G surf for a VPN demonstration at work.  After the test was over I was left with this piece of equipment that had little to no utility.  Well I paid $60 for it and I was going to get my money out of it.  

So, through trial and error I came up with a good basic setup for the eeepc that might work well on low power systems. I know of the netbook and Moblin remix.  They ran to slow and took up to much space

Partitioning:(This applies to the 2G surf only)

The biggest gripe about the 2G is space.  2 gigs of hd space courtesy of an SSD isn't big enough to install the OS these days.  One solution that I found on these very forums was to throw a SD card on it then place the /usr partition on it.  While it did make enough space for the OS, space left for files and programs was a little thin.  And just placing the /usr file on a 16GB SD card was a tremendous waste of space.

Let me emphasize that what I am listing here is far from optimal.  If you can do better then do so.  I am comfortable with this setup.  Or in other words "If it ain't broke then don't fix it".  Besides, I have broken things enough on this computer and am at the end of my patience.

I booted up my last X86 system that I have running went through the file system and made a list of the main files from largest to smallest.  My partition table is as follows based on what I saw.

sda: 2GB
/

sdb: 16GB (approx)
swap   =443MB
/tmp   =565MB
/opt   =565MB
/var   =2.56GB
/usr   =4.6GB
/home  =6.1

Why is /home so big?  Because, that is where you store the files and documents that you create or download.

OS:

Since this is a very bare bones system I needed a very bare bones OS.  So the first thing I did was download the minimal image (12.5 MB 10.04) and threw it on a thumb drive.  From there I did a basic install i.e. no packages or desktop.  Just the kernel and a terminal.

From the terminal I installed the following packages.
lxde-core (chosen for its light weight, small size, and small footprint)
lxtask
lxrandr (you might want to be able to move windows around without rebooting)
xorg
dkms (some packages do use this)
joe (easy to use and light weight text editor for the CLI) 
chromium-browser (I don't like the fact that Google is tracking my every keystroke but it's fast and lightweight)
chromium-browser-l10n
network-manager-gnome (yes I know, gnome is a bit bloated however this and the other tools I chose I chose because they work and are fairly easy to use)
gnome-power-manager
system-config-printer-gnome
cups
gnome system monitor
bum
gksu
gparted
ntfsprogs
menu
ntfs-config
software-center (easier to use than synaptic)
leafpad
guake (a godsend with a 7" screen)
prelink
preload
pentium-builder (works with AMD and Intel processors)
microcode.ctl (downloads Intel microcode only, if you have an AMD processor then don't bother with this one)

The last four were included to bump up performance since we're talking dealing with an 800MHZ processor.  But it's always good to have.

After you reboot your system you will notice that you have a nice pretty desktop. However with most things the work isn't over.  Your going to have to open the hood and get your hands a little dirty.  It's just a little, trust me.

First thing is first.  You have to have root access unless you really feel like adding sudo to everything.  So sudo su/sudo -i and get into root.  You don't have to do it, but when your doing this it just makes thing easier.  Just don't forget to type exit when you're done.

Chances are that you noticed that you have no sound.  Seems to be an issue with LXDE.  Type alsamixer -c 0 in guake and it will pull up the sound settings. Hit m. For some reason the sound is muted.  This will un-mute it.

Just because you installed prelink doesn't mean that it's working.  Go into the /etc/default/prelink file and find the line that says "PRELINKING= unknown".  Change that to "PRELINKING=yes".  It should come up on reboot.

On a sidenote.  Dig into the /etc/init.d/rc file and change the line "CONCURRENCY=none" to "CONCURRENCY=shell".  That should also boost performance a bit.

Lastly, startup items.  In LXDE there isn't a GUI to add startup items.  And i'm pretty sure that you noticed that the network manager and power manager haven't come up.  Go into the /etc/xdg/lxsession/LXDE/autostart file and add these two lines to it.

@nm-applet
@gnome-power-manager

That should resolve that.  On another sidenote, just because you don't see the icons on the toolbar doesn't mean they aren't there.  If you click the big open space by the CPU widget you will find the network manager applet.  The power manager applet comes up automatically when you run on batteries.  

And there you have it.  It's not perfect but it's a good, solid foundation to build on.  Initial install occupies a smidgin over 2GB of hard drive space and around 82-85MB of ram.  

As far as boot time.  I time boot time from the time I press the power button to the login screen.  It takes my 2G a three run average of 42.3 seconds.  And this is after I installed all of the software I wanted to install on the machine.  Sounds bad, I know.  But it takes my x64 Gateway with a dual core Pentium @ 2.16GHz a three run average of 39.7 seconds to boot.  Considering the huge disparity between the two chips, that's not bad.  And it's surprisingly responsive to boot.

This has taken about 3 months to compile.  I need the break before I go and recompile the kernel for this machine.  I just hope that someone can make use of this.

---

### Post by dabl on 2011-03-31
Nice writeup -- thanks!

I have a EEE PC 4G/701.  I made a 400MB swap space, and installed aptosid/XFCE on the remaining 3.3GB partition, and as long as I stick with one kernel and use apt-get clean, it lives in about 2.6GB.  My wife likes it.

I would say that you have done about all one can do with 2GB.

---

### Post by rvndmnmt on 2011-04-01
Thanks for the compliment.  And believe me I tried like hell to make this as good as I could.   With all of the partial guides I figured I would make as complete of a guide as I was capable of doing.  I spent the last month on partition issues alone if that gives any sort of indication of the effort I put into this.

So far it's working like a charm.  I have as complete as a desktop as I could hope for.  Figure the people that run some of the earlier machines could use this for a guide as well since it's footprint is so light.  I just hope for some feedback on how to make this a little more complete as I am certain that I am missing something.  Just not sure what that something might entail at this point in time.

---

### Post by dabl on 2011-04-01
Three comments, for consideration:

1. I recall that the SDHC card reader is in reality a USB device, right?  I vaguely recall that it doesn't automatically mount, when you boot the machine?  Or is that working OK?  It would be a problem if the parts of the filesystem that are on the SDHC card weren't mounted and available at boot time.

2. I chose ext2 for the filesystem type, and mount it with the "noatime" option, to avoid the journalling of ext3 and ext4.  Given the non-"mission critical" nature of the netbook, and the early stage of SSD technology, I traded longer SSD life for data recoverability (at least that's what I told myself). It's been working fine that way since 2008.

3. At the time I bought my EEE PC 4G/701, I put a 2GB memory module in it, in lieu of the 1G that came with it.  Then (after a lot of messing around with experimental configurations) I set it up to mount /tmp, /var/tmp, /var/spool, and /var/log in temporary filesystems (i.e. in RAM), to constrain the growth of the OS footprint on the SSD.  I did this after I satisfied myself that the hardware was working correctly -- understanding that the logs disappear when it is shut down.

Mine only runs at 630MHz, so there are limits to its capabilities.  Early on there was an overclocking module with which I was able to run it at 900MHz, but that hasn't kept up with Debian development, and hasn't worked in at least a year.

At one one point, the apt cache got full and it refused to accept an upgrade, so I've learned to use the apt-get clean command religiously.  Other than that, it just keeps chugging along.  I recently replaced the original battery, which was down to about an hour, so once again it's good for 5 or 6 hours.  It runs chromium-browser like a champ, which is the main thing she uses it for.

Thanks again for the nice writeup.

---

### Post by rvndmnmt on 2011-04-01
Yes.  The SDHC card reader is does read as a USB 2.0 device.  I am using a class 10 16GB card.  But that is only good for something like 200 read/writes.  I have noatime set up as an option and have set up half my ram as a ram disk to extend the life of both the SSD and the SD card.  These are the more advanced features I performed on this machine.  I could go more into detail on that.  I also autoclean autoremove pretty religiously.

I went with ext4.  Didn't really think of the issue you brought up since I know I am probably going to have to replace one of the drives in a few months.

---

### Post by dabl on 2011-04-01
One thing you can do with the ext4 filesystem is change the journal-writing frequency.  (Apparently the journal is overwritten on the same block of the SSD every time, thereby accelerating the "wear" on that block).  The default is every 5 seconds.  On my desktop system which is on a UPS and uses a large and newer SSD, I changed it to once every 5 minutes, which translates to a "commit=300" mount option in /etc/fstab.  So the mount line for my root filesystem looks like this:

```
UUID=c70374e7-97b3-4972-a704-285e9343f776     /                    ext4         defaults,noatime,errors=remount-ro,barrier=0,discard,commit=300  0    1
```

The "discard" option won't work on your EEE PC, so don't use that.  It enables trim on newer SSDs.

Correspondingly, I wanted to adjust the "virtual memory" or vm writes, down to the same level as the ext4 journalling.  These are the entries in my /etc/sysctl.conf:

```
vm.dirty_writeback_centisecs = 30000
vm.dirty_expire_centisecs = 30000
vm.dirty_ratio = 50
vm.dirty_background_ratio = 2
```

Google will help you learn the details of the vm tweaks.  Adjust to your personal comfort level.

---

### Post by rvndmnmt on 2011-04-01
Yes.  That will definitely help.  Especially with the fragile SD card.  Guess it's back into the breach lol.

---

### Post by tactus on 2011-04-02
I don't have the 2G, but I do have an Asus EeePC 900 "16G". Actually I am typing on it writing this right now.

What has worked best for me so far is a bare install of Debian Squeeze/6 from a netinstall image. I even run it with full disk encryption (an option that can be choosed during installation). After installation I simply do an apt-get install xorg slim lxde chromium-browser wpagui.

Performance wise the defaults have worked well, only main thing I found helped was to mount /tmp as a tmpfs and symlink chromium cache to /tmp (~/.cache/chromium).

For comparison I've also ran Debian Lenny with full Gnome, FreeBSD 8.2, Zenwalk with XFCE and Puppy Linux (+some more). Of these Puppy was fastest but too non-secure for my liking. Current setup is what I have been most happy with, actually satisfied enough I started using this machine again. I don't think it gets any better. :)

---

