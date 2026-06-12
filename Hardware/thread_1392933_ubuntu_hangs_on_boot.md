---
title: "ubuntu hangs on boot"
date: 2010-01-28
forum: Hardware
---

### Post by dmcfarland on 2010-01-28
I am getting dumped out to a prompt when I enable an extra hard drive or when I installed an USB card. Its says something about a timeout, and I have to CTRL+ALT+DEL to reboot. I am up and running now but I had to remove the card. 

Heres some of the messages I get.
"Gave up on waiting for root device"
"Busybox v1.13.3 (Ubuntu 1:1.13-3-1Unbuntu7) built in shell ash"
"Alert /dev/sdc1 does not exist"

Is there something I can do to fix that or is ubuntu just a buggy touchy linux distro?

---

### Post by quixote on 2010-01-29
Sometimes if boot media take a long time to come up, grub can lose interest.  That sounds like what happens in your case.  

In old-grub, you can add "rootdelay=XX", where XX is time in seconds, to the kernel line in /boot/grub/menu.lst.  If you're using Karmic, and hence Grub2, you'd need to look up what the new syntax is.

Eg in old grub (taken from [this comment]("http://www.uluga.ubuntuforums.org/showpost.php?p=6728885&postcount=5")):```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		00ad768f-79cf-48da-bc63-6fe5fab4a8a1
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=00ad768f-79cf-48da-bc63-6fe5fab4a8a1 ro quiet splash **rootdelay=90**  
initrd		/boot/initrd.img-2.6.27-11-generic
quiet
```

---

### Post by dmcfarland on 2010-02-01
> **quixote said:**
> Sometimes if boot media take a long time to come up, grub can lose interest.  That sounds like what happens in your case.  

In old-grub, you can add "rootdelay=XX", where XX is time in seconds, to the kernel line in /boot/grub/menu.lst.  If you're using Karmic, and hence Grub2, you'd need to look up what the new syntax is.

Eg in old grub (taken from [this comment]("http://www.uluga.ubuntuforums.org/showpost.php?p=6728885&postcount=5")):```
title        Ubuntu 8.10, kernel 2.6.27-11-generic
uuid        00ad768f-79cf-48da-bc63-6fe5fab4a8a1
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=00ad768f-79cf-48da-bc63-6fe5fab4a8a1 ro quiet splash **rootdelay=90**  
initrd        /boot/initrd.img-2.6.27-11-generic
quiet
```

I found the appropriate file to edit and that worked like a charm. Now the USB card is causing the system to hang on boot. However I don't know if its the card or the devices attached to it. Ill look into it later.

---

