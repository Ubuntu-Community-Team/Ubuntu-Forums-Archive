---
title: "[SOLVED] Debian installer can't find lpia kernel"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by andrewsimpson on 2008-12-05
I've been trying to install the lpia port on an Acer Aspire One.  The specific port for the Atom Processor is on this page
[http://http://cdimage.ubuntu.com/ports/releases/intrepid/release/]("http://http://cdimage.ubuntu.com/ports/releases/intrepid/release/")

The Aspire One does not have a CD drive, so the install has to be done by USB stick.  You need to use the 'usb-creator' software in Ubuntu to make the USB stick or the installer gets stuck trying to find a CD drive.  The usb-creator software adds a kernel boot parameter to fix this.

The installation goes fine until near the end of the base install, when it throws an error say there is no installable kernel in the apt sources (on the USB stick).  I've filed bug [#305402]("https://bugs.launchpad.net/bugs/305402").

The installer offers to let me install a kernel manually.  By ALT+F2, I can get to a busy-box shell, but I can't work out how to install a kernel.

I've tried the 'Rescue' option, but it looks to have the bug of not running on a USB stick.

So, how do I manually install a kernel?

---

### Post by kerry_s on 2008-12-05
i'm going to assume it's just a deb:

[B]cd /dev/sda?/location/of/deb
sudo dpkg -i name-of.deb[/B]

---

### Post by andrewsimpson on 2008-12-05
> **kerry_s said:**
> i'm going to assume it's just a deb:

[B]cd /dev/sda?/location/of/deb
sudo dpkg -i name-of.deb[/B]

Thank you ):P

Not quite the right answer, but it did help me get there.  After some Google-Fu: To install the kernel you need to run:

```
chroot /target apt-get install linux-image-lpia
```

It looks as though /target is new system (and /cdrom is the USB stick).  The root system is in fact the installer engine.

I then managed to get a base system installed, but the extra packages (X sever) wouldn't install.  However the installer let me install grub, so I've got a minimal system that boots. :D  I seem to have a network connection too. ;)

I'll report back later.

---

### Post by armon_d on 2008-12-07
Please let us know what steps are necessary to get a working ubuntu desktop environment. I am planning on putting 8.10 LPIA on my Dell Mini 9, so it would be helpful to know someone has gotten something similar working.

---

### Post by andrewsimpson on 2008-12-08
> **armon_d said:**
> Please let us know what steps are necessary to get a working ubuntu desktop environment. I am planning on putting 8.10 LPIA on my Dell Mini 9, so it would be helpful to know someone has gotten something similar working.

O.K. I wrote a report on my experiences on the aspireoneuser.com forum, so I'll cross post the important parts of the post here:

Downloaded the iso image and transferred it to a USB stick.  The image boots, but shortly into the install it crashes while trying to find a CDROM drive to install off.  This has been a problem for all the Ubuntu 'alternate' iso's, however there is now a solution:

1. Boot the stick with the kernel parameter "cdrom-detect/try-usb=true"

2. Create the stick with 'usb-creator' which is part of Ubuntu 8.10 default install and this will add the "cdrom-detect/try-usb=true" to the image

Having got past that hurdle, I got midway through the install when installer crashed again with an error message saying 'no installable kernel available'.  There's a couple of [bug reports]("https://bugs.launchpad.net/bugs/305402") already on Launchpad for this one, so it's a known bug.

After much Googling and playing around, I found the answer was to open a shell and install the kernel manually:

```
chroot /target apt-get install linux-image-lpia
```

After that - with lots more crashes - I managed to nurse the installer through a minimal install and get grub installed as a boot loader.  After that I had a bootable system - yay - but not much else.  I had to configure apt manually got the rest of Ubuntu:

```
sudo apt-get install ubuntu-minimal
sudo apt-get install ubuntu-standard
sudo apt-get install ubuntu-desktop
```

Apt didn't seem to know about the kernel so:

```
sudo apt-get install linux-image-lpia
```

The repository has the backports-module with the ath5 wifi modules, but I can't get it to install due to some conflict.  No wireless yet.  No sound either - but I'm sure that's due to my bad install and very fixable.

After my experience, I can't recommend this port for general use.  It's just too buggy and difficult to install.

If you do want to use a LPIA version (which is logical with an Atom processor), the I would look at Ubuntu Netbook Remix 1.01 which is based on Hardy, but apparently works very well. :p

---

### Post by armon_d on 2008-12-08
Thanks for the update. Please keep us posted as you work through your issues. 

I'm not new to linux, but I also don't want to spend 2 weeks getting things working. So, if the LPIA version is simply not ready, I hear that i386 works almost flawlessly. Maybe by Jaunty they'll have the LPIA version working.

---

### Post by armon_d on 2008-12-15
I thought I'd post a status update for anyone in a similar position.

I used the Ubuntu 8.10 Alternate LPIA disk, and as andrewsimpson said, near the end of the base installation it fails with "no installable kernel". Follow andrew's steps, to do the chroot and install the kernel. However, I didn't stop there. In the same console, do 

```
apt-get install ubuntu-minimal ubuntu-standard ubuntu-desktop
```


This will take a long while. It may complain about some dpkg configuration issues, so then do:

```
dpkg --configure -a
```

This may be a little off, but if you read the prompts, it will tell you to run something similar. Once it finishes, return to the installation window. Say either continue or don't, either way it will throw you back to the installation menu. 

Next I did the setup User selection, which creates a user account for you. Then do "Install Grub". Once you select that, you will see it is reconfiguring a lot of packages. This somehow forces dpkg to figure everything out. It will also install GRUB.

Then, finish the installation and allow the system to reboot. For me, the reboot placed me in a graphical environment.
For some reason, the apt sources are all messed up. So, open /etc/apt/sources.list, remove everything, and put the following:

```

deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) intrepid main restricted universe multiverse
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) intrepid-updates main restricted universe multiverse
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) intrepid-security main restricted universe multiverse
deb [http://ppa.launchpad.net/netbook-remix-team/ubuntu](http://ppa.launchpad.net/netbook-remix-team/ubuntu) intrepid main

```

The do a 

```

sudo apt-get update ; sudo apt-get upgrade

```

After that, to get wifi and bluetooth working, do

```

sudo apt-get install linux-restricted-modules-lpia

```

Also, to fix sound do:
```

sudo nano /etc/modprobe.d/alsa-base

```

And append the following:

```

options snd-hda-intel model=dell

```

After another system reboot, you should now have sound, wifi, and bluetooth working. There is a strange issue with the
apostrophe key to fix that, create ~/.Xmodmap and put it in:

```

keycode 48 = apostrophe quotedbl

```

Log out and in, and you should be prompted about loading the Xmodmap file, after which that key works.

Lastly, to be able to enable and disable both bluetooth and wireless search google for dell's "aircraft-manager" package. This does some magic to make that work. I have that mapped to the Fn-2 key (the one with the wifi symbol on it).

Overall, after getting all that setup I've been extremely pleased. Performance is very good, battery life is ~5 hours.

I think that is all I did, since its been a while and I didn't take notes, but let me know if you get stuck on something.

---

### Post by andrewsimpson on 2008-12-15
That all sounds like a very successful install :D

Since my last post, I actually installed the Ubuntu Netbook Remix 1.01 image onto my Aspire One.  That was very nice, but I decided to revert to the lpia port and solve the problems.

So, I installed again.  As always, much easier to do the installation second time around. ;)  This time I did an 'xubuntu-desktop' and it all went well.  I think your approach of loading the packages during the install would have been a good idea. 8)

Of the issues that I had: The sound issue took ages to fix, while I debugged the entire sound chain.  Finally fixed it in a few seconds by turning up *all* the volume controls...!!!  (The sound was muted).

Wifi was fixed by downloading the madwifi source code and compiling.  For some reason the Ubuntu linux-backports-module that is required for my card is currently not available for lpia (buildd failure).

I'm also very happy.  Battery life is good.  The system seems faster though I could be imagining it :)

---

### Post by vicox on 2008-12-22
This is what I did:

After the installation crashed (the first time), I selected "continue". After the second crash, I selected "aboard" and switched to the commandline with CTRl+ALT+F2 and typed

```
chroot /target apt-get install linux-image-lpia linux-restricted-modules-lpia
```

Then I switched back (CTRL+ALT+F1) and selected the GRUB-installation entry in the menu. GRUB got installed, installation finished.

I booted the system, and logged in with the account I've set up during the installation.

Then i edited the sources list with

```
sudo vim /etc/apt/sources.list
```

and made it look like this:

```

deb http://ports.ubuntu.com/ubuntu-ports/ intrepid main restricted universe multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ intrepid-updates main restricted universe multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ intrepid-security main restricted universe multiverse

```

Then:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-standard ubuntu-desktop

```

After reboot, I had a "normal" Ubuntu running. Works great, but frankly, I don't see any differences. Battery life is the same, and the system doesn't seem faster to me.

armon, how did you manage to get 5 hours battery life? :)

---

### Post by armon_d on 2008-12-22
You might want to check you battery. Apparently the ones made in Korea are 24 kWh and the Chinese batteries are like 32 kWh, or something along those lines. I did also do some additional optimizations, which may contribute the battery life.

I can list some of them:
In grubs menu.lst, add to defoptions

```
elevator=noop rootflags=data=writeback nobh commit=60
```

altoptions should also have 

```
rootflags=data=writeback
```

If you add rootflags, you need to do the following
```
sudo tune2fs -o journal_data_writeback /dev/sda1
```
for each partition

Add to /etc/rc.local

```
hdparm -W1 /dev/sda
```

Mount your root/home partitions with the following options:
noatime- don't write access times for files
nodiratime - don't write acces times for directories
commit=60 - change the meta-data commit interval from every 5 to 60 seconds
data=writeback - change the method of writing, see the grub modification and the tune2fs command
nobh - Something about writing buffer headers(?)

Add the following to fstab:
```

tmpfs      /var/log        tmpfs        defaults           0    0
tmpfs      /tmp            tmpfs        defaults           0    0
tmpfs      /var/tmp        tmpfs        defaults           0    0

```

This mounts those directories as tmpfs, which means they are kept in memory. I have 2 gigs of RAM, so I wouldn't recommend this if you have 512. This reduces writes and reads from disk.

If you mount /var/log as tmpfs you need to modify /etc/init,d/sysklogd to comment out the existing fix_log_ownership() function and add this one instead:
```

fix_log_ownership()
{
        for l in `syslogd-listfiles -a --news`
        do
                # Create directory for logfile if required
                ldir=$(echo ${l} | sed  's/[^\/]*$//g')
                if [ ! -e $ldir ] ; then
                        mkdir -p $ldir
                fi
                # Touch logfile and chown
                touch $l && chown ${USER}:adm $l
        done
}

```

And add to /etc/rc.local
```

for dir in apparmor apt cups dist-upgrade fsck gdm installer samba unattended-upgrades ; do
        if [ ! -e /var/log/$dir ] ; then
                mkdir /var/log/$dir
        fi
done

```

To optimize memory use, I added the following to /etc/sysctl.conf
```

vm.swappiness=1 (Strongly discourage swap)
vm.vfs_cache_pressure=50 (Prefer FileSystem cache)

```

---

### Post by Takilian Rueshin on 2008-12-28
Hi,
I followed the procedure described by vicox. Everything worked well, except the cable network (the wifi works well).
The NetworkManager applet behaving strangely, here's a screen-shot.

[img]http://www.amicidnd.info/forum/gallery2/main.php?g2_view=core.DownloadItem&g2_itemId=3274[/img]
*(Wired Network - unmanaged device)*

Although not detect any cable network, can connect via cable.
Moreover, before turning the system must connect the cable, otherwise the system remains pending for more than two minute in this way:

[[img]http://www.amicidnd.info/forum/gallery2/main.php?g2_view=core.DownloadItem&g2_itemId=3280[/img]](http://www.amicidnd.info/forum/gallery2.php?g2_itemId=3279)
*(Configuring network interface)*

Do you have any tips that can help me?


PS. thank you very much for the excellent work that you've done.

---

### Post by cjwatson on 2009-03-31
I've just merged Emmet Hikory's work to fix this bug in Jaunty.

---

### Post by lordnisse on 2009-04-02
I'm still stuck at the "common CD-rom detect failed", even using latest Alternate Lpia build (2 March).
I tried in every way, from USB stick using "cd-rom-detect/try-usb=true", from an external USB-CD, and the result is alway the message:
"No common CD-ROM drive was detected".

Do you have any clue?

---

### Post by cjwatson on 2009-04-02
> **lordnisse said:**
> I'm still stuck at the "common CD-rom detect failed", even using latest Alternate Lpia build (2 March).
I tried in every way, from USB stick using "cd-rom-detect/try-usb=true", from an external USB-CD, and the result is alway the message:
"No common CD-ROM drive was detected".

Note that it's cdrom-detect/try-usb=true, not cd-rom-detect/try-usb=true. Spelling matters.

Anyway, this is [bug 347458]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/347458"); it just needs the installer to be rebuilt against the new kernel.

---

