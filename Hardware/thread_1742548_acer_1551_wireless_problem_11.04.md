---
title: "acer 1551 wireless problem 11.04"
date: 2011-04-29
forum: Hardware
---

### Post by Halo.Light on 2011-04-29
I installed Ubuntu 11.04 on my acer 1551-4650 and can't get my wireless to work. when i enter lshw -C network it says

description: Wireless interface
product: BCM43225 802.11 b/g/n
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:06.0
logical name: eth1
version: 01
serial: c4:46:19:5e:f2:a8
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency
resources: irq:17
memory: d0300000-d0303fff

when i look at rfkill list it tells me

0: brcmwl-0: Wireless LAN
          soft-blocked: no
          hard-blocked:no
1: acer-wireless: Wireless LAN
          soft-blocked: yes
          hard-blocked: no
I tried rfkill unblock all , rfkill unblock 1 and tried them both again with sudo in front but it wont unblock. any help would be greatly appreciated

---

### Post by joshzam on 2011-04-29
My Acer Extensa 5620 laptop's wireless wouldn't connect after my 11.04 upgrade, either. After much searching, here's what worked for me:

1. Go to the Terminal and type sudo gedit /etc/NetworkManager/NetworkManager.conf  (or sudo vim /etc/NetworkManager/NetworkManager.conf)
2. A window would now popup displaying the contents of the NetworkManager.conf
3. Change “managed=false” to “managed=true“
4. Save the file and exit gedit (or vim/vi)
5. Reboot your machine
6. Connect to your wireless network and enjoy!

---

### Post by Halo.Light on 2011-04-29
Didn't work :( i tried doing it again after rebooting and it said "Managed=true" so i guess that isn't the reason my wireless wont work

---

### Post by angelsneverdie on 2011-04-30
I'm having the same problem with  my sony vaio y series.  worked fine until i did a clean install of 11.04 and wireless doesn't work.  under rfkill it lists acer wireless as being softblocked and the unblock command doesn't change anything.   i also tried the method suggested by joshzam with no luck.  I'd really appreciate any help on this.  fyi, in the network indicator at the top of the screen it will let me "enable wireless" but it always says above that "wireless is disabled"

---

### Post by angelsneverdie on 2011-05-04
I found a solution that worked for me, you might want to look it over:

[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/155219](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/155219)

---

### Post by Halo.Light on 2011-07-15
Holy cow it worked! I had given up on linux for my laptop and for some reason I decided to try again and blacklisting acer_wmi works. Thanks everyone for your help

---

