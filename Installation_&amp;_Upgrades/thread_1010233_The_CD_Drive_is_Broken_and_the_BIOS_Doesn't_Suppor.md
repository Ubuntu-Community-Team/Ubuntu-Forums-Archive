---
title: "The CD Drive is Broken and the BIOS Doesn't Support USB booting!"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by transkinetic on 2008-12-13
Hello all,

I am currently running Xubuntu 8.04. I want to do a clean install of Ubuntu 8.10. The CD drive on my laptop is broken. My BIOS doesn't support booting from a usb device. My options are CD, HDD, and Network.

How can I reformat my HDD and install 8.1?

The tools I have at my disposal are an XP machine with a working CD-r/rw drive, a large external HDD, and a large USB stick.

---

### Post by logos34 on 2008-12-13
Either [dl the iso]("http://www.ubuntu.com/getubuntu/download") and burn it to cd using the windows machine or use Unetbootin frm xubuntu:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by transkinetic on 2008-12-13
I should have clarified about the CD drive, it does not read or write CDs. Basically, there is no CD drive on my linux machine.

I'm a bit confused about the functionality of UNetboot.
Reading the documentation makes me think that my course of action should be to:
a) copy Ubuntu's 8.10 iso onto a usb memory stick along with UNetboot's executable,
b) from within my current Xubuntu installation, execute the UNetboot executable located on the memory stick,
c) UNetboot reformats my current drive and installs the Ubuntu 8.1 iso...

wait, that's not right, that would be formatting the drive containing the currently running system.

I'm unsure how to proceed.

---

### Post by transkinetic on 2008-12-13
Okay, so I installed the Unetbootin deb file. It's starts up and the screen it gives looks fairly straight forward.

I think what I want to do is copy the 8.10 image I downloaded onto a USB stick and have Unetbootin use that to install to my HDD.

I'm still a bit confused because Unetbootin is installed to my HDD. Will it then just overwrite its self?

Please let me know if this is the right way to do this.

---

### Post by logos34 on 2008-12-13
no, you want to copy the unetbootin installer to your hard disk--you can't boot from usb so that won't work.  Chmod +x the file, run it and it will get the iso and fix the bootloader so that when you reboot it'll start up the .iso live install session, which then proceeds to overwrite the xubuntu partition (if that is where you want /).

---

### Post by logos34 on 2008-12-13
> **transkinetic said:**
> 
I think what I want to do is copy the 8.10 image I downloaded onto a USB stick and have Unetbootin use that to install to my HDD.

oh, if you already have the 8.10 iso I think you can copy it to the same folder as the unetbootin installer.  not sure, though

---

### Post by transkinetic on 2008-12-13
I think i get it now. Control passes as follows:
bios -> mbr on hdd -> iso on usb...
yay!
I'll report back in an hour...

---

### Post by transkinetic on 2008-12-13
I rebooted and nothing happened. Can I manually edit Grub to point to my USB stick?

---

### Post by transkinetic on 2008-12-13
On the UNetbootin - Homepage there's a line labeled step 3...
"After rebooting, select the UNetbootin entry from the menu list as the system boots up."

I see what happened. Unetbootin saw that I was trying to make a USB disk bootable. It altered the MBR on the USB stick to point to the altered ISO. It left the MBR on my internal HDD alone. Basically I have a bootable USB stick with no way to access it.

Do I want to look into chain loaders? Chaining HDD's MBR to USB's MBR?

---

### Post by logos34 on 2008-12-13
Go back and run the unetbootin installer once more.  WHen the dialog box comes up select 'Diskimage' radio button, then browse to your 8.10 iso.  For 'Type', select 'Hard disk' in dropdown menu.  'Drive' should be '/'.  When you hit ok it should reboot I think and give you a choice of the installer in grub.  It will then start up the 8.10 iso from the hard drive.

---

### Post by transkinetic on 2008-12-14
I tried what you suggested and selected hard disk from the drop down menu. After rebooting, instead of adding an entry to my grub menu, Unetbootin erased all the menu options. Now all I see is a grub command prompt.

I know almost nothing about grub com/mands. I am reading the documentation right now in hopes that I can figure out how to boot from the USB stick.

Can anyone help walk me through the grub commands to boot from USB?

---

### Post by logos34 on 2008-12-14
> **transkinetic said:**
> 
Can anyone help walk me through the grub commands to boot from USB?

why do you keep saying 'boot from usb'???  Your thread title says 'BIOS Doesn't Support USB booting'

---

### Post by logos34 on 2008-12-14
follow [this]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot.") to do a direct kernel boot from the grub prompt:

---

### Post by transkinetic on 2008-12-14
I kept asking about booting from USB because I assumed that grub could load linux from USB even if my BIOS couldn't. Is this incorrect?

I made some progress. I ran UNetbootin again with the exact same parameters and it created the grub entries correctly this time. I watched the verbose of UNetbootin more closely this time as it did it's preparations. It seems that it extracted the contents of the iso onto my internal hard drive.

Anyhow, I'm typing this from the "live session" of 8.1. What I want to do is tell this live session to format my internal disk and to a full clean automatic install. I'm hesitant to proceed because this live session is actually installed to the drive which I'm preparing to format...

Again, I'm unsure how to proceed.

---

### Post by logos34 on 2008-12-14
> **transkinetic said:**
> Anyhow, I'm typing this from the "live session" of 8.1. What I want to do is tell this live session to format my internal disk and to a full clean automatic install. I'm hesitant to proceed because this live session is actually installed to the drive which I'm preparing to format...

ok, we're making some progress

at the partitioner choose 'use entire disk' option (not 'manual' and not 'largest continuous free space')

---

### Post by transkinetic on 2008-12-14
All of a sudden and quite unexpectedly, my CD drive is working again. I booted the Ubuntu 8.1 installer off of it. Unfortunately the partitioner doesn't detect my internal drive. It detects my USB stick and USB hard drive.

...maybe rebooting and doing a rain dance will fix it...

Any ideas?

---

### Post by transkinetic on 2008-12-14
I've devised a null hypothesis. I think booting from the CD drive failed and the boot process automatically fell through to the live session on my hard disk. I know that the CD drive works to some extent because I can browse it from the live session.

I'm now trying to install 8.1 onto a 4gig USB stick. I'm skeptical about booting to it later seeing as my BIOS doesn't support booting from USb devices...

---

### Post by transkinetic on 2008-12-14
> **logos34 said:**
> ok, we're making some progress

at the partitioner choose 'use entire disk' option (not 'manual' and not 'largest continuous free space')

Sadly, when using a disk to run the live session, the live session doesn't allow installing to that same disk.

My only hope is to somehow get a live session running on a disk that isn't the one I want to install to.

---

### Post by logos34 on 2008-12-14
then try the "guided--resize" option--it will shrink the existing ubuntu / partition and install in the resulting free space.  Then you can boot into your new ubuntu and delete the other.

---

### Post by transkinetic on 2008-12-14
I like that idea. It makes a lot of sense to me both logically and intuitively. Unfortunately, the partitioner doesn't show the existence of the drive at all. Possible it would show up if I were to partition it before going into the live session. I'm not sure how I would accomplish this though...
...possibly I could do something in the live session before going into the install wizard. I could try some other program like gparted to resize the partition. No, that doesn't make sense. In order to resize it, I would need to umount it. I don't think Ubuntu would let me umount the filesystem that it's installed to.

This is one twisted game of shanghai mahjong right here.

---

### Post by transkinetic on 2008-12-14
I rebooted after installing 8.1 onto my USB stick only to be greeted by the same UNetbootin gub menu. I hit c to get to a grub command line and entered

find /sbin/init

,hoping to find that I could tell grub to boot from the USb stick.

Unfortunately the only device returned was hd0,0.

At least I can still use Unetbootin to get into 8.1, live session.

---

### Post by logos34 on 2008-12-14
real catch-22 situ 

um, let's see: can't boot live cd, can't get unetbootin/ubuntu iso live session to see hard disk so you can shrink it, can't boot usb...At the very least you need to work from some live session--any--so you can resize /, because it can't be mounted during the operation.  looks like we're fresh out of options...dunno what to suggest.  What about gparted in the live session-->system>admin>partition editor--you try that?

---

### Post by logos34 on 2008-12-14
> **transkinetic said:**
> 
Unfortunately the only device returned was hd0,0.

that's got to be / partition.  Probably should try that next to boot back into ubuntu on the hard disk, remove unetbootin from /boot/grub/menu.lst, then if necessary run sudo grub-install /dev/sda to rewrite grub to mbr

---

### Post by transkinetic on 2008-12-14
Gparted doesn't let me umount the drive. I'm going to try a net install.

I'm really impressed with what I've seen so far of this latest version. It's way faster for me than Xubuntu was and this is the first time my tablet has worked plug and play!

---

### Post by logos34 on 2008-12-14
> **transkinetic said:**
> Gparted doesn't let me umount the drive.

wait--that may be because it's using /swap.  Right-click on it and select 'swapoff'.

---

### Post by transkinetic on 2008-12-14
I disabled the swap and deleted that partition. Now I have 310mb of empty space. Perhaps I could use UNetbootin from the ubuntu live session to install DSL onto what used to be the swap. I could then boot into that and do some beneficial formatting from there.

---

