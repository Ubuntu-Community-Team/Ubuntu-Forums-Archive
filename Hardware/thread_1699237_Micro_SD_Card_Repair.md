---
title: "Micro SD Card Repair"
date: 2011-03-03
forum: Hardware
---

### Post by bumder on 2011-03-03
I've somehow corrupted/bust a 32gb micro sd card I got off ebay, and consequently its now only showing up as 8mb!

I've tried formatting again using Disk Utility and Gparted, but to no avail.

Anyone had a similar problem, or have any advice?

---

### Post by Kirboosy on 2011-03-03
Even in gParted when you delete the partitions it still is only 8 Mb.? Cause if that is the case the MBR is corrupt and you might have to get a new one...

---

### Post by Grenage on 2011-03-03
Did you ever manage to store much data on it?

I only ask, because there are a lot of 'fake' storage devices going around; it never hurts to ask.

---

### Post by Joe of loath on 2011-03-03
dd if=/dev/zero of=/dev/sdX

See how much you can get onto it before it fills up.

---

### Post by bumder on 2011-03-03
When I first got it, it showed up as 34Gb for some reason in Ubuntu.

Now it shows up as 7.84Mb

Tried *dd if=/dev/zero of=/dev/sdb*, it said *dd: opening `/dev/sdb': Permission denied* 

Note, I am using a usb adapter that has no 'lock' switch.
I have also used it in a big SD card adapter, and in my sansa clip via usb. Not success in any of them :(

Was a cheap Kingston branded one off ebay, chinese origin possibly, but the other ppl that purchased one gave positive reviews of the seller...

EDIT: added 'sudo' before that command and it copied 8.4Mb

---

### Post by Joe of loath on 2011-03-03
Sounds like it's a fake. Often times, sellers or manufacturers will fake partition information so that a card appears bigger than it is.

---

### Post by jbiggs12 on 2011-03-03
Try running it as root.

> **bumder said:**
> When I first got it, it showed up as 34Gb for some reason in Ubuntu.

Now it shows up as 7.84Mb

Tried *dd if=/dev/zero of=/dev/sdb*, it said *dd: opening `/dev/sdb': Permission denied* 

Note, I am using a usb adapter that has no 'lock' switch.
I have also used it in a big SD card adapter, and in my sansa clip via usb. Not success in any of them :(

Was a cheap Kingston branded one off ebay, chinese origin possibly, but the other ppl that purchased one gave positive reviews of the seller...

---

### Post by bumder on 2011-03-03
Says 8.4Mb :(

Shows up in Gparted, but all the options (unmount, format etc) are greyed out.

---

### Post by Kirboosy on 2011-03-03
I'm sorry to say but you got ripped off. That is a fake card. A real card would not be oversized like that. A real card would actually come up as 31.2 Gb (or something close to it)

My friend got ripped off on ebay with a thumbdrive not to long ago. :(

Sorry about your loss :(

---

### Post by bumder on 2011-03-04
> **Caboose885 said:**
> I'm sorry to say but you got ripped off. That is a fake card. A real card would not be oversized like that. A real card would actually come up as 31.2 Gb (or something close to it)

My friend got ripped off on ebay with a thumbdrive not to long ago. :(

Sorry about your loss :(

Hmm, I've contacted the seller and he said he would refund the cost of the item if I return it to him. So all I lost was the cost of postage x2, which isn't too bad I guess.

Moral of the story, some things just aren't worth going cheap on (especially imported ebay stuff!)

---

### Post by Grenage on 2011-03-04
> **bumder said:**
> Hmm, I've contacted the seller and he said he would refund the cost of the item if I return it to him. So all I lost was the cost of postage x2, which isn't too bad I guess.

Moral of the story, some things just aren't worth going cheap on (especially imported ebay stuff!)

You're entitled to a _complete_ refund, and that includes the delivery charges.  Sellers like that are **scum**; they know exactly what they are selling, and only get away with it because the goods are low cost, and people are afraid of getting poor feedback.

There are obviously exceptions, but that's usually the case.

---

### Post by user024 on 2011-12-17
Well, after loosing some files, suposed to be in the sd card, I followed the dd suggestion and it came out that about 16GB was writen...
What do you think?
Is there any other way to test the capacity of the card?
Could it be something else than fake the problem?

I wouldn't mind "downgrading" the thing, but, without a windows based system, I don't seem to find the solution by googling it.

---

### Post by Joe of loath on 2011-12-17
If 16gb were written, it's a 16gb card. Are you sure you didn't lose the files due to corruption or a mistake?

---

### Post by user024 on 2011-12-17
I can't find a way to guess about it.
Via an USB adapter, the phone and a SD card slot (in a laptop), I tried to "load it" with music files and other data, but from the point of half its name capacity, files added from my PC, turn to nothing next time the card was used. Either in the phone, or mounted to the computer...

I already repartitioned some times, with Gparted and the hard disc utility.
If there is another way to follow, I am willing.
For the time being, I redeployed my previous, 8GB card for the phone.

-------------------EDIT--------------------

For anyone interested, I used the F3 utility ([http://oss.digirati.com.br/f3/](http://oss.digirati.com.br/f3/)) and found out that the SDHC card has only 2GBs of capacity in fact.
I used the instructions to change the partition table, tested again, and here I am with a rather expensive 2GB SD card...


I can not be certain about the legitimacy of the "dd" method, since it did not work out for me, but gave me a wrong impression. Either way, you could only lose your doubt and some time by trying the "f3" method.
:-)

---

