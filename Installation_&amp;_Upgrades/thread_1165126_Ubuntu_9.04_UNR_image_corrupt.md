---
title: "Ubuntu 9.04 UNR image corrupt?"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by naycon on 2009-05-20
I have been trying to install UNR 9.04 on my netbook, but it seems that something is wrong. The install fails and if I test the integrity of the install it keeps telling me that one file is corrupt. 

I've downloaded the image from different sources (Sweden and Ireland) and the MD5 checksum seem to be correct in both cases. I've tried two different USB pendrives, both giving the same result. I've tried writting the image from two different computers, with no better luck. Finally I've tried using both win32diskimager and flashnul to write the image to the pendrives, but the result is the same. 

I have formatted the pendrives between the atempts and have been using FAT32 with 4096 bytes as allocation unit size, is this correct or do I need to use FAT or some other unit size?

I'm out of ideas on what to try. Anyone else having any clue as to what I could be doing wrong? Or is this some sort of bug?

---

### Post by John Linq on 2009-05-25
My problem was that, I could not write the UNR 9.04 image to my USB devices successfully. After the image writing, the USB devices failed to boot. As what you did, I also tried several tools/methods/devices, but nothing worked. I guess this is because, UNR is designed for Netbook, but what I used is a Desktop, so I am very unlucky.

Finally, after the image writing, I copied all the directories and files from that USB device to a temporary place. Then I formatted a USB device, copied all the UNR directories and files into this formatted USB device, installed GRUB on it, provided related parameters to GRUB (kernel/initrd etc.), then it worked well as a UNR 9.04 Live USB.

---

### Post by naycon on 2009-05-25
Oh but I can boot and the live-image works just fine. It's just one file that is corrupt according to the check-cd utility, and this corrupt file makes the installer crash when I try to install UNR. 

I would say that you failing to create a bootable USB-device probably has nothing to do with whether you use a netbook or a desktop computer, they are both computers and the only difference between the UNR and normal ubuntu seem to be the graphical launcher (correct me if I'm wrong). I mean, it is possible to install normal ubuntu and then download the UNR-packages from the repositories, so the difference them between cannot be that great.

---

### Post by coffeecat on 2009-05-25
> **naycon said:**
> I have formatted the pendrives between the atempts and have been using FAT32 with 4096 bytes as allocation unit size, is this correct or do I need to use FAT or some other unit size?

I'm out of ideas on what to try. Anyone else having any clue as to what I could be doing wrong? Or is this some sort of bug?

I presume since you mention win32diskimager, that you know about the link below and have tried with Ubuntu ImageWriter, but in case you haven't, here's the link:

[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

I don't believe you need to reformat the pendrive because Image Writer uses a dd function and this rewrites the partition table anyway (if my understanding is correct). What netbook are you trying this with? I doubt that would make a difference but I managed to install Jaunty NBR successfully to two Asus Eee PCs, a 701 and a 900.

---

### Post by naycon on 2009-05-25
> **coffeecat said:**
> I presume since you mention win32diskimager, that you know about the link below and have tried with Ubuntu ImageWriter, but in case you haven't, here's the link:

[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

I don't believe you need to reformat the pendrive because Image Writer uses a dd function and this rewrites the partition table anyway (if my understanding is correct). What netbook are you trying this with? I doubt that would make a difference but I managed to install Jaunty NBR successfully to two Asus Eee PCs, a 701 and a 900.

Yes, I know about that page but I haven't tried Ubuntu ImageWriter since I don't have any computer with Ubuntu installed. Do you think there is some problems with how the windows image writers write the image onto the pendrive? I tried both win32diskimage and flashnul with the same result. Should I try to boot with the faulty liveCD, install Ubuntu ImageWriter and write the image to another pendrive?

I'm trying to install it to a Gigabyte M912m. It worked fine with 8.10, but then I thought to do a complete reinstall instead of just upgrading, to get a fresh start again.

---

### Post by coffeecat on 2009-05-25
> **naycon said:**
> Yes, I know about that page but I haven't tried Ubuntu ImageWriter since I don't have any computer with Ubuntu installed.

What you could do is to use any computer with the live desktop CD of Jaunty. So long as you can get internet connectivity in the live session, you can install Image Writer via Synaptic while still in the live session and burn your USB stick with it. Of course, you'll lose Image Writer once you've shutdown from the live session, but it's only a couple of hundred kilobytes anyway.

> **naycon said:**
> Do you think there is some problems with how the windows image writers write the image onto the pendrive? I tried both win32diskimage and flashnul with the same result. I don't know; I've not tried win32diskimage.

> **naycon said:**
> Should I try to boot with the faulty liveCD, install Ubuntu ImageWriter and write the image to another pendrive?

I'm not quite sure what you're saying here: "**faulty** liveCD"? If I'm reading you correctly, it's the NBR image that you're having trouble with, not the live CD iso image. Or have I missed something? I'm sure you know this but, just for the record, there are two Jaunty images you need to think about here. There's the netbook remix, which is an .img file, downloadable here:

[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)

And the live desktop CD image, which is an .iso file, downloadable here:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

So, if you didn't mean to say 'faulty', yes you can indeed do what I described above: boot with live CD, install ImageWriter and write image to a pendrive.

---

### Post by naycon on 2009-05-25
I'll try what you suggested with the ubuntu image writer. 

What I meant by 'faulty' was that the cd-check utility of the live-image (the one you can run when booting from the pendrive) reports that there is one file corrupt. That is, I don't have any problems with putting the image on my pendrive, it seem to be working just fine, but as I said, I'm always stuck with one corrupt file when checking with the cd-check utility. 

I've tried to download the UNR-image from multiple sources in Sweden, Denmark and Ireland, and the MD5checksum has always been correct, meaning that the image downloaded correctly (i.e I got all the data). I'm aware of the different versions of ubuntu and that they come in different formats (iso and img), and the one I'm trying to install is the ubuntu UNR9.04 image.

---

### Post by John Linq on 2009-05-25
> **naycon said:**
> Do you think there is some problems with **how the** windows **image writers write the image onto the pendrive**?

(Just My Guess.)

Yes, all these NAND Flash Storage are not real Hard-Disk; so BIOS has to simulate them as virtual Hard-Disk; different BIOS treat the same NAND Flash Storage as different Hard-Disk. 

I assume Netbook has different BIOS from Desktop.

---

### Post by naycon on 2009-05-26
> **John Linq said:**
> (Just My Guess.)

Yes, all these NAND Flash Storage are not real Hard-Disk; so BIOS has to simulate them as virtual Hard-Disk; different BIOS treat the same NAND Flash Storage as different Hard-Disk. 

I assume Netbook has different BIOS from Desktop.

I fail to understand how this can be, as there are plenty of people (myself included) that have succeded in creating a bootable pendrive from a normal windows desktop computer and installing ubuntu onto their netbooks with it. Can you explain this?

---

### Post by naycon on 2009-05-26
> **coffeecat said:**
> What you could do is to use any computer with the live desktop CD of Jaunty. So long as you can get internet connectivity in the live session, you can install Image Writer via Synaptic while still in the live session and burn your USB stick with it. Of course, you'll lose Image Writer once you've shutdown from the live session, but it's only a couple of hundred kilobytes anyway.

I tried this, with the same result as before, one corrupt file. =/

---

### Post by John Linq on 2009-05-26
> **naycon said:**
> I fail to understand how this can be, as there are plenty of people (myself included) that have succeded in creating a bootable pendrive from a normal windows desktop computer and installing ubuntu onto their netbooks with it. Can you explain this?

(I don't know much about this.)

Real Hard-Disk has real **_Cylinders/Heads/Sectors (CHS)_**; but flash drive doesn't. So BIOS has to set the Cylinders/Heads/Sectors geometry of a flash drive. 

I tried to find some articles for you, but didn't find a good one. 

Maybe you can take a look at the below link:

[http://www.lime-technology.com/wiki/index.php/USB_Flash_Drive_Preparation#If_the_Flash_will_not_boot.2C_read_over_the_following_tips](http://www.lime-technology.com/wiki/index.php/USB_Flash_Drive_Preparation#If_the_Flash_will_not_boot.2C_read_over_the_following_tips)

(The fourth paragraph, If the Flash will not boot, read over the following tips)

---

### Post by John Linq on 2009-05-26
Gigabyte M912m? It seems Gigabyte doesn't manufacture Netbooks? Maybe when users use an ASUS/ACER Desktop/Netbook, everything goes well.

---

### Post by coffeecat on 2009-05-27
> **John Linq said:**
> Gigabyte M912m? It seems Gigabyte doesn't manufacture Netbooks?

<cough> <cough> [Gigabyte M912M]("http://products.liliputing.com/products/?id=205") <cough> <cough> :wink:

---

### Post by naycon on 2009-05-27
> **John Linq said:**
> (I don't know much about this.)

Real Hard-Disk has real **_Cylinders/Heads/Sectors (CHS)_**; but flash drive doesn't. So BIOS has to set the Cylinders/Heads/Sectors geometry of a flash drive. 

I tried to find some articles for you, but didn't find a good one. 

Maybe you can take a look at the below link:

[http://www.lime-technology.com/wiki/index.php/USB_Flash_Drive_Preparation#If_the_Flash_will_not_boot.2C_read_over_the_following_tips](http://www.lime-technology.com/wiki/index.php/USB_Flash_Drive_Preparation#If_the_Flash_will_not_boot.2C_read_over_the_following_tips)

(The fourth paragraph, If the Flash will not boot, read over the following tips)

John, maybe you misunderstood something. I can boot just fine from my ubuntu UNR 9.04 pendrive. What fails is the install, since one file is corrupt (one can check the install files by booting from the pendrive and select the 'check cd' alternative in the boot menu that appears). 

Your proposale to why this is happening would not explain why I cannot create a pendrive from the same computer I want to put Ubuntu on. I am running windows on it right now and I get the same error (one corrupt file when checking the 'cd') when I write the pendrive from there. Same thing if I boot up with the 'faulty' live-image, and download the Ubuntu Image Writer and the img. So I don't think this has something to do with my bios.

---

### Post by dandnsmith on 2009-05-27
I found something, which I think must be akin to this error, when I tried to copy the content of a usb stick with the unr 9.04 installed so that I could modify it. I think it was in the neighbourhood of the ppp stuff.
I continued, bypassing this area, and both the original and the modified copy work as 'live CD' products.

What I haven't tried is installing from it.

---

### Post by John Linq on 2009-05-31
> **coffeecat said:**
> <cough> <cough> [Gigabyte M912M]("http://products.liliputing.com/products/?id=205") <cough> <cough> :wink:

WOW, sorry for my mistake.

---

### Post by fatsmithy on 2009-06-02
Just to say you are not alone!! I have tried downloading the img from a couple of mirrors and a torrent and have used three different usb sticks but everytime I check the usb for disk errors it tells me I have errors in 1 file.

I am off to try installing from it anyway.

BTW I have also tried imagewriter and win32diskimager, both give the same results so my money is on a corrupt .img

If anyone knows better please post and put me out of my misery.

---

### Post by digiapb on 2009-06-03
I had the same result when tested the integrity of the install...

I downloaded the image a couple of times, and kept getting the same result...

I finally just crossed my fingers, and did the install.

Everything worked fine as far as i could tell.

I am wondering if some one just forgot to update something in the integrity test when they remastered from the release candidate to the final release? (compete guess there...)

---

### Post by naycon on 2009-06-04
Good to see I'm not the only one having troubles.

digiapb, did you acctualy manage to install UNR? For me the install program fails after I've partitioned my hard drive.

---

### Post by pmfabri on 2009-06-08
I have the same problem, IMG passes md5, but the disk is corrupt. I have tried using chkdsk /f to fix this, didn't help. I tried reformatting. The disk boots succesfully, but mozilla crashes and the installer won't start. What could be the problem?

---

### Post by naycon on 2009-06-08
Since there seem to be a few now who has this problem, can anyone with a little more experience of Ubuntu and open source tell me if it is proper to place a bug report?

---

### Post by Axons&amp;Dendrites on 2009-06-09
I had the same problem with the USB live boot- with one file faulted by the cd check on the startup page, but thought it was just my file. I ran the live boot, but rather than choosing to install from the startup screen, i selected* install* from the icon list on the left side menue (uder *asseccories*, i think), and it seems installed with no trouble.  I am totally new to linux and totaly clueless about the OS, so i am not able to say for certain it installed 100% erroer free, but my netbook hasn't exploded (yet). All the same, it is disconcerting to see the error message, and if it can be fixed it is worth doing, so as not to turn off new users-- first impressions and all....

---

### Post by naycon on 2009-06-10
> **Axons&Dendrites said:**
> I had the same problem with the USB live boot- with one file faulted by the cd check on the startup page, but thought it was just my file. I ran the live boot, but rather than choosing to install from the startup screen, i selected* install* from the icon list on the left side menue (uder *asseccories*, i think), and it seems installed with no trouble.  I am totally new to linux and totaly clueless about the OS, so i am not able to say for certain it installed 100% erroer free, but my netbook hasn't exploded (yet). All the same, it is disconcerting to see the error message, and if it can be fixed it is worth doing, so as not to turn off new users-- first impressions and all....

Congrats! I cannot install even if I boot into the live-ubuntu and use the icon on the desktop. I would guess that if you succeded in installing it, and it seem to work, then you're off just fine. When I try to install using the icon, it crashes somewhere in the middle of copying files, claming some sort of problem with my dvd (check for scratches, etc).

---

### Post by Ampi on 2009-06-10
I couldn't install UNR because my laptop couldn't boot from USB. But my solution was simply installing the Desktop edition and then

```
$ sudo apt-get install ubuntu-netbook-remix
```

followed (after success) by

```
$sudo apt-get remove ubuntu-desktop
```

Which leaves you with the UNR without having to use any USB drive. 
Of course this only works with an available CD/DVD drive, but maybe it can help somebody..

---

