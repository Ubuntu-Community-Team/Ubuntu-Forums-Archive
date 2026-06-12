---
title: "RX 580 (AMD) not working with 18.04"
date: 2018-09-07
forum: Hardware
---

### Post by megamini on 2018-09-07
Hello,

I'm using Kubuntu 18.04
I switched my AMD HD 7950 with a RX 580, and I can't boot regularly with it. After the Grub boot menu, I get a glitched screen (mostly plain black, with a few colored lines at the bottom). Sometimes (but not systematically), the GPU fans launch for 2 secs at this step. Then the screen become plain black and nothing happen, I cannot enter a tty session with Ctrl+Alt+F(x). Only reset.
If I boot in recovery mode, I can enter the graphic session in low res mode. I tried enabling the proprietary drivers (amdgpu-pro), but to no avail (installation went well but it did not solve the abose mentionned symptoms).
I was expecting it to work out of the box with the open source AMD drivers. At this point you'll probably need more infos to help me, please let me know what I should provide !
Thanks !

Clem

(The card itself is in working condition, I can launch my games in hi res under Windows)

---

### Post by megaboz2 on 2018-09-14
Hi, Megamini.  You might want to try adding "iommu=soft" to your grub config file in the "GRUB_CMDLINE_LINUX_DEFAULT" line.  It worked for my Radeon 580 kernel panic problem described [here]("https://ubuntuforums.org/showthread.php?t=2400746").  Hopefully this does the trick for you as well.


--MB

---

### Post by sacnoth on 2018-09-17
I seem to have the same problem and tried to add "iommu=soft" to the list commands/parameters that I can change in GRUB when pressing 'e', but it didn't help.

How would I go about changing "GRUB_CMDLINE_LINUX_DEFAULT" when I can't boot my OS?

---

### Post by megamini on 2018-09-17
Good job megaboz2, unfortunately  it did not work for me :-(

sacnoth, you can add iommu=soft to the command parameters pressing e in GRUB. In my case, the relevant line is:
```
linux /boot/vmlinuz-4.15.0.34-generic root=UUID=(the uuid)  ro splash iommu=soft $vt_handoff
```
If you have the same problem as me, you should be able to boot in recovery mode (select recovery mode in grub, then wait for a recovery menu, choose resume and the session should start in mininal resolution). Then you can edit the /etc/default/grub configuration file, adding "iommu=soft" to GRUB_CMDLINE_LINUX_DEFAULT, save, run "update-grub" in terminal, and restart.

---

### Post by sacnoth on 2018-09-29
Thanks megamini, this worked for me :)

---

