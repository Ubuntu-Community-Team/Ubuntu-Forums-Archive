---
title: "New SATA II HD 8.04 fresh install - no boot into Ubuntu"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by metalhead on 2009-03-08
I just installed a new Western Digital 80 GB SATA II hard drive and installed 8.04 and I can't get it to boot into Unbutu. I have Windows XP installed on two Western Digital 150 GB Raptors in RAID 0. I have one other Western Digital 160 GB SATA for just files. I had 8.04 installed on a 80 GB IDE hard drive, but it was starting to tick (soon to die) and wanted to replace it with a newer and faster hard drive. When I installed 8.04 I first tried installing it to fully install on the new 80 GB SATA II drive, and when I went into the boot menu after restarting it won't boot into Ubuntu. I even wnet back and reinstalled and installed the boot loader on the same drive as XP, but no go. I'm currently downloading 8.10 and will try a fresh install with it, but does anybody have any ideas on this one? My new SATA II drive is the third SATA MASTER in the BIOS. The two Raptors are on their own RAID controller on the motherboard. I really don't want to go back to a IDE hard drive. Thanks for any help!

---

### Post by Lord Landis on 2009-03-08
It sounds like a boot order issue in the BIOS.  What is the full drive order you have listed?  Are you still able to boot into XP?

---

### Post by Mark Phelps on 2009-03-08
How are you controlling the boot options? GRUB or Windows boot loader?

---

### Post by metalhead on 2009-03-09
I have tried moving the SATA II drive to the first HD to boot yesterday when I was troubleshooting, but that didn't work. I can boot into Windows XP just fine. I normally like to use the F8 option for the BOOT MENU so I can select which OS (hard drive for the installed OS) I want. I've had previous issues with loading GRUB on my Windows hard drive and it messed with MBR to the point of screwing it up. I finally got it fixed and was quite happy until I had to replace the hard drive the yesterday. I get no loader at all now to make a selection of which OS I want. When I had my old IDE HD installed I had GRUB installed on it (the IDE HD) so I would have to use the F8 option. When I installed a fresh install yesterday I selected for the loader to install on the new HD. I even tried installing GRUB to the Windows XP hard drive, but no go. Now when I try and boot into the new HD it goes thru the normal post list of drives and other hardware, and then stops. I then have to reset the computer so I can boot into Windows and here I am again. I'm going to burn a new ISO of 8.10 and try installing it and maybe I can get back to the way it used to be? :(

---

### Post by shadowfirebird on 2009-03-09
You should try looking in /var/log/messages, or in the output of dmesg.  

I had a similar problem and it turned out that 8.04 did not support my SATA controller card because of something called "LB48" (or was it ("LBA48") -- I had to go with 8.10 to get it all to work.  (Which is another, and much more bloody story...)

In case this is a bit new for you: dmesg shows what happened, in excruciating detail, last time you booted.  In a terminal, type:
```
dmesg |less
```
...and look for any mention of SATA or hard disks.

/var/log/messages holds a lot of more general warnings  and errors.  Type:
```
less /var/log/messages
```
...and again, skim the thing for mentions of SATA, hard disks, etc.

Good luck, hope that helps.

---

### Post by metalhead on 2009-03-09
I still have not yet been able to boot into UBuntu on any install I do so getting to the terminal isn't possible. I just now finished installing 8.10 and it still won't show the loader for me to choose an OS. I'm in Windows XP now and I'm going to try the F8 BOOT MENU and see if I can see the loader!

---

### Post by shadowfirebird on 2009-03-09
Hmm, good point, I was booting from a PATA drive at the time.  

There must be a way to see those messages at boot time.  I have a feeling that F12(?) used to show them and doesn't now -- but maybe that's my imagination.

Still, if you have an old PATA drive lying around and the worst comes to the worst, I guess that's something.   Or you could see if the problem goes away in 8.10, I guess.

Sorry.

---

### Post by metalhead on 2009-03-09
Well, here I am again with no success. I could try re-installing again and install the GRUB to the Windows XP HD and see if 8.10 will boot. Or I could just hook up a external hard drive with a IDE hard drive in it and see if it works. There's got to be an easier way to get this installed or isn't 8.10 compatible with a SATA drive? IDE drives are not as plentiful as SATA drives and not as fast. I really hate going backwards. I've read disconnecting the Windows HD and installing Ubuntu works, but I shouldn't have to do that. It sounds like a last option.

---

### Post by metalhead on 2009-03-09
Yeah! I finally got it right. I got 8.10 to work on my SATA drive and here's how: when installing choose the MANUAL method. Then CREATE a new primary partition  of at least 3 GB and make it the SWAP PARTITION and make it the FIRST partition. Next CREATE a second PRIMARY PARTITION of the rest of the hard drive of the EXT 3. Before clicking on Forward, click on Edit and mount the EXT 3 with the / option. Next click on Forward and click on Advanced and install the loader to the EXT 3 partition by clicking on it - it will be the partition under SWAP. I then installed Ubuntu and used the F8 option on restart and selected my 80 GB SATA hard drive and grub popped up and showed Ubuntu and Windows XP. This is much better and faster than my PATA (IDE) drive. I hope this helps anyone else who's in the same situation of having multiple drives in one tower.:D

---

