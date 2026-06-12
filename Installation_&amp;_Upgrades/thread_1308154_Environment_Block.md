---
title: "Environment Block"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by mpianka on 2009-10-31
I have downloaded Ubuntu 9.10 Desktop and Netbook Remix 9.10.
Dell D410 && Dell D20 Laptops.

Installation of the System did not produce any errors first reboot.
First reboot after installation brings Ubuntu 9.10 Destkop up as well as NetBook remix (Computers do not matter here because both can be wipped, I tried them both).

I shut down the computer, or hibernate, or suspend... OS is no longer accessible.
Two types of error messages:
Error: Biosdisk read error
[SIZE=4]invalid environment block[/SIZE]

or

[SIZE=4]environment block is to small[/SIZE]
:(
I read something on the internet and did :
cd /boot/grub
rm grubenv
grub-editenv grubenv create
grub-editenv grubenv set default=0
grub-editenv grubenv list
default=0

Resault: The same error.
I tried to reinstall OS but it makes no difference, it always produce this error.
I wipped MBR and tried again, the same scenario it works after the installation reboot, but second reboot.
I tried to re-install grub2 - error changed to [SIZE=4]environment block is to small instead of invalid. 
[/SIZE]
Any ideas ? I read that many people got that sorted using commands I pasted here.
I can not get both laptops to use these systems though. 

Could someone help me please? 


[B][SIZE=4]
[/SIZE][/B]

---

### Post by mpianka on 2009-10-31
Error:biosdisk write error
 Failed to boot default entries.
Press any key to continue...

Once I press ANY key

error: invalid environment block
Failed to boot default entries.


this is pure, clean installation od D410 and D620 the same scenario.

D410 doesn't have option for AHCI as someone here on forum I can't change there anything.

Unbelivable, I just have no LUCK with linux.

---

### Post by mpianka on 2009-10-31
YES, I found it.

The only way to get this to work is to delete a file /boot/grub/grubenv

if i delete this file and reboot, computer boots as normal. After the first boot, this file is being created and next boot gives an error.

What Shall I do to prevent this file being created ?:)

---

### Post by swajime on 2010-04-08
I'm getting this error now too. "invalid environment block", "failed to boot default entries"

Have you (or anyone else) found the fix for this?

---

### Post by jeterfan1 on 2010-05-06
thanks for the solution, i have dual boot winxp so i was able to delete /boot/grub/grubenv 
boots fine now.

---

