---
title: "Ubuntu and other linux distros won't work."
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by JackSnow on 2009-01-31
[FONT="Arial"][/FONT][FONT="Tahoma"][/FONT]Hello. I recently got rid of my dell laptop and now I am using a dell dimension e501 desktop machine. When I try to install ubuntu, or any other linux distro(i've tried gOS, fedora, opensuse), It just doesn't work right. When I tried to install ubuntu and gOS they both had totally messed up graphics once i got to the desktop. GOS just flickers and changes colors and it's so messed up and ubuntu pretty much does the same thing. Is my computer too old? Vista worked great on it.

---

### Post by Pumalite on 2009-01-31
Memory? Graphics? You might need the Alternate CD and/or a lighter distro.

---

### Post by JackSnow on 2009-01-31
I have 1024 mb of memory and ati radeon graphics

---

### Post by Pumalite on 2009-01-31
Maybe you should try the Alternate CD. Make sure you have a bootable CD:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Make CD first in the boot order in BIOS
Clean the lens in your burner
Burn at 4x or less
You can download and install ImgBurn:
[http://www.imgburn.com/](http://www.imgburn.com/)
Once installed; go to Mode>ISO>Burn
Make 1x your speed to burn

---

### Post by JackSnow on 2009-01-31
Ok I'm downloading the alternate cd and i have imgburn. But why do i need to do this? It says the alternate cd is for computers with very low memory but i have 1024 mb. I'll mention also that when i managed to install ubuntu once, it would'nt boot after the restart. It would just get stuck at "grub loading"

---

### Post by JackSnow on 2009-01-31
Ok so I got it running but the graphics are still very messed up. I don't get it because it worked good on vista with no graphics problems at all. Is there anything i can do to fix this?

---

### Post by Pumalite on 2009-01-31
What are the specs of your monitor? Are you using SLI?
See if you can boot a Knoppix Live CD:
[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)

---

### Post by JackSnow on 2009-02-01
My monitor is a 22" hp w2207 and I use a vga cable.

---

### Post by albinootje on 2009-02-01
> **JackSnow said:**
> My monitor is a 22" hp w2207 and I use a vga cable.

Can you post the output of the following :
```

lspci
sudo lshw -C video
lsb_release -a
uname -a

```
Thanks.

---

### Post by JackSnow on 2009-02-01
Do you want the entire thing or just the end of it?

---

### Post by albinootje on 2009-02-01
> **JackSnow said:**
> Do you want the entire thing or just the end of it?

After each command you would hit <enter>, and the complete output of that please.

---

