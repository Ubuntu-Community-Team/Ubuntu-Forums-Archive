---
title: "Can't get bluetooth heaset to work"
date: 2020-05-06
forum: Hardware
---

### Post by pasogo91 on 2020-05-06
Hi, I recently got this headset:

[https://www.amazon.com/-/es/Auriculares-inal%C3%A1mbricos-E18-Plus-auriculares/dp/B07T59N7Y9](https://www.amazon.com/-/es/Auriculares-inal%C3%A1mbricos-E18-Plus-auriculares/dp/B07T59N7Y9)

I have a Kubuntu 18.04 on a HP 450 laptop. I can't get the microphone to work, only audio. I tried with these instructions:

[https://askubuntu.com/a/1223200/1067537](https://askubuntu.com/a/1223200/1067537)

It worked at first as I was able to select HFP/HSP profile and use the mic, but then there was no audio at all, audio only seems to work with A2DP and then the mic does not work. Now after rebooting I can't even select the profile.

I am working from home now and I would really like to chat with my co-workers with this pods, is this even possible? Because I've been reading about the lack of support for BT headset from Linux...

In the case I can't get them to work, would this (or something alike) help?

[https://www.amazon.com/-/es/ELEGIANT-Bluetooth-Receiver-Headphones-Streaming/dp/B086V6V71H/ref=sr_1_1?__mk_es_US=%C3%85M%C3%85%C5%BD%C3%95%C3%91&dchild=1&keywords=ELEGIANT+bluetooth&qid=1588764322&sr=8-1](https://www.amazon.com/-/es/ELEGIANT-Bluetooth-Receiver-Headphones-Streaming/dp/B086V6V71H/ref=sr_1_1?__mk_es_US=%C3%85M%C3%85%C5%BD%C3%95%C3%91&dchild=1&keywords=ELEGIANT+bluetooth&qid=1588764322&sr=8-1)

Because maybe that tool only makes me use the audio but not the microphone part from my pods...

Thanks in advance.

---

### Post by slickymaster on 2020-05-06
*Thread moved to **Hardware**.*

---

### Post by mIk3_08 on 2020-05-06
Please run this command and copy/paste the result here in thread wrap with ```


[CODE]dmesg | grep -i 'bluetooth'
```

---

### Post by pasogo91 on 2020-05-06
Here it is:

```
[    8.940078] Bluetooth: Core ver 2.22
[    8.940108] Bluetooth: HCI device and connection manager initialized
[    8.940112] Bluetooth: HCI socket layer initialized
[    8.940116] Bluetooth: L2CAP socket layer initialized
[    8.940121] Bluetooth: SCO socket layer initialized
[    8.986514] Bluetooth: hci1: read Intel version: 3707100100012d0d00
[    8.987208] Bluetooth: hci1: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.0.1.2d.d.bseq
[    9.150500] Bluetooth: hci1: unexpected event for opcode 0xfc2f
[    9.167010] Bluetooth: hci1: Intel firmware patch completed and activated
[   10.347860] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   10.347862] Bluetooth: BNEP filters: protocol multicast
[   10.347867] Bluetooth: BNEP socket layer initialized
[   10.508634] Bluetooth: RFCOMM TTY layer initialized
[   10.508640] Bluetooth: RFCOMM socket layer initialized
[   10.508645] Bluetooth: RFCOMM ver 1.11
[  150.286649] hid-generic 0005:046D:B017.0005: input,hidraw4: BLUETOOTH HID v0.17 Keyboard [MX Master] on 00:1A:7D:DA:71:0E
[  185.884922] hid-generic 0005:046D:B017.0006: input,hidraw4: BLUETOOTH HID v0.17 Keyboard [MX Master] on 00:1A:7D:DA:71:0E

```

Please keep in mind that in addition to the integrated BT of the laptop I have an external usb dongle plugged in. I this this for trying with another device, but it didn't solve anything.

Thanks in advance.

---

### Post by mIk3_08 on 2020-05-06
thus your system Bluetooth works completely? have you tried to connect your headset bluetooth device to your system directly?

---

### Post by pasogo91 on 2020-05-06
Yes, I tried, only audio through AD2P, can't select HFP/HSP, when I apply the ofono "fix" I can select the profile but no audio at all :(

---

### Post by mIk3_08 on 2020-05-06
I think your bluetooth wont work properly. Due to 

```
unexpected event for opcode 0xfc2f
```

Im not sure if this is will work on your bluetooth but I also had an issue with Bluetooth not working until I installed this
bluez packages and I manually started the bluetooth.

```
sudo pacman -S bluez bluez-utils
```

```
sudo systemctl start bluetooth.service
```

You can also try this command;
```
systemctl --user enable obex
```
Then start the bluetooth manually again.

---

### Post by mIk3_08 on 2020-05-06
You can also try install Blueman. This can also help;
```
sudo apt install blueman
```

---

### Post by pasogo91 on 2020-05-06
I don't have pacman, and through apt-get I can't find bluez-utils. But I do have bluez installed.

EDIT

I have bluez-tools though. I also have blueman.

---

### Post by pasogo91 on 2020-05-06
Now I can select HFP/HSP, but no audio at all, only like a milisecond when I change profiles. Apps are outputting sound, but none on my pods with that profile.

EDIT

It does sound for a liiitle bit when changing from A2DP to HFP/HSP (with blueman for example, the same goes for pavucontrol), then nothing at all. Maybe ofono related? I had to set up a virtual modem to be able to select that profile, maybe something's going on in there?

---

### Post by pasogo91 on 2020-05-06
As soon as I quit ofono I can no longer select HSP/HFP profile.

---

### Post by pasogo91 on 2020-05-07
OK, don't know what I did but it's working now. Only thing is, that in HSP/HFP mode I can't control the volume level. Is it normal? Any fix? Thanks.

---

### Post by mIk3_08 on 2020-05-07
Try to delete the device name that you are try to connect on your Bluetooth then, logout/restart When system booted;
run this command;
```
systemctl --user enable obex
```
then start the service bluetooth;
try to connect your Bluetooth headset device again; 
```

bluetoothctl
power on
scan on
discoverable on
pair 
trust

``` 

if still; nothing happens;

run this command again; 
```
sudo rfkill list
```
paste the result here;

and here;
```
sudo service bluetooth status
```

---

### Post by pasogo91 on 2020-05-07
Audio is already working fine, only thing is that now I can't control the volume for the HFP/HSP profile. Please look here:

[https://ubuntuforums.org/showthread.php?t=2442758&p=13954740](https://ubuntuforums.org/showthread.php?t=2442758&p=13954740)

Thanks in advance!

---

