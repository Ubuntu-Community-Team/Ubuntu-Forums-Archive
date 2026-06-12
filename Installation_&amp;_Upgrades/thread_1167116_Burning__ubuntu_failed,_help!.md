---
title: "Burning  ubuntu failed, help!"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by Camilia on 2009-05-22
I have downloaded ubuntu to document. Then downloaded freeisoburner from softpedia to documents. I opened up the iso burner. Then for file clicked open and ubuntu was put in the box. I set burn speed at 16x. The burning failed. I got message:
Failed to write ISO image, Error: Hardware Error 12288.

I tried express burner. Selected data disk - write image to disk and got no disk loaded. Have cd in tray.
In burner driver put image and get can't open iso file

I tried Xilisoft burner. It says I don't have a disk in the drive. I click to eject the drive and it ejects the cd tray. I am using CD-RW. Is this the correct CD

The computer is Sony Vaio notebook with windows xp.

What else can I do?

---

### Post by peakshysteria on 2009-05-22
Your profile says you're using Hardy Heron. You can update from 8.04 to 8.10. [Then update from 8.10 to 9.04 (Jaunty Jackalope)]("http://www.ubuntu.com/getubuntu/upgrading"). It very important that you do all mentioned steps. Alternatively you must burn an ISO of Jaunty (if that's your choice)and do a clean install. The CD/DVD creator in Aplications --> accessories should be sufficient for making an ISO.

---

### Post by Camilia on 2009-05-22
> **peakshysteria said:**
> Your profile says you're using Hardy Heron. The CD/DVD creator in Aplications --> accessories should be sufficient for making an ISO.

I don't have any ubuntu on this computer. This is my mother's computer. I trying to burn ubuntu 9 to a CD.

---

### Post by growled on 2009-05-22
Download CDBurnerXP and give it a try. I've used it a lot and it does a very good job.

---

### Post by QIII on 2009-05-22
I hate to ask the basic questions, but:

Are you using a 700MB/80 minute CD or the older 650MB/74 minute CD?

How old is the computer and CD drive?  Some older CD drives can't handle the 80 minute CDs.

(I think the .iso image is 698MB or something thereabouts...)

Your comments seem to point to a hardware issue.

---

### Post by pricetech on 2009-05-22
Deep Burner:  deepburmer.com
Infra Recorder:  infrarecorder.org
Burn CDCC:  terabyteunlimited.com

Kana CRC Check:  kanacolution.com

Ive used all of the above under winders and they all work fine.

---

### Post by Kevbert on 2009-05-22
Make sure you use a slow burn speed to minimize errors (x2 recommended).

---

### Post by peakshysteria on 2009-05-22
> **Camilia said:**
> I don't have any ubuntu on this computer. This is my mother's computer. I trying to burn ubuntu 9 to a CD.

Ah, then you have two choices as far as I can see; get a easy working program to burn the ISO in XP.There should be tons to choose from. Or, second, burn the ISO on you own Ubuntu machine ;) (i guess you have one since you profile says Hardy Heron).

---

### Post by trench.me on 2009-05-22
> **peakshysteria said:**
> Ah, then you have two choices as far as I can see; get a easy working program to burn the ISO in XP.There should be tons to choose from. Or, second, burn the ISO on you own Ubuntu machine ;) (i guess you have one since you profile says Hardy Heron).

Let's not forget the third choice. Ubuntu can send Camilia  (*and* Camilia's mom) the disc for free. :)

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

Not only does it take about as long to receive as burning it at Kevbert's recommended 2x speed, but sometimes you end up with some spiffy stickers as well.

---

### Post by Camilia on 2009-05-22
> **QIII said:**
> I hate to ask the basic questions, but:

Are you using a 700MB/80 minute CD or the older 650MB/74 minute CD?.

I don't know the basics so that is fine. I checked the CD and saw is 700MB

> **QIII said:**
> 
How old is the computer and CD drive?  Some older CD drives can't handle the 80 minute CDs.


Don't know.

---

### Post by Camilia on 2009-05-22
> **trench.me said:**
> Let's not forget the third choice. Ubuntu can send Camilia  (*and* Camilia's mom) the disc for free. :)

Not only does it take about as long to receive as burning it at Kevbert's recommended 2x speed, but sometimes you end up with some spiffy stickers as well.

It takes at least 2 weeks to recieve the disk. I ordered it when I got here, Florida, probably won't get here before I go home, Georgia. Prefer to use ubuntu os to do job searches. May have to use windows xp os.

---

### Post by QIII on 2009-05-22
Can you read other disks?

Copy to the drive?

Try burning something else to the disk and see if you get a hardware error.

---

### Post by trench.me on 2009-05-23
> **Camilia said:**
> It takes at least 2 weeks to recieve the disk. I ordered it when I got here, Florida, probably won't get here before I go home, Georgia. Prefer to use ubuntu os to do job searches. May have to use windows xp os.

You know, a fourth option would be to install VirtualBox and then install Ubuntu within it.  It's free, quick, and sounds like the most viable option for a person in your situation.

If you've never run virtualbox you are about to become a fan. A big fan.

Here's the tutorial & instructions you'll want to follow:

[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by peakshysteria on 2009-05-23
I just came to think of [**[COLOR="Red"]Wubi[/COLOR]**]("http://wubi-installer.org/"). That now sounds like a very good option I think. I remember once I was forced to work on XP. I just installed Wubi (8.04) inside XP. Smooth and Easy. Just download the .exe and install it like any other progs in Windows. This is by far the easiest and fastestway to get Ubuntu up and running on your mothers machine.

---

### Post by trench.me on 2009-05-23
> **peakshysteria said:**
> I just came to think of [**[COLOR=Red]Wubi[/COLOR]**]("http://wubi-installer.org/"). That now sounds like a very good option I think. I remember once I was forced to work on XP. I just installed Wubi (8.04) inside XP. Smooth and Easy. Just download the .exe and install it like any other progs in Windows. This is by far the easiest and fastestway to get Ubuntu up and running on your mothers machine.

Interesting. I'd never heard of Wubi... it *almost* makes me want to install Windows just to try it out. 

Almost. :D

**Camilia** - without having tried it, after reading the ArsTechnica review, I fully agree with **peakshysteri. **Go get you some Wubi.

---

### Post by ezsit on 2009-05-23
> I am using CD-RW. Is this the correct CD

Theoretically it should not matter, but try a cd-r disc and try the software you already have again. It should work if your cd burner works. Have you tested burning other discs with this burner?

If this is your mother's computer I would not use the Wubi installer and put Ubuntu on her computer, you are just asking for troubles that way.

---

### Post by trench.me on 2009-05-23
> **ezsit said:**
> Theoretically it should not matter, but try a cd-r disc and try the software you already have again. It should work if your cd burner works. Have you tested burning other discs with this burner?

If this is your mother's computer I would not use the Wubi installer and put Ubuntu on her computer, you are just asking for troubles that way.

If mom has Windows do you really think mom is going to notice Wubi and/or Ubuntu within the slew of other unknown things occupying her Windows environment? 

Just don't add the Wubi IE toolbar and I'm pretty sure it'll go unnoticed. :)

Edit: Not to suggest all moms are computer illiterate... I just couldn't avoid wasting a good punchline. I'm sure mom is awesome.

---

### Post by Camilia on 2009-05-25
> **trench.me said:**
> If mom has Windows do you really think mom is going to notice Wubi and/or Ubuntu? .

I was going to use as a trial by choosing option not to change anything. I told her of what I was going to do and that it would not be on her computer after I took the disk out.

> **trench.me said:**
> 
Not to suggest all moms are computer illiterate... 

She is very computer illiterate. There are a lot of icons on the desktop for AOL which are not used. Broadband is used but I have been told not to move the icons.

I believe it is impossible to copy anything on this computer. For I tried to copy data with the CD drop program on the computer and got message that there was no CD in the tray. I had a CD in the tray.

I have not been getting notifications of the replies. I will try the WUBI. Thank you.

I tried WUBI and it failed. I got message title Windows - No Disk Exception processing message c0000013 Parameters 75b6bf7c 4  75b6bf7c  75b6bf7c  Cancel, Try again/ continue option availble. None work. I have to shut down computer to get it off of desktop.

---

### Post by trench.me on 2009-05-25
> **Camilia said:**
> She is very computer illiterate. There are a lot of icons on the desktop for AOL which are not used.

I have a few family members like this as well. It's funny... until I have to work on their machines. Heh. 

A little off-topic here: it would be nice to have a program that notified me of old documents by turning their icons into "AOL Free Trial" icons. Yes, that would be awesome. I might write that.

Back on topic: I'm sorry but unfortunately I'm out of suggestions. Well, besides this one - see if you can burn a copy at a local library. I'm thinking that's a winnable scenario. 

Have fun in FL, even if it's Ubuntu-less.

---

### Post by peakshysteria on 2009-05-26
> **Camilia said:**
> I was going to use as a trial by choosing option not to change anything. I told her of what I was going to do and that it would not be on her computer after I took the disk out.



She is very computer illiterate. There are a lot of icons on the desktop for AOL which are not used. Broadband is used but I have been told not to move the icons.

I believe it is impossible to copy anything on this computer. For I tried to copy data with the CD drop program on the computer and got message that there was no CD in the tray. I had a CD in the tray.

I have not been getting notifications of the replies. I will try the WUBI. Thank you.

I tried WUBI and it failed. I got message title Windows - No Disk Exception processing message c0000013 Parameters 75b6bf7c 4  75b6bf7c  75b6bf7c  Cancel, Try again/ continue option availble. None work. I have to shut down computer to get it off of desktop.

Strange. What OS are your mom running? The requirement specs are:
```

Memory 256 MB memory

Harddisk Space 5 GB harddisk space

Operating System Windows 98, 2000, XP, Vista

```

As far as I can remember Wubi should install like any other progs. And it should be easy to remove it via add/remove programs if one should want to uninstall it.Did you try to run Windows update before you tried the Wubi installer?

---

### Post by Camilia on 2009-05-26
> **peakshysteria said:**
> .Did you try to run Windows update before you tried the Wubi installer?

Yeh, I have done it 2xs. The computer is just not recognizing that there is a disk in the drive.

---

### Post by peakshysteria on 2009-05-28
Are you sure your mothers machine has a burner. It sound like it's just a CD-rom station.

Did you try Wubi after you got all your updates from Windows Update?

---

