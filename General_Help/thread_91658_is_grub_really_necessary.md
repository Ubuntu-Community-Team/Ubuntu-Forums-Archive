---
title: "is grub really necessary?"
date: 2005-11-17
forum: General Help
---

### Post by Specialsauce on 2005-11-17
just out of curiosity....

is grub really necesary if your only gonna run one OS?

---

### Post by bonzodog on 2005-11-17
You have to understand that all linux distros need a boot loader. You cna hide grub at boot though, so it by-passes it.
The linux kernel cannot self-start and grub acts as a kernel starter motor.
Lilo and gag also do the same

---

### Post by taurus on 2005-11-17
If you only have one OS and don't want to see the grub menu, then use

timeout 0

in /boot/grub/menu.lst

---

### Post by matthewv on 2005-11-17
Usually, if you are installing ubuntu as the only os on the comp, it will display a press esc to see boot menu message when the comp starts for about 2 secs, then go straight in to booting ubuntu.

---

### Post by Jengu on 2005-11-17
Even WindowsXP uses a bootloader when it's the only OS -- in fact, what Grub does when you choose WindowsXP is just hand control over to the Microsoft bootloader. The difference is that grub lets you choose other OSs and waits before booting -- but as mentioned above you can alter your grub.conf to change that.

---

