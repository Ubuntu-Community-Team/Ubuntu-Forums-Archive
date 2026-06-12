---
title: "Unrecognized Device String"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by Tsarevich on 2009-02-19
Please don't point me to another thread because this is a unique case. I installed Kubuntu Intrepid three times. My sda5 is messy. fsck began its never ending check and I was forced to boot up my CRUX and edit the fstab of Kubuntu and to remove that line. But at the same time, I edited its menu.lst of GRUB to add an acpi=force arg, as I do always. But now the message is appearing:

Boot from (hd0,6) and a very long UUID

Error 11: Unrecognized Device String

I am not going to reinstall Kubuntu. I have CRUX CD. Please tell me what to do. I have also removed acpi=force from the menu.lst

---

### Post by cariboo on 2009-02-19
You will have to boot from your LiveCD, if you can't boot into your installation and find out what the uuid of /dev/sda5 actually is. To do this open a terminal and type:

```
sudo blkid
```

Then copy and paste the uuid into /boot/grub/menu.lst. You can also use the uuid to mount the partition in /etc/fstab.

I use uuid as I have have a mixed PATA, SATA system, and at times the device lables change, using the uuid solves the problem.

Jim

BTW: your problem is not as unique as you seem to think it is.

---

### Post by Tsarevich on 2009-02-20
I used the command ls -al /dev/disk/by-uuid to verify all UUIDs. I have also restored the old fstab (genuine one) as well I have removed that <snip> arg from the menu.lst. The system says the same though, when I replace the ROOT=uuid=..... with ROOT=(hd0,6), it starts fine without the bootsplash image until the following message is displayed:

```
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (Did the system wait for the right device?)
  - Missing modules (cat /proc/modules; ls /dev)
ALERT! does not exist. Dropping to a shell!

BusyBox ................
Press 'help' for ..................

(initramfs)

```

Any clue? My system is now configured as it was after the first boot.

BTW: / is sda7. sda5 is the culprit (because of which I edited the fstab out of system).

---

### Post by Tsarevich on 2009-02-21
Anybody?

---

