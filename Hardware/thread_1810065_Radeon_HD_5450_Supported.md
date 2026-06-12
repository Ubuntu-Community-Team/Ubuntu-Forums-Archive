---
title: "Radeon HD 5450 Supported?"
date: 2011-07-22
forum: Hardware
---

### Post by PPPP on 2011-07-22
I'm in the market to buy a new (budget) video card for HTPC use.  I am interested in getting the Sapphire Radeon HD 5450.  From the page ([https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)), that video card is not listed.  Does anyone know if the card will work?

---

### Post by ~!geek!~ on 2011-07-22
Some day before I saw a guy using fglrx driver for ati-radeon hd 5470 graphic card on ubuntu 11.04. So I hope it should work for the same series of these graphic cards.

---

### Post by PPPP on 2011-07-22
I don't know much about video cards...is nVidia preferred on Linux?  Any suggestion on which nVidia card to get for a budget HTPC?

---

### Post by coffeecat on 2011-07-22
> **PPPP said:**
> Does anyone know if the card will work?

Yes, and not only does it work, it will give you Unity and compiz out of the box with the default open source driver in 11.04. However, I see that you are running 10.04. It will work with the version of the open source driver that comes with Lucid but I can't remember whether I got 3d accleration and compiz when I tried it.

If you want to use the proprietary fglrx driver, I don't know how good that will be. Ever since I nearly lost the will to live (:wink:) trying out the fglrx driver in Karmic with a different ATI card, I've avoided it.

---

### Post by PPPP on 2011-07-22
I see.  Actually, I forgot to update my profile...I'm on 10.10, according to lsb_release.  If I upgrade to 11.04, it will work out of the box? Sweet!  :)

So does that mean the supported video card page from my first post is not kept up to date?

---

### Post by coffeecat on 2011-07-22
> **PPPP said:**
> So does that mean the supported video card page from my first post is not kept up to date?

Yup. It's up to people in the community - that's you and me - to contribute. In fact, if you look at the bottom of the page, you'll see that the last person to update that page (at the time of posting now) was me! On 9th May this year.

Which reminds me that I've forgotten to add a line for the HD5450, and I shall do so within the next day or so. Thanks for the reminder! :)

---

### Post by coffeecat on 2011-07-23
@PPPP, just to add.

I've refitted my...

```
$ lspci | grep VGA
02:00.0 VGA compatible controller: ATI Technologies Inc Cedar PRO [Radeon HD 5450]
```

... into my test machine which I'm posting from at the moment, using Natty/11.04. Just to confirm, Unity/compiz works just fine. I can boot into Lucid/10.04 and Maverick/10.10 and get a perfectly usable gnome desktop but I can't enable compiz desktop effects in either of those two versions. Not particularly surprising since the HD5450 was only released in Feb 2010 and it takes some time for support for newer chipsets to trickle into the video drivers. Lucid and Maverick use older versions of the ATI driver. It would probably be possible to get compiz working in Lucid and Maverick by means of the xorg-edgers ppa, but I'm not going to try that, and I see that you'll be upgrading to Natty anyway.

By the way, if you do upgrade to Natty, be careful with compiz if you install compizconfig-settings-manager. Unity is simply a compiz plugin and some other compiz effects are not compatible. For example, if you want the desktop cube, don't just enable it. You need to use a workaround which has been fairly widely posted by now.

Good luck! :)

I'll update the Ubuntu Wiki page you linked later today. **EDIT:** Done.

---

### Post by PPPP on 2011-07-26
Thanks coffeecat :)

---

### Post by morningstar.fallen on 2011-12-10
Sorry to revive this dusty ol' thread but I thought there might be someone out there who would be interested in reading this... :)

So basically, I have this older build that was starting to act slow and silly under windows so I've switched to Ubuntu 11.10 amd64. Everything works perfect so far but the above mentioned graphic card (HD 5450) is a fair bit of a pain. Mine isn't radeon but sapphire but it shouldn't really make any difference as the both use the same AMD CEDAR chip. And what I find with my current OS is that it works best on stock driver that comes out of the box. Do not bother installing ATI/AMD proprietary FGLRX graphics driver because it is just waste of time. It decreases performance when playing a high quality video (tested on 1080p mkv film) and it also causes XBMC not to close down properly (it blanks the screen after exiting the app and only restart helps). It the post-release update fixes it I don't know because it won't install through GUI and also voids the installation of the original FGLRX driver every time I try. And when you try to install it using terminal as described [here,]("http://askubuntu.com/questions/78906/ati-amd-proprietary-fglrx-graphics-install-fails-how-can-i-resolve-the-problem") all you get is again both drivers "not installed" after reboot.

So, this Gallium 0.4 stock (open-source) driver that runs my GPU now is doing a great job and shame on ATI for creating a non-opensource software that cannot properly handle it's own family product.

---

