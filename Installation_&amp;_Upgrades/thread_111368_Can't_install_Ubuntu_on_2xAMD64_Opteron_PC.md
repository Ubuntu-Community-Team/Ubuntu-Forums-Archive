---
title: "Can't install Ubuntu on 2xAMD64 Opteron PC"
date: 2006-01-02
forum: Installation &amp; Upgrades
---

### Post by x-ph on 2006-01-02
I have a problem installing Ubuntu 5.10 for 64 bit PC on my machine (Dual AMD64 Opteron). When I put the CD and press 'enter' for default instalation the setup stops on the first few lines (detecting IDE Devices or something). I thought there is a problem with the SATA HDD (Seagate 80GB) and tried starting the setup with different commands. I red all the help in F1 menu but still didn't understand most of it. Finally it started when i typed at the 'BOOT:' prompt 'linux noapic acpi=off'. But when the setup completed an error appears on the screen (after the login). The problem is that the Xserver is not running, so I can't run the GUI (my video card is ATI RADEON Saphire). With the live CD the situation is the same. I dont know what to do, this is my first try with linux, I don't know anything about it and this situation really make me confused. I hope someone can help me with this problems. Please explain in the simpliest way you can, because I am not familiar with the linux or programming stuff (and I strongly apologize for my bad english). Thanks in advance :)

---

### Post by kaamos on 2006-01-02
[QUOTE=x-ph]But when the setup completed an error appears on the screen (after the login). The problem is that the Xserver is not running, so I can't run the GUI (my video card is ATI RADEON Saphire). [/QUOTE]

Do you get a to a console login (try pressing ctrl+alt+F1)? If yes, login and try the command
```
sudo dpkg-reconfigure xserver-xorg
```
This could help you find a working configuration for your card.

Hope it works!

---

### Post by x-ph on 2006-01-02
Thanks a lot, unfortunately I can't try this at the moment because the PC is not at my desk. I forgot to write that I get a console login. Do you think the lines I have written after the 'boot:' prompt are ok and won't have problems bacause of them?

---

### Post by kaamos on 2006-01-02
I think those options only control power management, so they probably aren't related to the X error.

---

### Post by x-ph on 2006-01-03
It doesn't work. I tryed all that I could think of but nothing changed. I can't run the X server. It says 'fatal server error: no displays found'. My exact video card model is ATI RADEON Saphire X550 PCI.

---

### Post by kaamos on 2006-01-03
[SIZE="1"](made an ugly typo in the command earlier, now fixed)[/SIZE]

You could try installing ati's fglrx friver. This can be done from the conlsole, but it requires an internet connection. More instructions here: [http://ubuntuforums.org/showthread.php?p=408111](http://ubuntuforums.org/showthread.php?p=408111)

---

### Post by x-ph on 2006-01-03
i dont have internet connection. i'm writing this from a different pc. can i download it here and after that copy it to usb flash drive and install from there?

---

### Post by kaamos on 2006-01-03
Can probably be done. Just a sec. In the meantime, when running "sudo dpkg-reconfigure xserver-xorg", did you try the radeon driver or just only the ati?

And could you also tell me the output of this command:
```
uname -a
```
It spits out the kernel version you have

---

### Post by x-ph on 2006-01-03
uname -a:
2.6.12-9-amd64-generic

i only choose ati driver, there is no radeon option.

---

### Post by dcstar on 2006-01-03
[QUOTE=x-ph]uname -a:
2.6.12-9-amd64-generic

i only choose ati driver, there is no radeon option.[/QUOTE]
Do it again and select the VESA video driver, that should get it going in a basic mode, and you can try and get the right driver later on.

---

### Post by kaamos on 2006-01-03
The vesa driver is indeed a good idea.

For fglrx, you card does not seem o be on the supported list. Maybe the never driver driver from atis site could work though.

---

### Post by x-ph on 2006-01-03
[QUOTE=dcstar]Do it again and select the VESA video driver, that should get it going in a basic mode, and you can try and get the right driver later on.[/QUOTE]
it worked :))))))))))))))))))))))) thanks a lot!!! i'll try to run the internet and then i'll update the driver. real thanks to all

---

### Post by x-ph on 2006-01-03
only one thing - how to configure again the x server?

---

