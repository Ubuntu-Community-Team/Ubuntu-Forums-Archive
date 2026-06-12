---
title: "pcmcia problem with ibm t20"
date: 2005-11-26
forum: Hardware &amp; Laptops
---

### Post by Krash1201 on 2005-11-26
I have been trying to install a wifi card on my t20, using the dlink dwl-650 rev. M.  No problems with ndis wrapper at this point, the drivers are installed, and it sees the hardware, but i can't get Kubuntu to bring up wlan0.  After ifconfig, i only get eth0 and l0, same thing with iwconfig.  When i sudo ifup wlan0 i get "Ignoring unknown interface wlan0=wlan0.  The odd thing is that lspci lists the wifi card.

Any idea how to fix it?

---

### Post by Lambert on 2005-11-26
When you run lspci that's just a hardware layer command. It sees the device connected and can give basic information about the device.

When you run ifconfig and iwconfig and it doesn't show the device this is on a function layer where the driver is needed so the os and hardware actually communicate. Because you don't see any output showing a wlan0 device that tells me the driver is not functioning properly.

The most common problems I see in this case with ndiswrapper.
 
1. Incorrect driver was used. Go [here ]("https://wiki.ubuntu.com/forum/hardware/ndiswrapper?highlight=%28ndiswrapp%29")and read the section step 2

2. When the driver was installed it needs to be done from a directory on the harddrive and any .sys files need to also be in that directory as well as in some instances the .sys and .inf files are linked in some manner.

3. ndiswrapper is used prematuraly as the device has a native linux driver and it's loaded at the same time the ndiswrapper module is loaded so there is a driver conflict happening.

If you have done these then there is a problem somewhere else but your problem is in a non functioning driver.

There is a link to a wirelesstroubleshooting guide in my signature. You might be able to find more there.

---

### Post by Krash1201 on 2005-11-26
Thanks Lambert, i acutally used those pages to set up the the driver in ndiswrapper.  Ends up it was the drivers, used the ones from the oem install disk instead of what i downloaded off the web, also removed the linux-wlan-ng drivers to avoid any conflict.  Fired up just fine.  Now hte problem i have is accessing my network.  The SSID on my network is hidden, and even with the ssid in a config preset in kwifi manager it still isn't connecting.  Any ideas?

---

### Post by jrei on 2006-06-03
Hi,

I also have the problem with an orinoco card. It always worked with selfmade vanilla kernels, without any fancy NDIS drivers.

But I have further problems with the PCMCIA slots.
Using a PCMCIA adapter for CF Cards no storage is opend.
So I checked the "/var/log/syslog" and it tells me that he found a mass storage device and tries to use it as "/dev/hde" but then it looses the interupt.
1. If I then unplug the PCMCIA adapter and insert it a again, the system is frozen. 
2. If I then unplug the PCMCIA adapter and insert it into the second PCMCIA slot
I can access the data, but if I eject the device to remove the PCMCIA adapter the system freezes again.

Still searching for the reason.

Greetings, Jörn

---

### Post by jrei on 2006-06-03
update:

my kernel parameter changes are now
```

# kopt=root=/dev/hda2 ro acpi=off noapic

# defoptions=quiet resume=/dev/hda3

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro acpi=off noapic quiet resume=/dev/hda3 
initrd          /boot/initrd.img-2.6.15 -23-386 
savedefault
boot

```

And currently I don't have any freezes oder problems to get wifi or mass storage accessed. :) :cheers:

The last thing I changed was to turn off the FB use on boot removing the 'splash' parameter from the kernel params. But I think nothing good came from that 'apic' so 'noapic' is fine for me. Actualy I think it is turned off anyhow if the kernel tries to load acpi and recognizes that it is disabled from kernel params. So turning it of definately does no harm.

Hope I could help.

Greetings, Jörn

---

### Post by jrei on 2006-06-03
Ok, I have to correct myself.

Allot of harm comes from 'noapic'.
The integrated LAN of the T20 didn't work any more. 
I put it back again and it worked again.

---

