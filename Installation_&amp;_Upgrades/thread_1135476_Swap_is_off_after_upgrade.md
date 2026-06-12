---
title: "Swap is off after upgrade"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by epirsch on 2009-04-24
Hi,

I upgraded to 9.04 last night and it went really smoothly. This morning, I tried some of the things that where not working with 8.10, notably suspend and hibernate (using nvida).

Suspend to ram work perfectly. However, when I tried hibernate, the system froze with a blinking cursor.

After a reboot, I checked my swap file and it is off! I guess this is why Hibernate is not working. I turned it on using gparted and tried to hibernate again (without rebooting first). The system actually shutdown instead of hibernating and upon reboot, the swap is still off.

How to I permanently enable the swap partition?

Thanks!

---

### Post by logos34 on 2009-04-24
sounds like swap got formatted in the upgrade, which means the uuid changed.

compare

sudo bklid

to that for swap entry in /etc/fstab

---

### Post by epirsch on 2009-04-24
I don't have bklid on my system, but using gparted I did found out that the UUID for the partition is different than the one in fstab.

I guess I should just copy the one from gparted into fstab? or is there a better way to do it?

---

### Post by logos34 on 2009-04-24
yep, just copy it

gksudo gedit /etc/fstab

You can also crosscheck with these:

ls -l /dev/disk/by-uuid

vol_id -u /dev/sdax

(although they may still show the old uuid)

---

### Post by drs305 on 2009-04-24
> **epirsch said:**
> I don't have bklid on my system, but using gparted I did found out that the UUID for the partition is different than the one in fstab.

I guess I should just copy the one from gparted into fstab? or is there a better way to do it?

Yes, copy the results to fstab using a root editor (for example: gksudo gedit /etc/fstab ).

"sudo blkid" should give you the UUIDs of all your devices. It's a system process so it should be available - just use "sudo" with it. You can also "ls -la /dev/disk/by-uuid"

You should also update the resume file if the UUIDs don't match:
```
gksu gedit /etc/initramfs-tools/conf.d/resume &
sudo update-initramfs -uk all  # Creates new /boot/initrd.img-2.6...
sudo swapon -a    # Restore swap with new fstab settings
free -m   # Check swap

```

---

### Post by epirsch on 2009-04-24
Thanks... Swap is now enabled across reboot.

However, hibernate is still not working and hangs with a blinking cursor. I do have enough swap space (4G vs 3.2G of availlable system memory)

---

### Post by epirsch on 2009-04-24
Ok, **logos34** wrote bklid instead of blkid... I do have blkid and it display my filesystems UUID without any issue.

I also did the steps you mentionned. Rebooted just to make sure everything was ok. Everything is OK with the exception of hibernate still hanging with a blinking cursor (when hibernating). when I select Hibernate, the screen switch to black, the hardrive light blink for a few seconds and then nothing.

---

### Post by logos34 on 2009-04-24
> **epirsch said:**
> Ok, **logos34** wrote bklid instead of blkid... I do have blkid and it display my filesystems UUID without any issue.

I also did the steps you mentionned. Rebooted just to make sure everything was ok. Everything is OK with the exception of hibernate still hanging with a blinking cursor (when hibernating). when I select Hibernate, the screen switch to black, the hardrive light blink for a few seconds and then nothing.

oops, sorry about the typo

The only mention of hibernation issues in release notes concerns automatic partitioner making smaller-than-ram swap.  But yours is 4 gb.  And no 9.04 hibernation bugs yet reported over at launchpad

hmm

Personally, I've had issues with suspend and hibernate periodically over nearly every release.  Right now on 8.04 Hardy LTS both work (*most *of the time, I should say)

---

