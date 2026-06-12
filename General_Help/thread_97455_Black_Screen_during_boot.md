---
title: "Black Screen during boot"
date: 2005-12-01
forum: General Help
---

### Post by fweez on 2005-12-01
I get to load Ubuntu. the splash screen comes on, and then after a while it goes into text mode when it sets my system clock. The system still continues to load after that though until it reaches to "HP Printing and Imaging Manager" then the screen goes into a black screen with nothing on it except a white cursor which is not moving at all. The screen just freezes there and I cannot do anything. Any suggestions? Thanks

---

### Post by r0ll3r on 2005-12-01
I have just ideas, not solutions. I assume you boot with quiet and splash kernel options, so that way (i don't know, but maybe) it is possible that fsck (file system check) is running on your harddisk. Check if your hdd led is blinking or can you hear your hdd working?

If not, try booting in single user mode (choose recovery mode) from grub.

If even that fails, try hitting ctrl+alt+f2 (virtual console) when screen goes blank. Try to log in and investigate the logs if possible.

If all these fails, you need a live cd or anything to boot, and mount your filesystem, and check the logs that way. There should be a trace of your problems in the logs.

---

### Post by fweez on 2005-12-02
my hdd led is not blinking at all and there isnt any sounds coming from the cpu. I tried booting using the recovery mode as u suggested and i got it up till a root@ubuntu or something like that but have no idea what to type in next. 

Then i tried hitting ctrl-alt-f2 when the screen goes blank but nothing happens. the screen just freezes at that point.

I also tried using the Live CD and it ran fine until it reached the same point and the black screen came out again with the frozen white cursor. I tried tapping ctrl-alt-f2 but nothing came up as well.

Any other suggestions? So far I've got no other devices plugged in except for my keyboard and mouse which are both using PS/2 ports and of course the cable to the monitor. I'm running on a P3 600mhz with 128MB of RAM with a S3 Savage PCI 3D card. Thought the extra details might help.

---

### Post by r0ll3r on 2005-12-30
hi fweez,
sorry for the long delay, i don't know if you are still having this problem or not.
If the recovery mode works (as you said so), it means, your system is mostly ok.  At the root prompt you can investigate things better. At least you have the console to check out logs.
```
less /var/log/syslog
```
Scroll down to see the last messages, search for errors and warnings.
Also you can try running
```
gdm
```
to start the gnome by hand.

---

