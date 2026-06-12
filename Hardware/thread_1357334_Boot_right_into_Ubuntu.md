---
title: "Boot right into Ubuntu"
date: 2009-12-17
forum: Hardware
---

### Post by Harrison Pace on 2009-12-17
Is there a way I can boot straight into ubuntu rather than going into the grub menu. I don't really care about memtest and recovery mode. I want to go right to ubuntu! Is that possible :confused: I'm on Grub2 with Karmic using the ext4 file-system. Any help would be appreciated :KS :biggrin:

---

### Post by ricardo.gloe on 2009-12-17
Go to System (should be on top panel), then Start-up Manager and set the timeout to zero. 

This can also be done editing the grub file in /etc/default. 

This way, the menu is not shown and Grub goes directly to your default (there's no way to avoid Grub altogether).  

You can also remove entries from the Grub menu and leave only the one(s) you want (i.e. remove memtest and recovery). 

Memtest can be easily removed by issuing this command in the terminal:

```
sudo chmod -x 20_memtest86+
``` 

Recovery can also be removed by editing /etc/default/grub.

Open the file and find the last line, which read #GRUB_DISABLE_LINUX_RECOVERY="true"

and uncomment (remove the "#")

---

### Post by Harrison Pace on 2009-12-17
> **ricardo.gloe said:**
> Go to System (should be on top panel), then Start-up Manager and set the timeout to zero. 

This can also be done editing the grub file in /etc/default. 

This way, the menu is not shown and Grub goes directly to your default (there's no way to avoid Grub altogether).  

You can also remove entries from the Grub menu and leave only the one(s) you want (i.e. remove memtest and recovery). 

Memtest can be easily removed by issuing this command in the terminal:

```
sudo chmod -x 20_memtest86+
```Recovery can also be removed by editing /etc/default/grub.

Open the file and find the last line, which read #GRUB_DISABLE_LINUX_RECOVERY="true"

and uncomment (remove the "#")
 
Thanks very helpful new to ubuntu forums and for that matter ubuntu altogether anyway can I give you +rep somehow. Only thing Start-up-manager doesn't come pre-installed you must get it from Ubuntu Software Centre. Anyway Thanks and you rock :guitar:

---

