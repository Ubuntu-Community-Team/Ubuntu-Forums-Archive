---
title: "Suspend/hibernate and uswsusp problems"
date: 2008-08-05
forum: Hardware
---

### Post by gkkg on 2008-08-05
I'm trying to get suspend and hibernate working on Kubuntu hardy running on a desktop.
I get immediately back to the login screen as soon as I try either.

I know this is a problem that many have encountered, I have searched other posts, but without much success.

One thing I wanted to try was installing uswsusp - but another problem here: trying to configure uswsusp with "sudo dpkg-reconfigure uswsusp" I get:
update-initramfs: Generating /boot/initrd.img-2.6.24-20-generic
cryptsetup: WARNING: found more than one resume device candidate:
                     /dev/sda6
                     UUID=17295a28-4e7e-407b-8edd-8b5b8f623446
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
cryptsetup: WARNING: found more than one resume device candidate:
                     /dev/sda6
                     UUID=17295a28-4e7e-407b-8edd-8b5b8f623446


I am very new to Ubuntu and Linux, so if you can help me with this I would need a step-by-step guide. 
Thanks!

---

