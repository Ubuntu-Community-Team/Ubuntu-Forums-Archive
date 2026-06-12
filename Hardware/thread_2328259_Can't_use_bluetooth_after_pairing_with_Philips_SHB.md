---
title: "Can't use bluetooth after pairing with Philips SHB7000"
date: 2016-06-19
forum: Hardware
---

### Post by Starbeamrainbowlab on 2016-06-19
Hello,

I've recently purchased a pair of bluetooth headphones. I've got the Philips SHB7000.

I tried to pair them with my Dell Inspiron N5110 running Ubuntu 15.10 (I can't upgrade just yet for separate reasons) and it paired, but it apparently "failed to connect". I then restarted to see if that would fix it, but it made it worse. Now the one of the two bluetooth icons has disappeared, and the other one has a red cross through it. If I click "turn bluetooth on", then it appears to work initially, but all my existing devices have disappeared, and if I go to the "Devices..." window, this is all I see:

[IMG]http://i.imgur.com/Sa387bQ.png[/IMG]

There should a few phones in that list as well as my new bluetooth headphones. All the menus have a single option: "Activate....", which doesn't do anything.

I also checked [FONT=courier new]journalctl -u bluetooth[/FONT] and found a bunch of errors:

[FONT=courier new]-- Logs begin at Sun 2016-05-22 08:37:25 BST, end at Sun 2016-06-19 13:34:39 BST. --[/FONT]
[FONT=courier new]May 22 08:37:30 Snowflake systemd[1]: Starting Bluetooth service...[/FONT]
[FONT=courier new]May 22 08:37:30 Snowflake bluetoothd[827]: Bluetooth daemon 5.35[/FONT]
[FONT=courier new]May 22 08:37:30 Snowflake bluetoothd[827]: Starting SDP server[/FONT]
[FONT=courier new]May 22 08:37:30 Snowflake bluetoothd[827]: Bluetooth management interface 1.10 initialized[/FONT]
[FONT=courier new]May 22 08:37:30 Snowflake bluetoothd[827]: Failed to obtain handles for "Service Changed" characteristic[/FONT]
[FONT=courier new]May 22 08:37:30 Snowflake bluetoothd[827]: Not enough free handles to register service[/FONT]
[FONT=courier new]May 22 08:37:30 Snowflake bluetoothd[827]: Error adding Link Loss service[/FONT]
[FONT=courier new]May 22 08:37:30 Snowflake bluetoothd[827]: Not enough free handles to register service[/FONT]
[FONT=courier new]May 22 08:37:30 Snowflake bluetoothd[827]: Not enough free handles to register service[/FONT]
[FONT=courier new]May 22 08:37:30 Snowflake bluetoothd[827]: Not enough free handles to register service[/FONT]
[FONT=courier new]May 22 08:37:30 Snowflake bluetoothd[827]: Current Time Service could not be registered[/FONT]
[FONT=courier new]May 22 08:37:30 Snowflake bluetoothd[827]: gatt-time-server: Input/output error (5)[/FONT]
[FONT=courier new]May 22 08:37:30 Snowflake bluetoothd[827]: Not enough free handles to register service[/FONT]
[FONT=courier new]May 22 08:37:30 Snowflake bluetoothd[827]: Not enough free handles to register service[/FONT]
[FONT=courier new]May 22 08:37:30 Snowflake bluetoothd[827]: Sap driver initialization failed.[/FONT]
[FONT=courier new]May 22 08:37:30 Snowflake bluetoothd[827]: sap-server: Operation not permitted (1)[/FONT]
[FONT=courier new]May 22 08:37:30 Snowflake systemd[1]: Started Bluetooth service.[/FONT]
[FONT=courier new]May 22 08:37:42 Snowflake bluetoothd[827]: Endpoint registered: sender=:1.44 path=/MediaEndpoint/A2DPSource[/FONT]
[FONT=courier new]May 22 08:37:42 Snowflake bluetoothd[827]: Endpoint registered: sender=:1.44 path=/MediaEndpoint/A2DPSink[/FONT]
[FONT=courier new]May 22 08:51:16 Snowflake bluetoothd[827]: Endpoint registered: sender=:1.66 path=/MediaEndpoint/A2DPSource[/FONT]
[FONT=courier new]May 22 08:51:16 Snowflake bluetoothd[827]: Endpoint registered: sender=:1.66 path=/MediaEndpoint/A2DPSink[/FONT]
[FONT=courier new]May 22 08:51:16 Snowflake bluetoothd[827]: RFCOMM server failed for Headset Voice gateway: rfcomm_bind: Address already in use (98)[/FONT]
[FONT=courier new]May 22 08:51:33 Snowflake bluetoothd[827]: Endpoint unregistered: sender=:1.44 path=/MediaEndpoint/A2DPSource[/FONT]
[FONT=courier new]May 22 08:51:33 Snowflake bluetoothd[827]: Endpoint unregistered: sender=:1.44 path=/MediaEndpoint/A2DPSink[/FONT]
[FONT=courier new]May 22 19:33:47 Snowflake bluetoothd[827]: Endpoint unregistered: sender=:1.66 path=/MediaEndpoint/A2DPSource[/FONT]
[FONT=courier new]May 22 19:33:47 Snowflake bluetoothd[827]: Endpoint unregistered: sender=:1.66 path=/MediaEndpoint/A2DPSink[/FONT]


Here's my [FONT=courier new]uname -a[/FONT]: [FONT=courier new]Linux Snowflake 4.2.0-16-generic #19-Ubuntu SMP Thu Oct 8 15:35:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux[/FONT]

Here's a link to the output of lspci: [https://starbeamrainbowlabs.com/bin/96fg](https://starbeamrainbowlabs.com/bin/96fg)

...and lsusb: [https://starbeamrainbowlabs.com/bin/gtfq](https://starbeamrainbowlabs.com/bin/gtfq)

I can't use bluetooth at all now. Can anybody help me please?

**Update** Here's a larger snippet from journalctl: [http://hastebin.com/apunowixak](http://hastebin.com/apunowixak)

---

### Post by jeremy31 on 2016-06-19
I would shutdown the computer and do a cold boot to see if it works.
Check ```
pactl list short | grep bluetooth
``` for module-bluetooth-discover as it is needed for audio over bluetooth but I know a few versions of blueman would remove module-bluetooth-discover when it loaded

---

### Post by Starbeamrainbowlab on 2016-06-19
Thanks for the cold boot tip - I used the restart option last time. Don't know why that would make a difference. Here's the output of that command:
[FONT=courier new]
[/FONT][FONT=courier new]8	module-bluetooth-policy		[/FONT]
[FONT=courier new]9	module-bluetooth-discover
[FONT=arial]
Now that my bluetooth is working again, I just need to figure out how to get my headphones / microphone working. Last time I put the headphones into pairing mode and tried to connect them, but it said that it paired successfully, but failed to connect.

Does anyone have any ideas?

Thanks.
[/FONT]
[/FONT]

---

### Post by jeremy31 on 2016-06-19
Check ```
dmesg | grep -i blue
``` after it fails to connect

---

### Post by Starbeamrainbowlab on 2016-06-19
[COLOR=#000000]Thanks for the advice. Here's the output of that command after it fails to connect:[/COLOR]

[FONT=courier new][COLOR=#000000][ 36.931239] Bluetooth: Core ver 2.20[/COLOR]
[COLOR=#000000][ 36.931253] Bluetooth: HCI device and connection manager initialized[/COLOR]
[COLOR=#000000][ 36.931256] Bluetooth: HCI socket layer initialized[/COLOR]
[COLOR=#000000][ 36.931259] Bluetooth: L2CAP socket layer initialized[/COLOR]
[COLOR=#000000][ 36.931263] Bluetooth: SCO socket layer initialized[/COLOR]
[COLOR=#000000][ 45.473809] Bluetooth: BNEP (Ethernet Emulation) ver 1.3[/COLOR]
[COLOR=#000000][ 45.473812] Bluetooth: BNEP filters: protocol multicast[/COLOR]
[COLOR=#000000][ 45.473817] Bluetooth: BNEP socket layer initialized[/COLOR]
[COLOR=#000000][ 63.578906] Bluetooth: RFCOMM TTY layer initialized[/COLOR]
[COLOR=#000000][ 63.578915] Bluetooth: RFCOMM socket layer initialized[/COLOR]
[COLOR=#000000][ 63.578920] Bluetooth: RFCOMM ver 1.11[/COLOR]
[COLOR=#000000][ 9201.406157] Bluetooth: hci0 command 0x0428 tx timeout[/COLOR]
[COLOR=#000000][ 9203.412492] Bluetooth: hci0 command 0x1405 tx timeout[/COLOR]
[COLOR=#000000][ 9205.418661] Bluetooth: hci0 command 0x1403 tx timeout[/COLOR]
[COLOR=#000000][ 9207.425011] Bluetooth: hci0 command 0x0c2d tx timeout[/COLOR]
[COLOR=#000000][ 9209.431343] Bluetooth: hci0 command 0x1405 tx timeout[/COLOR]
[COLOR=#000000][ 9211.437622] Bluetooth: hci0 command 0x1403 tx timeout[/COLOR]
[COLOR=#000000][ 9213.443930] Bluetooth: hci0 command 0x0c2d tx timeout[/COLOR]
[COLOR=#000000][ 9215.450195] Bluetooth: hci0 command 0x1405 tx timeout[/COLOR]
[COLOR=#000000][ 9217.456468] Bluetooth: hci0 command 0x1403 tx timeout[/COLOR]
[COLOR=#000000][ 9219.462783] Bluetooth: hci0 command 0x0c2d tx timeout[/COLOR]
[COLOR=#000000][ 9221.469117] Bluetooth: hci0 command 0x1405 tx timeout[/COLOR]
[COLOR=#000000][ 9223.475390] Bluetooth: hci0 command 0x1403 tx timeout[/COLOR]
[COLOR=#000000][ 9225.481685] Bluetooth: hci0 command 0x0c2d tx timeout[/COLOR]
[COLOR=#000000][ 9227.487959] Bluetooth: hci0 command 0x1405 tx timeout[/COLOR]
[COLOR=#000000][ 9229.494259] Bluetooth: hci0 command 0x1403 tx timeout[/COLOR]
[COLOR=#000000][ 9231.500561] Bluetooth: hci0 command 0x0c2d tx timeout[/COLOR]
[COLOR=#000000][ 9233.506735] Bluetooth: hci0 command 0x1405 tx timeout[/COLOR]
[COLOR=#000000][ 9235.513129] Bluetooth: hci0 command 0x1403 tx timeout[/COLOR]
[COLOR=#000000][ 9237.519412] Bluetooth: hci0 command 0x0c2d tx timeout[/COLOR]
[COLOR=#000000][ 9239.525721] Bluetooth: hci0 command 0x1405 tx timeout[/COLOR]
[COLOR=#000000][ 9241.531981] Bluetooth: hci0 command 0x1403 tx timeout[/COLOR][/FONT]

[COLOR=#000000]Strangely enough, the headphones say that they are apparently connected when it says "Please wait" on the screen (a blue light flashes every 6 seconds).[/COLOR]

---

### Post by jeremy31 on 2016-06-19
Please use code tags- see link in my signature when posting terminal output, it keeps the formatting and prevents smilies from appearing.

Can you post the output from ```
dmesg | grep -i 0cf3
```
 I suspect the bluetooth might change it's ID after the firmware is loaded

Please install updates as the issue might be fixed in a newer 15.10 kernel

---

### Post by Starbeamrainbowlab on 2016-06-19
Here's the output of that command:

```

[    1.803326] usb 3-1.4: New USB device found, idVendor=0cf3, idProduct=3002
[   38.024268] usb 3-1.4: New USB device found, idVendor=0cf3, idProduct=3005
[ 3697.470200] usb 3-1.4: New USB device found, idVendor=0cf3, idProduct=3002
[ 3700.754196] usb 3-1.4: New USB device found, idVendor=0cf3, idProduct=3005
[12627.277134] usb 3-1.4: New USB device found, idVendor=0cf3, idProduct=3002
[12628.374507] usb 3-1.4: New USB device found, idVendor=0cf3, idProduct=3005

```

I've also run [FONT=courier new]apt update[/FONT] and [FONT=courier new]apt full-upgrade[/FONT], and no updates were available. Please note that I can't currently upgrade to Ubuntu 16.04 because the following bugs also affect me (my laptop boots to a black screen):


[LIST]
[*][https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1555434](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1555434)
[*][https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1589006](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1589006)
[*][https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1559576](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1559576)
[/LIST]

Is there a ppa for the latest stable kernel that I could try? That way I could upgrade the kernel without upgrading to Ubuntu 16 which causes the black screen problem.

---

### Post by jeremy31 on 2016-06-19
Looks like the black screen issue(bug report #3) was caused by snapd(bug report #2) and this [url=https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1559576/comments/68]comment[/code] makes me think that the issue might be resolved.  The bug report team doesn't like comments from people other than the one who reported the issue.

I actually have the same wifi/bluetooth combo that you have and a pair of SHB4000 headphones and I had issues when using a 16.04 ISO but after installing 16.04 the tx timeouts stopped.  Do you have a large enough hard drive that you could install 16.04 along side 15.10 and allow it to download updates while it installs to see if the latest updates do fix the black screen issue and bluetooth.

That dmesg info isn't quite right but I remember some posts on the kernel mailing list about a couple bluetooth chips that would change ID after the firmware was loaded and I do believe this was one of them.

Post ```
modinfo ath3k | grep -i 0cf3
``` The ath3k module is responsible for loading the firmware.

You could try a newer kernel but it is not something that is recommended in Ubuntu as newer kernels patched for Ubuntu are usually available through updates.  Are you still using the same kernel from the first post because I think the 4.2 series is up to 4.2.0-38 now?

---

### Post by Starbeamrainbowlab on 2016-06-20
I don't think my hard drive is large enough to try to install both alongside each other :( I could try upgrading to Ubuntu 16 again though. If I'm greeted with a black screen, I should follow the solution suggested in [this comment]("https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1589006/comments/23") then?

Here's the output from that command:

```

alias:          usb:v0CF3pE006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p817Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3121d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p311Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p311Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p311Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p0036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3000d*dc*dsc*dp*ic*isc*ip*in*

```

I tried connecting it again today. It worked momentarily, but then it stopped working again.

I believe I am using the same kernel. Here's my latest uname -a, just to be sure:

```

Linux Snowflake 4.2.0-16-generic #19-Ubuntu SMP 4.2.0-38Thu Oct 8 15:35:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

I'm not sure why I'm not on 4.2.0-38 yet. I've checked for updates and everything.

---

### Post by jeremy31 on 2016-06-20
If comment 32 is correct you shouldn't need to edit anything.

---

### Post by Starbeamrainbowlab on 2016-06-20
That can't be right. I've tried upgrading 4 times now (using Timeshift to restore in between), and I haven't been successful on any of the aforementioned attempts. The last time I tried was last weekend, on ~12th June - after that comment was posted. Perhaps that isn't my exact issue after all?

---

### Post by jeremy31 on 2016-06-20
If the next install fails use the live USB or DVD to see if you can access the dmesg and kern.log from the hard drive.  They are in /var/log directory 
There is a chance that the updated snaps package was not in the repos right away

---

### Post by Starbeamrainbowlab on 2016-06-20
Just finished upgrading again, and I've got a black screen. I can, however, use the other TTYs (CTRL + ALT + F3 for instance). Using that I've checked dmesg and kern.log. I've found nothing out of the ordinary (apart from a few 'ACPI Warning: ... Argument #4 mismatch'es). I'm going to try an apt-get update && apt-get dist-upgrade, although I'm not hopeful. Thoughts?

**Update:** Just tried an update / dist-upgrade, no packages needed upgrading.

---

### Post by jeremy31 on 2016-06-20
check ```
dpkg -l | grep snapd
```

---

### Post by Starbeamrainbowlab on 2016-06-20
Output: [https://starbeamrainbowlabs.com/bin/6s98](https://starbeamrainbowlabs.com/bin/6s98)

---

### Post by jeremy31 on 2016-06-20
Any errors in /var/log/Xorg.0.log?

---

### Post by Starbeamrainbowlab on 2016-06-20
Can't tell. Here's the whole thing (thanks to my personal installation of termbin again): [https://starbeamrainbowlabs.com/bin/z3ia/](https://starbeamrainbowlabs.com/bin/z3ia/)

---

### Post by jeremy31 on 2016-06-20
See if removing init=/sbin/e4rat-preload from grub allows you to boot correctly.

---

### Post by Starbeamrainbowlab on 2016-06-20
Nope. No luck. Here's that /var/log/Xorg.0.log file again after that boot: [https://starbeamrainbowlabs.com/bin/hlgt/](https://starbeamrainbowlabs.com/bin/hlgt/)

---

### Post by Starbeamrainbowlab on 2016-06-20
Just managed to fix the black screen issue by rolling back to the 4.2.x kernel instead of the 4.4.x kernel, and rolling the nvidia drivers back to 364 instead of 367.
[B]
Update:[/B] I also get the following pop-up when I login: 'UnicodeDecodeError: 'ascii' codec can't decode byte 0xff in position 0: ordinal not in range(128)'. I've tried googling it, but I can't find anything that isn't on stackoverflow (I'm pretty sure I don't have a programming problem.)

---

### Post by jeremy31 on 2016-06-20
I wonder if this would help with the 4.4 kernel [http://askubuntu.com/a/760935/300665](http://askubuntu.com/a/760935/300665)

---

### Post by Starbeamrainbowlab on 2016-06-21
Thanks for the link, but I've tried that already :(

On the plus side, the bluetooth headphones are now working! Woohoo! Thanks for all your help.

Now I've just got a few other issues I need to sort out, like the 4.4 kernel, the 367 driver, and the strange pop-up message I get on every boot I mentioned in an earlier post.

**Update:** Umm actually they just stopped working again. It's really odd. They were working this morning.... and now they've stopped working again. Humm. Here's my dmesg: [http://hastebin.com/kijalotove](http://hastebin.com/kijalotove)

**Update 2:** They've mysteriously started working again. Perhaps it's just temperamental. It connects fine with no hiccups on my phone on with windows machines I've tested it with though

---

### Post by jeremy31 on 2016-06-21
The last dmesg just shows the bluetooth disconnecting for some reason and that doesn't make sense as it is on the same card as wifi.  Do you have any sound issues when the bluetooth doesn't work as there are quite a few sound module errors, this is just a few
```
[   42.635387] snd_hda_codec_hdmi hdaudioC1D0: out of range cmd 0:5:707:ffffffff
[   42.641144] snd_hda_codec_hdmi hdaudioC1D0: out of range cmd 0:5:707:ffffffff
[   42.641341] snd_hda_codec_hdmi hdaudioC1D0: out of range cmd 0:5:707:ffffffbf
[   42.641660] snd_hda_codec_hdmi hdaudioC1D0: out of range cmd 0:5:707:ffffffff
[   42.649138] snd_hda_codec_hdmi hdaudioC1D0: out of range cmd 0:5:707:ffffffff
[   42.649315] snd_hda_codec_hdmi hdaudioC1D0: out of range cmd 0:5:707:ffffffbf
[   42.649641] snd_hda_codec_hdmi hdaudioC1D0: out of range cmd 0:5:707:ffffffff
```

It looks like UFW is blocking mDNS traffic between the wifi card and router also

```
[ 9451.886964] [UFW BLOCK] IN=wlan0 OUT= MAC=84:4b:f5:30:d6:25:5c:f9:dd:6a:f1:96:08:00 SRC=192.168.0.12 DST=192.168.0.2 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=2219 DF PROTO=TCP SPT=51597 DPT=515 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 9451.887250] [UFW BLOCK] IN=wlan0 OUT= MAC=84:4b:f5:30:d6:25:5c:f9:dd:6a:f1:96:08:00 SRC=192.168.0.12 DST=192.168.0.2 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=2220 DF PROTO=TCP SPT=51598 DPT=9100 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 9451.888092] [UFW BLOCK] IN=wlan0 OUT= MAC=84:4b:f5:30:d6:25:5c:f9:dd:6a:f1:96:08:00 SRC=192.168.0.12 DST=192.168.0.2 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=2221 DF PROTO=TCP SPT=51599 DPT=2191 WINDOW=8192 RES=0x00 SYN URGP=0 
```

---

