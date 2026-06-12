---
title: "Suspend and Wake-On-Lan"
date: 2012-06-25
forum: Hardware
---

### Post by the_MKay on 2012-06-25
Hi,

I have a server with an ASRock B75M motherboard running Ubuntu Server 12.04 [64bit].
The server is going to suspend if no user is connected to it for about 30 minutes. If the server is suspended I can boot it using WOL by sending a magic packet or just try to connect to the pc.

So far, so good. This works fine ;)

However **sometimes** when the server wakes up from suspend, the network is not working anymore.

I already searched on the internet and found that the driver (r8169) is somewhat buggy :confused: However the most of these reports are a few years old.

The solutions I found was about to unload the r8169 module on suspend and load it on resume. For example by creating the file /etc/pm/config.d/unload_modules with the following content:
```
SUSPEND_MODULES="$SUSPEND_MODULES r8169"
```
But with this, WOL is not working anymore.

Is there any solution for this problem to allow for suspend and WOL?

---

### Post by ahallubuntu on 2012-06-25
Perhaps you could build the r8169 module yourself from Realtek's source code, which they provide online:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=4&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8110SC(L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=4&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8110SC(L))

This is a "tarball" you'll have to build using make/gcc in a terminal.  I've done it for other Realtek drivers - it's not too hard.

You'll have to blacklist the existing kernel module to make sure the one you build gets picked up instead.

I know one of my motherboards uses r8169 but I haven't had the exact problem you mention.  I do use WOL on a couple of my servers successfully, without resume issues, but I'm not sure I'm using the one with that module regularly.

---

### Post by the_MKay on 2012-06-26
Thanks for your reply. I compiled the driver as follows:
```
sudo make all
sudo depmod -a
update-initramfs -v -u -k `uname -r`
```
But after reboot I had no network anymore -.-

Any ideas?
You see I have not blacklisted the existing r8169 because I don't know how to differentiate between the old r8169 and the new one. It seems like "sudo make all" just overrides the r8169.ko-file in /lib/modules/3.2.0-25-generic/kernel/drivers/net/ethernet/realtek/ with the compiled file.

Because the network was not working anymore I replaced the mentioned r8169.ko with the original file and now network is working again. Do I have to restore more files/is there a clean way to undo the network-driver-compile-install-thing? :)

Moreover I did a "sudo lspci -k":
```
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/**[COLOR="Red"]8168[/COLOR]**B PCI Express Gigabit Ethernet controller (rev 06)
	Subsystem: ASRock Incorporation Motherboard (one of many)
	Kernel driver in use: r8169
	Kernel modules: r8169
```
Seems like I should use r8168? I already compiled the r816[COLOR="Red"]**8**[/COLOR] driver like the previous one. Moreover I did the following:
```
sudo nano /etc/modprobe.d/blacklist.conf
--> blacklist r8169

echo "r8168" >> /etc/initramfs-tools/modules
update-initramfs -v -u -k `uname -r`
```
After that network was working after reboot. But Wake On LAN was not working anymore :confused:

[COLOR="DarkOrange"]**EDIT:**[/COLOR]
Interesting. I installed the r8168 again (this time using autorun.sh).
Network does still work after reboot. And I noticed that WOL is working ... but only using a magic packet.
With the default driver WOL even works with any unicast packet. However the configuration says that unicast should also work:
```
sudo ethtool eth0 | grep Wake-o
	Supports Wake-on: pumbg
	Wake-on: ug
```
(And of course the PC sending the unicast-packet has static ARP-entries :) )

So r8168 **_may_** fix the resume-problems (I have to test that) but without WOL it's not an option.

Any ideas? :)

---

### Post by the_MKay on 2012-07-01
Update:
Using the latest r8168-driver:
a) WOL per magic packet works when shut down or suspended.
b) WOL per unicast-packet works only when shut down, but not when suspended.

Any ideas?

---

