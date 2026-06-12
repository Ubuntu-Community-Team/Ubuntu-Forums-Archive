---
title: "Installing to USB as a test"
date: 2010-08-03
forum: Hardware
---

### Post by X5-655 on 2010-08-03
I want to give Ubuntu another chance, as it used to be my main OS before Windows 7..

See, last time I gave it up, was because I got a new laptop that was seemingly incompatible with the ATI Proprietary driver, as, as soon as that was installed, the screen would go black and never come back up, and just flashed a CLI login prompt constantly back and forth.  (Since laptop ATI graphics chips even on Windows, can't use the official ATI drivers and especially for HP, MUST use the HP ATI OEM drivers for graphics..)

Well I want to try it again, but instead of reformatting my hard drive again, I want to install to USB..  I know the one method to put the live CD on the USB and run that, but it doesn't keep settings, as if it's a CD, and every reboot is a default..  I want to be able to actually install the proprietary driver on the USB disk, and see if it works this time, along with attempting to fix the sound on headphones only bug..

---

### Post by Kyentei on 2010-08-03
So, your question is how to create a persistent USB device with ubuntu? You can either boot the Ubuntu live CD and then create a persistent USB stick with ubuntu bij choosing "System>Administration>Startup Disk Creator" or find yourself a tutorial at [www.pendrivelinux.com](www.pendrivelinux.com) :-)

---

### Post by X5-655 on 2010-08-03
Startup Disk Creator seems to be the better route.

PS:  Does anyone else with a 64-bit ubuntu install and an ATI graphics chip laptop have the black screen problem at boot?  I tried to Google this but just find a bunch of generic linux ATI black screen problems, including one where a 64-bit OS may try to run the 32-bit driver..

---

### Post by Kyentei on 2010-08-03
Can't help you with that. I suggest you try both x64 and x86.. ;-)

---

### Post by X5-655 on 2010-08-03
I'll try the 32-bit version under one condition, that Ubuntu can use the 4GB of RAM my laptop has..  Yes some of it is used towards video, but will it in theory be able to address all 4GB?

(I ask because technically Windows 32-bit can access more than 4GB but MS disabled that and only for the server versions, using PAE)..

If that's the case and all 4GB can be seen and used in 32-bit Ubuntu, I'll just go for that then.

---

### Post by Kyentei on 2010-08-03
I've never seen my 32-bit OS'es use more than 3,5GB. So I don't think so.

---

### Post by X5-655 on 2010-08-03
That will be a problem for me then..  I want my full 4GB usable..

EDIT:  I'm gonna try and do it while at work today..  My laptop doesn't have a BIOS, instead has EFI, so hopefully I'll get lucky and EFI won't assign anything to the "under 4GB" mark for it's own devices.

---

### Post by spydeyrch on 2010-08-03
Well, you have two options really (I am assuming that your USB drive is a USB thumb flash drive):

1.)  You could create a persistent USB. Basically it is a Live USB but has a file on it that keeps any and all changes. i.e. updates, driver installs, program installs, personal settings, folder settings, etc.....

Pro - Faster than a Live CD. You are able to save changes to it and take your OS with you. It doesn't rely heavily on the USB for read/writes because when you boot from it, everything is placed into your main memory and run from there. The only reads/writes that happen are at boot, access a program not currently loaded into memory, and at shutdown when the persistent file is written to.

Cons - Much slower compared to option #2 and a regular HDD. System may be a little unstable at times (at least in my experience)

2.)   You can install ubuntu to your usb drive as if your USB drive was a normal HDD. You would go through all the normal steps of the installation but select your USB drive as the install point.  Also, make sure that you install GRUB to the USB drive too and not to any of your internal HDD. I would recommend that you disconnect any of your internal HDD before you start the installation program so as not to accidentally install grub to your USB drive and not be able to boot when it isn't connected.

Pros - Runs faster than the live USB. Portable. Keeps all changes made because it acts just like a normal HDD.

Cons - More reads/writes than the Live USB due to full install onto USB drive, this lowers the life of your USB device. 

These are just my thoughts on what you could do.

-Spydey :KS

---

### Post by X5-655 on 2010-08-03
Hmm, all good thoughts from you spydeyrch, and kyentei..  And yes, my USB disk is flash..  I thought I said that, but I guess I didn't, oops..

Do you think Wubi could be a good alternative to test the installation out?  If it does infact work without problems now I will in the end, install linux on the entire hard drive..

---

### Post by Kyentei on 2010-08-03
WUBI will do to test, why not? :) If you're going to test it out, please post back the results :-)

---

### Post by oldfred on 2010-08-03
If you have efi you may have issues. I saw were they were making some fixes to make it work better with efi. It seems to work with apple mac via the mac software but straight booting with efi needed some fixes. I installed gpt to see if it would work. I converted one drive and a flash drive to gpt and both boot just fine, but I still have a MBR bios.

If you are just experimenting you may actually have better luck installing Maverick to a flash drive that is gpt formated. A new version is due Thursday.

grub EFI
[http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html](http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html)

I do not know if you have a efi partition if you also need the bios_grub partition or they become the same??
However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img.  Thus, you must make a separate "BIOS boot partition" to hold core.img.  Make it 128 kiB as recommended in the following link.  Actually, using ext2 for example, and GParted Live CD, the minimum partition size is 8 MB, or 32 MB for FAT32.
sudo parted /dev/sda set <partition_number> bios_grub on
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)

---

### Post by X5-655 on 2010-08-03
Yes I do have EFI, not the normal BIOS.

I just tried Wubi on both 32-bit and 64-bit version 10 LTS, and it works, CompizFusion works on the extra setting (telling me opengl works)..  But the proprietary driver didn't install.

I'm gonna try doing the proprietary driver now on Wubi..  But so far, this looks good!

Now, if I do 64-bit distro, will I have problems with 32-bit apps, or is it not so easy like other OS's?  I'm only a linux user from a 32-bit world.

If I do 32-bit, can I get more than 3.4GB of RAM useable?  (32-bit on my laptop only gave 3.4GB, 64-bit gave 3.6GB which is correct due to onboard video)..

---

### Post by oldfred on 2010-08-03
I have 4GB and before Karmic ran only the 32 bit versions. Since Karmic I have run the 64bit without any issues that I could identify to the 64bit kernel.

With 32bit you used to only get 3+GB unless you installed the server version with PAE. Now I understand they include PAE but that still is a workaround.

---

### Post by X5-655 on 2010-08-03
But what about using 32-bit apps on 64-bit linux?

PS:  the proprietary drivers work now, but it boots in 640x480 and not 1366x768 like the open source driver does.  Once it gets to login all is good.

---

