---
title: "Is there a problem with the way Ubuntu installs from CD?"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by paradigm2 on 2009-04-02
I'm trying to put Ubuntu 9.04 on my laptop (Acer Aspire 5100 series).  I've burned over 10 CD-Rs and wasted them attempting this.  Each time I checked the MD5's and they have all been okay.  I've used different burning applications to try to burn the iso.  All ten burns were done at the lowest possible speed. Failure each time.  I/O errors with the buffers.  Sometimes it just freezes before it even gets that far.  Errors are always found on the CD. I know it could just be my drive.... but here's the thing.  It installs windows just fine.  I can watch and burn DVD's to it just fine as well...

Now I've used Ubuntu before.  For years now.  In fact I just burned 9.04 a few days ago and installed it on another system.  I at first had issues there too.  I/O Errors when using the LIVE CD.  But when I rebooted it and tried an actual install using the same CD (I had nothing to lose) by some miracle it actually worked....at least for that computer (not my laptop).  Anyway I've probably Installed Ubuntu on five different computers (burning with different burners) over the course of about three.  It seems as if 4/5 have always had these sorts of issues!  Its always a hold your breath kind of thing.

Is there something wrong with how it is being done?  It puzzles me.  I don't understand why I am always able to burn movies or windows installations CDs but for some reason doing the same for Ubuntu is always so much more hit and miss.

What's going on here?  Is there a difference in how Ubuntu reads and writes from the CD?  Is it just not allowing for multiple retries and giving up too easily?  What if anything, is different?

Don't get me wrong.  I love Ubuntu and I love Open Source.  And I very much appreciate the work of the developers.  I'm just frustrated after spending seven hours and ten CD-Rs in order to try to get this working.  And it makes me think back and wonder about why I've always had problems in the past (and I note these problems are VERY COMMON).  

Can someone explain?  Is there a technical reason perhaps?  Something that can be done?

I've ordered (thank you for providing this for free, very generous) a CD and I guess I will just have to wait to put Ubuntu on this laptop.  I have another Ubuntu desktop but apparently there is no network install either without doing some very complex hacking (I don't have a crossover cable or hub and I don't feel like setting up a tftp and DHCP server on my working Ubuntu system!)...  If anyone has any other ideas, please let me know.  Thanks.

---

### Post by unisol on 2009-04-02
try burning it with a program called infrarecorder.it worked well for me. its free just google it.

---

### Post by paradigm2 on 2009-04-02
> **unisol said:**
> try burning it with a program called infrarecorder.it worked well for me. its free just google it.

Thanks.  Ill give it a go. Why not!  Good thing I bought 100 CD-R's for $10 at Circuit City before they folded. :lol:

---

### Post by paradigm2 on 2009-04-02
> **unisol said:**
> try burning it with a program called infrarecorder.it worked well for me. its free just google it.

I tried burning it with that program at 1x speed.  No dice.  The song "Maybe I should just give up" is running through my mind. :lol:  I guess I will just wait for the CD to arrive or attempt the tftp server installation (which looks hellish).

Oh well at least my other one works....

---

### Post by Partyboi2 on 2009-04-03
You could try using [[COLOR=Blue]Unetbootin[/COLOR]]("http://unetbootin.sourceforge.net/") which allows you to install without having to use a cdrom.

---

### Post by paradigm2 on 2009-04-03
> **Partyboi2 said:**
> You could try using [[COLOR=Blue]Unetbootin[/COLOR]]("http://unetbootin.sourceforge.net/") which allows you to install without having to use a cdrom.

Thanks but I don't have a USB drive.  I'm in the process of using the QuickNetBoot instructions from:

[https://help.ubuntu.com/community/Installation/QuickNetboot](https://help.ubuntu.com/community/Installation/QuickNetboot)

I set up an old Wireless-B router (with 4 port switch), changed its IP and subnet to be different than the main router.  Then I disabled wireless and DHCP on the secondary router (now just a glorified switch) .  I'm on the laptop right now just testing to make sure it has internet access behind the secondary router (it obviously does :) ).

I verified that my Laptop's BIOS has the network boot option so that should be okay.  Next step is to install the packages and reconfigure on the existing Ubuntu desktop which will be my tftp and dhcp server.  Wish me luck.  I'll need it.... :-k ]

---

### Post by paradigm2 on 2009-04-03
> **paradigm2 said:**
> 

[https://help.ubuntu.com/community/Installation/QuickNetboot](https://help.ubuntu.com/community/Installation/QuickNetboot)


SUCCESS!!!  ... when using the quoted instructions for quicknetboot with some minor changes so that I could run the tftp server on jaunty and in order to install jaunty on my laptop.  Will see about updating that info tomorrow maybe.  The instructions for the tftp server are slightly different.

---

### Post by ronparent on 2009-04-03
Congratulations. 

I fully agree and sympathise with your original rant. I have done many windows installation of several version, including some from backup copies of the install disks, with never a failure on this account.

---

