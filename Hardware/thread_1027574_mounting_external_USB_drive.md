---
title: "mounting external USB drive"
date: 2009-01-01
forum: Hardware
---

### Post by DOS Chuck on 2009-01-01
To begin with, here's my system:
   Soyo Dragon Pentium 4 overclocked to 3.04Ghz,1G RAM
   drive c: Maxtor 320Gb w/WinXP
   drive d: Seagate 160Gb empty
   drive g: Maxtor 120Gb (RAID) w/Ubuntu 8.04
   drive e: DVD/DC/RW 
   drive f: CD/CDRW
   drive h: Maxtor 3200 USB external

During the boot sequence, I can see that all the drives are being found and recognized. Once Ubuntu finally boots, it takes an HOUR to find the USB drive. Also, the optical drives aren't available until the USB drive is mounted.

I have researched and read all I can find on Linux forums and have done everything suggested. I have re-installed Ubuntu 3 times. It flat refuses to install on my d: drive. Why?

I tried entering mounting information in the drive properties window for the USB drive and now it won't mount at all. How do I change that?

How do I update driver "SD" and "SR" (error messages I see during verbose booting) and what is "bus_type methods"?

Please, help. I really like the rest of Ubuntu. I tried Mandriva and it works, first time, everytime. But, it's sluggish, just like WinXP. I just don't like it.

Any suggestions would be greatly appreciated.

TIA

---

### Post by Tomatz on 2009-01-01
Sounds like a hal (hardware abstraction layer) problem. Which version of ubuntu are you using?

EDIT duh 8.04 (as said)

---

### Post by DOS Chuck on 2009-01-01
Yes...8.04

For whatever reason, I can't install 8.10. I've downloaded and burned it twice (GOOD media) but it just runs forever checking "ata1:00.............

---

### Post by Tomatz on 2009-01-01
Download the following .deb, install it and see if the problem persists:

[http://launchpadlibrarian.net/15194224/hal-info_20080508%2Bgit20080601-0ubuntu0.8.04_all.deb](http://launchpadlibrarian.net/15194224/hal-info_20080508%2Bgit20080601-0ubuntu0.8.04_all.deb)

All dependancys should already be met. All it contains are files hal can use to better detect hardware.

---

### Post by DOS Chuck on 2009-01-01
If it's a HAL problem (I'm sorry,Dave...) wouldn't reformatting and reinstalling have fixed that? I haven't seen anything about hal bugs. Are there? Anyway to fix it or upgrade it?

---

### Post by DOS Chuck on 2009-01-01
Ok, just tried it....the package manager says I have a later version already installed.

---

### Post by Tomatz on 2009-01-01
LOL dave ;)

I just had a google and found a simelar problem to yours. If you edit the boot line in your grub config file (boot/grub/menu.lst) to disable hpet support hopefully it will solve the issue.

The boot line should look something like this:

> title Ubuntu intrepid, kernel 2.6.27-4-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.27-4-generic root=UUID=75ffa061-25f6-44b8-ac61-07452816b281 ro quiet splash **[COLOR="Red"]hpet=disable[/COLOR]**
initrd /boot/initrd.img-2.6.27-4-generic
quiet

Note the [COLOR="Red"]hpet=disable[/COLOR] in red. This is how you should edit yours ;)

---

### Post by DOS Chuck on 2009-01-01
Do that as soon as it starts to boot? When I have the option to edit or whatever?

---

### Post by DOS Chuck on 2009-01-01
Found it....edited it...let's try it. I'm rebooting.

---

### Post by Tomatz on 2009-01-01
Did it work? If you are now having problems booting. You can edit the line (temporarily) from grub (bootloader) by pressing **E**.

---

### Post by DOS Chuck on 2009-01-01
OK...I get "Cannot mount volume" details...mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)

I'll try editing the GRUB next

---

### Post by thomas228 on 2009-01-01
> **DOS Chuck said:**
> To begin with, here's my system:
   Soyo Dragon Pentium 4 overclocked to 3.04Ghz,1G RAM
   drive c: Maxtor 320Gb w/WinXP
   drive d: Seagate 160Gb empty
   drive g: Maxtor 120Gb (RAID) w/Ubuntu 8.04
   drive e: DVD/DC/RW 
   drive f: CD/CDRW
   drive h: Maxtor 3200 USB external

During the boot sequence, I can see that all the drives are being found and recognized. Once Ubuntu finally boots, it takes an HOUR to find the USB drive. Also, the optical drives aren't available until the USB drive is mounted.

I have researched and read all I can find on Linux forums and have done everything suggested. I have re-installed Ubuntu 3 times. It flat refuses to install on my d: drive. Why?

I tried entering mounting information in the drive properties window for the USB drive and now it won't mount at all. How do I change that?

How do I update driver "SD" and "SR" (error messages I see during verbose booting) and what is "bus_type methods"?

Please, help. I really like the rest of Ubuntu. I tried Mandriva and it works, first time, everytime. But, it's sluggish, just like WinXP. I just don't like it.

Any suggestions would be greatly appreciated.

TIA

Hi

Realative newbie here so disregard if you want

When I installed 8.04 onto a bootable 8GB thumb I ran into a problem of not being able to load my laptop hard drive ubuntu because as it turned out I had edited out it's UUID on my thumb's menu.lst.

Part of your problem (at least for your usb drive) may lie in your ubuntu's menu.lst

Posting menu.lst may shed more light but I'm not sure how as I was trying to boot into my laptop's harddrive from a thumb grub


Good luck
Tom

---

### Post by DOS Chuck on 2009-01-02
Well, so far no change. I still have to wait an hour after re-booting for the external drive to show up and I still get the error message about being unable to mount the drive.

Once, and only once,the external drive AND both of the IDE drives showed up, immediately after rebooting. ONCE. It's never done that since.

Whatever changed when I entered the mounting options on the drive's property page is still there and causing the error message. I don't know what file got changed or I'd change it back.

---

### Post by Tomatz on 2009-01-02
Hmmm its defiantly a hardware problem (i don't think its a config problem). This may sound stupid but what happens if you boot with a CD in the drive?

Also can you post the contents of ***/etc/fstab*** and the output of ***sudo fdisk -l***

---

