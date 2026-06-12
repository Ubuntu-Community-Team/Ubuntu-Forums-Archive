---
title: "Wifi not working after update"
date: 2017-10-05
forum: Hardware
---

### Post by Romulo Carlos on 2017-10-05
I have a weird problem here, and I have no idea how to solve it ...


I have an HP Pavilion DV2000 notebook, somewhat limited hardware. My intention is to have only Kodi and VLC in it, nothing more. But for both, I need **WIFI** internet connection. The wired network card is defective.


The wifi card is model **Intel PRO / Wireless 3945ABG**. Well, I installed Ubuntu 14.04 LTS on it, and everything was normal, until a warning appeared that there were some updates. So, I installed all, it asked to restart, I rebooted. When it came back, no more wifi! NONE! A warning appears saying that the wifi card is disabled by hardware, but I did not even touch the physical key of the wifi, which is in front of the note. To try to solve it, I plugged a USB-WIFI adapter in the note, and to my surprise, it also appears as "hardware disabled" once it's plugged in! The adapter has NO key!


Well, not satisfied, I searched for another Ubuntu distro, and decided to use Ubuntu Minimal, because is lightweight and I can build a system form almost zero. So, I downloaded Minimal 16.04, rebooted with the DVD and installed it, erasing all the HD (I do not need backup). During installation, it detected the card normally, asked the wifi network to be used, asked for a password, and installed everything normally. After installation and restart, almost the same thing happened, including the USB adapter: the wifi card does not appear. 'ifconfig' only shows loopback interface.


Searching around, I found some commands with rfkill for start, but when trying to use it, a message appears saying rfkill is not installed. And since I do not have a wired network on the notebook, I can not install it or use the USB adapter.


What more can I try to do here?

I also have a DVD and a ISO with Ubuntu 16.04 LST (not the Minimal), but want to use Minimal. Thanks in advance!

---

### Post by Autodave on 2017-10-05
While this may not help at all, it will not cost anything but 10 minutes of your time. I repair computers on the side and this fixes quite a few of them that I get:

   1. Power down and disconnect power cord.
2. Unplug all peripherals.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. If good so far, now you can reconnect peripherals.

---

### Post by ajgreeny on 2017-10-05
See **Wireless-info** in my signature and run the script then report back the output here or using [pastebin]("http://pastebin.ubuntu.com/") if the output is too large.

---

### Post by Romulo Carlos on 2017-10-05
> **Autodave said:**
> While this may not help at all, it will not cost anything but 10 minutes of your time. I repair computers on the side and this fixes quite a few of them that I get:

   1. Power down and disconnect power cord.
2. Unplug all peripherals.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. If good so far, now you can reconnect peripherals.

Thanks. Is a very simple notebook. It don't have peripherals, the battery is very old, so I removed it and use it only with ac power. But I turned it off for about 10 minutes, and turn it on. No go.

> **ajgreeny said:**
> See **Wireless-info** in my signature and run the script then report back the output here or using [pastebin]("http://pastebin.ubuntu.com/") if the output is too large.

Thanks, too. Tried to run your script, but no success. As I don't have a connection, I saved it to a pendrive, copied it into my Dowloads folder, and try 'sh wireless-info': it gives me an error 'Syntax error: "(" unexpected'. If I try to change the permissions with 'chmod u+x' and run, it gives the error 'invalid intepreter: file or folder not found'.

---------------------------

An update:

I get an USB-ETHERNET adapter, and it works. So, I installed rfkill and xubuntu-core^. Here is some results without the adapter, maybe usefull, based on some search:

rfkill list all:
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

lsmod | grep hp:
```
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
shpchp                 32768  0
wmi                    20480  1 hp_wmi

```

lsmod | grep iwl:
```
iwl3945                65536  0
iwlegacy               90112  1 iwl3945
mac80211              659456  2 iwl3945,iwlegacy
cfg80211              499712  3 iwl3945,iwlegacy,mac80211

```

lspci:
```
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
    Subsystem: Hewlett-Packard Company PRO/Wireless 3945ABG [Golan] Network Connection
    Physical Slot: 5
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at f4200000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945

```

Also tried 'sudo service network-manager restart', 'rfkill unblock all', and others withou success.

UPDATE 2: tried with another card, same problem. Is a software problem, since this card works on 14.04 without updates!

---

### Post by Romulo Carlos on 2017-10-05
SOLVED!! At least, I think is...

After some research, I ran the command:

sudo modprobe -r hp_wmi

3 seconds after, I can see available networks and can connect with it, and access internet. But after a reboot, the problem returns. How I can change this?

---

### Post by ajgreeny on 2017-10-06
You needed to run that script using its full pathway so in terminal use command ```
./Downloads/wireless-info
``` to specify the Downloads folder and it should then run fine.

It may still help our wifi experts (probably not me) to see the full output you get from that.

---

