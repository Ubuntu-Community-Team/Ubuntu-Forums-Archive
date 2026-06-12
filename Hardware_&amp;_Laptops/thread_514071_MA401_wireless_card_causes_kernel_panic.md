---
title: "MA401 wireless card causes kernel panic"
date: 2007-07-31
forum: Hardware &amp; Laptops
---

### Post by dlublink on 2007-07-31
My problem may be related to this site:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/95817](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/95817)



Hello,

I have a laptop that I just installed with the latest Ubuntu release (7.04) and immediately updated all the packages (100 updates!).

I have a MA401 wireless card plugged into the laptop, if I boot with the card plugged in the computer will have a Kernel Panic (although I will only see this information if I do ALT+F1 before it panics otherwise the splash screen simply freezes).

If I plug the card into the computer after the computer boots, it seems to mostly work. I can see wireless access points ( I wasn't able to connect last night, but it might have been my router acting funny).

I tried to find a graphical tool to manage my wifi connection and in 'Supported Ubuntu applications', I found nothing for my search 'wifi'. In unsupported I found wifi-radar. 

What is the Ubuntu way of managing wireless network connections?
( [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo) makes reference to a System->admin Networking , but I only see network and network tools. Network seems to allow me to control my networking devices, but I don't see how I would save a WEP or WPA key like I would in Windows XP.)

What is the best way to use WPA on ubuntu? (I did not see WPA in System->admin->network. When I was using Gentoo, I use wpa_supplicant. Is the Ubuntu network interface compatible with WPA Supplicant?)

Why does my kernel panic with the ma401 card? (It ran fine using 2.6.19, 2.6.20, 2.6.21 on Gentoo). Could it possibly the ubuntu patchset?

Thanks,

David

---

### Post by dlublink on 2007-07-31
Btw, other hardware on my computer that took 3-6 months to get working on my gentoo linux, just work on ubuntu.

Also, I noticed that on both ubuntu and gentoo, my wireless card is seen as wifi0 (which seems to be an invalid interface since the hardware address is wrong and it never seems to have an IP) and another interface(wlan0 on gentoo, eth1 on ubuntu).

Does anyone know why it has two interfaces for the same card ?

Thanks,

David

---

### Post by dlublink on 2007-07-31
Looks like it is happening during a modprobe :

Here is part of the panic

[22.980000] Modules linked in: hostap_cs hostap ieee80211_crypt snd_maestro3 ...
[22.980000] Process modprobe (pid: 3599, ti=ccb2a000, task=cfa70a70, task.ti=ccb2a00)

Also included is a stack with a lot of hexidecimal numbers in a call trac:

do_IRQ+0x40
common_interrupt+0x23/0x30
delay_tsc
__delay
pcmcia_request_configuration
hostap_cs_probe
psmouse_interrupt
__activate_start
__switch_to
pccard_get_next_tuple
PCCARD_GET_TUPLE_DATA
pcmcia_device_probe
really_probe
driver_probe_device
__driver_attach
__bus_for_each_dev
driver_attach
__driver_attach
bus_add_driver
sys_init_module
register_netdevice
sysenter_past_esp

Code: Bad EIP value
EIP: [<00000000>] 0x0 SS:ESP 0068:ccb2babc

I am trying to get my hands on a serial cable so that I can output the panic to another computer and post the full panic in the forums.



Thanks,

David

---

### Post by dlublink on 2007-07-31
In the bootup sequence, the message appears shortly after the 'Loading hardware drivers' line.

Loading hardware drivers seems to be part of the udev service. I restarted the service with the card plugged in and it didn't crash. Still looking...

---

### Post by dlublink on 2007-07-31
Ok.

I found that in the script /etc/init.d/udev there is a line like this:

/sbin/udevtrigger

That command is calling something that causes the kernel panic. I disable this line, my computer boots (but all the hardware is messed up). After it boots, I enter this command, the command completes but shortly afterwards (2 or 3 seconds) the machine does a kernel panic.

Now that I am able to trigger the kernel panic from a booted system, is there anyway to store the output to the disc?

David

---

### Post by dlublink on 2007-07-31
Still trying to figure this out. Anyone else have any ideas?

Currently I am trying to use kexec to catch the output, but when I load the kernel using kexec -p kernel-name, it says it cannot find 9000 bytes of free memory.

I typed 'init 1' to switch to single user mode, there is almost nothing left running.

Top says:

152,136k used
103,948k free
15,208k buffers
117,916 cached

Which means, there is really only 19,012k used out of 270,052k of memory.

How is it not able to find 9,000 bytes of memory when there is 250 megabytes of free memory?

I am confused...

David

---

### Post by dlublink on 2007-07-31
I upgraded to Ubuntu 7.10 ( Gutsy ) and I am experiencing the same problem.

Anyone have any idea?

David

---

### Post by lo_toad on 2008-01-29
hi, I had exactly the same problem in xubuntu Gutsy and solved it by adding 'hostap_cs' to the /etc/modprobe.d/blacklist .

Just add "blacklist hostap_cs" to the end of the file and it will use the Orinoco driver instead.

Hope this helps.

James.

---

### Post by lo_toad on 2008-01-29
Hi,

Sorry Ive just seen somewhere else that you sorted it!! :)

J

---

