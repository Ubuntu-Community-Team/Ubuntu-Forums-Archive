---
title: "NXT LejOS"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by rp181 on 2009-04-12
I have a NXT Lego Mindstorms brick, and i am trying to download lejos firmware to it.

When running  nxjflash (supposed to download firmware to it) i get this message:
/usr/share/lejos/bin>
/usr/share/lejos/bin/nxjflash
VM file: /usr/share/lejos/bin/lejos_nxt_rom.bin
Menu file: /usr/share/lejos/bin/StartUpText.bin
VM size: 48096 bytes.
Menu size: 32527 bytes.
Total image size 80655/81920 bytes.
Found nxt name %%NXT-SAMBA%% address 1
Failed to open device in SAM-BA mode.

I think this is a permissions problem, what do you guys think? I cant figure out how to get it to work.

---

### Post by jose2000web on 2009-05-04
I had the same problem until I decided to access as a root  using su
and my password and it worked!

---

### Post by lingonl on 2010-12-07
The system recognizes the nxt brick as some kind of acm device:
(/var/log/messages)
```
usb 3-1: new full speed USB device using ohci_hcd and address 4
cdc_acm 3-1:1.0: ttyACM0: USB ACM device
usbcore: registered new interface driver cdc_acm
cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
```When the nxjflash tool is executed this happens:
(/var/log/messages)
```
usb 3-1: usbfs: interface 0 claimed by cdc_acm while 'java' sets config #1
```A fix for this would be to blacklist the cdc_acm kernel module:
(/var/log/messages)
add:
```
blacklist cdc_acm
```And make sure the cdc_adm is unloaded:
```

sudo rmmod cdc_acm
```

---

### Post by lkjoel on 2010-12-29
Thanks lingonl!

For others reading this, and who don't know how to blacklist cdc_adm, simply type this into a terminal:
```
sudo -s
echo "" >> /etc/modprobe.d/blacklist.conf
echo "blacklist cdc_adm" >> /etc/modprobe.d/blacklist.conf

```

I hope this helps!

---

### Post by bastia3 on 2011-01-12
Hi guy
i have your same problem and i have fix it with your suggestions!
i confirm that is the solution!!
thanks

---

### Post by cinus on 2011-07-22
HI,

you can solve this problem by flashing the ROM using nxjflash with root privileges. You should only take care that the root user has access to the nxjflash (add the bin directory of the place where you installed lejos, e.g export PATH=/path/to/lejos/bin:$PATH , this should be done as root).

Then you flash the NXT 2.0 without any problems.

I had to perform also the step to remove the cmc_acm (rmmod)

---

