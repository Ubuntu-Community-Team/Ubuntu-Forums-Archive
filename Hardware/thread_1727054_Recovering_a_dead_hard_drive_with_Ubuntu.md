---
title: "Recovering a dead hard drive with Ubuntu"
date: 2011-04-12
forum: Hardware
---

### Post by Ghosthaven on 2011-04-12
I hope I put this in the right area.

To give you an idea of my knowledge, long time computer user. I've been using Ubuntu for a couple
years now but only on virtual machines and the typical Family Tech Support Guy uses. I'm learning
the CLI but I'm more comfortable with GUI programs still.

I've recently had a Windows hard drive start clicking, booted from a Ubuntu 10.10 LiveCD to check SMART,
yup... hard drive is dying.

I can still access the data but it clicks and is quite slow, so I figured I'd better get that data off of there as
soon as possible.

I just purchased a new 1TB drive (which should be here in a day or two) so I'm trying to plan exactly how to do everything.

I'm aware that I'm on the clock now, the drive could fail completely in 10 minutes of use, or 10 weeks.
So I've currently got the drive disconnected, awaiting my new drive.

I've been studying these forums and google in general trying to come up with the best way to get the data
off my drive. I've come up with a few solutions but I'm not sure if my data is outdated, or if there are better
ways of doing it.

Here's what I have so far:
Option 1: Use a LiveCD (or USB) to copy the data, folder by folder from the drive.
   Upside: I'm sure to get the most important data first.
   Downside: I will have to do a complete reinstall of windows and set everything up from scratch.

Option 2: Use GNU ddrescue to image the drive on to my new drive.
   Upside: ddrescue can recover even off of bad sectors, and won't abort if it encounters an error or
                corrupted data.
   Downside: What do I do with the disk image once I have it? I'll have a drive with nothing but a single
                     huge iso on it with no way of installing it FROM that iso.

Option 3: Figure out a way to make a disk-to-disk mirror of all the data.
   Upside: I won't have to bother with imaging and then restoring from image. If nothing is too horribly
                corrupt, I'll basically just be able to plug the drive in and turn the computer on and it'll be as if
                nothing ever happened.
   Downside: I don't know how. I think dd can do this, but it will abort when it encounters an error, unlike
                     ddrescue. I've looked and looked but I see nothing in ddrescue that will allow this option.

So there is where I'm at... trying to decide between the three. I really don't want to do option 1 as there's
always a chance that I'll miss something, or won't remember how I did something. On top of that, I don't
believe I have all the original discs anymore (danged windows drivers! I wish they would learn a lesson
or two from linux).

I don't mind having an image (option 2) but again, what do I do with it? I have no place to put a 1TB
file that I can then use to restore data on to my new drive. Is there a way to split up an image to burn
on to dvds (ouch 240 dvds. Worth it though) and then restore from those, with it prompting me to insert
a new disc as needed? All options I've seen for splitting image files requires the files to be recombined
before restoring from it.

Again, Option 2... will the image file by the size of the original drive? If it'll be less than the roughly 1TB
of data on the old drive (say, 750GB), then I can possibly borrow someone else's computer to store it
on then attempt to restore via LAN.

Also with Option 2: I know its possible to mount an image file. Is it possible for me to go into that mounted
file and delete un-needed content, thus reducing the size of the file? Or is a mounted image read-only?

As far as Option 3: Anyone know a error-friendly way of mirroring one disk on to another?

A possible option 4: There are recovery discs out there for windows, like Hiren's Boot CD that has a
bunch of windows recovery software on it that can do some of this stuff. Has anyone had better luck
with something like that then using linux tools?

Finally, I'm considering using a liveUSB instead of a LiveCD, as it should read the flash drive faster
and generally do everything faster, thus increasing the chances of me getting my data before the drive
dies. Am I right in this assumption or does it not really matter?

Sorry for the long post, but like all of you, my data is important to me (although it seems not important
enough to get through my thick skull that I needed to backup ages ago).

Thank you for any insight you can provide.

---

### Post by dandnsmith on 2011-04-12
Have you looked at [this guide to ddrescue used](http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html)?

You can mount the iso image, but not delete stuff (it wouldn't reduce the size, even if it appeared to delete stuff)

I don't think LiveUSB would be faster - excepting for the initial load, but you could use usb connected devices to receive the data.

I've no idea what the best solution is, but you could also consider partimage.

HTH

---

### Post by LostFarmer on 2011-04-12
ddrescure will copy partition to partition , do not have to make a image file. With partition to partition the new will be bootable or what not.  The new partition must be large enough to hold all the old partition data. Be sure to use the logfile.
'ddrescue -n /dev/hdd8 /dev/hda4 logfile'   hdb8 is from and hda4 is to , basic command.

---

### Post by Ghosthaven on 2011-04-12
Thanks for the reply guys...
LostFarmer: I just want to make sure that we're both talking about GNU ddrescue, installed with sudo apt-get install gddrescue.
Not the older and obsolete ddrescue installed with sudo apt-get install ddrescue, right?

dandnsmith: Thanks for the guide, I had actually saw that one. It uses the older version of ddrescue though,
and several other guides and sites recommend not using it in favor of GNU ddrescue.

Don't you hate when two programs have the same name?

---

### Post by Gaming4JC on 2011-04-12
or... you could just use CloneZilla? Little easier imo... :)
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by Wiebelhaus on 2011-04-12
> **Gaming4JC said:**
> or... you could just use CloneZilla? Little easier imo... :)
[http://clonezilla.org/](http://clonezilla.org/)

This is the bomb but if it's a mechanical failure which is what it sounds like , there will be no successful software level solution.

---

### Post by fela on 2011-04-12
My advice is go with manual file copy, in the order of data importance.

Why? If your disk has a bad bit on it, using ddrescue to go through the whole drive byte for byte might trigger the bad bit, causing the drive to fail permanently.

---

### Post by LostFarmer on 2011-04-12
Not sure, I use Mepis to transfer my Ubuntu partition .  From terminal 'ddrescue --version' it says GNU ddrescue version 1.2 Copyright (C) 2006 Antonio Diaz Diaz. .  I looked in Synaptic and both ddrescue ver 1.13-3and gddrescue ver 1.2-1.3 are installed but trying to run gddrescue -command not found. Looking at versions I would guess gddrescue ??

---

### Post by luis6268 on 2011-04-19
I just want to make sure that we're both talking about GNU ddrescue, installed with sudo apt-get install gddrescue.Not the older and obsolete ddrescue installed with sudo apt-get install ddrescue, right
___________________________
[Mortgages](http://www.wisebuy.co.uk/)
[Mortgage](http://www.wisebuy.co.uk/)

---

