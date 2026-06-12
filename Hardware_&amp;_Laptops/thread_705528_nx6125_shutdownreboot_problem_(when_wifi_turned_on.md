---
title: "nx6125 shutdown/reboot problem (when wifi turned on)"
date: 2008-02-23
forum: Hardware &amp; Laptops
---

### Post by Zeratul7 on 2008-02-23
Hi,
I have a problem with HP nx6125 shutdown and reboot - the screen freezes during the shutdown/reboot splash screen and suddenly shows some errors and freezes (can be seen at the foto). Then only manual shutdown helps. It only happens when wifi button is turned on. The wifi card is Broadcom 4318 and works fine. Ubuntu version is Gutsy X86. I have tried every trick from related topics but none of them works. Any ideas?

---

### Post by Zeratul7 on 2008-02-27
Any ideas?

---

### Post by CrazyGuy123 on 2008-02-28
Hi

I have the same laptop, but don't have your problem.

What version of ubuntu are you running?

Does it happen every time with the wireless light on?  Does it always succeed with the wireless light off?

---

### Post by Zeratul7 on 2008-03-01
Version is Ubuntu Gutsy X86 as i mentioned in my first post. This problem occured after bios update (version F11). No, there is no problem when wifi switch is  turned off. I tried to add "sudo ifconfig eth1 down" into /etc/rc0.d and etc/rc6.d but for some reason the wifi was still not turned off at reboot or shutdown.

---

### Post by iamkrazee on 2008-06-12
> **Zeratul7 said:**
> Version is Ubuntu Gutsy X86 as i mentioned in my first post. This problem occured after bios update (version F11). No, there is no problem when wifi switch is  turned off. I tried to add "sudo ifconfig eth1 down" into /etc/rc0.d and etc/rc6.d but for some reason the wifi was still not turned off at reboot or shutdown.

I used to get this a lot. It even showed segfaults sometimes. And this was without the bios updates. Work-around is to hit the wireless button before shutting down. Just like you've already mentioned. But I saw this problem back in Gutsy x86 ONLY and no problems whatsoever on Hardy (kubuntu) x64. It even mutes, and changes volume on the laptop keys. I very strongly recommend you to upgrade to Hardy.

---

### Post by headlessspider on 2008-07-08
i am in hardy already and i also get this problem -- it suddenly shutsdown. the wifi is not even on. and i'm on an hp compaq nx6120. in the message logs i see "... exiting on signal 15"

---

