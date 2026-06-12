---
title: "I Had to mess with it!"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by OnlyTim on 2009-08-19
Hey all, I  installed the grub2 package from synaptic and did a reboot. All seemed well. It showed the proper grub screen with my option of chain-loading.

I selected chain-load but recieved an error. The one thing I noticed was it no longer showed my Ubuntu versions, but rather, Debian versions in the grub menu. 

Now I can't get back into Jaunty 9.04 at this point and used the live cd to get access to this forum. Is their a way to recover my old grub or do I have to reinstall everything.

I use a second hard drive for Ubuntu. The 1st for XP. 

Any ideas?

Thanks

---

### Post by OnlyTim on 2009-08-19
OK, just a follow up. I discovered that the synaptic install of Grub2 removes grub. That may be why it doesn't see my original generics.

---

### Post by presence1960 on 2009-08-19
I would try this: boot into recovery mode. Be patient as all the text scrolls on your screen, let it finish. Then scroll down the menu and choose command prompt with networking. Run ```
sudo apt-get remove grub2
```
When complete run ```
sudo apt-get install grub
``` When complete type exit or quit then choose resume normal boot and see what happens.

or you can try those commands from terminal from the Live CD desktop

---

### Post by OnlyTim on 2009-08-19
Thanks for the comeback. I tried a reboot and the recovery option, but still get the error:  " ERROR 11 Unrecognized device string" I get that response on all generics listed. The Windows loader still works.

Here is the string that doesn't work.

Debian GNU/Linux,Kernel 2.6.28-15  It looks like the correct Kernel, but wont load.

Does the Live CD have a recovery option in the install mode?

Thanks

---

### Post by presence1960 on 2009-08-19
> **OnlyTim said:**
> Thanks for the comeback. I tried a reboot and the recovery option, but still get the error:  " ERROR 11 Unrecognized device string" I get that response on all generics listed. The Windows loader still works.

Here is the string that doesn't work.

Debian GNU/Linux,Kernel 2.6.28-15  It looks like the correct Kernel, but wont load.

Does the Live CD have a recovery option in the install mode?

Thanks

Boot the Live Cd and when desktop loads use terminal to run those commands in post #3

---

### Post by OnlyTim on 2009-08-19
Okay, I tried that, and I got this message: "Grub2 not installed, so not removed." I did find the grub edit command when I did a reboot without the live CD. Can I some how make changes there?

As you can see, I'm really new to Linux and appreaciate your help.

---

### Post by OnlyTim on 2009-08-19
[B] I found this thread in the forum that focused on my problem.

[https://wiki.ubuntu.com/KernelTeam/Grub2Testing](https://wiki.ubuntu.com/KernelTeam/Grub2Testing)

[/B]I was able to edit the chain loader changing the boot line from Root to UUID. That did it as I was able to load Ubuntu. I removed grub2 and re-installed grub but find I still have to edit the grub from root to uuid to access at startup.

---

### Post by OnlyTim on 2009-08-19
[[ubuntu] Grub 2 Error 11 - Page 3 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1022594&highlight=grub-pc&page=3") 

sudo update-grub2

sudo upgrade-from-grub-legacy

sudo update-grub

I found the three above cmds on a thread addressing error 11 on grub2. It did the trick.
Grub2 now works and it recognized my generics.

---

