---
title: "Can't get past memory test"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by jahgamer189x on 2009-10-04
Hi, I have just installed Ubuntu 9.04 using the live CD without any problems. When the installation was complete, the installation window closed and I restarted my computer. Then, my computer started to boot up. It came up with something about Grub Menu. When the 3 second timer had finished counting down, my system went into a memory test (unasked). I let it do it's thing and then when it said that it was done (I know it loops) I pressed escape. However, when it boots back up, it still does the memory test. I can't even get to where  I would choose to boot into either XP or Ubuntu!
Basically, whenever I start up my computer, a memory test is automatically started and I cannot get past it.

Please help!:confused:

---

### Post by rreese6 on 2009-10-04
did you try to hit ESC to get in to the menu?
if that doesn't work, do this :

1. Boot up with LiveCD. Once you are on the Desktop, got to this link and download:
```
[Download Boot Information Script]("http://sourceforge.net/projects/bootinfoscript/")
```
This Script will gather your current configuration and make a report.
This gives us a better idea of what your problem is and how to fix it.

2. Open up terminal and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will make a file called "Readme.txt" on your desktop.

3. Post the contents of that file here.

---

### Post by jahgamer189x on 2009-10-04
Escape doesn't work and I used Unetbootin, so I can't boot using a live cd.

---

### Post by ottosykora on 2009-10-04
> **jahgamer189x said:**
> Escape doesn't work and I used Unetbootin, so I can't boot using a live cd.

do you mean you have no optical drive? (netbook?)
You might boot from usb stick?

---

