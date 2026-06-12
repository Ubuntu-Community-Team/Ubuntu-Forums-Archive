---
title: "Need MBR help!"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by rmhartman on 2009-06-30
Ok, I installed Ubuntu onto a thumb drive (/dev/sdb2) ... well and good.  grub got installed onto my hard drive /dev/sda.  I do not know why it was doing *anything* with my sda, but it did.  

I tried a quick-n-dirty fix copying the MBR from another laptop ... foolishly forgetting that the partition table is also in the MBR.  @#$*@#!!!!!

I am hoping that as part of the grub installation process, a copy of the original MBR is saved.  Does this happen, and if so where can I find it?

If not ... does anybody know some signatures I can look for to identify the start of two NTFS partitions on my hard drive???

It would be really nice if grub hadn't made free with my hard drive in the first place ... I am *really* hoping that it makes an automatic backup ......

---

### Post by Polaris96 on 2009-06-30
I think you're SOL.

---

### Post by thefirstbruce on 2009-06-30
download a  prog called BootIt. 
you'll need to spend a day or two reading the documentation but you should be able to recover your partitions if you haven't written over them, and rebuild partition table.

I've just had a load of trouble with grub as well. Why these goons insist on making the default install overwrite the mbr is a sick joke. most newbies are going to try and install it on the same hdd as windows. 

And once I get 904 working, I can't get flash installed or something that plays mp4 

Ubuntu really have a long way to go before it  is anything more than a tinkerer's headache. I'm not wasting another hour on top of the 4 hours I've pi$$ed up against the wall on it already.

---

### Post by unutbu on 2009-06-30
rmhartman, your problem is fixable using simple tools.

Boot from an Ubuntu LiveCD.
Click System>Admin>Synaptic and install the "testdisk" package.

Open a terminal (Applications>Accessories>Terminal), type
```

sudo testdisk

```
Select "No Log", "Proceed", "Intel", "Analyse", "Quick Search", "Deeper Search". 

Testdisk will search and find your lost partitions.

Use the up/down arrows to move among your partitions.
Press 'p' to try to list files inside the partitions. (This will help you identify your old partitions -- they'll be the ones with files.)
Use the left/right arrows to make the appropriate partitions Primary or Logical.
If you are unsure what to do, post a screenshot of the terminal screen showing the results of the Deeper Search.

---

### Post by ajgreeny on 2009-06-30
Steady on, thefirstbruce.

The reason that ubuntu puts grub on the MBR by default is because that is the best place for it in 99% of cases.  If you are doing an install on the same drive as windows where else would you put it?  If you are doing an install on a second drive that is fixed in the computer, it still makes sense to put grub on the MBR to avoid the need to switch the boot device just to choose which OS to boot.

If you ask someone who is new to linux where to put the grub bootloader when the install gets to that point, you either need to have pages of explanation on what grub is, and then explanations about the possible optional placing of grub.  This would totally confuse the majority of new installers, and in my view would be a retrograde step for a distro that is generally accepted as a good one for the newby.

If you want to put grub elsewhere because you are putting ubuntu on a non-fixed drive such as a usb flash, then you can do so, but you need to look a bit more deeply into things before you start playing around with your computer  and adding new OSs.

The easiest way to sort out your grub/MBR problem is possibly to download and burn supergrub which can search out and mend your MBR, boot your linux partitions and many other things as well.

With regard to your flash and mp4 problem it is the work of a very few minutes to put those right, and this is not a problem just of ubuntu, but just about every linux distro available. I do appreciate that you are very frustrated with your situation, but your criticisms are not really justified, in my opinion.

---

### Post by rmhartman on 2009-06-30
Thank you everyone.

the "testdisk" utility did the job beautifully.

as far as "grub on mbr by default" I was installing 
on /dev/sdb ... there is no reason IMO it should have 
written *anything* to /dev/sda -- a completely 
different device.

---

### Post by ajgreeny on 2009-06-30
> as far as "grub on mbr by default" I was installing 
on /dev/sdb ... there is no reason IMO it should have 
written *anything* to /dev/sda -- a completely 
different device.As I said above, if ther system put grub onto /dev/sdb the destination device, you would have to change the bios boot device each boot, instead of just choosing from a grub menu.  Perhaps it needs to be re-written in some way to make that clearer, or if an external disk is the destination of the OS install, perhaps grub should then be written to that by default.  I do see your reasoning, but still think the MBR is best place for grub for 99% of installs.

Glad you're sorted, in any case.

---

### Post by Polaris96 on 2009-06-30
Thanks from me, also, everyone.  Sorry I gave you bad advcie, hartman, and hope you don't mind that I followed along.  Cheers!

---

