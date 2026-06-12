---
title: "upgrade failure stoping boot ver 8.10"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by westconn1 on 2009-03-22
i am pretty (very) new to ubuntu, ihave just done a live cd install from downloaded cd image
the installation worked ok, 

screen saver came on during upgrade, but on activation after screensaver stop the computer was frozen, had to reboot

now i get error on boot **Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(0,0)** machine just hangs then

i can just reinstall and make sure to disable screen saver, then see what happens but seems like some problem should be resolved, and to learn how to fix (if it can be fixed)

i can boot from the live cd, but not sure where to go from there

---

### Post by cariboo on 2009-03-22
Have you tried booting in recovery mode? IF you can, once at the menu choose drop to root prompt and type:

```
apt-get update && apt-get dist-upgrade
```

---

### Post by tommcd on 2009-03-22
Can you boot to recovery mode? When the system boots you will see the grub menu. If you fo not see the grub menu, then as the system boots hit the **Esc** key to see the grub menu. Use the arrow keys to select the recovery mode option. When you get to recovery mode you will have a root terminal. Run this command:
> sudo apt-get update
sudo apt-get dist-upgrade
If that doesn't work the boot to recovery mode again and run:
```
sudo update-initramfs -k all -u
```
Then reboot and see if you can boot Ubuntu the normal way.

If you can not get to recovery mode, or this does not work, then write back and we will see if we can fix it from the live CD.

I always disable the screen saver (just set it to blank screen) for this (and other) reasons.


And welcome to the Ubuntu forums!

---

### Post by westconn1 on 2009-03-23
can not get to recovery console for the latest version (2.6.27-11) in the recovery menu, but can for previous (2.6.27-7), however running the get-update command, resulted in dns errors, the update-initramsfs, appeared to work, but the problem remained the same

i got these errors trying to get into the recovery console for later version
cannot open root device UUID=9b76aadf-da92-44d9-825f-29fcde-906b85 or unknown block (0,0)
please append a correct "root=" boot option; here with available partitions
kernel panic - not syncing VFS unable to mount root fs on unknown block(0,0)

and thnx for the welcome

update
i have now managed to change the grub menu file so the default is to boot into the previous version, so at least it starts up and runs, but how to fix properly?
i turned the screen saver activation off as blank screen still seemed to be an issue

---

### Post by westconn1 on 2009-03-23
thnx guys once i found out how to get into the boot menu i was able to sort out all the problems, finish the upgrade, just took a while to figure

all seems fine at this point, but i am sure i will be back............

---

