---
title: "Booting help!"
date: 2008-09-16
forum: General Help
---

### Post by vijay_wai on 2008-09-16
Dear All,

I revisited Ubuntu again after good 3 years and my oh my, its probably the sweetest ever OS I used!

I have a few quesries though,

I share my laptop with my wife and she is a Windows Visa user...
I prefer Ubuntu...

I did mess a bit with GFX GRUB and its pretty cool... but I need an easy option...

Can I configure GRUB to sit on a USB stick at all?
My laptop is capable of booting off a USB device.... so if the USB key is plugged in, then the laptop will boot into Ubuntu by default....if its not, then it will boot into Vista....

Is this possible??

Some one please help...

---

### Post by Pro-reason on 2008-09-16
Yes, I suppose so.

In the terminal:

```

sudo grub
root (hd0,0)
setup (hd3)
exit

```

Where I have put “0,0”, put the correct identifier for the partition that holds your GRUB files.  Where I have put “3”, put the correct identifier for your USB drive.

You will have to understand a bit about how GRUB refers to drives to know what numbers to put.

Make sure that your /boot/grub/menu.lst points to the right locations.  If you get it wrong, you will be able to type in the correct data at boot time (if you have the know-how).

Then, make sure that your BIOS is set up to boot from USB first, if present.

Then, use your Windows installation CD to restore the Windows bootloader (thus removing GRUB from the MBR of your hard drive).

DISCLAIMER: if you're a newbie, you'll probably mess some part of that up, and end up coming back here to complain!

---

### Post by vijay_wai on 2008-09-16
Thanks a lot for a quick reply... and yups I suppose I undertsand the way grub refers to disks...

Couple more questions...

When I did install GFX Grub, I notice that my memory stick pro drive was listed when I typed fdisk -l .... its a 4mb stick that I have ... can I configure this as well for grub?? Would that be enough space??... of course I will have to check if my BIOS supports this device as a boot device...

And, any way I can restore MBR without using VISA setup CD ...all I have is 3 system restore disks and they pretty much reinstall everything instead of just restoring the MBR...

What happens if I just uninstall grub from within Ubuntu?? Does it not restore my previous MBR?

---

### Post by Pro-reason on 2008-09-16
I don't know anything about GFX.

I don't know how your system restore disks work.  It may or may not be possible to restore the MBR with them.

If you uninstall GRUB in Synaptic, it will just remove the /boot/grub directory and the command-line tools.  It won't do anything to the MBR.  It's very easy to remove GRUB from the MBR (with something like &#8220;dd if=/dev/zero of=/dev/hda bs=512 count=1&#8221;), but there is not much point, because the only reason for getting rid of one bootloader is to replace it with another.

If you'd made a backup of the MBR before installing GRUB and Ubuntu, then you could restore it now.

---

### Post by caljohnsmith on 2008-09-16
> **Pro-reason said:**
> with something like &#8220;dd if=/dev/zero of=/dev/hda bs=[COLOR="Red"]512[/COLOR] count=1&#8221;
As you've written that command, it will erase the *entire* MBR, which contains both the boot loader [COLOR="Red"]and the HDD's partition table[/COLOR]. His HDD will be unusable until he tries to recover the partition table with something like testdisk. Under normal circumstances, there is no good reason to "delete" the boot loader in the MBR, because then the HDD is of course un-bootable; usually you should simply overwrite the MBR boot loader with another one, which is what vijay_wai wants. I know you had no malicious intention, but please be more careful when giving commands like that. :)

Vijay_wai, to overwrite Grub with a Windows MBR that will boot Vista, you can do it from within Ubuntu. Can you still boot into Ubuntu? Also, uninstalling Ubuntu does no uninstall Grub from the MBR unfortunately.

---

### Post by phidia on 2008-09-16
To reset the mbr you use the rescue mode of your windows install disk and issue "fixmbr". The format of that command changes with different versions of windows but that is the generic command. See this small [guide]("http://pcsupport.about.com/od/termsf/p/fixmbr.htm").

---

### Post by vijay_wai on 2008-09-16
> **caljohnsmith said:**
> 
Vijay_wai, to overwrite Grub with a Windows MBR that will boot Vista, you can do it from within Ubuntu. Can you still boot into Ubuntu? Also, uninstalling Ubuntu does no uninstall Grub from the MBR unfortunately.

Hi yes, I can boot both ... and I intend to use both Ubuntu and vista ...its just that I want to load vista as a default OS when laptop is started (no menu displayed)....load Ubuntu as a default when a USB key is plugged... I intend to put grub on the USB drive

Can you please help??

---

### Post by tangibleorange on 2008-09-16
> **vijay_wai said:**
> Hi yes, I can boot both ... and I intend to use both Ubuntu and vista ...its just that I want to load vista as a default OS when laptop is started (no menu displayed)....load Ubuntu as a default when a USB key is plugged... I intend to put grub on the USB drive

Can you please help??

ok you just want GRUB on the memory stick? boot into a live CD and then issue this command:

```
sudo fdisk -l
```

so then we can tell you how to set it up. the problem is that commands issued above are risky because of the possibility that you accidentally install GRUB to the wrong place. Issue that command and then post the output.

---

### Post by caljohnsmith on 2008-09-16
> **vijay_wai said:**
> Hi yes, I can boot both ... and I intend to use both Ubuntu and vista ...its just that I want to load vista as a default OS when laptop is started (no menu displayed)....load Ubuntu as a default when a USB key is plugged... I intend to put grub on the USB drive

Can you please help??
So just to clarify, you want to put Ubuntu plus Grub on your USB stick, right? Also, once you post the output of the fdisk command like tangibleorange recommended, I can give you directions for reinstalling a Windows MBR to your Vista drive to get that booting again.

---

### Post by vijay_wai on 2008-09-16
caljohnsmith, I only want grub on the USB but linux is still on the hdd of laptop...

---

### Post by caljohnsmith on 2008-09-16
> **vijay_wai said:**
> caljohnsmith, I only want grub on the USB but linux is still on the hdd of laptop...
OK, that can be done. Just create a really small ~10 MB partition at the beginning of the USB stick, and then format it to either ext2 or ext3. Also, like I mentioned earlier, please post the output of:
```
sudo fdisk -lu

```

---

### Post by Pro-reason on 2008-09-16
> **caljohnsmith said:**
> As you've written that command, it will erase the *entire* MBR, which contains both the boot loader [COLOR="Red"]and the HDD's partition table[/COLOR].

Informative point.  Although I *was* telling him *not* to use such a command.

> **caljohnsmith said:**
> OK, that can be done. Just create a really small ~10 MB partition at the beginning of the USB stick, and then format it to either ext2 or ext3. Also, like I mentioned earlier, please post the output of:
```
sudo fdisk -lu

```

Hang on.  Why would he want to do that?  GRUB is too things: a bootloader and a whole load of files.  The files are already on his Ubuntu partition, and the bootloader is trivial to install to the MBR of the USB drive.  Why would he create a new partition on the USB drive?  It's a waste of space.

---

### Post by tangibleorange on 2008-09-17
you can put the ROOT of GRUB (the files) onto the Ubuntu partition, but have GRUB itself on the MBR of the memory stick. i think this is what **Pro-reason** was referring to, and what would be the best option for the OP.

---

### Post by caljohnsmith on 2008-09-17
> **Pro-reason said:**
> 
Hang on.  Why would he want to do that?  GRUB is too things: a bootloader and a whole load of files.  The files are already on his Ubuntu partition, and the bootloader is trivial to install to the MBR of the USB drive.  Why would he create a new partition on the USB drive?  It's a waste of space.
You're right, my mistake, he doesn't have to put his Grub files on the USB drive if he doesn't want to. If he is only going to use his USB drive to boot the Ubuntu on his HDD and nothing else, there's no reason to have his Grub files independent of his HDD like I was originally thinking. So I agree, probably the best solution would be to install Grub to the MBR of his USB drive and have it point to his Ubuntu partition on his HDD for all the Grub system files.

---

### Post by tangibleorange on 2008-09-17
> **caljohnsmith said:**
> You're right, my mistake, he doesn't have to put his Grub files on the USB drive if he doesn't want to. If he is only going to use his USB drive to boot the Ubuntu on his HDD and nothing else, there's no reason to have his Grub files independent of his HDD like I was originally thinking. So I agree, probably the best solution would be to install Grub to the MBR of his USB drive and have it point to his Ubuntu partition on his HDD for all the Grub system files.

yep. in which case we need the output of:

```
sudo fdisk -l
```

so we know how to write your /boot/grub/menu.lst file :)

---

### Post by vijay_wai on 2008-09-19
Hi Guys,

Thanks a lot for all your advice.

Sorry for the delayed post ... my USB stick arrived today and I shall post the fdisk -l output soon...

Here is what I want to do:

1) I want both Ubuntu and Visa installed on my HDD on native partitions (No linux on USB)

2) Configure BIOS to boot from USB flash (I know how to do this in BIOS....)

3)Make grub and all sit into the USB stik, so if USB is plugged into laptop while booting, it loads Ubuntu straight away.... (as I have set booting preference in BIOS to seek USB flash MBR first and then the native HDD)

4) If no usb is plugged then it loads VISA straight away ... as this boots from the HDD MBR

Few things to note:

I have GFXgrub installed already on my HDD MBR and will have to remove it so only VISA boot loader sits on my HDD MBR

I hope this helps the experts here ...

Thanks again for your time all ... its great to be in the Ubuntu community...

---

### Post by tangibleorange on 2008-09-19
> **vijay_wai said:**
> Hi Guys,

Thanks a lot for all your advice.

Sorry for the delayed post ... my USB stick arrived today and I shall post the fdisk -l output soon...

Here is what I want to do:

1) I want both Ubuntu and Visa installed on my HDD on native partitions (No linux on USB)

2) Configure BIOS to boot from USB flash (I know how to do this in BIOS....)

3)Make grub and all sit into the USB stik, so if USB is plugged into laptop while booting, it loads Ubuntu straight away.... (as I have set booting preference in BIOS to seek USB flash MBR first and then the native HDD)

4) If no usb is plugged then it loads VISA straight away ... as this boots from the HDD MBR

Few things to note:

I have GFXgrub installed already on my HDD MBR and will have to remove it so only VISA boot loader sits on my HDD MBR

I hope this helps the experts here ...

Thanks again for your time all ... its great to be in the Ubuntu community...

yeah that's what i assumed. we will put the GRUB files on the HDD, but not the actual GRUB boot loader. when you plug in the stick, the GRUB on the stick knows to look into the ubuntu partition and the files there tell it how to boot.

both parts will be needed in order to boot ubuntu. the stick and the HDD files. the MBR of your HDD will be unaffected.

---

### Post by Pro-reason on 2008-09-19
The poster has been asked for the output of fdisk three times now.

I only help people who can be helped.  I'm removing this thread from my watchlist.

---

### Post by vijay_wai on 2008-09-19
Guys, I don't have internet at home ... so, please be pateint!
I shall get the screenshot, copy it ro USB and will post it over week end....

sorry for this delay!

---

### Post by vijay_wai on 2008-09-20
fdisk -l output as below....

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf95e41c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1314    10553344   27  Unknown
/dev/sda2   *        1314        7842    52428800    7  HPFS/NTFS
/dev/sda3            7842       24321   132374241    f  W95 Ext'd (LBA)
/dev/sda5            7842       23710   127462891    7  HPFS/NTFS
/dev/sda6           23711       24287     4634721   83  Linux
/dev/sda7           24288       24321      273073+  82  Linux swap / Solaris

Disk /dev/sdc: 4143 MB, 4143972352 bytes
249 heads, 32 sectors/track, 1015 cylinders
Units = cylinders of 7968 * 512 = 4079616 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1016     4046832    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(249, 248, 32) logical=(1015, 192, 32)

Disk /dev/mmcblk0: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         984     1983619+   6  FAT16

---

### Post by caljohnsmith on 2008-09-20
What is that 2 GB "Disk /dev/mmcblk0" drive? Is your USB stick the 4 GB /dev/sdc drive? If you can only have your USB stick connected, and no other drives connected other than your internal HDD, that would be ideal. Once you let us know that I can give you specific instructions for making sure Grub gets installed to your USB drive MBR and points to the correct Linux partition on your internal HDD.

---

### Post by vijay_wai on 2008-09-22
Hi,
Thx for reply.
4 GB /dev/sdc drive is my USB.

---

### Post by caljohnsmith on 2008-09-22
OK, while you are in Ubuntu, do:
```
sudo grub
grub> device (hd0) /dev/sdc
grub> device (hd1) /dev/sda
grub> root (hd1,5)
grub> setup (hd0)
grub> quit
```
That should work assuming that your sda drive is 2nd in the boot order when you boot from your USB stick. But that other strange drive you have /dev/mmcblk0 could complicate things, making sda actually 3rd in the boot order; we can't know for sure. In that case we will have to change the above steps. Try the above first, and let me know exactly what happens when you boot from your USB stick. We can go from there. :)

---

### Post by vijay_wai on 2008-09-22
will I be able to use my USB key as a memory storage device on otner windows machine? ... ie. at work?

---

### Post by caljohnsmith on 2008-09-22
> **vijay_wai said:**
> will I be able to use my USB key as a memory storage device on otner windows machine? ... ie. at work?
Yes, as long as you are just using it as a data drive, not a boot drive. In other words, if you try to boot from your USB stick from another computer, you will get a Grub error, but if you just want to access files on it, you should be fine. :)

---

### Post by vijay_wai on 2008-09-22
Thanks a tonne!

Shall try that tonight at home and will let you know if tit worked!!

That other 2gb device is my SD memory card I think... and I am not able to boot from it as its not there in bios....

---

### Post by vijay_wai on 2008-09-24
:(

Sorry guys, this did not work!

It comes with message like no such device.... 

any ideas?

---

### Post by caljohnsmith on 2008-09-24
Have you first confirmed that you can boot off a USB device with that computer? It doesn't sound like BIOS can even boot your USB stick, or you should have at least gotten a Grub error I think. Did you get any errors running those commands I gave previously? 

Also, the following command will create a really small file on your desktop called "sdc_MBR.gz": 
```

sudo dd if=/dev/sdc bs=512 count=17 | gzip -c > ~/Desktop/sdc_MBR.gz

```
Please attach that sdc_MBR.gz file in your next post so I can look at it.

---

### Post by vijay_wai on 2008-09-24
Hi for sure I can boot off the USB...

I did get the usual 'disk error, replace and reboot' message before I did the gurb install on USB....

Infact, I did get the grub menu when I booted off the USB and when I selected the option, it gave me error....

---

### Post by caljohnsmith on 2008-09-24
> **vijay_wai said:**
> 
Infact, I did get the grub menu when I booted off the USB and when I selected the option, it gave me error....
OK, it would have been helpful if you had mentioned this before. :) It sounds like you just need to modify your Grub's menu.lst so that you can boot Ubuntu at this point. 

So first reboot to your USB drive, and when you get the Grub menu, select Ubuntu, hit "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd1,Y)" or in other words just change the first number, press return to save the change, then press "b" to boot. If that doesn't work, then repeat the process, but change the "root (hdX,Y)" to "root (hd2,Y)" and try and boot it. One of those two cases should work. 

When you figure out which works, once you get into Ubuntu, do:
```
gksudo gedit /boot/grub/menu.lst
```
And where the line says:
```
#groot=(hdX,Y)
```
Change the (hdX,Y) to be whatever worked to boot Ubuntu. Save and close the file, then do:
```
sudo update-grub
```
That should be all you need to do. Let me know how it goes.

---

### Post by vijay_wai on 2008-09-25
Hi,

It seems working!! :D

I managed to boot into Vista from the USB ... still to figure out what works for Ubuntu...

One thing though, my grub outputs text message after I select the option (like all the entries from menu.lst) ...can I disable this?...so I have a smooth transition from graphical boot menu to Ubuntu or Vista...

---

### Post by vijay_wai on 2008-09-26
Thanks experts!!

Its indeed working for me!!
I have removed grub (restored vista MBR) and the Grub now lives in my USB...

Next question though, how do I diable boot menu and make grub load Ubuntu by default??

Also, I installed GFX Grub and it still echoes all the manu.lst commands once I select the option...any way there to disable that ... so get a smooth transition from GFX Grub menu to grapgical 'Ubuntu Loading....' screen?

---

### Post by TeXtonyx on 2008-09-26
There is a timer which waits 10 seconds or so before booting the grub default.
If you set the timer to zero, 0, then it boots the default very quickly.

---

### Post by vijay_wai on 2008-09-26
> **vijay_wai said:**
> Also, I installed GFX Grub and it still echoes all the manu.lst commands once I select the option...any way there to disable that ... so get a smooth transition from GFX Grub menu to grapgical 'Ubuntu Loading....' screen?

Is it possible to get rid of the command echos is GFX Grub though?

---

### Post by caljohnsmith on 2008-09-26
I think the GFX Grub splash screen can be disabled by simply removing a line in your menu.lst that refers to it. If you can post your menu.lst, we can see:
```
cat /boot/grub/menu.lst
```

---

### Post by vijay_wai on 2008-09-26
I like the slash screen and graphics ... its just the in between text messages annoy me .... thats the reason I wanted to boot into linux directly without any menu as such....

Isn't there a way just to disable the echoes?

Can we modify the source to disable the echoes at all?

---

