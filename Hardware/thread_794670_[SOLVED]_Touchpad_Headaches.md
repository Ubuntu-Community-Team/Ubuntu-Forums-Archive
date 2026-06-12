---
title: "[SOLVED] Touchpad Headaches"
date: 2008-05-14
forum: Hardware
---

### Post by Nosferatu1 on 2008-05-14
It seems that there is a pretty major problem with *ubuntus and Touchpads. I first encountered my own version of the headache after buying a new Acer Aspire 5310 with an Alps Glidepoint Touchpad, and installing Kubuntu 7.10.

The Symptoms - erratic jumpy mouse cursor behavior including warping across the screen and automagically left or right clicking something, sometimes repeatedly, whereas an ordinary USB mouse would work as expected. However the problem didn't happen on every boot, and a reboot sometimes fixed it.

The Cure - after a week of reading about similar problems and trying various fixes - no joy - always eventually returned to its erraticness. So I decided  to wait for 8.04.
I installed Kubuntu & Ubuntu & Xubuntu 8.04 (also Live) - still the same situation. After a few days of reading I think it is definitely a  kernel issue and not an xorg or mouse issue.

When the touchpad is working properly I get this:

```
ubuntu@ubuntu:~$ dmesg | grep mouse
[   48.783371] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   48.824901] mice: PS/2 mouse device common for all mice

```

When I have the erraticness I get this:

```
ubuntu@ubuntu:~$ dmesg | grep mouse
[   36.373992] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   36.417694] mice: PS/2 mouse device common for all mice
[  173.202839] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[  173.223405] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
[  178.277189] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1

```

So it seems that there is a problem with the kernel or in psmouse.c which has lingered over from 7.10.

Since there seem to be numerous problems with touchpads in general, I thought that the developers would have sorted it all out by now, since this is meant to be the easiest linux for newbies.

I am currently testing this solution without reconfiguring xorg as mentioned at the bottom, and will let you know of the outcome:

>  Originally Posted by mrtwister123  View Post
Hi All,

I've finally got my Alps touchpad working on my Fujitsu 6120 laptop (albeit on PCLinuxOS 2007). My problem originated from the fact that Linux (Ubuntu Fiesty) refused to detect my Alps touchpad device correctly and was detecting it as a PS/2 Mouse.

I was able to fix this by editing my /boot/grub/menu.lst entry for my installation by tagging i8042.reset i8042.nomux to the end of the kernel entry. Thus my main boot entry in my menu.lst file now looks like this:

title linux
kernel (hd0,0)/vmlinuz BOOT_IMAGE=linux root=/dev/sda5 acpi=on splash=silent vga=788 i8042.reset i8042.nomux
initrd (hd0,0)/initrd.img

This is an entry for a PCLinuxOS install, but the principle should be the same for Ubuntu (i.e. add the i8042.reset i8042.nomux parameters to the kernel boot options).

This works on the Intel i8042 keyboard/mouse driver.

After getting the OS to recognise the Alps device, it's a simple case of configuring your xorg.conf file with the correct entries for synaptics. Further details for doing so can be found at [http://web.telia.com/~u89404340/touchpad/](http://web.telia.com/~u89404340/touchpad/)

Regards,
Mark

---

### Post by Nosferatu1 on 2008-05-16
Still testing with and without the entries added, and it seems that it works, and no changes have been made to xorg.conf

---

### Post by Nosferatu1 on 2008-05-19
Problem fixed. No more mouse issues after applying the methodology as outlined above. Now I need to figure out what the kernel options I passed actually do, and why they work.

---

### Post by Flix83 on 2008-09-11
Wohoo, this actually works, finally I can use Linux while sitting in the lecture. BIG THX

---

