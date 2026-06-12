---
title: "Switching over to Ubuntu"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by AND_YOU_ARE on 2009-03-16
Currently I am more committed to making the switch to Ubuntu.  I am dual booting with XP until I get Ubuntu squared away.  I have come here for some assistance in getting Ubuntu fully up and running.

I have installed it on a second drive, updated everything.  However I dont have sound yet.  I have both an Audigy 2 and onboard sound on my P5B Dlx.  For linux drivers, where do I look?

Aside from the sound card, is there a check list of other things that I should consider installing?

---

### Post by AND_YOU_ARE on 2009-03-16
Alright, I feel stupid.  The default setting was digital out.  I have analog speakers.  So that problem has been solved.  

My other question remains.  Is there a checklist of software or drivers I should consider installing?

---

### Post by cariboo on 2009-03-16
It really depends on what you do with your Linux installation. The one thing I would suggest to install ins the ubuntu-restricted-extras meta package. This will install fLash, java, mscorefonts and most of the codecs you will need to play most type of audio/video media. THe ubuntu-restricted-extras meta package can be installed using Add/Remove Programs, Syanptic Package Manager and of course the command line to install it.

Jim

---

### Post by bendib on 2009-03-16
I must warn you, Linux hates wifi. If it works, lucky. I love linux so much for all it's wonderful qualities I will use ethernet instead.
I would just click applications and add remove, when it asks you to reload the list,clik reload provided you are on the net.
Then you should be all green, but playing mp3s is easy open it and select every codec available so you don't have to worry later. Simple.

---

### Post by tony1212 on 2009-03-16
Just a follow up to bendip's post, I have been useing a PCI D-link wifi card in several diferent towers with no problems (8.04 and 8.10) although I cannot get my laptop to recognise my Blkin wifi card. If you need a card for a desk top then D link seems to be the way to go.

I'm at uni at the moment but I'll post the model number later.

---

### Post by AND_YOU_ARE on 2009-03-16
Ubuntu was able to find my Cisco Aironet 350 wireless adapter right off the bat.  I would like to install Logitech's setpoint for my MX Revolution.  Also Ubuntu found my nvidia GTX 260, is there anything I have to do to make sure that card is fully installed and working properly?  

As for what I use my pc for, with windows I used google's picasa with my canon si5s.  I was attempting to learn photoshop, but never did.  So I would need to set up my canon software, picasa and a photo editing program that I can learn.  I was using MS office 07 in windows, can I use the same install disc over in Ubuntu?

I was playing games through steam every once in a while, however I would prefer to get other things up and running before I worry about that.

---

### Post by Tibuda on 2009-03-16
> **AND_YOU_ARE said:**
> Ubuntu was able to find my Cisco Aironet 350 wireless adapter right off the bat.  I would like to install Logitech's setpoint for my MX Revolution.  Also Ubuntu found my nvidia GTX 260, is there anything I have to do to make sure that card is fully installed and working properly?Try to enable the visual effects in System > Preferences > Appearence.

> As for what I use my pc for, with windows I used google's picasa with my canon si5s.  I was attempting to learn photoshop, but never did.  So I would need to set up my canon software, picasa and a photo editing program that I can learn.  I was using MS office 07 in windows, can I use the same install disc over in Ubuntu?If you want to learn a new photo editing program, you can try Gimp which is already installed in Ubuntu. Your MS Office CD will not work out of the box, as it was compiled for Windows. You can try to use OpenOffice, which is already installed. It has as many features as MS Office, and can read and write MS format. If you really miss something, you can try to install it with Wine, but it is not recommended. Wine is a compatibility layer that allows you to run some Windows programs. You can install Wine in Applications > Add/Remove.

> I was playing games through steam every once in a while, however I would prefer to get other things up and running before I worry about that.Some Windows games works with Wine, but some don't. Search [http://appdb.winehq.org/](http://appdb.winehq.org/) for game compatibily with Wine. There are some nice games for Linux too, but they just don't have many users. [Urban Terror]("http://www.urbanterror.net/"), [Spring]("http://spring.clan-sy.com/"), [Frets on Fire]("http://fretsonfire.sourceforge.net/")... Those games works in Windows too, so you can tell your friends to play them too.

---

### Post by AND_YOU_ARE on 2009-03-16
bendib, should I install everything on that list?

danielrmt, the visual effects are working, the ones I have seen so far.

One tweak I found in XP was a folder size mod, where when in list view in explorer, the size of the folder would be displayed.  Is there something similar in Ubuntu?

---

### Post by Mark Phelps on 2009-03-16
> **AND_YOU_ARE said:**
> One tweak I found in XP was a folder size mod, where when in list view in explorer, the size of the folder would be displayed.  Is there something similar in Ubuntu?

If you right-click on the folder in Nautilus, and select properties, it will open a panel that will tell you the size of the folder and its contents.

---

### Post by AND_YOU_ARE on 2009-03-16
> **Mark Phelps said:**
> If you right-click on the folder in Nautilus, and select properties, it will open a panel that will tell you the size of the folder and its contents.

Yes.  One can do that in windows as well.  I would prefer not to do that every time I want to look at the size of a folder.  This tweak would tell you the size of the folder in the size column when in list view, rather than telling you how many items are inside.

Also, does utorrent work with ubuntu?  Transmission does not seem to have all the features I have used with utorrent.

---

### Post by tony1212 on 2009-03-16
Just a follow up to bendip's post, I have been useing a PCI D-link wifi card in several diferent towers with no problems (8.04 and 8.10) although I cannot get my laptop to recognise my Blkin wifi card. If you need a card for a desk top then D link seems to be the way to go.

I'm at uni at the moment but I'll post the model number later.


The Card is a D-Link AirPlusG DWL-G510 (Wirless G desktop adapter)

---

### Post by Surkow on 2009-03-16
> **AND_YOU_ARE said:**
> [...]

Also, does utorrent work with ubuntu?  Transmission does not seem to have all the features I have used with utorrent.

Yes, utorrent will work with wine. But I would recommend to use [Deluge]("http://deluge-torrent.org/").

---

### Post by AND_YOU_ARE on 2009-03-18
Thanks, I'll have to give Dluge a try when I am back to my pc.

Since I am very new to ubuntu, I have been reading this book:

 [http://www.amazon.com/Official-Ubuntu-Book-2nd/dp/0132354136]("http://www.amazon.com/Official-Ubuntu-Book-2nd/dp/0132354136")

I have a question about hard drive, their format and why linux mounts them.  My hard drive set up right now is 2x320gb, 2x1.5tb.  A 320 for each os, and 1.5tb of storage that both os have access to.  What is the format that I should be using for those 1.5tb drives so both os can write to?  NTFS, or FAT32?  Also is it typical that ubuntu mounts the drive on the desktop before you can access them?  Is there some way to keep the drive off the desktop?

I am also looking at a good docking program.  In windows I used rocket dock.  What is recommended for working with ubunut?

---

### Post by Tibuda on 2009-03-21
> **AND_YOU_ARE said:**
> I have a question about hard drive, their format and why linux mounts them.  My hard drive set up right now is 2x320gb, 2x1.5tb.  A 320 for each os, and 1.5tb of storage that both os have access to.  What is the format that I should be using for those 1.5tb drives so both os can write to?  NTFS, or FAT32?  Also is it typical that ubuntu mounts the drive on the desktop before you can access them?  Is there some way to keep the drive off the desktop?FAT32 support is better than NTFS, so that's what I would use.

> I am also looking at a good docking program.  In windows I used rocket dock.  What is recommended for working with ubunut?
Cairo-dock, Avant-Window-Navigator or Docky are the ones I have used. I use Docky because it is more than a dock, but it does not all have the features cairo/awn have.

---

### Post by roblubbers on 2009-03-23
For the filesystem you need to consider file size. Fat32 support files up to 4gb. Files bigger then that will not fit on a fat32 partition. On the other hand, fat32 has been around way longer and is supported way better by linux then ntfs

---

