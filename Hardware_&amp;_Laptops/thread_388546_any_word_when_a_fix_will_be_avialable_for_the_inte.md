---
title: "any word when a fix will be avialable for the intel 965 chipset?"
date: 2007-03-19
forum: Hardware &amp; Laptops
---

### Post by lime4x4 on 2007-03-19
I really would like to get my pata controller working.I loaded edgy thru a usb cd-rom drive
and i installed another nic card since the marvell lan controller isn't supported yet either

---

### Post by colo on 2007-03-19
You will need to use Feisty, linux-2.6.17 just does not support your EIDE-Controller.

---

### Post by lime4x4 on 2007-03-19
well i did try loading fiesty.And that wouldn't load either

---

### Post by colo on 2007-03-19
Try booting its kernel with "all-generic-ide" as an additional parameter.

---

### Post by lime4x4 on 2007-03-19
well i already have edgy loaded and up and running minus the built in marvell lan and the ide controller

---

### Post by apeman_spaceman on 2007-03-23
I just installed Feisty Beta on my Intel DG965OT board and the Marvell PATA seems to work great so far. I installed the system using my IDE CDROM, and the system now boots off of an IDE Hard Drive.

Prior to the Beta ISO image (released today), I was able to install Feisty using Herd 5 *Desktop* ISO.  The Alternate ISO did not work.

If you're having troubles with Edgy, try the Feisty Beta.
- apeman

---

### Post by lime4x4 on 2007-03-23
well i upgraded my motherboard to the 975 chipset and edgy loaded fine and everything was recognized

---

### Post by mep on 2007-03-28
My new Intel DG965OT mb arrived yesterday.  After a few hours of what I thought would be an easy installation I deceided to Google this model on my son's computer..  I originally was running 6.10 off IDE on a D915AG intel board but thinking I could just install the ide into the new mb was wishful thinking to put it politely.  Anyhow I downloaded the new beta and decided to install a spare SATA drive and redo my installation.  Luckly I had my home directory backed up so all will be well.

My question, What could I have done differently to get my IDE drive going ??With its already installed 6.10.

Also forgot to mentioned after trying again for hrs to get IDE DVD drive to work.  Would go along so far then stop I used my USB drive to install beta..

Anyhow I guess IDE is going away soon as the placement for the IDE plug on the DG965OT is terrible especially when you have a Coolermaster Hyper 6 in there.. :)

Any comment appreciated..

Thanks in advance,

---

### Post by chili555 on 2007-03-28
It is possible to install the 2.6.20-x kernel from Feisty which has several fixes in it. I have done it twice on my laptops and it goes well for me. YMMV. Here is how you can do it:

1. backup /etc/apt/sources.list```
cp /etc/apt/sources.list /etc/apt/sources.list.bak
```2. replace temporary (!) all edgy with feisty in sources.list```
sudo gedit /etc/apt/sources.list
```In any line the is not commented out #, replace the word edgy with feisty. Save and close gedit.
3. apt-get update
4. apt-get install linux-headers-2.6.20-13 linux-headers-2.6.20-13-generic linux-image-2.6.20-13-generic. You may also need linux-restricted-modules-2.6.20-13-generic. Some image or header or resticted stuff may be offered and you should accept. IMPORTANT! Firmly reject the offer for ALL other updates. Ignore the little orange icon.
5. restore your /etc/apt/sources.list from step 1:```
mv /etc/apt/sources.list.bak /etc/apt/sources.list
```6. Reboot

The beautiful thing about installing a new kernel is that if it does not go well (very doubtful), your grub menu, at start-up will still allow you to boot into 2.6.17-x and then remove 2.6.20-x.

---

### Post by mep on 2007-03-28
Thanks  chili555.  I still do have a problem with my old IDE drive that has 6.10 on it.  This board must have named the partitions different than what my bootloader called them.  When I have the IDE hd setup and try to boot from it I get as far as the ubuntu logo screen then it just hangs.  Upon more looking I see it hangs on looking for root partition?.  So as I sit here right now I cant even get into 6.10 with new mb.. :(

If you know how I could I could at least do the kernel upgrade like explained above

Thanks gain in advance

---

### Post by chili555 on 2007-03-28
mep-
As your system starts to boot, you will see a screen that offers to take you to the boot menu if you press ESC. You have all of three seconds! When you get to the boot menu, you will see options to boot into 2.6.17-x. Us the arrow keys to highlight that entry and boot up.

Then *sudo gedit /boot/grub/menu.lst* to amend the location of your root partition in 2.6.20-x to match 2.6.17-x. In my case root is at (hd0,0). If 2.6.20-x got installed elsewhere, I would have to amend it to (hd0,0). Your location may vary.

Save, close and reboot. Post back,please.

---

### Post by mep on 2007-03-29
Hi Chili555,

I still get the hanging on the boot logo ( ubuntu splash screen ) even after trying to boot from a couple of different boot kernels that I have.  My settings are like yours as (hd0,0) for the IDE drive.  I have been trying it for a while now.  I also booted up Gparted latest version to see if it even saw the IDE Master boot drive.  Gparted didnt even see it  No devices found.

So now I am running the 7.04 beta on a SATA and it all worked fine.  Loaded it up from usb dvd drive and went thru install and all updates.  I had backed up my home directory onto another SATA drive so I just copied over my mail and bookmarks and all is well.

I have this funny feeling that IDE is not liked in the Intel DG965OT motherboard.. :)  So I have kept IDE everything out of there..  Even might buy a SATA DVD drive as that Pioneer DVR-212D looks like it will be a good one to pick up.

I gave up on the IDE when Gparted didnt see it...

Now as this thread is kinda about the Intel Board I am sitting here trying to figure out how to get a driver for the onboard ( I heard the shrieks ) video to go to a smaller res of 1200 or something around there..

Anyhow Chili555 thanks...

-mike

---

### Post by maku-d on 2007-04-02
I'm having the same problem, which seems pretty 
    common at the moment. When attempting to boot 
    into the feisty amd64 beta disc, my computer freezes 
    during the initial ubuntu splash screen. 

    I'm using a gigabyte 956p-ds3p motherboard- which 
    has an onboard marvell yukon ethernet adapter which was 
    undetectable in edgy, and seems to be causing similar 
    problems here- unless it's related to the ide/sata 
    controller. 

    Either way, just thought I'd post to add another 
    user with the same problem on a different motherboard.

---

### Post by IM12RU on 2007-04-15
> **lime4x4 said:**
> I really would like to get my pata controller working.I loaded edgy thru a usb cd-rom drive
and i installed another nic card since the marvell lan controller isn't supported yet either

I downloaded Ubuntu 7.04 Beta (Feisty Fawn) on 1 April, 2007.  I have installed it twice (Once to see if it would load and once to get rid of Windows (spit spit) ) on my Intel 965 motherboard with a Intel Core 2 Duo chip.  I installed both time.  It had no problems and detected all my hardware.  I'm using the Gnome desktop and it it fantastic :D .
Bob Jones

---

### Post by mikebravo on 2007-06-21
For IM12RU: Please be more specific. There is more to a system than a motherboard and a processor. The problem has a lot to do with what you are connecting to that motherboard. Do you have a floppy drive connected? Do you have any PATA devices connected? If so, are they optical drives or hard drives or both, and what is their master/slave relation?  Are you using SATA hard drives?  SATA optical drives?   Is your boot drive SATA or PATA?  Have you changed any BIOS settings, especially in relation to AHCI?

Knowing that Feisty works on one 965 motherboard is nice, knowing why would be nicer.

MikeBravo

---

### Post by stadt on 2007-06-23
I have an Asus P5B-E Motherboard, attached Samsung SATAII Harddisk and LG 30N SATAII DVD-Writer. For installation of Ubuntu 7.0.4 it was necessary to disable AHCI in Bios.

After installation AHCI can be enabled and everything is fine. At least here.

Hint: If you have a parallel installed Windows it depends wether you've installed it with AHCI drivers or without. If Windows is installed with AHCI you have to revert to AHCI after Ubuntu installation, otherwise Windows won't boot. Quite similar Windows won't work with enabled AHCI if the AHCI drivers aren't installed.

---

### Post by kyphi on 2007-06-30
In my experience with the 965 chipset, any installation of Ubuntu or any other distro will not eventuate via a PATA drive.

The options to circumvent this are:

a.  use an IDE to SATA converter and connect your optical drive to SATA.
b.  take out your PATA optical drive and replace with a SATA optical drive.

While the first option is cheaper, more SATA optical drives are becoming available and, yes, the Pioneer 212D is a very good option.  If you use the adapter, it needs to be connected to power so you will have to make sure that a spare connector is available from your power supply.

I ended up disconnecting and discarding the IDE cable once my optical drives were connected to SATA ports.  I am sure that my computer will stay a bit cooler now since airflow is not as badly disrupted.

The other change I had to make, was to install an ethernet card.  The onboard chip would not work in Ubuntu.

I also installed a sound card since onboard sound is never satisfactory in my opinion but that applies to all motherboards.

The lesson I have learned from all this is that the next time that I want to build a new computer, I will have to do more research into the different components before making any choices as well as staying away from what was then quite recent technology - perhaps too new.

---

### Post by kyphi on 2007-06-30
Addendum:

Feisty Fawn works fine with the above mentioned system.

---

