---
title: "Hardware for HTPC"
date: 2008-07-11
forum: Hardware
---

### Post by DanielReidal on 2008-07-11
Hi! I am a newbie and I have set up a ubuntu server just to learn. Now I will build a HTPC and install mythbuntu.

I have heard that nVidia video card has the best linux drivers. But the motherboard I like has intel gma X4500HD chipset.

Can I expect any problem if I choose the intel motherboard (INTEL DG45FC G45 S-775 MINI-ITX) or should I go for a Asus with nVidia chipset (Ausus P5N-EM HDMI)?

I will connect my TV directly to the HDMI/DVI connector.

Cheers Daniel

---

### Post by tubbygweilo on 2008-07-11
Daniel, [Phoronix]("http://www.phoronix.com/scan.php?page=home") often review [Motherboards]("http://www.phoronix.com/scan.php?page=category&item=Motherboards") and more often than not pass comment on how hardware and software work in the Linux environment. A little time spent browsing may well supply the answers to some of your questions.

---

### Post by notanatheist on 2008-09-06
FWIW, the DG45FC only very recently (and finally!!) became available. If you haven't decided on a board yet (it's September already) then you may want to peek at the Nvidia based board for at least another month. The X4500HD isn't fully supported yet but works fairly well. I'm running Mythbuntu and had to install the latest build (8.10 A4) to even get something running. Using a 24" Samsung T240HD took a little initial work. Initially I set mine up with DVI then switched to HDMI. Everything looks great. 1080P AVI ran beautifully. 1080P MOV was a bit sluggish. 

No audio over HDMI yet either. Now I'm trying to find a small stylish HTPC case that doesn't cost a bajillion dollars. So far the really nice ones have been in the $250 range.

---

### Post by wandalalakers on 2008-09-06
Daniel if you don't mind me making this suggestion, you should join this HTPC forum also.

[http://www.avsforum.com/avs-vb/forumdisplay.php?s=&daysprune=-1&f=76](http://www.avsforum.com/avs-vb/forumdisplay.php?s=&daysprune=-1&f=76)

---

### Post by fusionisthefuture on 2008-09-07
hey OP, 
ive never used an intel graphics card, but i plan to get a similar board to you, the asus p5q-em (microATX), with the same chipset.  intel also makes a board with this chipset in microATX form factor, but it has no PCIe 16x slot, and supports far less memory.  i was originally looking at miniITX too, but its really difficult to find a nice case for that form factor, and most of what you do find is actually made for microATX, so you might as well just buy a bigger, cheaper board, with more features.  
from what i understand, intel is the only big company that allows completely open source drivers to be made for their video cards.  i know ati's are generally crap on linux, they may look good in the beginning, but you try to run mythtv and everyone looks like smurfs.  nvidias have been the best for high intensity applications, but the drivers are still released by nvidia, and this new intel 4500 should be pretty powerful.

oh, and if you havent decided on a tv tuner yet, check out the HDHomerun.

---

### Post by tmclaugh on 2008-09-15
I really like this board, and it seems to have great potential, but I'm having a heck of a time getting the audio ports to work properly.  Any tips would be great, but from what I gather it will be a bit before the problem is fixed.

*Actually, updated Ubuntu 8.04 and the sounds works now!*  
Loving the board, works great!

---

### Post by fusionisthefuture on 2008-09-15
> **tmclaugh said:**
> I really like this board, and it seems to have great potential, but I'm having a heck of a time getting the audio ports to work properly.  Any tips would be great, but from what I gather it will be a bit before the problem is fixed.

*Actually, updated Ubuntu 8.04 and the sounds works now!*  
Loving the board, works great!

you must be running a PATA hard drive?  are you using hdmi, vga, or dvi?

edit: i just realized this thread isnt specific about the board were speaking about.  which one are you using?

---

### Post by tmclaugh on 2008-09-16
Unable to use PATA because it has all SATA connections.  Also, I'm currently using a DVI to VGA adapter.  I'm using the new Intel DG45FC ITX board.  I'm hoping to mod it into an ammo can shortly.  Overall, I've had trouble getting used to linux distros and initially really hated the GNOME interface offered by mainstream UBUNTU.  But now it's turning out really well, and I can pretty safely recommend it.  I'm really glad free and stable software exists for those of us who enjoy tinkering.

Edit - Just realized you made a point regarding of price vs. size.  

This board is usually $145 shipped and has all of the features of a full fledged board, I was extremely happy and surprised that is lived up to my expectations.  Only sad thing is that it doesn't do quad core processors, but I think dual core is decent enough for a HTPC/Server

---

### Post by Antal on 2008-09-30
> **tmclaugh said:**
> Unable to use PATA because it has all SATA connections.  Also, I'm currently using a DVI to VGA adapter.  I'm using the new Intel DG45FC ITX board.  I'm hoping to mod it into an ammo can shortly.  Overall, I've had trouble getting used to linux distros and initially really hated the GNOME interface offered by mainstream UBUNTU.  But now it's turning out really well, and I can pretty safely recommend it.  I'm really glad free and stable software exists for those of us who enjoy tinkering.

Edit - Just realized you made a point regarding of price vs. size.  

This board is usually $145 shipped and has all of the features of a full fledged board, I was extremely happy and surprised that is lived up to my expectations.  Only sad thing is that it doesn't do quad core processors, but I think dual core is decent enough for a HTPC/Server

I got mine in this weekend and am stuck installing Ubuntu. I dont have a usb cd-rom drive so I am trying to install via a USB key. When the install starts I get to the stage where it shows me the partitions you can install on, 'guided' or 'manual' but then all it finds is the USB key...

Any ideas how I can get Ubuntu installed on a hdd/make a drive visable to install onto??? 

See my other post: [http://ubuntuforums.org/showthread.php?t=934023](http://ubuntuforums.org/showthread.php?t=934023)

---

