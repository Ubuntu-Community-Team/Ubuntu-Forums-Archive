---
title: "SD Card Support!!!!"
date: 2006-06-17
forum: Hardware &amp; Laptops
---

### Post by steve k on 2006-06-17
wow, 

so i'm having a much better experience running Dapper on my x40 than I was running it with Breezy, however, i have a few questions about the SD card reader.

If I boot the computer with an SD card in the SD slot of my x40 laptop it appears on the desktop, however, if i remove the card and then put it back in, it doesn't re-appear. What command can I issue to make it recognize the card again?  And is there any place file I can modify to make the issuing of this command automatic when i insert or remove a card?  

Thanks!

---

### Post by luis_a_diago on 2006-06-17
Hello steve,
 I have a Panasonic let's note with Breezy and I don't know how to use my SD card.
 any idea?
regards
Luis 
[QUOTE=steve k]wow, 

so i'm having a much better experience running Dapper on my x40 than I was running it with Breezy, however, i have a few questions about the SD card reader.

If I boot the computer with an SD card in the SD slot of my x40 laptop it appears on the desktop, however, if i remove the card and then put it back in, it doesn't re-appear. What command can I issue to make it recognize the card again?  And is there any place file I can modify to make the issuing of this command automatic when i insert or remove a card?  

Thanks![/QUOTE]

---

### Post by Egalus on 2006-06-18
I guess this problem is related to the early beta stadium of the sd-card drivers in 2.6.15 and 2.6.16 kernel series.
As development only takes place in 2.6.17 kernels for these drivers (and no backports are available) I guess you will have to wait for 2.6.17 to reach stable and compile your own kernel.

I use 2.6.16.20 with some patches and have sd-card support - but with miserable transferrates, 100kb/s write and 200kb/s read is hardly worth anything.

And as 2.6.17.rc6 is not stable for me I will have to wait for better sd-card-reader support too.

---

### Post by Egalus on 2006-06-18
Just to mention that 2.6.17 is out with fast read, but still slow writespeed to my sd-card in my internal sd-card reader.
I am applying a serious of patches for the sd-reader atm to test if that helps with performance.

---

### Post by steve k on 2006-06-19
my transfer rates seem to be ok, it's a bit slow but not bad!

i'm convinced that it's not so much the kernel as something to do with the HAL or something, i'm sure there's a script that i could run or intiate to have whatever recognition procedure that finds the card in the first place find it again.  even manually... anyone know?

also: luis,

maybe just try updating your kernel to the latest version mentioned here in Egalus' post?  If not, i'd recommend upgrading entirely to Dapper, it's nice.

---

### Post by BungaMan on 2006-06-20
Can you guys post what the card reader chipset is?  I'm looking for support on my OZ2 but the hardware manufacturer doesn't want to release the specs and I don't know if someone is doing some reverse engineering on it or whatever.

---

### Post by nolongerlivecd on 2006-06-20
lspci

---

### Post by steve k on 2006-06-20
[QUOTE=BungaMan]Can you guys post what the card reader chipset is?  I'm looking for support on my OZ2 but the hardware manufacturer doesn't want to release the specs and I don't know if someone is doing some reverse engineering on it or whatever.[/QUOTE]
I think this is the right thing that lspci spits out:

Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter

that's what i've got on my laptop.

---

