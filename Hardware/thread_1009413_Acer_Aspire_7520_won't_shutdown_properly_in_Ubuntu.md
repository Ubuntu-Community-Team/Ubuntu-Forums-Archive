---
title: "Acer Aspire 7520 won't shutdown properly in Ubuntu 8.10"
date: 2008-12-12
forum: Hardware
---

### Post by CrazymanBrad on 2008-12-12
Hi,

I have an Acer Aspire 7520 with Ubuntu 8.10 (installed from the alternate 64 bit disc image), and when I choose shutdown, it gets almost to a shutdown state, but will not shut off on it's own. 

This is quite inconvenient because I use my laptop for work and battery life is important.  I need to be able to make sure it shuts off completely.  Currently I need to baby-sit the computer until it's almost completely shut-down.

Here's the weird part - if I press the left (Ctrl) key on the keyboard, the laptop powers off.

I did not have this problem in Ubuntu 8.04.

After doing a couple of searches, I was unable to find any information on this issue.  Has anyone else experienced this?

Maybe posts and problems that have solutions should have the means to add it to a "common issues and solutions" section or a sticky added to it.

Thanks in advance for any assistance.

---

### Post by karhulitos on 2009-01-02
Hi,

I have 7520 and very same problem - PC won't power off. If I press any button or even touch touchpad -> off it goes. 32bit 8.10.

Any ideas where to start from?

---

### Post by karhulitos on 2009-01-03
Mine started to work with acpi=force. Not that I like it as all worked fine on Hardy/7520 but this allows me to upgrade now.

```
sudo gedit /boot/grub/menu.lst
```

```

...excerpt from menu.lst file

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		217b274f-a4c6-4df9-92ca-2a92bbd79b52
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=217b274f-a4c6-4df9-92ca-2a92bbd79b52 ro quiet splash[COLOR="Red"] acpi=force[/COLOR]
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

...

```

[COLOR="Red"]No, it does not work. For some reason first shutdown did work but next ones didn't.. :([/COLOR]

---

### Post by karhulitos on 2009-01-15
Hey, I noticed that stopping network from Network Manager lets 7520 to shut down properly. However, the /etc/init.d/alsa-utils -tweak doesn't help either (symptoms changed a bit but still no power off).

This Acer 7520G has Atheros AR5007 chip and I think after the latest kernel update I didn't need to compile any Madwifi things (or somehow last manual driver install was still valid).

Can any of you more experienced point me to right direction now that I noticed net-stop-from-NM appears to let this laptop to power itself down?

---

