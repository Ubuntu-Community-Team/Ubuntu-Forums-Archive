---
title: "Ubuntu 9.10 on Acer Aspire 7738G"
date: 2009-11-16
forum: Hardware
---

### Post by RD1945 on 2009-11-16
Hello all,

I recently installed Ubuntu 9.10 on this laptop.
Everything is working fine except 1 thing, the touchpad.

There is a button next to the touchpad to disable/enable the touchpad.
When I press it, the touchpad is disabled just fine but when I press it again it won't enable again.

Is there someone that can help me?

---

### Post by coffeecat on 2009-11-19
Same thing on this Acer Aspire 7540. Solution = don't touch the touchpad disable button! :p

I found that nothing short of a reboot would re-enable the touchpad. I tried a restart of the xserver, but that didn't work. Fortunately, plugging in a USB mouse gave me mouse cursor control back. Moral of the story - keep a USB mouse handy in case you accidentally touch the disable button.

Touchpad response is not as good as on my Sony laptop. Finger scrolling is particularly clunky. And I noticed that in System > Preferences > Mouse, there is no third 'Touchpad' tab, which is there with my Sony. **RD1945**, is the touchpad tab missing in yours as well? If so, this could be a general issue with Acer touchpads. I'll do some digging around.

**Edit:** actually, the touchpad is just as unrefined in Windows 7 - single finger scrolling is worse, if anything. But two-finger gestures work in W7, which they don't in Ubuntu.

Hmmm - "two-finger gesture". That has a special meaning here in the UK, particularly appropriate to Windows.  :rolleyes:

---

### Post by coffeecat on 2009-11-20
Curious - just discovered something. Having plugged a mouse in, I disabled the touchpad with the button next to the touchpad. That's so that I could type a post here without having the cursor jump around every time I accidentally brushed the touchpad. Anyway - I put the machine into suspend, but just before it suspended, and with the mouse still plugged in, I clicked on the disable/enable button again. Then, after I had woken the machine up again, the touchpad was working.

:-k

---

### Post by RD1945 on 2009-11-22
The tab you are talking about is there on my machine.

I'll try to change my xorg.conf to see if I can get the touchpad to work like it should.

I will keep you informed.

---

### Post by RD1945 on 2010-07-05
It's been a while since I posted in this topic.

In the meantime I upgraded to Ubuntu 10.04 and the touchpad is still not working as it should. The same problem applies.

However, there is a "fix" for this:

In /etc/default/grub add the following to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash": i8042.nomux

The line should now read: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nomux"

You can now run "update-grub" and reboot your machine.
All should be fine after this.

Hope the Ubuntu team will fix this soon as this is an annoying problem.

---

