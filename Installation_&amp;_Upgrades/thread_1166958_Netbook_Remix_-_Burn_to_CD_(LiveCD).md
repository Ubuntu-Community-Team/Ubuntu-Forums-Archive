---
title: "Netbook Remix - Burn to CD (LiveCD)"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by Dulwithe on 2009-05-22
Hello All,

I am trying to load/install the ubuntu netbook remix.

However, it seems as though you can only do this from usb stick.

Has anyone on the netbook remix team ever heard of live CD's?

Is there any way I can burn the image to a CD and boot from there?

For example, I just downloaded Moblin (which looks VERY promising, BTW) and it also was a .img file.  I renamed it to a .iso file and burned no problem with K3b.  However, when I try this with the ubuntu netbook remix, I am told by K3b that the file is not a valid image file.

Any ideas??  (Please don't say, "copy it to USB stick" because that is not a solution.  I do not have one available and don't plan to buy one just to try.)

Thanks.

D.

---

### Post by dandnsmith on 2009-05-22
Shame that you rule out a USB stick - for the needed 1G is really cheap, and is the only way I devised to get the file usable in any way.

---

### Post by Dulwithe on 2009-05-22
> **dandnsmith said:**
> Shame that you rule out a USB stick - for the needed 1G is really cheap, and is the only way I devised to get the file usable in any way.

I don't get it...  LiveCD technology has existed for years now...  Much longer than the technology to boot from a USB stick.

Also, many distros even include their own "make distro" tool, so a person can adapt a distro as necessary for a specific implementation (ie: specific hardware, specific software, language environment, etc) and then create a new distro "remix" specific to the target environment.

D.

PS - Also, I have tonnes of cd/dvds available for burning...  But to go buy yet another usb stick that I will only use once then discard seems even more frivolous than adding to my collection of old distro cd/dvd coasters.

---

### Post by Therion on 2009-05-22
> **Dulwithe said:**
> I don't get it...  LiveCD technology has existed for years now...  Much longer than the technology to boot from a USB stick.
I'm pretty sure the logic behind **Netbook** Remix is that it will be installed on a NETBOOK (hence the name?!!!  OMG!!) which, typically speaking, do not have optical drives.

> **Dulwithe said:**
> ...my collection of old distro cd/dvd coasters.
Coaster collec... Wait, what??

---

### Post by Dulwithe on 2009-05-22
> **Therion said:**
> I'm pretty sure the logic behind **Netbook** Remix is that it will be installed on a NETBOOK (hence the name?!!!  OMG!!) which, typically speaking, do not have optical drives.


Coaster collec... Wait, what??


EXTERNAL DVD/CD BURNER... OMG!!!  These have existed for years, too!

Never heard the expression "coaster" to refer to a liveCD/DVD image burned to a disc, used a few times, then never used again??  Pretty common expression...

D.

BTW, I am not sure why you actually posted, other than to perhaps stir up some trouble, because your post really adds no information useful to the original issue.

---

### Post by snowpine on 2009-05-22
Ubuntu distributes NBR as an .img because the majority of netbooks do not have CD drives. It is a question of what is more convenient for the target audience.

To address your specific concern, creating an UNR live USB does not ruin the thumb drive for other purposes. Once you have installed Ubuntu, you can reuse the thumb drive for anything you want (unlike a CD, which then becomes a "coaster").

---

### Post by snowpine on 2009-05-22
ps The best suggestion I can make if you have a CD drive but not a USB thumb drive is to download the Ubuntu minimal CD (mini.iso) and perform a command line install: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Once the install is complete, the following command will install UNR on top of your minimal system, just as if you'd installed from the .img in the first place:

```
sudo apt-get install ubuntu-netbook-remix
```

Hope that helps!

---

### Post by Therion on 2009-05-22
I was trying to clear up why there are no LiveCD's for Netbook Remix since you appeared unclear on the concept.  Perhaps you could try directing the output of Imagewriter to another device?  Often times simply renaming the .img file to .iso will work. Barring that there are applications for both Ubuntu and Windows that can convert an .img to .iso as well.

> **Dulwithe said:**
> Never heard the expression "coaster" to refer to a liveCD/DVD image burned to a disc, used a few times, then never used again??  Pretty common expression...
I'm familiar with the expression, I'm just unclear... Why do you collect them?

---

### Post by dandnsmith on 2009-05-23
I have to say that I'm with OP in this respect - I use an external CD device to try out distros with my netbook, so the addition of a proper iso would be extremely useful.

I've tried renaming, and find that this gets the img file thrown out by my favourite tools as of improper format (for use as iso).

I noticed that when using the img file, you have to devote the whole usb stick to it, and there is no flexibility - the partition table is screwed.

---

### Post by Dulwithe on 2009-05-26
> **dandnsmith said:**
> I have to say that I'm with OP in this respect - I use an external CD device to try out distros with my netbook, so the addition of a proper iso would be extremely useful.

I've tried renaming, and find that this gets the img file thrown out by my favourite tools as of improper format (for use as iso).

I noticed that when using the img file, you have to devote the whole usb stick to it, and there is no flexibility - the partition table is screwed.

Thanks for the vote of support, Derek.

D.

---

### Post by unavenged on 2009-06-02
Does any one have a way to convert the img to iso? I need to try UNR on a 
POS system and it doesn't boot from the flash disk, It does boot the desktop version from flash disk fine though

---

### Post by BatPenguin on 2009-08-03
> **unavenged said:**
> Does any one have a way to convert the img to iso? I need to try UNR on a 
POS system and it doesn't boot from the flash disk, It does boot the desktop version from flash disk fine though

Not sure if anybody's watching this thread anymore, but there is a Netbook Remix CD for Karmic Koala, so these complaints have clearly been heard. Not supporting CD installs is just silly.

I tried the 9.10 Netbook Remix on an old laptop last night and it worked OK for the most part but crashed on codec installations etc... so I think I'll go with installing minimum CD and then the netbook remix packages for Jaunty to get my old laptop some UNR goodness.

---

### Post by Dulwithe on 2009-08-05
> **BatPenguin said:**
> Not sure if anybody's watching this thread anymore, but there is a Netbook Remix CD for Karmic Koala, so these complaints have clearly been heard. Not supporting CD installs is just silly.

Still watching...  Thanks for the info...

---

