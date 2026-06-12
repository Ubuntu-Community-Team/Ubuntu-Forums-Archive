---
title: "Dell Mediadirect button on 6400"
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by incubusnb on 2007-04-19
Hey, I have a Dell 6400 laptop, i've been dual booting XP/Ubuntu for the past few months, i've been trying to figure out how to launch ubuntu when i use the mediadirect button bet have been unsucessfull

basically, i want to eliminate the boot choices from the boot loader and make it so the power button loads XP, while the mediadirect button loads Ubuntu or vice versa, this will probably require some hooks from the MBR, but i'm not sure how to make it work.  any advice would be appreciated

---

### Post by incubusnb on 2007-04-19
Sorry, I hate bumping posts, but i was kinda hoping to get an answer either way on this

---

### Post by incubusnb on 2007-04-19
sorry again, this will be the last time i bump this, if I can't get a reply to this, i'll look somewhere else for an answer

---

### Post by revilodraw on 2007-05-17
great idea... no idea how to do it though... but i bet someone does!! come on people!

---

### Post by Prometheus.172214 on 2007-05-17
The Media Direct button is a non mappable option that is designed to send a singal only to the onboard hidden media direct partition. If you try setting it, you would need to sit with Linux and change the bootloader settings manually to use the button, which is a complicate process. Remember, O.S.s are designed to recognize only the power button for bootloader options and features such as hibernate etc. So, I am nearly sure that the assignment cannot be done, because the BIOS might not permit the assignment of this button for a bootloader. Best of luck on your quest !

---

### Post by thayerw on 2007-05-17
I must say I've never heard of anyone doing this either.

However, on the upside you can use the Media Direct button to launch your media player once you've got linux up and running.  Previously I had to do this manually, but I think that with Feisty (K)ubuntu is is mapped automatically to the default media player (Amarok, etc). Good luck!

---

### Post by lucads on 2007-05-21
> **thayerw said:**
> I must say I've never heard of anyone doing this either.

On the italian hwupgrade forum there is a very good thread dedicated to Inspiron 6400 where it is explained in detail the procedure to install a different operating system into MediaDirect partition and have it booting via the MediaDirect key, the procedure is explained here at point III :

[http://www.hwupgrade.it/forum/showpost.php?p=13586185&postcount=3392](http://www.hwupgrade.it/forum/showpost.php?p=13586185&postcount=3392)

Unfortunately the post is in italian language, I hope an online translator makes a good work on it since the procedure is not "for dummies".

Regards.

---

### Post by MEW on 2007-07-31
I have been successful (as of today) at using my MediaDirect button for something similar. (I have an E1505, which is basically the same as the 6400).

First off, an explanation of what the button does (as far as I can tell) - when you turn on the machine (with either the power or MediaDirect buttons), the BIOS checks which button was pressed. If the power button was pressed, it shows the Dell POST screen; if it was the MD button, it shows the MD logo while POSTing. Then the BIOS loads the MBR.

Dell has a special MBR bootloader that will boot from one partition if the power button was pressed, and another if the MD button was pressed. You probably overwrote this bootloader with grub.

On the MediaDirect reinstallation CD provided by dell, there is a program called rmbr.exe. This program reinstalls their special MBR, and lets you specify which partitions to boot from. The trick is that the Dell MBR can only boot from a primary partition. 

Before you start mucking around with the bootloader, make sure you have a grub boot-floppy or something like that (I use my portable hard disk). It comes in really handy.

If grub is currently installed on a primary partition, then you're in business. If not, you have to somehow get it installed on one. You can install it in the boot sector of your extended partition if you don't have any primary partitions left. Boot from your grub boot-disk (or use the grub shell in Ubuntu), and:

```

grub> root (hd0,5)         # Use your Ubuntu partition number here (remember: Grub numbers from zero)
grub> setup (hd0,3)        # Use your extended partition number here

```
To emphasize: I mean installing in the *extended* partition, not a *logical* partition. The extended partition is the one that contains all the logical ones. It seems that extended partitions have boot sectors, but they're just almost never used.

Now use your grub boot disk to check that the installation worked:
```
grub> root (hd1,3)        # The disk number has changed, because (hd0) is whatever disk the system booted from
grub> chainloader +1
grub> boot

```
And you should see your grub menu. If you do, continue:

Boot into Windows. Start the Command Prompt, and:
```

C:\Documents and Settings\MEW> X:   # Your CD-ROM drive letter
X:\> cd DellKit
X:\DellKit\> rmbr /?
      Read its description of what it does, and then
X:\DellKit\> rmbr DELL 4 1       # 

```
Replace '4' with the number of the partition you want the Power button to boot                                  (in my case, it boots grub from the extended partition), and replace '1' with the partition you want to boot if the MD button is pressed (in my case, a minimalized Linux install, from partition 1). Although the rmbr program calls the MD-button partition the "Windows embedded partition", it can boot any OS from it.



Then shut down your computer and try it!

If it doesn't work, you can boot your system from the grub boot disk as in the second code listing.

EDIT: I hope my explanation makes sense. I'm not very good at explaining things.

EDIT2: This worked for me with Dell MediaDirect version 3, which does not use the Host-Protected Area on the hard disk. I don't know if it works with other versions, and I don't have any way of finding out. Please let me know whether it works for you.

---

### Post by TrinitronX on 2007-12-02
I have a Dell XPS m1710 laptop  on which I've been attempting to get a configuration like this to work for a while now, and I've gotten Ubuntu installed and bootable from within the extended partition.
I can boot Super Grub Disk, press c for command line and manually enter:
```
root (hd0,3)
chainloader +1
boot
```... And it will boot ubuntu fine.  Pressing the power button boots into Vista fine.

Here is my partition table as reported by fdisk (both normal and advanced display:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda3   *           1       13020   104583118+   7  HPFS/NTFS
/dev/sda4           13021       14593    12635122+   f  W95 Ext'd (LBA)
/dev/sda5           13021       13151     1052226   82  Linux swap / Solaris
/dev/sda6           13152       14593    11582833+  83  Linux

Nr AF  Hd Sec  Cyl  Hd Sec  Cyl     Start      Size ID
 1 00   0   0    0   0   0    0          0          0 00  #removed DellUtility
 2 00   0   0    0   0   0    0          0          0 00  # removed Dell Restore
 3 80   1   1    0 254  63 1023         63  209166237 07  # Vista (hd0,2)
 4 00 254  63 1023 254  63 1023  209166300   25270245 0f  # Extended Part. (hd0,3)
 5 00 254  63 1023 254  63 1023         63    2104452 82  # Swap (hd0,4)
 6 00 254  63 1023 254  63 1023         63   23165667 83  # Ubuntu (hd0,5)
```As you can see, /dev/sda3 is the Vista partition, and /dev/sda6 is my root linux partition, WITHIN the Extended partition (/dev/sda4... type 0f is correct).

I want the power button to boot vista, and the media direct button to boot Ubuntu.  So after booting vista, I run:
```
E:\DellKit\rmbr DELL 3 4
```I press the Media Direct button to test it, and it shows the splash screen during POST, however, it fails to get into grub.
I see an error at the top of the screen:
"MD extended partition table erro"
(Note: the last r isn't shown on screen... it got cut off for some reason)
Vista boots fine with power button.


Next I tried to switch the functions (and ended up wishing I didn't): Power button for Ubuntu, MD button for Vista
```
E:\DellKit\rmbr DELL 4 3
```I press the power button and get a blank screen with blinking cursor.... no grub
I press the MD button and get the same error.  System is completely unbootable, even when using Super Grub Disk, I couldn't boot vista any possible way (even in safe mode).. it would tell me "autochk program not found -- Skipping AUTOCHECK", and then flash a very quick blue screen error before rebooting.  Ubuntu was still bootable of course.
I booted the Vista install CD to try and repair the problem... each time it failed.

Finally I ended up figuring out that somehow the MD button must've borked up my windows partition, and I had to boot Super Grub Disk and use this command:
```
unhide (hd0,2)
```Then vista could boot again!

I'm definitely not going to mess with having vista boot from the MD button now, that was too much of a pain to fix.

I think I may have figured out why the previous setup wasn't working though... I see an error when trying to install GRUB into the Extended partition.
```
root (hd0,5)
setup (hd0,3)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0,3)"... [COLOR=red]failed[/COLOR] (this is not fatal)
Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... [COLOR=red]failed[/COLOR] (this is not fatal)
Running "install /boot/grub/stage1 (hd0,3) /boot/grub/stage2 p /boot/grub/menu.lst"... succeeded
Done.
```Why won't it install e2fs_stage1_5 to the Extended partition?
It also seems to fail installing it to the Ubuntu partition too.  Is this normal?
Any help will be appreciated.

EDIT:
So it seems that in the case of setting the MD button to boot vista resulted in whatever code Dell put into the BIOS or MBR checking what it thought was the "Media Direct" partition (now set to Vista's partition type 0x07 NTFS), and if the partition type was 0x07, then it changed it EVERY boot to 0xD7.  This type is how Dell hides the Media Direct partition normally, and vista couldn't boot since it couldn't find the filesystem on that partition, hence the "cannot find autochk" errors.  Luckily, after the "unhide (hd0,2)" grub command, it changed the type to 0xC7 (syrix or something??).. and also luckily vista could boot in that case even though the type in the partition table was wrong.

Since 0xC7 != 0x07, it wasn't changed subsequently back to 0xD7, and would work for every boot.  However, when I changed it back to 0x07 with fdisk, again the BIOS changed it back to 0xD7.  After again running rmbr.exe with the first parameters, setting the MD button to linux, and the power button to vista, no partition table changes were observed.  I also tested running "rmbr.exe DELL 3 6", in an attempt to have the MD button run grub from the main Ubuntu root partition, but it did not work.  The good news is that it doesn't change the partition table for a type of 0x83 either, it only appears to be looking for 0x07.

---

