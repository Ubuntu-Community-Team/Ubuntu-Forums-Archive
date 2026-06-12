---
title: "Completely New to Linux - Seriously Need Help"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by derekmcluckie on 2009-06-01
Hi Guys n Gals,
 
I've been using windows all my life, because it was easy and already installed. Recently my Hard drive died and I didn't have a copy of windows to reinstall on a new hard drive. So in all my wisdom and so that I didn't have to pay that B**tard Bill Gates another hundred odd pounds for a copy of an operating system that I already owned... or should I say owned a liscence to I decided to buy a brand new hard drive and attempt to install Ubuntu on it. I'm having major problems installing from the CD I downloaded and burnt. The CD boots no problems but when I run the installation process it fails at the same bit each time. Something about failed to create ext3 on the new hdd. I have downloaded numerous files to make sure the files weren't corruppted, burned a quite a few iso's at slow speed < x8 just to make sure the files were being burned properly and not lost but it seems to still stick at the same bit. Is there something I need to do to my new hdd before I install ubuntu?? I'ts being recognised in Bios and by the live CD. Any ideas greatly appreciated
 
Derek
 
P.s sorry if this all seems a bit simple but i really am completely new to linux and although I can used windows with no problems my knowledge of how everything works is near zilch.:popcorn:

---

### Post by MichaelSammels on 2009-06-01
What is the error message given by the installer, and what version of Ubuntu are you trying to install?

---

### Post by thomasboleyn on 2009-06-01
> **derekmcluckie said:**
> Hi Guys n Gals,
 
I've been using windows all my life, because it was easy and already installed. Recently my Hard drive died and I didn't have a copy of windows to reinstall on a new hard drive. So in all my wisdom and so that I didn't have to pay that B**tard Bill Gates another hundred odd pounds for a copy of an operating system that I already owned... or should I say owned a liscence to I decided to buy a brand new hard drive and attempt to install Ubuntu on it. I'm having major problems installing from the CD I downloaded and burnt. The CD boots no problems but when I run the installation process it fails at the same bit each time. Something about failed to create ext3 on the new hdd. I have downloaded numerous files to make sure the files weren't corruppted, burned a quite a few iso's at slow speed < x8 just to make sure the files were being burned properly and not lost but it seems to still stick at the same bit. Is there something I need to do to my new hdd before I install ubuntu?? I'ts being recognised in Bios and by the live CD. Any ideas greatly appreciated
 
Derek
 
P.s sorry if this all seems a bit simple but i really am completely new to linux and although I can used windows with no problems my knowledge of how everything works is near zilch.:popcorn:

Download GParted from here and burn it to a cd [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) then boot in to it like you would Ubuntu. Use the partition editor to delete everything on your hard drive and either leave it as 'unallocated' or format it to ext3, which is the filesystem Ubuntu uses instead of NTFS, which is what Windows uses. Make sure you click 'Apply all changes' before booting in to the Ubuntu live cd and installing again. It should work, good luck!

PS. Keep GParted for future use, it is absolutely invaluable.

---

### Post by derekmcluckie on 2009-06-01
Thanks for the quick responses.  I'm at my parents house at the moment so as for the exact error I cannot get that till I get home.  It's at the point were it is at partition formatting, only ever gets to 5% and a message explaining it cannot write ext3 to the hard drive.  I've already downloaded the Gparted w hilst I was on my mums computer there so was intending on trying that when I get home so thanks for that reply, gives me a little more confidence that I'm on the right track.  I thought that the ubuntu cd formats the drive during the installation process?
 
Cheers Derek

---

### Post by derekmcluckie on 2009-06-01
should also mention that it's the latest version 9.04 i'm installing

---

### Post by thomasboleyn on 2009-06-01
> **derekmcluckie said:**
> Thanks for the quick responses.  I'm at my parents house at the moment so as for the exact error I cannot get that till I get home.  It's at the point were it is at partition formatting, only ever gets to 5% and a message explaining it cannot write ext3 to the hard drive.  I've already downloaded the Gparted w hilst I was on my mums computer there so was intending on trying that when I get home so thanks for that reply, gives me a little more confidence that I'm on the right track.  I thought that the ubuntu cd formats the drive during the installation process?
 
Cheers Derek

It does yeah, which is why you can either leave it as 'unallocated' or just format it to ext3, it doesn't really make any difference timewise..even if your hard drive is huge it'll still only take a few seconds. Hope it all works out for you!

---

### Post by derekmcluckie on 2009-06-01
Hi,
 
Back home.  The exact message I get when attempting to install ubuntu is;
 
The attempt to mount a file system with the type ext3 in SCSI1 (0,0,0), partition #1 (sda) at/failed.  
 
Hope this helps anyone to help me!!! 
 
I tried to run gparted from the cd my computer didn't load it up?  I'm going to try downloading and copying it again.
 
Derek

---

### Post by gordintoronto on 2009-06-01
Derek:

The partition editor is a little quirky.  Perhaps you already know this, or maybe not: you say do something, and the partition editor *doesn't* do it until you click on the "apply" button.

You need to delete any partitions, create new partitions and format the new partitions -- which means using the "apply" button several times.


> **derekmcluckie said:**
> Hi,
 
Back home.  The exact message I get when attempting to install ubuntu is;
 
The attempt to mount a file system with the type ext3 in SCSI1 (0,0,0), partition #1 (sda) at/failed.  
 
Hope this helps anyone to help me!!! 
 
I tried to run gparted from the cd my computer didn't load it up?  I'm going to try downloading and copying it again.
 
Derek

---

### Post by derekmcluckie on 2009-06-02
Keep the responses coming I'm loosing mymind.  

Here's where I am at the moment,  tried Gparted from live CD and it runs but as I'm not great with this stuff I'm using the default options and the CD fails to continue.  Tried Gparted from the live CD of Ubuntu and have managed to format partition for ext3.  I've managed to get a little further forward than the original error message and thought excellent must be there now until...  Got another message;

[Errno 30] Read-only file system:/target/lib/modules/26.28-11-genericc/kernel/drivers/misc/c2port.

It says that this is often due to a failed HDD, I'm obviously hoping this is not the case as it's brand new.

I also noticed another message when loading ubuntu live CD up, not sure if this actually an error or not as the CD continues to boot ok afterwards.  It's a black screen and says;

BIOS bug 8254 timer not connected to Io-APIC?

Again all help is appreciated


Derek

---

### Post by presence1960 on 2009-06-02
check this out: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
scroll down to the section detailing F6. That's what you want to do when you boot the Live CD. Try the noapic option. See if that does it. If not you may want to try the alternate text installer. You can get it here : [http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

Hope one of these work for you!

---

### Post by thomasboleyn on 2009-06-02
> **presence1960 said:**
> check this out: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
scroll down to the section detailing F6. That's what you want to do when you boot the Live CD. Try the noapic option. See if that does it. If not you may want to try the alternate text installer. You can get it here : [http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

Hope one of these work for you!

I had to use this option on an old Vaio laptop I used to use, solved a lot of problems for me! That first error message you mentioned though makes me think that it is something to do with the hard drive. See how noapic or apci=off fair.

---

### Post by derekmcluckie on 2009-06-02
thanks,
 
Ill keep you updated I'm currently runnung the seagate diagnostic tool on the hard drive.  it was playing up a bit there after i removed it wasn't being recognised possible a bad cable too but it seems to be recognising now and just awaiting the test results.  when it finishes i will try the no apic option though

---

### Post by derekmcluckie on 2009-06-02
Hmm hard drive failed test within 3 minutes!!!!
 
Brand new my backside, just read the label certified repaired!
 
Guess where I'm going with that?

---

### Post by thomasboleyn on 2009-06-02
> **derekmcluckie said:**
> Hmm hard drive failed test within 3 minutes!!!!
 
Brand new my backside, just read the label certified repaired!
 
Guess where I'm going with that?

Take that **** straight back!

---

### Post by presence1960 on 2009-06-02
Get your money back and go somewhere else to get a new hard drive. Give a thief another chance and they will rob you again!

---

### Post by derekmcluckie on 2009-06-04
Hey, got another hard drive, have installed xp on it at the moment.  Tried to install ubuntu again which was successful. version 8.04.  meant to install the 9.04 version.  Anyway when i installed it my windows failed to load up any ideas why this is?

Derek

---

### Post by presence1960 on 2009-06-04
> **derekmcluckie said:**
> Hey, got another hard drive, have installed xp on it at the moment.  Tried to install ubuntu again which was successful. version 8.04.  meant to install the 9.04 version.  Anyway when i installed it my windows failed to load up any ideas why this is?

Derek

run these two commands in terminal and post the output here.
```
sudo fdisk -l
``` That is a lowercase L in both commands.

```
gksu gedit /boot/grub/menu.lst
```

Let's see what you have there after your windows & Ubuntu installations.

---

