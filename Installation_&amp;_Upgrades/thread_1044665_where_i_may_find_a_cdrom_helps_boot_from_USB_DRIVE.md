---
title: "where i may find a cdrom helps boot from USB DRIVE ?"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by lse123 on 2009-01-19
where i may find a cdrom or burn it[iso] which it helps[BOOT] my old PC boot from USB DRIVE ?

---

### Post by ssorc on 2009-01-19
If your PC is old, you may not be able to boot from a USB device. The first thing to do is check your PC's BIOS to see if there is an option to boot from a USB device.

The following document should help you with the rest of your question:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by boof1988 on 2009-01-20
Does [this link](http://www.pendrivelinux.com/category/usb-boot-cds/) help any?

There should be a link somewhere on that page that could help... Take a look...

Hope this helps...

---

### Post by lse123 on 2009-01-20
i make a usb with ubuntu free cd but do not boot , i buy my laptop at 06 dec 2004, proceed to try usb boot cd ? by what date pcs - laptops started boot from usb auto ?

---

### Post by Mze on 2009-01-20
You'd have to enable booting from USB in your BIOS if you haven't done so yet. 

Then restart your machine to effect the change.

---

### Post by boof1988 on 2009-01-20
> **lse123 said:**
> i make a usb with ubuntu free cd but do not boot , i buy my laptop at 06 dec 2004, proceed to try usb boot cd ? by what date pcs - laptops started boot from usb auto ?

You can try (pressing repeatedly) each of the following keys as your computer starts up.

<F2> <F12> <F11> <del> 

Hopefully this will allow you to enter either your bios-setup or your boot selection menu.  There should be an option somewhere to tell the computer to boot from USB (if the computer has the capability).  If there is no option to boot to USB flash, then you might need to create one of the CDs to get your computer to boot to USB.

---

### Post by lse123 on 2009-01-21
If my laptop built at november 2004 is new enough to boot from usb ?

---

### Post by lse123 on 2009-01-21
How i enter bios from vista ?

---

### Post by boof1988 on 2009-01-21
> **lse123 said:**
> How i enter bios from vista ?

You can get to the bios configuration during the boot up process.
[LIST=1]
[*]Start with your computer turned off.
[*]Press the power button (to turn the computer on)
[*]Repeatedly press each of the keys I mentioned in the previous post (i.e. <F2>)
[*]One of those key presses should either take you to the "BIOS" or to a "Boot Order Selection".  If you don't succeed, before Windows starts, you can turn your computer off after windows has loaded (like you usually do) and start from step "1" again.
[*]If you are in the "Boot Order Selection" (or some other similar name), choose boot from USB.  It may not be one of the options.  If it is not you will need to make a "BootCD for USB".
[*]If you are in the "BIOS", there should be an option to change boot order.  If this is the case, you can make the USB device to be the first boot device.  But only if it is actually one of the options.  If it is not one of the options you will need to make a "BootCD for USB".
[*]Post back here with any results from these steps.
[/LIST]

---

### Post by lse123 on 2009-01-21
if for a reson do not confg BIOS and can be confg-ed to boot from usb, may optionally make a "BootCD for USB" and use it or this needs absolutelly to confg[ENABLE IN] BIOS the boot from usb ?

---

### Post by boof1988 on 2009-01-21
> **lse123 said:**
> if for a reson do not confg BIOS and can be confg-ed to boot from usb, may optionally make a "BootCD for USB" and use it or this needs absolutelly to confg[ENABLE IN] BIOS the boot from usb ?

I think you are going to need to make a CD that can boot the USB-drive.  All this sort of disk does (I believe) is load drivers needed to boot the USB-drive and also provide a bootloader to do the job.

I haven't done this yet... but I will try to find the links and help you do this if you like.  It could take a long time, though, as it appears hard to communicate somewhat.

I'm willing to help you as much as I'm able.

Can you post the "Manufacturer" and "Model Number" of your computer so I have a better idea of what hardware you're using?

---

### Post by lse123 on 2009-01-21
MAY use the CD: "BootCD for USB", even if NOT setup BIOS[BOOT from USB] ?
I had XP in my laptop but now VISTA HOME BASIC, MODEL:
"Sony Vaio Notebook VGN-A297XP, Pentium M1.8GHz, 2GB RAM" 
TO MAKE THIS CD EXIST THE: 
Make a USB Boot CD for Ubuntu
[http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/#more-680](http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/#more-680)

---

### Post by boof1988 on 2009-01-22
> **lse123 said:**
> MAY use the CD: "BootCD for USB", even if NOT setup BIOS[BOOT from USB] ?

Yes... you should be able to use the CD to boot a USB-Flash Drive.

EDIT: I just noticed that the link you posted is for Ubuntu  8.10.  This may mean that the CD will only boot the Ubuntu 8.10 Desktop USB.  It may not boot any other USB-flash drives.

> **lse123 said:**
> I had XP in my laptop but now VISTA HOME BASIC, MODEL:
"Sony Vaio Notebook VGN-A297XP, Pentium M1.8GHz, 2GB RAM"

Thanks for the information... It helps.
 
> **lse123 said:**
> TO MAKE THIS CD EXIST THE: 
Make a USB Boot CD for Ubuntu
[http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/#more-680](http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/#more-680)

I just looked at this website.  If you do not want to go through the whole tutorial, there is a link on that page to download the pre-made iso image.  If you use this iso image, you wont have to go through the whole tutorial.

The link on that page is labeled "USBCD810.ISO".  Here is the text from the area of the page where the link is located:

> If you wish, you can skip this tutorial and download the [SIZE="3"]**[COLOR="Blue"]USBCD810.ISO[/COLOR]**[/SIZE] we created using the same process.

USB Boot CD for Ubuntu 8.10 creation essentials

    * PC with a BIOS that does not support booting from USB
    * Working CD Drive and USB Port
    * Ubuntu 8.10 Live CD
    * USB flash drive with Ubuntu 8.10 preinstalled


I will download the iso and see if it works on my computer since I haven't done it yet. :)

---

### Post by lse123 on 2009-01-23
may extract the iso to a folder and burn it's contents on a CD ? Or is needed directly burn it ?

---

### Post by boof1988 on 2009-01-23
> **lse123 said:**
> may extract the iso to a folder and burn it's contents on a CD ?

No.  You do not want to extract the iso first.

> **lse123 said:**
> Or is needed directly burn it ?

Sort-of...

[LIST=1]
[*]Do not copy a file called USBCD810.ISO onto the CD.  This will create a file called USBCD810.ISO on the CD and that is not what is needed.
[*]You do want to use one of the applications that can burn a "CD image" or "image type: iso" to the CD.  See explanation below.
[/LIST]

You must burn it as an image to the CD (use the "burn as iso", "burn as image", "image type: iso" or something similar).

Two CD burning software packages you could use (of course you could use any other package that can "burn as image" etc.) are:

[LIST=1]
[*]If you have Ubuntu on a machine, one option is to use "Brasero".  Brasero is a default install in Ubuntu.  I have attached a screenshot of Brasero's opening screen.  If you use Brasero, you should use the "Burn image" option and use the file USBCD810.ISO for the "Image Path".
[*]If you have Windoze, one option is to download/install/use "Isorecorder".  Here's a link to [ISO Recorder's website](http://isorecorder.alexfeinman.com/isorecorder.htm).
[/LIST]

---

### Post by boof1988 on 2009-01-23
I just tried out the bootmanager which I mentioned below.  It seems like it might be pretty flexible.  But I think it may be a bit difficult to use.

Was going to remove the text... but I figured it may help someone eventually... So I left it in.

> I just found another bootmanager (mentioned on another thread) for using the CD to boot the USB.

Here's a link:  [http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

---

### Post by lse123 on 2009-01-23
i can not find burn iso but i extracted iso contents in a folder and copy this folder contents ,not the folder, to cdrom , is it wrong ?
After boot from usb with an
CD to boot the USB
may eject this cdrom ? or must be in till shut down ?

---

### Post by boof1988 on 2009-01-23
> **lse123 said:**
> i can not find burn iso but i extracted iso contents in a folder and copy this folder contents ,not the folder, to cdrom , is it wrong ?

I don't know... When you boot your computer from the CD, does is show a grub-boot menu?  (I have attached an image of what the screen should/could look like)

> **lse123 said:**
> After boot from usb with an
CD to boot the USB
may eject this cdrom ?

Yes..  You can eject the CD anytime after it is done booting the USB-device.

> **lse123 said:**
> or must be in till shut down ?

You do not have to shut down the computer before removing the CD.

---

### Post by lse123 on 2009-01-24
in my case it does not boot, CD for usb boot HAS: 5 files 2 folders...if my pc does not support boot from usb, with CD help, may boot ?

---

### Post by boof1988 on 2009-01-24
> **lse123 said:**
> in my case it does not boot, CD for usb boot HAS: 5 files 2 folders...if my pc does not support boot from usb, with CD help, may boot ?

Are you saying the computer wont boot the CD?  If so, then continue to the following suggestions.

You need to burn a new copy of the CD.  It probably didn't boot properly because the files/folders were copied to the disk rather than the *iso image* being burnt to the disk.

What program do you have installed for burning CDs?  If your program doesn't have the option to burn as an iso, would you consider downloading/installing Infra Recorder?

I assume you are using a Windows Operating System...  So here's a link to [Infra Recorder download page](http://infrarecorder.org/?page_id=5).  I recommend that you download/install Infra Recorder to burn the iso image (of "CD to boot USB") to the CD.  Burning the CD as an iso image is different than copying the folders/files to the disk.  And burning an iso image is what you need to do.

Here's a link to [BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) at the Ubuntu Community Documentation.

---

### Post by lse123 on 2009-01-25
if my pc **does not support** boot from usb[BIOS], with CD help, may boot ? If no, i must confirm this first ? I use nero9 burning software, supports <burn as an iso> directly ? i can NOT find it...

---

### Post by boof1988 on 2009-01-25
lse123,

I'm having a little trouble understanding your questions.  Let us use one question at a time.

Are you using a Windows operating system?

---

### Post by boof1988 on 2009-01-25
On a side note...  Here is another link to an iso-burning software package for Windows.  The web-page includes screen shots of the utility.  This one seems easier to use than Infra Recorder. I can't find any good screen shots of Nero 9, that's why I am recommending you download a burning utility that has online screen shots available.

[http://www.ntfs.com/iso_burner_free.htm](http://www.ntfs.com/iso_burner_free.htm)

---

### Post by lse123 on 2009-01-25
yes i use vista...if my pc does not support boot from usb[BIOS], with CD help[boot from usb CD], may boot ? If no, i must confirm this first ?

---

### Post by boof1988 on 2009-01-25
> **lse123 said:**
> yes i use vista...

I don't know much about Nero 9.  So if you insist on using that to burn the CD, all I can say is to use the option most similar to "Burn as iso" or "Burn as Image".  If you need more help with actually burning the CD, than I would recommend using one of the CD-burning utilities I have mentioned (isoburner).  It has an option that will burn the image properly.

> **lse123 said:**
> if my pc does not support boot from usb[BIOS], with CD help[boot from usb CD], may boot ?

You *should* be able to use a CD (with the USBCD810.ISO image burned to it as an iso image) to boot a USB-flash that has a bootable image of ubuntu-8.10-desktop-amd64.iso (or ubuntu-8.10-desktop-i386.iso) iso image copied to it using [Unetbootin](http://unetbootin.sourceforge.net/) or some other method like the ones at [PenDriveLinux](http://www.pendrivelinux.com/).

But we wont know for sure until you can actually boot the CD.  And the screen looks like the attached image.

> **lse123 said:**
> If no, i must confirm this first ?

Can you try to clarify this?  I'm not sure what you mean.  Do you have a limited number of CD disks to burn and don't want to waste them?  Or is there some other difficulty?

---

### Post by lse123 on 2009-01-25
the software you mention can run in a pc with nero9 ?
Please answer: if my pc does not support boot from usb[BIOS], with CD help[boot from usb CD], may boot ? **yes can boot / no must support this to boot **

---

### Post by boof1988 on 2009-01-25
> **lse123 said:**
> the software you mention can run in a pc with nero9?

Yes, you can have more than one CD-burning applications on your computer.

> **lse123 said:**
> Please answer: if my pc does not support boot from usb[BIOS], with CD help[boot from usb CD], may boot ?

Maybe... We wont know until you have a [boot from usb CD] that actually boots up on your machine and shows the GrUB bootloader screen (that is attached in my earlier post).  You will just have to try using the [boot from usb CD] and it that doesn't work, we can try to find something that does work.

> **lse123 said:**
> **yes can boot / no must support this to boot **

I don't know how to answer this question.  I did some searching and it seems that your computer can't boot the USB directly (but I can't be sure since I'm not at your computer).  But your computer may be able to boot the USB by loading the drivers from the [boot from usb CD], which I have been trying to help you make.

---

