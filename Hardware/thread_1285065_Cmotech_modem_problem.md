---
title: "Cmotech modem problem"
date: 2009-10-07
forum: Hardware
---

### Post by zero-n on 2009-10-07
I use a cmotech modem to connect to the Internet the problem that if my modem is pluged in & i restart the Ubuntu the system will hang-up in booting process i have tried to use Ctrl+Alt+Delete the boot continued but it gave me x-server error message i can fix that problem from the recovery option but i want to know is there is a way to avoid this process (don't say unplug the modem) ;) thanks is advance

---

### Post by IcarusR on 2009-10-07
Will it boot OK with modem unplugged? Rules out other problems. 
It is possible to edit a file & stop the animation during startup so you can see what is causing it to hang. 
Can't for the life of me remember where it is though. Maybe someone can help here.
More info on the modem would help. ie model & type.

---

### Post by zero-n on 2009-10-09
Can anyone help with this ?

---

### Post by IcarusR on 2009-10-10
Yes I have tried, but you chose to ignore my questions, suggestions & requests for further information in my previous post

Just can not help some folk !!

---

### Post by zero-n on 2009-10-10
I did not ignore you suggestion.
i have search for something to tell you what is going behind the the boot loading screen but i didn't come with something useful so i asked people if they can help me in this.

---

### Post by superdav42 on 2009-10-10
I believe you can just press alt+F1 and it will show you what it's doing as it boots up. But does it do a hard hang? Does num lock change the num lock led? Is this a USB modem? If so what's the output of lsusb?

---

### Post by zero-n on 2009-10-10
it not a hard hang the num-lock is still running & it's a usb modem
this is the output of lsusb:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 16d8:6803 CMOTECH Co., Ltd. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04fc:757a Sunplus Technology Co., Ltd Aiptek, MP315 MP3 Player
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by zero-n on 2009-10-18
my Comtech modem will be recognise as a CD & flash memory i think that is the problem , cause i used startup-manager to manage Grub option so i can make text appear during booting & i saw that my system hang-up when recognising the flash memory.

so can anyone help

---

