---
title: "Can't boot after after update"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by wah fun on 2009-10-21
I am running 9.04 and let the system update. After that, I could no longer boot into ubuntu. I get an "error 11: unrecognized device string"

I have reinstalled 9.04 and before I let the system update again I thought perhaps someone could tell me if there is a problem with the updates or what I can do to ensure I can boot after the update.

Thx in advance for your help.

---

### Post by stlsaint on 2009-10-21
it appears that something went wrong with your menu.lst or partitions. You should be fine with updating this go around. I used to get that error when editing the menu.lst and adding a wrong structured stanza for windows. I wouldnt know why you would get it off updates. make sure that you are not trying to do an UPGRADE.
only use the update cmd when in terminal:

```
sudo apt-get update
```


also you can always get back to your filesystem using the livecd should you not be able to boot for some reason.

---

### Post by ColdFFF on 2009-10-21
"error 11: unrecognized device string" is a grub error message.

I think the most likely reason this happened is that when the system performed the update, it downloaded a new kernel and modified grubs menu.lst to use it.

Personally, I find letting it automatically update this file causes problems (multiboot machine), so I opt to modify it myself. **NOTE: This isn't the hardest thing to do, but messing this up will also cause grub errors**

To do this, when asked whether to keep the existing menu.lst or use the updated menu.lst, I keep the old one and gedit /boot/grub/menu.lst

Then I find the options, which look like:

```
title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		1093c86c-436a-4c52-98db-ea976cc433e5
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=1093c86c-436a-4c52-98db-ea976cc433e5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet
```

and change the kernel number to reflect the latest downloaded version like:
```
title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		1093c86c-436a-4c52-98db-ea976cc433e5
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=1093c86c-436a-4c52-98db-ea976cc433e5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet
```

This way it doesnt change the uuid by accident and shouldnt cause any problems. To find the latest kernel version I just look for the highest number of vmlinuz-xxx-generic in /boot/

---

### Post by wah fun on 2009-10-21
Thanks to all. Keeping the current menu.lst did the trick.

---

