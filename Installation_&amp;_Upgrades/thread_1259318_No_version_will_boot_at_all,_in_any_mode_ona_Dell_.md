---
title: "No version will boot at all, in any mode ona Dell Optiplex 320"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by aj_the_first on 2009-09-06
Okay, I have been working on this for about a week, and then I remembered ubuntu forums can help.
 
I am trying to convert a Dell Optiplex 320 (desktop small tower) into a file server for my wife and me. Here is how it went:
 
Installed a spare 320GB HDD I had sitting around, installed Ubuntu Server 9.04 64 bit, no errors came up, booted, and it went through the grub countdown, then went to a black screen with a blinking white cursor in the upper left corner... and that was it.
I installed it a few different times with a few different options, but everytime the boot went the same way: black screen with blinking cursor in the upper left.
 
So I decided that there may be some issues with 9.04 on that mirror. I downloaded from a different mirror, same results.
So I decided that the machine may not be able to run 9.04 for some reason, and I tried Hardy server edition 8.04.3. Same results with the black screen after grub countdown. Tried different install options, tried a different mirror, so I began to get a bit irritated and figured there may be an issue with this machine being able to run server edition for some reason...
So I tried 9.04 desktop. (64 bit) It would run in live mode from the CD with no problems, but after install the same thing happened: black screen, blinking cursor in the upper left.
So I tried 8.04, same results; so I tried the 32 bit versions of 9.04 and 8.04: all the same results.
At this point it was bordering on absurdity, so I swapped back to the original HDD with WinXP installed to see if it was a SATA controller issue. Nope, windows booted right up.
I decided that it must be a problem with my spare hard drive, and I decided to wipe my WinXP install from the hard drive and try it all over again.
Let's just say I tried all the above steps all over again with exactly the same results, only difference is that I did it on my known-good HDD. Tried differet versions, different options, different mirrors, ect, all stop after th grub countdown on this black screen with the blinking cursor in the upper left.
In order to appease my mind about the SATA controller on the computer being okay, I re-installed WinXP. No problems, it booted right up.
So, I reinstalled 9.04 32 bit, and tried to go to any of the grub menu options of generic kernel, generic kernel recovery mode, and even memory test. all resulted in the exact same black screen with blinking white cursor.
Is this the Linux version of the BSOD in windows?  I can't even get into recovery mode to see what may be going wrong.
 
Here are some more details: all installs were done from an .iso image on a CD that was thrice data checked, during burn, after burn, and pre-install, (I even used the disc to install ubuntu on a spare computer just to make sure I didn't have a problem with my other disc burner)
I did the hour long memory test on the machine, with 0 errors reported.
 
I just... I just guess the Dell Optiplex 320 can't run Linux? What could possibly be happening?
AJ

---

### Post by Bartender on 2009-09-06
I've never installed Server Edition, but my understanding from skimming lots of posts is you're SUPPOSED to get a black screen with cursor blinking.

It sounds like you don't mind getting downloads.  How about downloading/burning to CD the alternate install version of plain old Ubuntu and see what happens?  I suggest alternate install because I don't know how much RAM you've got.  The LiveCD gets quirky and very slow at 256 or less RAM.

---

### Post by squenson on 2009-09-06
I am not an Ubuntu expert but a fresh eye may sometimes be helpful:

1. Could it be a faulty disk? From all your tests, I cannot see whether you tried with WinXP on the new drive.

2. Have you tried the LiveCD mode? just to see whether Ubuntu can run on your machine.

3. Is your new drive properly partitioned and formatted? I assume so, as you describe that the installation process goes well because you can reboot and see the grub menu.

---

### Post by aj_the_first on 2009-09-06
Yeah, I tried the regular Ubuntu desktop versions and XP on both hard drives.  XP had no issues, but Ubuntu regular desktop did the exact same non-boot to a black screen.
I also tried Ubuntu from the Live CD with no issues, but after the install it was just black with the cursor.  I have 1GB of RAM, so I can't see there being a problem.
Most of my tests were conducted with regular desktop Ubuntu, only the first two were server, and after they both failed, I wanted to see if regular desktop ubuntu would run.... it won't, in any of the circumstances.
 
I should note that nothing happens after the cursor.  you can not type, you can not execute any commands or quick keys or escape to anything, it is just dead.
 
Still can't figure it out.

---

### Post by wojox on 2009-09-06
Hey aj,

I run a Dell Optiplex GX 150 which I converted to a server. I started with 8.10 Server 32 bit. I've upgraded to 9.04 no problem. It had recently had Windows XP on it. 

Now before I install a new OS I run a program called KillDisk which is just a hdd scrubber. It's free to download, just google it. It always seems to do a good job of getting rid of old mbr and grub.

You may also want to try adding acpi=off:

```
boot: /boot/vmlinuz-2.6.15-26-k7 root=/dev/hda1 ro quiet splash acpi=off 
```

---

### Post by cs_at_colorado on 2009-09-06
> **aj_the_first said:**
> Yeah, I tried the regular Ubuntu desktop versions and XP on both hard drives.  XP had no issues, but Ubuntu regular desktop did the exact same non-boot to a black screen.
I also tried Ubuntu from the Live CD with no issues, but after the install it was just black with the cursor.  I have 1GB of RAM, so I can't see there being a problem.
Most of my tests were conducted with regular desktop Ubuntu, only the first two were server, and after they both failed, I wanted to see if regular desktop ubuntu would run.... it won't, in any of the circumstances.
 
I should note that nothing happens after the cursor.  you can not type, you can not execute any commands or quick keys or escape to anything, it is just dead.
 
Still can't figure it out.

Hi - I have an Optiplex 320 and have had similar problems with various version of ubuntu, and have also attempted Mint and Mandriva and had no luck, there is lots of talk about the LINUX loaders and the OPTIPLEX series on this board as it appears there is a serious conflict somewhere in software with the DELL hardware in the OPTIPLEX series (I installed 9.04 on a Dimension 4700 no problems what-so-ever recently)

Anyways, there are some tricks people have pointed out as far as managing to get a working version of LIVE and (I would assume, installed) Ubuntu: check out this post:

[http://ubuntuforums.org/showthread.php?t=992172&highlight=optiplex+320](http://ubuntuforums.org/showthread.php?t=992172&highlight=optiplex+320)

Let me know about your results! I haven't experimented with my 320 in a while but I really wanted Linux but it had more problems running 4GB of ram with a PCI-e card -- so don't get me started... I'm running seven...gag

---

### Post by Bartender on 2009-09-06
You using USB keyboard and mouse?  This is probably not gonna help any, but I'd at least try PS/2 input devices.

---

### Post by aj_the_first on 2009-09-07
> **wojox said:**
> Hey aj,
 
I run a Dell Optiplex GX 150 which I converted to a server. I started with 8.10 Server 32 bit. I've upgraded to 9.04 no problem. It had recently had Windows XP on it. 
 
Now before I install a new OS I run a program called KillDisk which is just a hdd scrubber. It's free to download, just google it. It always seems to do a good job of getting rid of old mbr and grub.
 
You may also want to try adding acpi=off:
 
```
boot: /boot/vmlinuz-2.6.15-26-k7 root=/dev/hda1 ro quiet splash acpi=off 
```
 
 
Okay, I installed 9.04 desktop on my HDD, and then with the liveCD .iso disc in the machine, I selceted the "boot from HHD" option, but changed the boot options to the line of code above, and for the first time it booted the OS from the hard drive...  however, as soon as I restart, it goes back to the black screen.  The only way I can get it to boot right now is through the install CD "boot from HDD" option with the boot exceptions typed in to the boot options.  How do I make acpi=off a permanent part of the boot process?
 
I tried all the options in cs_at_colorado's thread link in the boot install options, but none of them worked.

---

### Post by cs_at_colorado on 2009-09-07
> **aj_the_first said:**
> 
 
I tried all the options in cs_at_colorado's thread link in the boot install options, but none of them worked.

Bummer -- Ill give them a shot myself and see what I get...

---

### Post by aj_the_first on 2009-09-09
> **aj_the_first said:**
> Okay, I installed 9.04 desktop on my HDD, and then with the liveCD .iso disc in the machine, I selceted the "boot from HHD" option, but changed the boot options to the line of code above, and for the first time it booted the OS from the hard drive... however, as soon as I restart, it goes back to the black screen. The only way I can get it to boot right now is through the install CD "boot from HDD" option with the boot exceptions typed in to the boot options. How do I make acpi=off a permanent part of the boot process?
 
I tried all the options in cs_at_colorado's thread link in the boot install options, but none of them worked.
 
 
Does anyone know how to keep the "acpi=off" boot options permanent?

---

