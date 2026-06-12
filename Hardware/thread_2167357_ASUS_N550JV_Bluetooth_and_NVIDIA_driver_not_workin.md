---
title: "ASUS N550JV: Bluetooth and NVIDIA driver not working"
date: 2013-08-13
forum: Hardware
---

### Post by sgehlich on 2013-08-13
Hey all,

a couple of days ago I bought a new ASUS N550JV laptop. I tried everything, but I can't get my bluetooth to work (it only works from time to time with a 3.11rc5 kernel). Here's what I tried

- Install Ubuntu 13.04, Bluetooth didn't work ("Bluetooth is disabled")
- Install Ubuntu 13.04, installed latest 3.10 kernel, Bluetooth didn't work
- Install Ubuntu 13.04, patched the kernel so that my bluetooth controller (0x13d3 / 0x3402) works - only works from time to time, I have to reboot a lot to get it to work

Can it really be this hard to get Ubuntu running on a new laptop? Also, since my laptop is using Optimus technology, the nvidia drivers do not work. Even when using bumblebee I only run into problems with the ACPI driver (there was a but that has been fixed in 3.11, but unfortunately the nvidia drivers do not support linux kernels > 3.10).

I switched over from Mac and hoped to have a good start. But no, I'm fighting with these problems since 7 days. It's really exhausting.

If you need any more information, feel free to ask.

Best,
Sascha

---

### Post by duklex on 2013-09-10
Hi, same laptop, same situation...

---

### Post by Linuxisfast on 2013-09-10
Go to the BIOS to check if it isn't disabled there. On my ASUS K53M and K55M the bluetooth works out of the box.

---

### Post by starfall2 on 2013-09-12
> **sgehlich said:**
> Hey all,

a couple of days ago I bought a new ASUS N550JV laptop. I tried everything, but I can't get my bluetooth to work (it only works from time to time with a 3.11rc5 kernel). Here's what I tried

- Install Ubuntu 13.04, Bluetooth didn't work ("Bluetooth is disabled")
- Install Ubuntu 13.04, installed latest 3.10 kernel, Bluetooth didn't work
- Install Ubuntu 13.04, patched the kernel so that my bluetooth controller (0x13d3 / 0x3402) works - only works from time to time, I have to reboot a lot to get it to work

Can it really be this hard to get Ubuntu running on a new laptop? Also, since my laptop is using Optimus technology, the nvidia drivers do not work. Even when using bumblebee I only run into problems with the ACPI driver (there was a but that has been fixed in 3.11, but unfortunately the nvidia drivers do not support linux kernels > 3.10).

I switched over from Mac and hoped to have a good start. But no, I'm fighting with these problems since 7 days. It's really exhausting.

If you need any more information, feel free to ask.

Best,
Sascha


If you have the Atheros wifi card, this is the reason why it doesn't work (missing id in driver) -

[https://bugzilla.kernel.org/show_bug.cgi?id=60726](https://bugzilla.kernel.org/show_bug.cgi?id=60726)

It's really simple, but requires a kernel compile until the patch gets accepted upstream.

You also need to enable bluetooth coexistence on your ath9k driver as the bluetooth and wifi are integrated.

My advice is if you really need bluetooth, to swap out the wifi card for an Intel one. They are relatively cheap nowadays.

---

### Post by InFro on 2013-09-19
Same laptop.
Could not get bumblebee working in any way on 13.04. Now installed 13.10 beta 2, kernel 3.11.0-7. Added xorg-edgers, installed bumblebee and it just works.

Just tested bluetooth - also works without problem. I have Atheros wifi but I guess kernel already has the patch for it as starfall2 mentioned.

---

### Post by side2k on 2013-12-05
[InFro]("http://ubuntuforums.org/member.php?u=314683"), can you show, what version of bumblebee package are you running and also /etc/X11/xorg.conf and /etc/bumblebee/bumlebee.conf?
I got nvidia card running but not with bumblebee 8(

---

### Post by kogz on 2014-02-17
> **InFro said:**
> Same laptop.
Just tested bluetooth - also works without problem.
Hi, could anybody please confirm bluetooth is working for this laptop out of the box just after fresh installation of 13.10 and apt-get dist-upgrade?

Thank you and kind regards,
Kokos

---

