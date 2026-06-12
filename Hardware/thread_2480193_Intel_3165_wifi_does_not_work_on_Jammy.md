---
title: "Intel 3165 wifi does not work on Jammy"
date: 2022-10-22
forum: Hardware
---

### Post by johnaaronrose on 2022-10-22
[]("https://askubuntu.com/posts/1436632/timeline")  
          
                                        Intel 3165 wifi does not work on jammy new install. Ubuntu's Network  Manager sees the router but never manages to connect to it. I've tried the purge of the backport iwlwifi module but that didn't  help. I followed the instructions elsewhere to give diagnostics.  They are at [https://pastebin.ubuntu.com/p/6tgVfYkmFj/](https://pastebin.ubuntu.com/p/6tgVfYkmFj/)

 Some more info:
 admin@Server:~$ lspci -nnk | grep 3165 
02:00.0 Network controller [0280]: Intel Corporation Wireless 3165 [8086:3165] (rev 81) Subsystem: Intel Corporation Dual Band Wireless AC 3165 [8086:4010] 
admin@Server:~$ rfkill list all
0: hci0: Bluetooth Soft blocked: yes Hard blocked: no
1: hci1: Bluetooth Soft blocked: yes Hard blocked: no 
2: phy0: Wireless LAN Soft blocked: no Hard blocked: no –
 Not dual boot. BTW Computer is an old Intel NUC.

---

### Post by Yellow Pasque on 2022-10-22
```
[ 4260.993213] iwlwifi 0000:02:00.0: Microcode SW error detected.  Restarting 0x2000000.
```

There are some things to try here: [https://bugzilla.kernel.org/show_bug.cgi?id=207409](https://bugzilla.kernel.org/show_bug.cgi?id=207409)
I know it's a different chipset, but I think it may help.

---

### Post by johnaaronrose on 2022-10-23
@Yellow Pasque I looked at that bug report. It's above my pay grade. I tried 'sudo dmesg|grep microcode' but it showed nothing.

---

### Post by johnaaronrose on 2022-10-24
I've reported this on Launchpad as bug 1993890.

---

### Post by Yellow Pasque on 2022-10-24
> **johnaaronrose said:**
> It's above my pay grade.

Heh, I've been there. Try this:
```
echo 'options iwlwifi power_save=0 uapsd_disable=0' | sudo tee -a /etc/modprobe.d/wifihacks.conf
echo 'options iwlmvm power_scheme=1' | sudo tee -a /etc/modprobe.d/wifihacks.conf
```

And, of course, reboot. That will disable powersaving on the wifi chip, which can cause firmware errors and other issues. Note that if you're on a battery-powered device, your battery life might take a bit of a hit. I think it would be minor, but don't quote me on that.

If you want to undo the changes, you can just remove the file you created:
```
sudo rm /etc/modprobe.d/wifihacks.conf
```

---

### Post by johnaaronrose on 2022-10-25
@Yellow Pasque Thanks for the instructions. The instructions created the wifihacks.conf file Ok. But after rebooting the wifi still says connecting and doesn't work. Any other ideas?
I'll report it at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1993890](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1993890)

---

### Post by johnaaronrose on 2022-10-25
I've tried changing /etc/modprobe.d/wifihacks.conf to conform with [https://bugzilla.kernel.org/show_bug.cgi?id=207409](https://bugzilla.kernel.org/show_bug.cgi?id=207409) but wifi still does not work.
admin@Server:~$ cat /etc/modprobe.d/wifihacks.conf
options iwlwifi swcrypt=0
options iwlwifi power_save=0
options iwlmvm power_scheme=1
options iwlwifi uapsd_disable=1

---

### Post by Yellow Pasque on 2022-10-25
> **johnaaronrose said:**
> Any other ideas?

Unfortunately, no. But I would suggest you ask the the mods to have this moved to the Networking & Wireless subforum, as it may get better attention.

---

### Post by johnaaronrose on 2022-10-27
It's created anew at post [https://ubuntuforums.org/showthread.php?t=2480324&p=14117014#post14117014](https://ubuntuforums.org/showthread.php?t=2480324&p=14117014#post14117014)

---

