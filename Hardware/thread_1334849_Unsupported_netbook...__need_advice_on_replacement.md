---
title: "Unsupported netbook...  need advice on replacement."
date: 2009-11-22
forum: Hardware
---

### Post by stevejesus on 2009-11-22
Hi all,

I bought an Acer Aspire ZA3 today.  I got it for US $299 which is pretty good considering it's display is 1366x768, it has 2gb on ram and a 250gb disk...  Anyhow, I had assumed that Ubuntu would be just fine on it.  My wife has a different Aspire One that works just fine...  Anyway I have the GMA500 chipset.  I finally got the display working at the right resolution but no matter what I do, performance is unacceptable.

I have thrown in the towel on this one and want to avoid this chipset at all costs.  I am taking it back to the store tomorrow and would like some friendly advice on which netbooks have these specs, with the most important being screen resolution, and work OOTB with Ubuntu.

Thanks in advance.

---

### Post by wilee-nilee on 2009-11-22
My Acer aspire one with the atom 1.6 chip and 2 gigs ram runs W7 and Karmic with no problems. W7 is only just slightly slower then Karmic hardly noticeable.

---

### Post by stevejesus on 2009-11-23
So yours must not have the GMA500 chipset...  Which does yours have?  Does it have a screen resolution of 1366x768?

---

### Post by stevejesus on 2009-11-23
Surely someone has a high resolution netbook that works OOTB...  I'm only throwing in the towel because from what I understand, the 3d portion of this hardware will never have a FOSS driver from intel, thus I will never be able to build it against future kernels...  Seems like it will be a headache each time I upgrade to new releases or update my kernel.

---

### Post by rastoboy on 2009-11-24
Hi there,

I, too, have an Acer One with that resolution.  Can you tell me where you got your information about the Intel drivers?

That is appalling...especially since I got mine a couple months ago and returning it would be difficult at best.

---

### Post by stevejesus on 2009-11-24
Just google "linux GMA500".  I wouldn't necessarily call it appalling since the driver for this is intended to be closed source.  As I understand it, Intel is not to blame for this as this chipset was designed for a different type of device.  What is upsetting is that these laptop vendors chose to implement it in their netbooks.  But shame on you and I for buying the device before doing a little homework...

Now back to the question at hand...  any netbooks with these specs that use FOSS drivers and work OOTB?

---

### Post by rastoboy on 2009-11-27
Just fyi, it looks like the Ubuntu community has a workaround sorted out for 9.10:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

Just ran the second script and it worked, and is now the correct resolution and fast as well.

I would have to respectfully disagree that we should in any way tolerate not having good drivers available (although I can't argue that it is foolish to go shopping without doing due diligance).

Anyway, it's as good as Windows now, thanks to the benevolent programmer(s) who provided the patches.

---

### Post by stevejesus on 2009-11-28
> Anyway, it's as good as Windows now, thanks to the benevolent programmer(s) who provided the patches.
My gripe is that this driver needs patches to work.  It cannot be built against future kernels.  I am not a programmer or more accurately, a hacker that is able to make such a thing work on my own, thus I returned the product.  For future releases I would have to rely on the work of others, and for something not very many people are working on I would be foolish to count on a solution being available with each Ubuntu release.  Thus, instead of gripe about the unavailability of an elegant solution, I have moved on.  Again I am asking if there is anyone out there using a comparable netbook with a supported chipset.

> Just ran the second script and it worked, and is now the correct resolution and fast as well.

I really would not like to hear any more success stories.  I feel like everyone is rubbing it in that they have working hardware that is unsupported by by FOSS while I am trying to move on to something fully supported.
I also ran the script but my results varied.  I achieved the right resolution but was stuck with poor performance.  But this is inconsequential since I had full intentions on returning the netbook.

I am mostly interested in hearing about success stories with other fully-supported hardwares that are similar in dimension and specifications to the laptop I purchased.

---

### Post by mikewhatever on 2009-11-30
> **stevejesus said:**
> .................
[COLOR="DarkOrange"]I really would not like to hear any more success stories.[/COLOR]  I feel like everyone is rubbing it in that they have working hardware that is unsupported by by FOSS while I am trying to move on to something fully supported.
I also ran the script but my results varied.  I achieved the right resolution but was stuck with poor performance.  But this is inconsequential since I had full intentions on returning the netbook.

[COLOR="Orange"]I am mostly interested in hearing about success stories[/COLOR] with other fully-supported hardwares that are similar in dimension and specifications to the laptop I purchased.

You have to decide whether you want success stories or not, cause it can't be both. Anyway, as you know by now, none of the currently supported Ubuntu releases support gma500 by default. One can fix that by installing the driver manually for now, which works quite well, although you don't want to here. On the other hand, it seems like a new closed source driver will be available in the upcoming release. Last, but not least, if you want an out of the box support for gma500, try Mandriva one edition.

---

### Post by Greenwidth on 2009-11-30
Have a look at:
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

I have #23 - and, like it says, it "Works very well."

Atom N270 1.6
Nvidia ION 256Mb
2Gb RAM
1280x800 screen
320Gb HDD

---

### Post by mikewhatever on 2009-11-30
> **Greenwidth said:**
> Have a look at:
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

I have #23 - and, like it says, it "Works very well."

Atom N270 1.6
Nvidia ION 256Mb
2Gb RAM
1280x800 screen
320Gb HDD

Glad it works well for you, but the OP has gma500, and not Ion.

---

### Post by Greenwidth on 2009-11-30
OP said:
> **stevejesus said:**
> I am mostly interested in hearing about success stories with other fully-supported hardwares that are similar in dimension and specifications to the laptop I purchased.

---

