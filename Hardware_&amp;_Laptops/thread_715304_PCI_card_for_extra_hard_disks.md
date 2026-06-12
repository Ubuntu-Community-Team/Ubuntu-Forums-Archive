---
title: "PCI card for extra hard disks"
date: 2008-03-04
forum: Hardware &amp; Laptops
---

### Post by jmlaniel on 2008-03-04
I have installed a PCI IDE controller card so that I can add two more hard disks in my computer. For now, Ubuntu is neither showing nor recognizing the disks when they are plugged in. I would like to know if there are any way of recognizing these disks and mounting them (they are NTFS for now). Do I need so drivers for the card?

I am wondering if the problem comes from the fact that I installed ubuntu before adding the PCI card...

Anybody can help me with that?

---

### Post by oldsoundguy on 2008-03-04
IDE on board chip will only support 4 drives .. including your opticals.  plugging in a PCI card will not change that.
My solution was to get some USB 3 1/2" powered hard drive enclosures and utilize the USB buss.

---

### Post by jmlaniel on 2008-03-04
@oldsoundguy

Thanks for the reply.

I know about the four drives only limitation... the only problem is that my motherboard only have one IDE bus. This is why I bought a PCI IDE controller card.

I am also aware of the solution to simply use the USB drive, it's just that I am more looking for a solution to my problem instead of an alternative...

---

### Post by bwang on 2008-03-04
Does your card show up in System>Preferences>Hardware Information?

---

### Post by oldsoundguy on 2008-03-04
your bios will have to support IDE 0 and IDE 1 .. if it is not there, the card will not be able to add the drives, no matter the software installed after POST.  Trouble with a lot of E machines is that the bios will not support the added drives .. card or not.

---

### Post by jmlaniel on 2008-03-05
So basically, what you are saying is that if I don't see the IDE port in the BIOS (even though the port are on a PCI card), ubuntu won't see it? Is that right?

From what I can remember, my BIOS is not seeing the extra IDE port for now...

---

### Post by oldsoundguy on 2008-03-05
That is correct.  you can go into the bios and see if you can activate the second set of IDE ports.  But if that option is not there, the card won't change that.  OR you can go to the board maker's site and search for an update for the board and re-flash the bios.  (to find the REAL manufacturer of your mother board, take the FCC number off of the board, go to the FCC site and plug it in.  You will get the real maker and model of the mother board and most likely a PDA of the manual will be available.)

---

### Post by oldsoundguy on 2008-03-05
PDF not PDA sorry!

---

### Post by egalvan on 2008-03-05
I've got three extra PCI IDE cards in my home file server, running Kubuntu.

No problems. 

And yes, I have a LOT of drives in that box, it's a LianLi server case with space for 23 drives. It has 12 IDE and 3 SCSI at the moment. Along with a dvd rom.

---

### Post by oldsoundguy on 2008-03-05
you are running a server .. not trying to convert an E machine.

---

### Post by BLTicklemonster on 2008-03-05
> **oldsoundguy said:**
> IDE on board chip will only support 4 drives .. including your opticals.  plugging in a PCI card will not change that.
My solution was to get some USB 3 1/2" powered hard drive enclosures and utilize the USB buss.

Do what? I've got an ide card, and I've had four hard drives hooked up to IT, and a cd rom / dvd on ide 2, and a master and slave on ide 1 running. All in Windows. But I can't get the ide card to work in linux.

---

### Post by Whiffle on 2008-03-05
Sooo, what card are we talking about here?  My dads old dell at home has an addon IDE card in it that works fine....2 whole extra IDE channels.  I'd get the brand/model if it weren't 200 miles away.  Pretty sure we got it on newegg though.


actually I think its this one:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16816102007](http://www.newegg.com/Product/Product.aspx?Item=N82E16816102007)

---

### Post by oldsoundguy on 2008-03-05
I have never been able to get more than four IDE devices to run on a computer except for a SERVER setup.  Since every one of my 5 computers has 4 IDE devices INSIDE, I opted for external USB for the extra drives, of which there are 5 more right now.

---

### Post by egalvan on 2008-03-11
So I run a "server". So what? :( 

It's just a name, slowly creeping towards an attitude (see below).

My "server" is a computer running Kubuntu DESKTOP.  Soyo KT880 motherboard, 4g RAM, but it started life as a PIIx board with a "no-cache" Celeron, 128m RAM, running Windows 98. That first case only had space for two hard drives, so the third drive was placed on top of the case with an extra-long IDE cable. In other cases, the extra drive (or two) was velcro'ed to the inside bottom. I agree, not elegant, but it works. (yes, I still do this, on occasion)

There is nothing magical about the word "server". It CAN denote special hardware and hardware, or just a computer that "serves up" files. In my case, it's just a big storage unit, No other computer in my house has more than one drive (just big enough to boot with).  I have one in my living room, bedroom, kitchen, workroom and garage. Hooray for flat-panel displays!

Ubuntu (K,X,Ed,etc) server editions don't "by default" load any special software if the hardware is not found. In fact, the server editions "by default" load LESS software, such as  GUI's.

As to the brand name of the IDE card making a difference, yes it does. I have three "no-name" PCI-IDE cards. All work under Win2K-XP; only one works under Linux.
So my machine has one "no-name" card, one Western Digital, and one Belkin.
(The other two slots hold Adaptec SCSI cards.)


So why do I run Kubuntu Desktop on my server? Short answer, I'm lazy. Longer answer, I run Kubuntu Desktop on all my other machines as my usual installation. I'm comfortable with KDE,  and I haven't gotten up-to-speed with the command line. Since my server has cycles to spare (and then some) I may as well let my computer do the heavy work. It's what I pay it to do. :)

"SERVER"   can be a nothing more than a name, or an attitude, or a total way of life. Let your needs indicate which you need.

---

