---
title: "impossible to start bluetooth"
date: 2016-05-10
forum: Hardware
---

### Post by al.adab on 2016-05-10
hello, 

can't find specific reference to the following issue - apologies if it's a duplicate: 

I've installed Ubuntu 16.04 on a Asus UX301. I can't start bluetooth. Going to settings>bluetooth>off>on doesn't help (bluetooth remains off, see screenshot, plus there's no icon on the taskbar). I tried to install *blueman* but didn't get very far: the icon appeared on the taskbar, it was possible to turn bluetooth on&off, though it was impossible to detect and connect from/to any device (specifically on Ubuntu: error message: "no adapter found"). urg

I've now removed/purged *blueman* as I thought it might conflict with *gnome-bluetooth*. 

can you please help? thanks.

---

### Post by jeremy31 on 2016-05-11
Did bluetooth work in a previous version/OS?

Please open a terminal window and enter
```
lspci -nnk | grep -iA2 net; lsusb; lsmod | grep blue; dmesg | egrep -i 'blue|firm'
```

Post the output using code tags

---

### Post by al.adab on 2016-05-11
Thanks Jeremy31. Here's the output: 

```
~$ lspci -nnk | grep -iA2 net; lsusb; lsmod | grep blue; dmesg | egrep -i 'blue|firm'
02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c070]
	Kernel driver in use: iwlwifi
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 03eb:8a0c Atmel Corp. 
Bus 001 Device 003: ID 1bcf:2987 Sunplus Innovation Technology Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
bluetooth             520192  9 bnep,btbcm,btrtl,btusb,btintel
[    1.871688] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x671f07)
[    2.420028] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7260-17.ucode failed with error -2
[    2.428446] iwlwifi 0000:02:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm
[    2.435723] Bluetooth: Core ver 2.21
[    2.435740] Bluetooth: HCI device and connection manager initialized
[    2.435744] Bluetooth: HCI socket layer initialized
[    2.435748] Bluetooth: L2CAP socket layer initialized
[    2.435756] Bluetooth: SCO socket layer initialized
[    2.471087] Bluetooth: hci0: read Intel version: 370710018002030d00
[    2.472385] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[    2.596227] Bluetooth: hci0 sending Intel patch command (0xfc8e) failed (-19)
[    4.598383] Bluetooth: hci0 command 0xfc8e tx timeout
[    4.598405] Bluetooth: hci0 sending frame failed (-19)
[    6.266233] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    6.266238] Bluetooth: BNEP filters: protocol multicast
[    6.266242] Bluetooth: BNEP socket layer initialized
[    6.602530] Bluetooth: hci0 command 0xfc11 tx timeout
[   12.595038] Bluetooth: hci0 exiting Intel manufacturer mode failed (-110)
```

---

### Post by jeremy31 on 2016-05-11
Can you remove the wireless card and reinstall?  For some reason the bluetooth isn't shown in the lsusb results and a dirty or bad connection may cause it

---

### Post by al.adab on 2016-05-11
you mean physically remove it? I wouldn't know where to start from/haven't got any tool/no pc repair shop near where i live...

can i simply reinstall the wifi? (how?)

sorry I'm confused :) I don't understand the "dirty/bad" connection bit either...the thing is that (I think) the connection at home is quite good. I had Mint 17 on the Asus till last week and never had any troubles with bluetooth or wifi in general. I realised I like Ubuntu better in general, that's why I switched to the 16.04

hope there's a solution somewhere?

---

### Post by jeremy31 on 2016-05-11
You could try going into BIOS and reset to defaults.  The bluetooth in my Dell uses the same bluetooth firmware file and it works fine in 16.04.  It has a 7260 card and I have used it with a bluetooth speaker.

The dirty/bad connection I was referring to was between the wifi card and the motherboard socket.

The only difference between the dmesg results from yours to mine, is that mine doesn't show
```
[    2.596227] Bluetooth: hci0 sending Intel patch command (0xfc8e) failed (-19)
[    4.598383] Bluetooth: hci0 command 0xfc8e tx timeout
[    4.598405] Bluetooth: hci0 sending frame failed (-19)
[    6.602530] Bluetooth: hci0 command 0xfc11 tx timeout
[   12.595038] Bluetooth: hci0 exiting Intel manufacturer mode failed (-110)
```

My bluetooth shows in lsusb as ```
Bus 001 Device 003: ID 8087:07dc Intel Corp.
```

---

### Post by al.adab on 2016-05-14
Resetting the Bios to defaults didn't help. I had a look inside the Asus and - as far as I can see - it's quite difficult to remove the wireless card (it probably entails cutting some wires and then soldering them back together. 

I've got this nasty feeling you might be right about a "dirty connection": I replaced Ubuntu with Mint and - unlike before - I now can't start bluetooth in Mint either. 

on the other hand, I have a stupid question: isn't the wireless card also responsible for a good wifi (internet) connection? in other words, there's no separate, dedicated card for bluetooth, so it's one card that handles both. 

If that's the case, is it safe to assume that the problem might not be in the hardware at all but in whatever software Ubuntu and Mint share (I guess) to make the card work properly? 

I'm asking this because I came across quite a number of people posting in various forums whose bluetooth stopped working after some kind of upgrade. 

Is there any way to check the integrity of the wireless card - some magic terminal formula, for instance? 

If there is and the result shows that the card is all right, could it be a software bug or something like that?

forgotten to say that my wifi connection (internet) works flawlessly.

also forgotten to say that - in my ignorance on the subject - I kind of suspect some kind of conflict between wifi (internet) and bluetooth: I tried to disable wifi and the bluetooth comes to life (kind of). It still doesn't work but its behaviour slightly change, both in terms of its icon re-appearing on the taskbar and the possibility to turn it on/off clicking on the icon. Still it doesn't communicate with other devices, etc. 

any idea?

---

### Post by jeremy31 on 2016-05-14
You could try shutting down the computer with wifi disabled and see if it affects bluetooth when rebooted

---

### Post by al.adab on 2016-05-14
OK, I shut down and started the PC with the wifi disabled. 

This seems to confirm that slight difference in terms of behaviour I mentioned earlier: the bluetooth icon in the taskbar "lits up", apparently I can turn on bluetooth (but can't make it visible), and if I click on settings...please see png in attachment. Still no communication from/to devices.

---

### Post by jeremy31 on 2016-05-14
You are likely still not getting the firmware loaded.  I found an old bug report with the same issues [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1523108](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1523108) could even be the exact model as yours

The logs in the bug report seem to indicate another issue with video that might cause issues with the kernel

I think about all that can be done is to file a new bug report against package linux, you can find info [https://bugs.launchpad.net/ubuntu/+source/linux/+filebug](https://bugs.launchpad.net/ubuntu/+source/linux/+filebug)

---

### Post by al.adab on 2016-05-14
bug report submitted - hope there's a solution somewhere. Thanks very much for your help.

---

### Post by jeremy31 on 2016-05-14
Looks like you are having problems with apport-collect, does anything change if you chose to send report rather than view?  The apport-collect should add error logs and other info to your bug report

And bluetooth might work if XHCI is disabled in BIOS, however that means that USB 3.0 will be disabled

---

### Post by al.adab on 2016-05-15
Tried just now and chose "S": 

[I]Please choose (S/V/K/I/C): S
weword@UX301 ~ $  [/I]

supposedly the report was sent? do you mean the report I posted at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1581814](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1581814) is incomplete? 

I also tried to disable XHCI, unfortunately to no avail. Same situation as before with bluetooth.

---

### Post by jeremy31 on 2016-05-15
They now have the info they asked for.  Now you just wait for further instructions from them

---

### Post by al.adab on 2016-05-18
just wanted to report on a new development: 

bluetooth now works on the following kernel

[I]
$ dpkg --list | grep linux-image
ii  linux-image-3.19.0-32-generic               3.19.0-32.37~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-32-generic         3.19.0-32.37~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP[/I]

my question now is: can i now prevent "update manager" from installing new, more recent kernels - without ruling out necessary software updates? how?

thanx again for your help!

forgotten to add that it works following a fresh install of Linux Mint 17.3
and
that it no longer work if I follow the "update manager" instructions to update the system.

i don't know which package in the update causes the problem. I'll refer to the Linux Mint forum if this isn't the right place to discuss such issues.

---

### Post by jeremy31 on 2016-05-18
Strange that Linux Mint would work until the Update Manager is used to update the system as the bluetooth support should be mostly kernel and unless you have level 4 and 5 updates selected to update, your kernel shouldn't change

There are ways to force the use of a certain kernel or you can use Grub to select an older kernel to boot to in Ubuntu.  I hope your bug report gets some attention as I doubt it is just you having the issue

---

### Post by al.adab on 2016-06-19
don't know if it's too late to update this thread...anyway, here it goes:

if you Ctrl-F "To achieve that effect, just add *blacklist asus-nb-wmi* to* /etc/modprobe.d/blacklist.conf*" at [http://askubuntu.com/questions/396021/what-is-causing-my-intel-7260-bluetooth-device-to-disconnect-when-i-unblock-it-w](http://askubuntu.com/questions/396021/what-is-causing-my-intel-7260-bluetooth-device-to-disconnect-when-i-unblock-it-w)

you'll see that a temporary workaround exists. The only thing is that - after modifying */etc/modprobe.d/blacklist.conf* bluetooth does work flawlessly, except that some Fx keys don't, and specifically:

Fn+F3/4 (backlit keyboard),
Fn+F10/11/12 (volume control)

I was wondering if it might be possible to do something about this...any idea?

---

### Post by jeremy31 on 2016-06-20
Remove the blacklist, reboot and see if ```
rfkill unblock all
``` helps any or try the FN combo to enable/disable wireless, you may have to use the combo multiple times to have bluetooth and wifi unblocked.  Check ```
rfkill list all
```

---

### Post by al.adab on 2016-06-20
thanks for getting back to me on this. 

*rfkill unblock all* doesn't produce any result. 

[I]~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no[/I]

Fn + F2 (wireless) disables/enables wifi all right (but has no effect on bluetooth)

---

### Post by al.adab on 2016-06-20
actually...

[I]~$ rfkill list all
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no[/I]

after disabling/enabling wifi via Fn+F2

---

### Post by al.adab on 2016-06-20
same result at *rfkill list all* after re-booting + bluetooth still unresponsive (even "show bluetooth status in taskbar" doesn't work).

---

### Post by jeremy31 on 2016-06-20
Please post ```
hciconfig -a
``` After removing hard and soft blocks from rfkill

---

### Post by al.adab on 2016-06-21
here you go (can't see any results):

[I]~$ rfkill list all
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
xxxx@UX301:~$ hciconfig -a
xxxx@UX301:~$ 
[/I]

---

### Post by jeremy31 on 2016-06-21
```
lsmod | grep blue; uname -a
```

---

### Post by al.adab on 2016-06-21
[I]~$ lsmod | grep blue; uname -a
bluetooth             520192  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
Linux UX301 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:27:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux[/I]

---

### Post by jeremy31 on 2016-06-21
See if ```
echo "options asus-nb-wmi wapf=4" | sudo tee /etc/modprobe.d/asus-nb-wmi.conf
```

Reboot

The wapf parameter affects the functioning of the wifi toggle so it may help

---

### Post by al.adab on 2016-06-22
[I]~$ echo "options asus-nb-wmi wapf=4" | sudo tee /etc/modprobe.d/asus-nb-wmi.conf
[sudo] password for weword: 
options asus-nb-wmi wapf=4[/I]

no difference, I'm afraid, after re-booting (after which the code above produces the same output).

---

### Post by vandelsand on 2017-02-22
I think I managed to fix this in my system with

systemctl enable bluetooth

enter your password a number of times

and then reboot! I don't have the problem anymore.

---

