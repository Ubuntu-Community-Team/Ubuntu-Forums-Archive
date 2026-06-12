---
title: "GRUB2 and removing Windows OS from boot menu"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by bigeslp on 2009-11-06
First of all I am a noob to Ubuntu or Linux in general. Also sorry if this post appears in the wrong area.

My question is this:
I had desktop PC with 2 harddrives. Drive 0 was WIN95, Drive 1 was XP. I installed Ubuntu on drive 1 and made a seperate partition for Ubuntu. When it boots it shows the Ubuntu 9.10 install, memtest, and both windows options for booting. I only would like just the XP option to appear as the WIN95 is much outdated. I have briefly read the GRUB2 articles on how to configue a custom boot menu and such but have not been able to pinpoint what I want to do. 

Any help would be greatly appreciated.

Thank You Erich

---

### Post by Rambar on 2009-11-06
Under the root account, you have to edit menu.lst in the /boot/ folder and add an entry with your XP location.

---

### Post by oldfred on 2009-11-06
Since grub2 auto updates with just about any change it would be best to create a manual entry and turn off the osprober.

You should be able to copy your XP entry from grub.cfg into the custom file.

If you put your menu entry in /etc/grub.d/40_custom it will not be over written and will be at the end of your menu.

In /etc/default/grub edit this to be true to stop it from updating:
GRUB_DISABLE_OS_PROBER=true

If you ever add another system remember to turn the prober back on so it can find it.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Finally, don't forget to run either the 'sudo update-grub' or 'sudo grub-mkconfig' command.

---

### Post by bigeslp on 2009-11-07
Oldfred thank you much for the help. Everything worked like a charm. Thanks again, Erich

---

