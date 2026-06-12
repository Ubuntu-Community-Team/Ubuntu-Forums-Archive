---
title: "Can I load Kubuntu/Ubuntu Into This Laptop?"
date: 2020-11-29
forum: Hardware
---

### Post by DeadlyOats on 2020-11-29
Can I load Kubuntu / Ubuntu into [this laptop]("https://www.newegg.com/acer-a515-56-56dj/p/N82E16834316938?Description=laptop&cm_re=laptop-_-34-316-938-_-Product")?  Is it compatible?

---

### Post by mastablasta on 2020-11-30
have you seen this?: [https://community.acer.com/en/discussion/607762/installing-linux-on-my-new-aspire-5-a515-55](https://community.acer.com/en/discussion/607762/installing-linux-on-my-new-aspire-5-a515-55)

i would rather go with AMD Ryzen. they cost less and you can get them with no OS preinstalled. Lenovo business, many HP's, Dell with Ubutnu preloaded will work out of the box.

---

### Post by DeadlyOats on 2020-11-30
Thanks for your advice.

What about an [ASUS]("https://www.newegg.com/aluminum-blue-asus-vivobook-l203ma/p/1TS-001A-02GT7?Description=laptop&cm_re=laptop-_-1TS-001A-02GT7-_-Product") laptop?

---

### Post by CelticWarrior on 2020-11-30
The Asus one is easier to install but it isn't comparable to the first Acer, in size or performance.

---

### Post by DeadlyOats on 2020-11-30
Thanks.  I am looking for a small machine.  I need it for portability, concealability, and I only need it to process text documents.

But you think Kubuntu/Ubuntu will work fine on it?

---

### Post by CelticWarrior on 2020-11-30
You don't know what you're looking for... 

First you ask about a regular sized laptop (15.6") with a FHD screen with mid-range performance, enough for pretty much any productivity software, all your web browsing and services, any multimedia and even some modern games that don't require a top notch discrete graphics card. Plus it has a fair amount of RAM that can be expanded (up to 32GB, probably) and it comes with a very modern, very fast and relatively expensive 512GB NVMe SSD, also replaceable/upgradeable.

Then you ask about an ultra-portable slim 11" (not FHD) laptop which is a toy and a very much a disposable one. It has everything soldered on-board, RAM and the eMMC. Both the processor which is from completely different line of products - very entry-level, low power - and the much slower 64GB eMMC aren't comparable in any way and, again, not replaceable. The only positive characteristics are the small size and, going by the equivalent product from HP that I own (HP Stream 11), it should have a very comfortable autonomy when on battery. That said, its expected lifespam is no longer than 3 years. After one year of almost daily use mine has only ~80% of the original battery capacity. I expect a drop to 50% or less in the next year and it to be dead at the end of its third year or less. At that point it can still be used plugged in (it will be a nice media player still) but not longer after that the battery will start to swell and break everything else. Again, disposable.

Also of note:


[LIST]
[*]The ACER is good for dual-booting with Windows. The caveats Mastablasta alerted to are important, especially for people not familiar with modern hardware and its peculiarities (and this one has many). That said pretty much you can install Ubuntu or one of its variants on anything! The only notable exceptions are the first generations of the Intel "Bay Trail" and "Cherry Trail" families but those are crap anyway and in any case any major desktop Linux can be installed although making all the hardware work acceptably is hard and not for anyone.
[*]If you don't want to keep Windows then with a couple of settings changed in the firmware (UEFI) installing Ubuntu in this ACER is as easy as any other.
[*]The ASUS "toy" is NOT for dual-booting. It's small 64GB eMMC is barely enough for Windows. In a similar one I replaced Windows with Ubuntu. The size is enough (nothing to brag about but just enough) for any major Linux distro. Huge multimedia files can be saved on an additional microSD card (up to 128GB) or external HDDs/SSDs.
[*]Considering the installation of standalone Ubuntu there's really no notable difference except that in the ACER one you may need to set a supervisor password in UEFI in order to "trust" the Ubuntu's (or other's) EFI files and change the drive mode to AHCI on top of the usual disabling of Secure Boot and Fast Boot, whereas in the ASUS "toy" only the usual last two are recommended.
[/LIST]

---

### Post by CatKiller on 2020-11-30
I agree with CelticWarrior about needing to be clear on what you want out of something when selecting it.

If your description of wanting something small and Linux-supported for text is accurate, I'd recommend Dell's XPS 13 Developer Edition. It comes with Linux already installed, and its high quality, high-DPI, screen is great for text. Mine fits in a handbag.

---

### Post by DeadlyOats on 2020-11-30
My apologies for the confusion.

I really need a small laptop.  Something I can hide behind a clipboard while walking around.  I won't use it to surf the net, nor to watch any movies.  It will be purely for creating text documents.

My intent is to repartition the drive and reformat it and only have Linux on it.  I don't want to use Win10.

I asked about the Acer first, thinking that if one Acer works well with Linux, then all Acers would, and then I could find a small Acer and go with it.  However, mastablasta indicated that Acer doesn't play well with Linux.  That's when I asked about Asus.

Celtic Warrior indicated that it would be an easier install, but I want to be sure that all of its features and hardware would be supported with Kubuntu/Ubuntu installed.

EDIT:

I planned to buy an external USB DVD/CD ROM/Burner, to install Linux via DVD...  Is that a bad idea?  Do I really have to make a bootable install USB drive?

---

### Post by CelticWarrior on 2020-11-30
All of either one's feature and hardware is supported but some WiFis are a particular case that may not work OOTB. Even in those cases a one-time driver installation that takes a minute or less is all it needs.

You don't have to be fussy about it if what you really want is to do is texts. A potato will do (well, not really, you know what I mean). You can choose the cheapest one if the small screen doesn't bother you, or get some older used computer from eBay, anything from the last 20-25 years will do. Heck, even an 8-bit computer from the 80s already did it.

---

### Post by DeadlyOats on 2020-11-30
O.K.  Thanks.  Then I'm getting the ASUS.

By the way, I don't think I would be able to conceal an old 80's computer behind a clipboard....

PS

Would I be able to install via external USB DVD/CD ROM/Burner with install DVD?  Or does it have to be via bootable install USB thumb drive?

---

### Post by CelticWarrior on 2020-11-30
> [COLOR=#000000]By the way, I don't think I would be able to conceal an old 80's computer behind a clipboard....[/COLOR]

Sir Clive Sinclair begs to differ: [https://en.wikipedia.org/wiki/ZX_Spectrum](https://en.wikipedia.org/wiki/ZX_Spectrum)
And regarding software [Tasword]("https://spectrumcomputing.co.uk/entry/8856/ZX-Spectrum/Tasword_Two") does exactly what you want. It also runs on all the major architecture families of the same vintage (Commodore 64, Amstrad CPC, MSX and the original IBM PC and clones) and even in its predecessor, the Sinclair ZX81. 

> [COLOR=#000000][INDENT]Would I be able to install via external USB DVD/CD ROM/Burner with install DVD? Or does it have to be via bootable install USB thumb drive?[/INDENT]
[/COLOR]


Yes, but if you need to use an USB device why not use the much faster, simpler and cheaper thumb drive?

---

### Post by DeadlyOats on 2020-12-08
Thank you for your reply, and sorry for taking so long to reply.

> **CelticWarrior said:**
> Yes, but if you need to use an USB device why not use the much faster, simpler and cheaper thumb drive?

I haven't had success making a bootable install USB.  I follow the instructions, but Kubuntu won't install...  So, I still use DVD install.

---

### Post by CelticWarrior on 2020-12-08
Just use Balena Etcher in Windows. It's fool-proof.

---

### Post by DeadlyOats on 2020-12-08
Thanks for all of your help!  I succeeded in using a USB Kubuntu install, and now have Kubuntu 20.04 installed in the Asus device.

---

