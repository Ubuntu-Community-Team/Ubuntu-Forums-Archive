---
title: "NAS advice"
date: 2011-03-11
forum: Hardware
---

### Post by foxy123 on 2011-03-11
I wonder if anyone could recommend a good NAS? I've never used/bought it before so I do not know what things are important. Something not awfully expensive.

---

### Post by papibe on 2011-03-11
Tell us a little bit more.

What do you need the NAS for?
Do you have any specific space requirements (like how many Gigs)?
Do you have a budget?
Do you have apartment space limitations (little NAS box, vs. a PC)?
etc....

In my case, I bought a refurbish PC (~ $150), installed Ubuntu Server, and use both Samba ans NFS. After a while I had to buy a bigger hard drive, though.

Regards.

---

### Post by foxy123 on 2011-03-12
> **papibe said:**
> Tell us a little bit more.

What do you need the NAS for?
Do you have any specific space requirements (like how many Gigs)?
Do you have a budget?
Do you have apartment space limitations (little NAS box, vs. a PC)?
etc....

In my case, I bought a refurbish PC (~ $150), installed Ubuntu Server, and use both Samba ans NFS. After a while I had to buy a bigger hard drive, though.

Regards.
Cheers a lot for the response :)

I'd like to use it to store backups and media files, like music, photos, videos etc. and probably some shared stuff. In terms of capacity I am thinking about 1Tb for a start with a possibility to add some more in future. Moneywise, I would not like to spend more than £100-150, including the drive.

I was thinking about buying a cheap PC and use it as a storage/server, but it will take more space, consume more electricity and may be noisy, which is irritating.

---

### Post by foxy123 on 2011-03-25
Any advice? I have looked at Ebuyer website and there are so many of NAS there that it is hard to choose.

---

### Post by ottosykora on 2011-03-26
look for NSLU2

this is not very fast, but versatile, since the drives can beconnected simply by usb port.

---

### Post by coffeecat on 2011-03-26
> **foxy123 said:**
> Any advice? I have looked at Ebuyer website and there are so many of NAS there that it is hard to choose.

I have the 1TB version of the MyBookWorld.

[http://www.ebuyer.com/product/160490](http://www.ebuyer.com/product/160490)

It works well with my mixed network of Ubuntu, MacOS, Windows and a Sony PS3. If you put music/videos/pictures in the Public folder, the PS3 sees it as a streaming multimedia server.

One little wrinkle if you're running Lucid or Maverick. You need to apply a couple of the tweaks in the OP of this thread before Ubuntu connects to it reliably:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

In particular you need to add netbios name to smb.conf and install winbind and add the "wins" option to the hosts line of /etc/nsswitch.conf. Make sure you have installed the samba package before you make those edits.

---

### Post by foxy123 on 2011-03-26
Thanks a lot, guys. MyBookWorld looks quite nice and value for money. As alternative I am thinking about buying [COLOR="DarkRed"][Netgear STORA MS2000 2-bay NAS Enclosure]("http://www.ebuyer.com/product/225067")[/COLOR] and two [COLOR="DarkRed"][Seagate ST31000528AS 1TB Hard Drive SATAII 7200rpm 32MB Cache]("http://www.ebuyer.com/product/158798")[/COLOR] hard drives. As I understand you can install Debian on Netgear. Also you can have two backups simultaneously in case one of the drives fails. However, it is a slightly more expensive solution. Any thoughts?

---

### Post by Lanser on 2011-03-26
foxy123. As the others have said, you need to decide what you want to use a NAS for.
I ran an old PC running FreeNAS for 6 months before I figured out what I really wanted.

File Sharing, Central File Backup, Music streaming and some video streaming around the house.  It came down to a choice of QNAP or Synology devices. I selected a QNAP TS 119.
Very power use, No Fan. No Noise. Runs Linux. Good Support by an excellent forum. 
Device runs 20 hours a day, every day, in the back ground, with no issues.

regards

Lanser

---

### Post by foxy123 on 2011-03-27
> **Lanser said:**
> foxy123. As the others have said, you need to decide what you want to use a NAS for.
I ran an old PC running FreeNAS for 6 months before I figured out what I really wanted.

File Sharing, Central File Backup, Music streaming and some video streaming around the house.  It came down to a choice of QNAP or Synology devices. I selected a QNAP TS 119.
Very power use, No Fan. No Noise. Runs Linux. Good Support by an excellent forum. 
Device runs 20 hours a day, every day, in the back ground, with no issues.

regards

Lanser

Well, I'd like to use it for backups and occasionally as a media server (streaming videos and music). What should I pay attention to? QNAP look like a decent devices but with HDs the solution will cost over £250, which is probably a bit too steep for me.

---

### Post by fela on 2011-03-27
I built my server myself which I use partly as a NAS. Cost £120 originally (in total), however spent £35 on a new PSU and some money on two terabyte hard drives (to upgrade the original 500GB drive in it).

A cheap PC won't cost you much to build. Also, if you want it purely to use as a NAS, it won't need much CPU power or anything, so you can go with a passively cooled CPU and it won't make a sound :)

---

### Post by foxy123 on 2011-03-29
> **fela said:**
> I built my server myself which I use partly as a NAS. Cost £120 originally (in total), however spent £35 on a new PSU and some money on two terabyte hard drives (to upgrade the original 500GB drive in it).

A cheap PC won't cost you much to build. Also, if you want it purely to use as a NAS, it won't need much CPU power or anything, so you can go with a passively cooled CPU and it won't make a sound :)

what is a passively cooled CPU?

---

### Post by fela on 2011-03-29
> **foxy123 said:**
> what is a passively cooled CPU?

Normally CPUs are cooled by putting a heatsink (array of heat-dissipating metal fins) on top, and a fan ontop of that.

Passive cooling involves simply sticking a decent heat sink on it, and not using a fan. This brings the advantage of no noise, and also fans build up dust inside the machine of course by drawing air in all the time, so it also removes that worry.

---

