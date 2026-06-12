---
title: "[SOLVED] Problem running ubuntu on a vaio laptop"
date: 2008-09-26
forum: General Help
---

### Post by titico on 2008-09-26
hello

well i've got a little problem here.

I have a vaio laptop running ubuntu. I upgraded it from version 7.10 to 8.04 using the Update Manager.

I had no problem with installation, but now when I start the computer it remains freeze after the BIOS check...

I only get this message

Starting up...
[ 12.194676] ACPI: EC: acpi_ec_wait timeout, status = 0, expect_event = 1
[ 12.194722] ACPI: EC: read timeout, command = 128

If someone can help me please =]

---

### Post by Partyboi2 on 2008-09-27
Try passing acpi=off as a boot option. When you see grub loading...  press Esc to get to the grub menu then then highlight the kernel you are booting into and press "e" then highlight the 2nd line (starts with kernel) and press "e" again then add acpi=off then press enter and finally "b" to boot.
If it works you will need to make it permanent by adding it to your grub menu.lst

---

### Post by titico on 2008-09-27
Wow, great. 
It worked perfectly!
Do you know the origin of this problem might be?

And how do I add it to the grub menu.lst?

Thank you!

---

### Post by NoWayBill on 2008-09-27
sudo gedit /boot/grub/menu.lst

---

### Post by Partyboi2 on 2008-09-28
open a terminal (Applications>Accessories>Terminal) and type
```
gksudo gedit /boot/grub/menu.lst
```
Once it has open look for this part
> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=805b623e-614e-4560-ae10-e1cf0b44876a ro quiet splash
Add acpi=off to the line starting with ```
# kopt=root=UUID=805b623e-614e-4560-ae10-e1cf0b44876a ro quiet splash
```
```
# kopt=root=UUID=805b623e-614e-4560-ae10-e1cf0b44876a ro quiet splash [COLOR=Red]acpi=off[/COLOR]
```
then save the changes and back in the terminal update grub
```
sudo update-grub
```

---

### Post by titico on 2008-09-28
It works only when I set the acpi off before the boot...

When i save the changes to the grub menu.lst and then i restart the computer
the error remains the same...

---

### Post by titico on 2008-09-28
In the grub menu i have this

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=3c3dafdc-6931-4d37-b957-dea421a0e6af ro
# kopt_2_6=root=/dev/mapper/ubuntu-root ro

---

### Post by blakamin on 2008-09-28
Get rid of the "#" in front of the line with acpi=off. 
# makes it a comment, not a command


just a thought:confused:

I'm no guru

---

### Post by titico on 2008-09-28
well thanks i'll try it =]

---

### Post by Partyboi2 on 2008-09-28
> Get rid of the "#" in front of the line with acpi=off. 
# makes it a comment, not a commandYou don't need to remove the # from in front, for comments in the grub menu they are shown with ## infront of them.
> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
[COLOR=Red]# kopt=root=UUID=3c3dafdc-6931-4d37-b957-dea421a0e6af ro[/COLOR]
# kopt_2_6=root=/dev/mapper/ubuntu-root ro     add it to this line ```
# kopt=root=UUID=3c3dafdc-6931-4d37-b957-dea421a0e6af ro

``` line and remember to update grub.
Another way you can do this is to look for this section

```
## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-22-386
root            (hd0,0)
[COLOR=Red]kernel          /boot/vmlinuz-2.6.15-22-386 root=/dev/hda1 ro quiet splash [/COLOR]
initrd          /boot/initrd.img-2.6.15-22-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-22-386 (recovery mode)
root            (hd0,0)
[COLOR=Red]kernel          /boot/vmlinuz-2.6.15-22-386 root=/dev/hda1 ro single[/COLOR]
initrd          /boot/initrd.img-2.6.15-22-386
boot

title           Ubuntu, kernel 2.6.15-21-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-21-386 root=/dev/hda1 ro quiet splash noapic nolapic vga=0x33f
initrd          /boot/initrd.img-2.6.15-21-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-21-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-21-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-21-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

```add acpi=off to the kernel lines and update grub. The only down side to this way is that when ever you get a kernel update you will need to re add acpi=off

---

### Post by titico on 2008-09-28
Thanks, it worked the second way i tried with the first one without success.

Thank you a lot.

---

