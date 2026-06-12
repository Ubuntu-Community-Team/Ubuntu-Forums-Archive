---
title: "Ubuntu/Lubuntu 11.04 on Toshiba Satellite A135-S2326"
date: 2011-06-24
forum: Hardware
---

### Post by travisHAZE on 2011-06-24
I can boot Lubuntu from a USB with the "noacpi=off noapic nolapic" if I set the settings in the USB menu. Upon attempting to boot the installed version of Lubuntu, it hangs on a black screen with a flashing underscore.

I can get to GRUB no problem, however, when I edit it (non recovery mode), and place:
 
acpi=off
noapic
nolapic

It will return saying noapic and nolapic do not exist, and it cannot boot, so it goes back to the black screen with a flashing underscore, any attempts to enter into the GRUB boot manager result in that line being replaced with (going from memory on this part)

[[[[[f7\/ and then hangs.



Now to Ubuntu, I can usually get it to boot from USB, and usually get it to install, however, same problems persist upon booting from Hard-drive.

My apologies if this turns out to be a simple fix, Vista corrupted itself on this laptop, so I'm trying to make it useful by installing Linux and this is my first time dabbling in it

---

### Post by Beacon11 on 2011-06-24
Yeah no problem. You need to do two things-- make the change temporarily so you can boot, then make the change permanent. To temporarily make the change, you need to get into GRUB at boot-time by pressing ESC or whatever (I'm assuming you already know how to do this). You then see a list of boot options. Press the 'e' key on the first one. Then use the arrow keys to navigate to the line that begins with "kernel" and press 'e' again. At the end of that line, you add your parameters one after the other, separated by spaces. When you're done, hit the 'enter' key, and then the 'b' key to boot with those parameters. This will work, but that change only exists for this boot.

To make the change permanent, you need to edit /etc/default/grub and add those parameters to the GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" line (right after splash). Save that file, and run:
```
sudo update-grub
```

Then you should be good to go.

---

### Post by travisHAZE on 2011-06-24
Entered into GRUB, Editing Parameter 'Ubuntu, with Linux 2.6.38-8-generic' (first boot option)
 
Looks like this (with this field being editable, adding or removing any part of it)
```

setparams 'Ubuntu, with Linux 2.6.38-8-generic'
 
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 29fd3458-afd1-43f7-9361-4e2fc1addc1d
linux /boot/vmlinuz-2.6.38-8-generic root=UUID=29fd3458-afd1-43f7-9361-4e2fc1addc1d ro  quiet splash vt.handoff=7
initrd /boot/initrd.img-2.6.38-8-generic
```
 
I see no kernel I can press e on
Also, GNU GRUB version 1.99~rc1-13ubuntu3 is where I'm at in the boot
 
My GRUB menu is populated with
```

Ubuntu, with Linux 2.6.38-8-generic
Ubuntu, with Linux 2.6.38-8-generic (recovery mode)
Memory test (memtest86+)
Memory text (memtest86+, serial console 115200)
```

---

### Post by Beacon11 on 2011-06-24
Ahh, shoot sorry-- edit the "linux /boot/..." line the same as the "kernel" line in my previous directions.

---

### Post by travisHAZE on 2011-06-24
Is the initrd /boot/... line part of the linux /boot/... line?

---

### Post by Beacon11 on 2011-06-24
> **travisHAZE said:**
> Is the initrd /boot/... line part of the linux /boot/... line?

Nope.

---

### Post by travisHAZE on 2011-06-24
OK, successfully booted without the USB Flash Drive there, seems stable, so going to make it permanent now, now, when editing the grub file, do I add the parameters before or after the quotations?
 
ie should it look like ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off noapci nolapci"
 
or
 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" acpi=off noapci nolapci
```
I'm assuming the former rather than latter, correct?
 
Also, right below the GRUB_CMDLINE_LINUX_DEFAULT there is one GRUB_CMDLINE_LINUX=""
Why is it empty? What is the difference between these two lines simply by adding default?

---

### Post by Beacon11 on 2011-06-24
> **travisHAZE said:**
> I'm assuming the former rather than latter, correct?

Correct; within the double quotes.

---

### Post by Beacon11 on 2011-06-24
> **travisHAZE said:**
> Also, right below the GRUB_CMDLINE_LINUX_DEFAULT there is one GRUB_CMDLINE_LINUX=""
Why is it empty? What is the difference between these two lines simply by adding default?

Now that you bring it up, you should probably put your new parameters in GRUB_CMDLINE_LINUX. It doesn't matter much, but then it keeps the defaults and your customizations separate. For more information, see [http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Editing_etcdefaultgrub](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Editing_etcdefaultgrub)

---

