---
title: "Upgrade &amp; GRUB problems....."
date: 2008-10-04
forum: General Help
---

### Post by seymour71 on 2008-10-04
Hope someone can help me with this one.

I’ve just upgraded my system to a Q6600 + MSI P43 mobo & 4gb ram. I have 4 hard drives 1 with xp on, 1 with Vista, 1 with Ubuntu, and 1 for storing music etc. I connected the XP one through and IDE, and the Vista and Ubuntu one through SATA.

Thing is the Mobo doesn’t detect the Ubuntu drive. It is an ancient 20gb IDE drive that I’ve stuck a converter thingy on to make it a SATA one – this was working fine before I upgraded. I presume that this has the GRUB loader thingy on, because all I get is error 21. I do have a live Ubuntu cd, so I could re-install it on the Vista hard drive, as I’m guessing the Ubuntu drive may be knackered?

Unless I could change the GRUB thingy from within the live cd?

Any ideas guys? I’m itching to start playing with my new toys!

---

### Post by fsmithred on 2008-10-05
The device names for your hard drives are probably different in the new computer. If you're getting to a grub menu, you can type "e" to edit the kernel line or "c" to use grub commands, fix whatever is wrong, and you should be able to get it to boot. Then you can edit /boot/grub/menu.lst to make the changes permanent.

This should help - [http://users.bigpond.net.au/hermanzone/p15.htm#cli](http://users.bigpond.net.au/hermanzone/p15.htm#cli)

---

### Post by seymour71 on 2008-10-05
Thanks for that mate, but I fear I've made things worse now!

I now have 4 hard drives connected 2 via ide & 2 via Sata.

On the master Ide I Have installed Ubuntu, but I also need to be able to boot into xp, which is on the slave ide. Can anyone please give idiot proof instructions on how to do this?

Any help is much appreciated, and may save me from divorce!:)

---

### Post by fsmithred on 2008-10-05
If you can boot into ubuntu, post the output of 'sudo fdisk -l' and the contents of /boot/grub/menu.lst. Generally, if ubuntu is on the master and windows is on the slave, the windows entry in menu.lst should look something like this:
```
title        Windows XP
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```

---

### Post by seymour71 on 2008-10-07
Nice one mate - worked like a charm! My divorce is off!:)

Ideally, what I'd like to do now is this:

I’d like to have just 3 hard drives: 2 sata and 1 ide. I’d like to use the ide one as my master – with xp on, and one of the sata drives with both vista & ubuntu on. I’d like to make XP the default choice at startup – just to keep the Mrs. Happy. 

Thing is, Ubuntu doesn’t ‘see’ the sata drives.

---

### Post by der_hede on 2008-10-07
Is the sata controller set to ahci? Windows Vista and Ubuntu both are capable of using AHCI drives, which btw. is the privileged method to access sata drives anyway. (Advanced SATA features are only usable with AHCI mode)

If the sata options in bios are set to "IDE emulation" or something else, Ubuntu maybe is not able to use it because the P43 Southbridge is unsupported, I do not know.

If the bios option is set to IDE and you switch it to ACPI, Vista maybe gets into trouble. But there will be a way to enable Vista to use AHCI mode, I'm pretty shure.

---

### Post by fsmithred on 2008-10-07
> **seymour71 said:**
> 
I’d like to have just 3 hard drives: 2 sata and 1 ide. I’d like to use the ide one as my master – with xp on, and one of the sata drives with both vista & ubuntu on. I’d like to make XP the default choice at startup – just to keep the Mrs. Happy. 

Thing is, Ubuntu doesn’t ‘see’ the sata drives.


I found this in newegg customer reviews of MSI P43 Neo:
"Replaced a motherboard running Ubuntu Linux (Gutsy). Gutsy did not recognize the primary SATA controller (slots 1-6) and the bios would not allow me to set the SATA controller to AHCI mode. However, slots 7 and 8 are driven by the JMicron controller which does allow setting it to AHCI+IDE, and the OS booted fine with the drives in those slots. I have not tried updating the BIOS, and I have not tried newer versions of Ubuntu."

Other than dealing with the SATA issue, there are a few steps to doing what you want. 

You'll need to put grub in the mbr of your XP drive. Boot ubuntu and run 'sudo grub-install /dev/hdb' (Assuming the XP drive is slave on IDE.) 

You'll need to edit /boot/grub/menu.lst and maybe /etc/fstab to reflect the new device names for the drives. For instance, XP will now be on hd0 or /dev/hda instead of hd1 or /dev/hdb. That means you'll no longer need the map command. I think the UUID numbers in fstab will stay the same. If they do change, you can find them with the 'blkid' command.

Ubuntu will be on /dev/sdX. You get to figure out what X is. If you know your way around the grub command line, you can find the information you need if your first guess is wrong. This can help you with that - [http://users.bigpond.net.au/hermanzone/p15.htm#cli](http://users.bigpond.net.au/hermanzone/p15.htm#cli)

Shut down, switch the drives around, pray, reboot.

If for some reason it doesn't work out, you can restore the windows mbr by booting a windows XP cd, going into recovery console, and running 'fixmbr'.

---

### Post by seymour71 on 2008-10-08
Cheers for that mate, all sounds quite complicated for a newbie like me though.

What I may do though, is remove the Ubuntu drive, and do a fresh install of it on the Vista drive. How do I remove the Grub loader in the meantime though? is it just a case of uninstalling ubuntu and that will take care of it?

Thanks for your continued help.

---

### Post by louieb on 2008-10-08
> **seymour71 said:**
> ...How do I remove the Grub loader in the meantime though? is it just a case of uninstalling ubuntu and that will take care of it?

You don't uninstall GRUB you replace it with something else.   [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm") 

:)With 3 OSs, 4 hard drives that are a mix of ide and sata you won't be a newbie long.    
Good Luck,

---

### Post by seymour71 on 2008-10-08
Thanks for that, I'll have a good look at the info there.

3 OS's - I know I like making life difficult for myself! If one has to go though, I'd get rid of Vista. I need XP for a couple of programs i can't live without - Photoshop for me & Publisher for the Mrs.

Essentially, all I now want is for xp to be the default option, on either the the IDE master drive, or one of the SATA drives, and for Ubuntu to be an option at boot stage. 

I worry if I mess around with the drives again now though, I'll mess up my system that works at the mo!:)

---

### Post by fsmithred on 2008-10-08
What I suggested is less complicated and less risky than reinstall. If you just want xp to be the default, you only need to edit /boot/grub/menu.lst. Find the place where it says "default 0" (Hint: it's the first uncommented line) and change the zero to whatever XP is in the list. Counting entries starts with zero, so if XP is the third entry, you'd make it "default 2".  The other thing worth changing is right near the end of the default options, look for "# updatedefaultentry=false" and change it to "# updatedefaultentry=true". Don't remove the "#" from that line.


Try plugging the sata drives into slots 7 and 8 to see if ubuntu can find them.

If you're so completely new that you don't know how to edit system files, here are the instructions again:

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
sudo gedit /boot/grub/menu.lst
```
Now that you're in a text editor, you can make the changes. (e.g. default=something other than zero, and updatedefaultentry=true. Then save the file. Next time you reboot, it should go into XP without touching the keyboard.

---

### Post by seymour71 on 2008-10-08
Hi mate, I think the mobo review may be for the US version of this board, as mine only has 6 sata slots. I have read elswhere that I may need to update the BIOS in order to let Ubuntu see them, think I'll try that 1st, then follow your instructions.

Cheers.

---

