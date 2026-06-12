---
title: "New Computer Build"
date: 2019-10-28
forum: Hardware
---

### Post by daniell59 on 2019-10-28
I am in the process of building a new computer. I was thinking of AMD Ryzen with integrated graphics. I have not decided which motherboard. I am having difficulty in learning whether the chosen components will support Linux. Any suggestions will be appreciated.

---

### Post by Autodave on 2019-10-28
The Ryzen is not a problem.  However, some Ryzens do not have onboard graphics.....make sure before you buy!

---

### Post by TheFu on 2019-10-28
The older Ryzens that end in 'g' in the name 1xxxg and 2xxxg models should all work fine with graphics drivers.  I haven't kept up with the 3xxxg series to know if any issues with GPU drivers exist or not. Probably fine by now, but do your own checking.

As for which motherboard to choose, certain vendors will ignore any Linux questions, so their support would be non-existent.  Whether a vendor refuses to support Linux customers or not **is** a key differentiator in my mind.  I have a Ryzen 2600 with an Asus B450 motherboard that uses an Intel I211 GigE NIC, so I don't have to fight with funky, broken, driver issues.  To me, the $20 extra for Intel NICs is worth avoiding hassles.  Plus the Intel GigE NICs are more efficient with offloading network workloads to the NIC chips.

Other peripherals would each need vetting for Linux compatibility.  Well-known, name brand, disks, SSDs, all work.  2nd-teir brands can be hit-miss. For scanners, printers, it is always hit-miss.  Wifi is always miss-hit ... with more hassles than it is worth, IMHO.

---

### Post by Skaperen on 2019-10-29
i've always chosen vendors that are explicit about supporting Linux, when buying for companies i worked for.  that was always 100% success.  for my own personal stuff, back when i liked to build, i would spend a lot of time researching my selections and/or buy from the vendors that are explicit about supporting Linux.  everything was always compatible.  i did have to take a board back once that was dead (not even a beep out of it).  they took my word for it and handed me a replacement in a new box (it worked).

---

### Post by daniell59 on 2019-10-29
I am currently using an Epson Scanner Perfection V30. I am satisfied with it. There is a problem however. It wont work on Ubuntu later than 16.04. When contacting the company, they replied by saying that they don't support Linux.

---

### Post by TheFu on 2019-10-29
> **daniell59 said:**
> I am currently using an Epson Scanner Perfection V30. I am satisfied with it. There is a problem however. It wont work on Ubuntu later than 16.04. When contacting the company, they replied by saying that they don't support Linux.

Yep. Epson is on my "avoid" list.  I gave an Epson inkjet away in the early 2000s.

BTW, Seems Ryzen 3000 had an issue so be certain you get any firmware updates available.  BIOS updates are important BEFORE a new install.

---

### Post by oldfred on 2019-10-29
New Ryzen 3000 systems must have UEFI update from vendor that includes AMD's update.
AMD UEFI/BIOS update for Ryzen 3000 series
[https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good)
ASUS ROG CROSSHAIR VIII HERO WiFi - update supports Ubuntu 19.04
MSI has also put out BIOS updates last week as a "beta" though without explicitly acknowledging the Linux fix. 
 Asus ROG Strix B450 E motherboard UEFI update worked
[https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679](https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679)

---

### Post by daniell59 on 2019-11-05
I am now looking for a Ryzen compatible MB. I want one that will support 3rd generation Ryzen without a BIOS update. Two years ago it was a nightmare building my wife's computer. I was told that it was compatible with the 2nd generation Ryzen. It took 3 boards to finally have a working computer.

---

### Post by mastablasta on 2019-11-06
can new BIOS be updated, if you don't have windows?
i really miss a list of well supported desktop motherboards or at least vendors that offer support.

been thinking of getting a PC for the kids, but officially it's either pre-built business/pro intel based desktops or a few laptops (again mostly intel only). officially.
but to build one yourself you would need to know the motherboard compatibility (since now motherboards have network chips and audio chips. the rest is standard drivers and should work.

i wonder whta th esupport for ITX baords is. i was thinking of getting smaller box if i go with desktop.

---

### Post by oldfred on 2019-11-06
I have not had an issue updating UEFI on my Asus or Gigabyte motherboards. They directly read from within UEFI an update file from a FAT32 formatted partition. I use my ESP, since it is FAT32.
Many have three ways, Windows, DOS bootable flash drive, and directly from within UEFI reading a FAT32 partition for update file.

Now some systems support direct update from Linux.
Devices using LVFS for firmware updates
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

This is now an old build, so most parts either are not available or expensive. Newer parts would be cheaper.
oldfred's new SFF system with skylake i5-6500 and 16.04
[http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024](http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024)
[http://pcpartpicker.com/p/8QKkCJ](http://pcpartpicker.com/p/8QKkCJ)

---

### Post by CatKiller on 2019-11-06
> **mastablasta said:**
> can new BIOS be updated, if you don't have windows? 

Of course it can. Just the idea of allowing Windows to update the BIOS gives me chills. Plonk the file on a USB stick, boot into the BIOS, hit the update button. 

Many motherboards don't even need a CPU to be able to update the BIOS, and for the specific case of AMD chipsets not being able to boot with a new CPU they'll lend you one so that you can do the update. 

>  but to build one yourself you would need to know the motherboard compatibility (since now motherboards have network chips and audio chips.

Intel network devices are generally completely painless. They win both sides: their devices tend to comply with standards, and they're heavily involved with drivers in the kernel, too, if there were any quirks.

For audio, if they just say that *it's got some* then it will probably be fine. It's when they make a big song-and-dance about it that means they've monkeyed around with it as a "value add" and you'll need to check the ALSA compatibility matrix.

External devices are pretty much the same: boring standards-compliant stuff will probably work; stuff where they've messed with things might not. My network printer, USB sound card, Bluetooth headphones, and Steam controller all work out of the box because they just behave according to standards.

---

### Post by CatKiller on 2019-11-06
> **daniell59 said:**
> I am now looking for a Ryzen compatible MB. I want one that will support 3rd generation Ryzen without a BIOS update. 

That's pretty easy to achieve. The 500 chipsets were introduced with the 3000 Ryzens. They'll all be fine. 400 chipsets that were made before the 3000 Ryzens were released would need a BIOS update to support the new CPUs. 400 chipsets that were made after the 3000 Ryzens were released will have had the BIOS update already applied, and will probably have a sticker to that effect.

Should you inadvertently purchase an older motherboard that hasn't had the BIOS update, and your motherboard is unable to boot with the new CPU, and you're not near a computer shop where they can do it for you, AMD will lend you a CPU to boot with to do the update.

---

### Post by mastablasta on 2019-11-07
> **CatKiller said:**
> Of course it can. Just the idea of allowing Windows to update the BIOS gives me chills. Plonk the file on a USB stick, boot into the BIOS, hit the update button. 

Many motherboards don't even need a CPU to be able to update the BIOS, and for the specific case of AMD chipsets not being able to boot with a new CPU they'll lend you one so that you can do the update. 

interesting. and goot do know that BIOS update is easier these days. cause we had these cheap Acer laptops with Ryzen and 16GB RAM (no OS preloaded) and they took a lot of effort to get them working with Linux. the starting point was to use windows 10 to upgrade BIOS :-)


> 
Intel network devices are generally completely painless. They win both sides: their devices tend to comply with standards, and they're heavily involved with drivers in the kernel, too, if there were any quirks.

For audio, if they just say that *it's got some* then it will probably be fine. It's when they make a big song-and-dance about it that means they've monkeyed around with it as a "value add" and you'll need to check the ALSA compatibility matrix.

External devices are pretty much the same: boring standards-compliant stuff will probably work; stuff where they've messed with things might not. My network printer, USB sound card, Bluetooth headphones, and Steam controller all work out of the box because they just behave according to standards.

oh right, they have USB sound cards now. well then this is not an issue really. yeah intel chips for network or at least with their standards.

yeah standard stuff is best even if it's oldest. was just looking into getting a mechanical keyboard cause i "destroyed" 3 keyboards in the past year. too much e-waste & i feel bad about it. the standard mechanical ones seem to work well (e.g. Cherry). the gaming ones... well issues here and there. i don't have time to deal with that. i spend 0,5 - 1,5h hours on home PC. and i would prefer to use that time well rather that fiddle with settings and OS. that is also why i just use standard desktop environments and LTS. the only pimping i do is occasionally changing the default wallpaper. :)

---

### Post by CatKiller on 2019-11-07
> **mastablasta said:**
>  was just looking into getting a mechanical keyboard cause i "destroyed" 3 keyboards in the past year. too much e-waste & i feel bad about it. the standard mechanical ones seem to work well (e.g. Cherry). the gaming ones... well issues here and there. i don't have time to deal with that. 

I can tell you from experience that Summer Fruits squash is an EMP in a cup, even for mechanical keyboards. The media buttons and awesome volume control on the Das Keyboard mechanical keyboard all work perfectly with Linux.

Most of the "gaming" peripheral manufacturers aren't remotely interested in supporting Linux. Logitech stuff has been reverse-engineered fairly well because it's widespread, but there aren't any standard ways of doing RGB or force feedback.

In general if a piece of hardware requires additional software to work, even on Windows, then it means that the hardware itself is inadequate.

The Piper project has done well with bringing the means to configure mice into one interface.

---

### Post by mastablasta on 2019-11-08
i don't really need RGB or force feedback or volume. i would just like to have back light and descent mechanical keys. i see Das keyboard has some basic version that would fit, so i need to look into that as well.

i had cheap 30 EUR gaming bling keyboards with official linux support. and the ligths and all worked perfect. keys were soft to the touch. but unfortunately the membrane sucked so i ruined them fairly quickly.

---

