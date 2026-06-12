---
title: "Choosing which SSD to install Netbook Remix on"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by jmacg on 2009-10-31
I have an Asus Eee PC900 with a 4Gb (boot) SSD and a second 16Gb SSD. I know from experience with Eeebuntu that having the OS and all the applications on the 4Gb SSD is not practical - it's not big enough.

I want to try Ubuntu 9.10 Netbook Remix on this machine and would like to know whether the installation process from a Live CD USB drive gives me an option to either (a) install the OS and apps on the 16Gb SSD or (b) install the OS on the 4Gb SSD and apps on the 16Gb SSD.

Is it a simple point and click process to do these installations, or do I have to do stuff at the command line? (I prefer not to do command line stuff if I can help it - I'm not a confident Linux person.)

I can use a utility on my Eeebuntu install flash drive to delete all partitions from both SSDs before I start.


Any answers and tips would be appreciated

Any comments on the stability of the 9.10 Netbook Remix would also be appreciated.

---

### Post by earthpigg on 2009-10-31
back up your important data before proceeding, of course.

nothing requiring command line. select 'manually partition' during the install process. make sure your / partition (the one that you set the 'mount point' to be '/') has the 'bootable' flag.

towards the end, click 'advanced' and choose which hard drive to install the bootloader onto.

give it a shot. you may be underestimating yourself. since your data is backed up, you have nothing to lose as a result of a failed install. it isn't like anyone is charging you money for the LiveUSB, after all. :D

if you have problems, post back and we can help you.

---

### Post by jmacg on 2009-10-31
Thanks for coming back so quickly with some help.

I'd appreciate some clarifications:

"make sure your / partition (the one that you set the 'mount point' to be '/') has the 'bootable' flag."

What is the 'mount point'? Is it the place where the OS is? 

Is the 'bootable flag' something that's obvious? What should I look for?

I guess it should be reasonably straightforward if I have both the OS and the apps going onto the 16Gb drive, but I gather it would be advantageous for the OS to go on the 4Gb drive, I think because it's a faster drive. If I did this, I would want as much as possible other stuff (certainly the apps) to go onto the 16Gb drive. 

How easy is it to do this? If it's tricky, I might be better to just put everything on the 16Gb driveand just use the 4Gb drive for storing data. I looked at this mixed destination option for Eeebuntu, and it it was anything but straightforward for a Linux noob.

I'm about to set the netbox remix downloading and go to bed - I'm in NZ. I'll try installation tomorrow.

---

### Post by earthpigg on 2009-10-31
hi,

setting the mount point is the closest thing to setting the drive letter that exists in linux. but not exactly. ***everything*** has a mount point. when you put a thumb drive in, it typically will be /media/disk or something similar -- instead of "E:\" or something like that.

/ is the root filesystem. where the OS and the rest is. sounds like you want that on your 4gb.

for what you want, you could set the 16gb partition to have a mount point of /home.

---

### Post by shaggy999 on 2009-10-31
My recommendation would be to put:

/ - first drive
/home - second drive
swap - second drive (if you need it, I have 2 gigs of RAM on my 900a and don't use swap)

You'll have to select manual partitioning and configure all of this setup yourself to do this.

---

### Post by jmacg on 2009-10-31
I installed Netbook Remix this morning, opting to put all of it on the larger 16Gb drive. When starting up, it gave me exactly the same problem I had when I did the same thing with Eeebuntu:

First of all I get the American Megatrends bootup screen, which stops at the message 'Press F1 to resume. When I press F1, I see:

Grub loading stage 1.5
Grub loading. please wait...
Error 22.

When this appeared with my Eeebuntu installation I thought that maybe it was still trying to boot from the 4Gb SSD. I tried to turn the 16Gb into the boot drive in the bios, without success.

I then thought that if I couldn't change the boot drive, perhaps I should choose the third installation option, in which I'd define which drive the OS should be (I wanted to put it on the 4Gb drive) and which drive the rest of the stuff should be. This option was labelled 'advanced' and frankly, going through that process, I had no idea what to choose among the options that were offered.

These installation options were identical on Netbook Remix.

I will take screenshots of the various options and construct a more useful 'help' message. That might take a day or three.

Certainly one way or another, it seems to me that both Netbook Remix and Eeebuntu would benefit from having a clear text description, or even better, a totally automated click-through process that allows for someone who wants the keep the OS on the 4Gb drive and put as much as possible of the rest (certainly the apps) on the 16Gb drive. (I'm using the drive sizes as in the PC900, but the general principle is to be able to easily sort things out between the two drives on a two-drive netbook.)

---

### Post by jmacg on 2009-10-31
Further to my post above, -  shaggy999 and Earthpigg's responses came in while I was writing my post and I missed them.

Thanks for the information about / and /home. 

I don't, at this stage, understand how to do the installation so that / goes on the 4Gb drive and /home goes on the 16Gb drive.

To be honest, I could live with having everything on the 16Gb drive, as I really have space to burn on that drive, and on a separate 16Gb SD card. It might be easier than trying to figure out how to spread things over both the drives.

That was my thinking when I decided to install Netbook Remix on the 16Gb drive this morning. But as I described in my previous post, this isn't working for me either, as the machine is refusing to boot.

---

### Post by Mylorharbour on 2009-10-31
jmacg,

You may wish to consider reverting to Jaunty(?) for now.

[http://forum.eeeuser.com/viewtopic.php?id=78533](http://forum.eeeuser.com/viewtopic.php?id=78533)

---

### Post by jmacg on 2009-10-31
Reverting to Jaunty wouldn't solve my basic problem - I can't boot at all, let alone worry about how long the boot takes!

But the general comment about Ubuntu 9.10 is noted.

I'd actually be happy to go back to Eeebuntu 3.0 (based on Ubuntu 9.04) if I could sort out these issues. I just thought I'd try Netbook Remix to see it would work where Eeebuntu didn't. 

I liked Eeebuntu until the fact that everything was on my 4Gb drive created insurmountable problems of lack of space. I had to pare my applications right back and eventually there wasn't even enough room to do security updates.

---

### Post by shaggy999 on 2009-11-01
Part of the reason why you can't boot might have something to do with the files critical to bootup are past the 1024th "cylinder" when you install the entire OS to a single partition. The fix for this is to create a separate partition for /boot.

It is really easy to do this and what has been mentioned above.

During the install process it will get to the point where it asks about where to install it. Select "Manual Partition". Delete all the partitions off of your drives so have a fresh slate.

Tell it to create a partition of maybe 256 MB on your first drive. Then go into those settings and set it as ext2 or ext3 and in the dropdown box tell it to mount to /boot.

Now create a partition that fills up the rest of that 4 gig drive, tell it to format as ext3 or ext4 and tell it to mount to /. This gives about 3.75 GB for the OS + Apps which is plenty, IMHO

Then create a partition on your secondary drive equal or greater than the amount of your RAM. Tell the system to use it as swap. This step is optional as you may not want swap.

Then create a partition on your secondary drive that fills up the rest of the space and set it to ext3 or ext4. Then in the dropdown box tell it to mount to /home. This is where all your user files will go so you get a whole 16 gigs if you don't have swap which is tons of space.

Later on during the install there is an "advanced options" button. Click it and in the window that opens up just make sure that the bootloader is being installed to your first hard drive's mbr. You shouldn't have to actually change the value unless something quirky happened.

---

### Post by shaggy999 on 2009-11-01
BTW, you will really want to put the OS on the 4 gig drive anyway as the 4 gig drive is a lot higher quality and faster than the 16 gig drive. Asus designed it that way. A small, quick drive to put the OS on and a bigger, slow, lower quality drive to put the user data files on.

---

### Post by jmacg on 2009-11-03
Thanks shaggy999 and others for all your help and suggestions. However I've wimped out. Although you said doing those things was dead easy, it wasn't easy for a non Linux expert. I started to do the manual setup things, but I was presented with more options I didn't understand. I was going to have to ask a whole lot more questions.

So first, I decided to try installing Eeebuntu 3.0 Base again on the 4Gb drive - i.e. accepting the default. I had earlier, however, deleted all partitions with GParted, so at least I was starting out with a clean slate. It installed OK (and it boots - yay!) and I was able to add the extra apps I wanted and still have a little over 1Gb to spare.

I'm hoping this will be OK for me now. I suspect that my first installation of Eeebuntu 3.0 Base, several months ago, didn't reformat the 4Gb drive and it retained a fair bit of stuff left over from the original Xandros installation.

The only thing that isn't right, and I'm hoping someone can tell me how to fix, is that when I reboot, I get the American Megatrends screen, which ends with a "Press F1 to resume" message. How can I make it move on automatically, without pressing F1, as it always used to?

---

