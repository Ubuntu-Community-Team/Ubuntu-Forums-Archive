---
title: "Thinkpad T42/Edgy Bluetooth not even installed ??"
date: 2007-01-01
forum: Hardware &amp; Laptops
---

### Post by Piwai on 2007-01-01
Hi all !!

First of all, I wish you a happy new year !!

Well, I'm having some little trouble getting my thinkpad T42 working with Bluetooth, on Edgy. I'm even wondering if it isn't broken, or whatever.

I followed some tutorials to install Bluetooth, they are quite simple in fact, here is the summary :

```

sudo apt-get install nautilus-sendto
sudo apt-get install bluez-utils
sudo apt-get install bluez-pin
sudo apt-get install bluez-pcmcia-support
sudo apt-get install gnome-bluetooth

```

And then that's about all.

Well, in fact it's not working at all. I searched in the Internet for a long time, and well, I couldn't find any interesting answer.

Let me show you what I get with a few different commands :

```
sudo /etc/init.d/bluetooth restart
 * Restarting Bluetooth services                                                                                                                                     [ ok ]
```

```
hcitool scan
Device is not available: No such device
```

```
hcitool dev
Devices:
```

This may be interesting :
```
cat /proc/acpi/ibm/bluetooth
status:         not installed
```
```
ls /proc/acpi/ibm
bay  beep  bluetooth  brightness  cmos  driver  ecdump  fan  hotkey  led  light  thermal  video  volume  wan
```
```
 lsmod | grep ibm
ibm_acpi               28672  1
```

Well... So, you know, I'm quite new to Linux, and I'm doing my best to enjoy it and try to find the solution by myself, but there... I'm even wondering if I really have bluetooth material (well, I should).

Thx a lot

Piwai

PS : I hope you'll get the meaning of what I'm writing, I'm sorry my English is poor, but I'm doing my best to be understood.

---

### Post by Piwai on 2007-01-02
No idea ?

---

### Post by neoflight on 2007-01-02
just a dumb question.... r u sure, bluetooth hardware is in ur thinkpad...? i dont have it in my thinkpad 42... unless if u bought one and installed !!!

---

### Post by albesan on 2007-01-11
hello,

I'm getting the same kind of behavior and wondering wether the machine has the hardware or not.

I would have thought that you'd get some sort error message or warning when starting the service up. Then again I'm new to all this.



I'm on a Dell inspiron 6400 Intel Core Duo. Edgy. Everything else worked OOTB.

---

### Post by omarino on 2007-03-08
Same on my nx7400!
And bluetooth is installed. I opened the box and checked - it's a Broadcom 2045 bluetooth on USB0.
o.

---

### Post by beercz on 2007-03-13
I have exactly the same problem on by HP Compaq nx7400.

I recently upgraded to feisty and it has stopped working.

It worked running edgy (and dapper prior to that).

Any ideas anyone?

---

### Post by rrwo on 2007-04-04
I have the same problem with my ThinkPad Z60m. No Bluetooth devices on Edgy after upgrading, but it does have bluetooth hardware. I've just noticed the problem as I've gotten a bluetooth device to finally use.

---

### Post by rrwo on 2007-04-04
I just found something here: [http://www.thinkwiki.org/wiki/ThinkPad_Bluetooth_with_Enhanced_Data_Rate_%28BDC-2%29]("http://www.thinkwiki.org/wiki/ThinkPad_Bluetooth_with_Enhanced_Data_Rate_%28BDC-2%29")

Use Fn-F5 to enable your bluetooth device.

---

