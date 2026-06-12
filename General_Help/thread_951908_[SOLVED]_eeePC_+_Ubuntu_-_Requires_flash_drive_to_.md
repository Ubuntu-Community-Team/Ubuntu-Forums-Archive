---
title: "[SOLVED] eeePC + Ubuntu - Requires flash drive to boot?"
date: 2008-10-18
forum: General Help
---

### Post by chazdraves on 2008-10-18
Greetings, all!

Well, I finally broke down and got one of these eee PCs. I stumbled across Ubuntu eee and gave that a whirl. Everything seems to work (including sound and wifi), but I have to have the flash drive in to get it to boot. At first I thought I had accidentally installed Ubuntu to my flash drive, so I removed it to see what would happen. I've now figured out that it is actually installed on the SSD, but it requires me to hit ESC on startup and select the flash drive as my boot device.

I can't get my head around this... The flash drive does NOT have Ubuntu installed on it, only the Ubuntu eee Live CD, but it's still required to get Ubuntu loaded from the SSD. I can pull out the flash drive immediately after selecting to boot from it and everything goes normally...

Any ideas?

Thanks, guys!
- Chaz

P.S. Is there any way to get a normal version of 8.10 working on the eee? I don't want to go through any real hassle, and I only got the 4GB version. Thanks again!

---

### Post by mikewhatever on 2008-10-18
Was the flash drive plugged in when you installed?
Could it have happened that GRUB got installed to the MBR of the flash drive?
Are you booting from it?
I think reinstalling GRUB may help, here is a guide -> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub)

---

### Post by chazdraves on 2008-10-18
I appreciate the tip, and I think you're probably right.

That said, I'm no expert with the terminal. Can anyone tell me exactly which set of instructions I should be looking at?

Also (off topic): Has anyone tried the 8.10 beta on an eee PC? I heard there will be better support for these in future releases. If flash and wifi worked out-the-gate, I wouldn't have need for Ubuntu eee.

Thanks again, guys!
- Chaz

---

### Post by mikewhatever on 2008-10-18
Actually, I've just realized you are on a PC with no cd-rom. All instructions on the page I linked to earlier are for conventional computers with cdroms, so they aren't exactly helpful in your case. You can try reinstalling grub with Super Grub USB though. It's CLI, but the instructions are very good.
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html#Super_Grub_USB_Disk](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html#Super_Grub_USB_Disk)
If you think that too much of a hassle, it may be easier to start from scratch with the external disk unplugged.

---

### Post by C.S.Cameron on 2008-10-19
Installer seems to get mixed up when installing from flash to flash.
You can run grub booting from your Live USB.
bobnutfield wrote this:

Code:

sudo grub

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)

Finally exit the grub shell
Code:

quit

That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.

If you still have a problem after the above you may have to change 'root' in /boot/grub/menu.lst from (0,1) to (0,0).
This can be tested at grub by hitting 'Esc' and then 'e' to temporarily edit the first boot option.
Then you can hit 'b' to boot.

---

### Post by C.S.Cameron on 2008-10-19
Oop's double post.

---

### Post by chazdraves on 2008-10-20
I was pleased to see how simple your instructions were. Unfortunately, they don't seem to do the trick. The console returns this:

 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+16 p (hd1,0)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

Which seems like it was successful, but when I boot I still need the flash drive in. Its interesting to note that if I leave the drive out during booting, the grub menu still comes up, but if I click on any of the options it tells me "Error 21 Invalid Disk" or something to that effect... I am also wondering how to reformat the offending flash drive so I can try re-installing... I tried fdisk /dev/sda1, but that didn't work...

I really appreciate the help, guys!
- Chaz

---

### Post by chazdraves on 2008-10-20
Nevermind, that last line solved my problem. It was hd0,0 and not 1,0. Thank you very kindly. Though that flash drive trick was a neat security measure, it was also quite the hassle.

Again, thank you both!
- Chaz

---

