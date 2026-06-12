---
title: "Dell 355 internal bluetooth, please help"
date: 2007-02-20
forum: Hardware &amp; Laptops
---

### Post by redman0570 on 2007-02-20
I have a Dell E1505 running Edgy EFT will Dell 355 internal Bluetooth, specs below.  The internal Bluetooh does don't work, see details below.  The 355 bluetooth adapter works well in Win MCE2005.  I've attached an Ultra USB dongle and it works fine, I've also attach a USB cradle for a logitech bluetooth mouse and it works file also.  The internal Dell 355 is not work for me with Ubuntu, can anyone help?

-Intel® Core 2 Duo processor T5600
-15.4 inch Wide Screen XGA Display with TrueLife
-1GB DDR2 SDRAM
-Network Card and Modem Integrated 10/100 Network Card and Modem
-Optical Drive 8X CD/DVD Burner (DVD+/-RW) with double-layer DVD+R write capability
-Integrated Audio
-Dell Wireless 
-Dell Wireless 355 Bluetooth Internal (2.0 + Enhanced Data Rate) 

I've installed Bluez these two ways,

	sudo apt-get install bluez-utils

	sudo apt-get install bluetooth bluez-utils bluez-pin bluez-passkey-gnome gnome-bluetooth libbluetooth2 libbtctl4 libgnomebt0 nautilus-sendto

I've installed and apt-get removed a couple times to make sure it is completely installed.

hcitool dev

Devices:
        hci0    00:16:CF:FA:7A:8C

hciconfig -a

hci0:   Type: USB
        BD Address: 00:16:CF:FA:7A:8C ACL MTU: 1017:8 SCO MTU: 64:1
        UP RUNNING 
        RX bytes:233 acl:0 sco:0 events:30 errors:0
        TX bytes:621 acl:0 sco:0 commands:30 errors:0
        Features: 0xff 0xff 0x8f 0xfe 0x9b 0xf9 0x00 0x80
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
        Link policy: RSWITCH HOLD SNIFF PARK 
        Link mode: SLAVE ACCEPT 
Can't read local name on hci0: Input/output error (5)

hciconfig hci0 reset

	Can't down device hci0: Permission denied (13)

hcitool scan
Scanning ...
Inquiry failed: Connection timed out

hcitool inq

Inquiring ...
Inquiry failed.: Connection timed out	

sudo hciconfig hci0 inqmode 0
Can't set inquiry mode on hci0: Input/output error (5)

Am I missing something?  Why is this nothing working?  Is the Dell 355 working for anyone else.

I'm read a lot of bluetooth setup guides but none seem to address my problem and/or my device.

---

### Post by fordracerguy on 2007-03-01
I have the same exact problem and error messages... It's really bizarre that the kernel says it finds the bluetooth butyet it doesn't work.

Doesn't anyone know how to get the dell 355 bluetooth working?

---

### Post by fordracerguy on 2007-03-01
Just got it working. hciconfig hci0 reset got it to work...

How to make this manual on startup I don't know yet. :)

---

### Post by redman0570 on 2007-03-02
Yes, after long research I got it to work.

Manually you have to do
 
sudo hciconfig hci0 reset

I was missing the sudo.

To make it start automatically to this.

add the 'hciconfig hci0 reset' to /etc/rc.local file.  Anywhere before the exit 0.  Do not add the sudo command to the rc.local file.

Everything should work great!  So far every bluetooth device I have works fine and connects on boot up automatically.

---

### Post by Xamindar on 2007-03-26
This is a weird issue.  I had this dell bluetooth working fine sense I bought my laptop back in November.  Then, one day it all of a sudden had this problem.  It seemed to start around the time I installed Vista on the other half of the drive.

Anyway, thanks for the fix!  Gentoo forums were no help.  But I have now switched over to Ubuntu on my lappy and I love it!

---

### Post by ctschap on 2007-04-09
Thank you redman. I have been searching for a few days now on how to get the internal bluetooth module to work after it mysteriously stopped.
The hci0 reset command worked like a charm.

---

### Post by zeddock on 2007-04-15
> **ctschap said:**
> Thank you redman. I have been searching for a few days now on how to get the internal bluetooth module to work after it mysteriously stopped.
The hci0 reset command worked like a charm.

I have been searching but the above fix does not work either for me....   but I am happy for the rest of you!

Can someone help me with BT?

I am on a Dell Latitude D800.  I know there is some function working because if I hit Fn+F2 keys and give the command...
hcitool scan

it gives me:
Device is not available: No such device

But if I hit same again and give the hcitool scan command I get:

Scanninig...

Then after a few seconds I get nothing but a prompt.  No timeout, or any other indication.

Thanx!
zeddock

---

### Post by Xamindar on 2007-04-16
Sounds like yours is working fine.  It would only show something if you have another active bluetooth device nearby.  Make sure your device that you are trying to scan for is broadcasting its self for a connection.  I know motorolla phones for example only turn it on for a minute then turn off again.

---

### Post by zeddock on 2007-04-16
> **Xamindar said:**
> Sounds like yours is working fine.  It would only show something if you have another active bluetooth device nearby.  Make sure your device that you are trying to scan for is broadcasting its self for a connection.  I know motorolla phones for example only turn it on for a minute then turn off again.

I have tried both a bt headset and a cell phone. 
Both were broadcasting when attempted each.
Both were on top of laptop and in other close proximity.
Scan finds nothing and soon gives prompt without error.

zeddock

---

### Post by Unicast on 2007-07-21
```
sudo hciconfig hci0 reset
```

Got me going as well. :D

Wasted 5 frikkin hours today trying to get my BT dongle to work, and time after time I kept getting:

```
Scanning ...
Inquiry failed: Connection timed out
```

Anyway, all working now thanks to this neat trick!

Thanks guys! ;)

---

### Post by sr20ve on 2007-07-26
> **zeddock said:**
> I have been searching but the above fix does not work either for me....   but I am happy for the rest of you!

Can someone help me with BT?

I am on a Dell Latitude D800.  I know there is some function working because if I hit Fn+F2 keys and give the command...
hcitool scan

it gives me:
Device is not available: No such device

But if I hit same again and give the hcitool scan command I get:

Scanninig...

Then after a few seconds I get nothing but a prompt.  No timeout, or any other indication.

Thanx!
zeddock

I have an E1505 with this same problem. I can use and external dongle and it works fine, but I just can't get the internal to work.

The hciconfig hci0 reset command does not work because I don't have an hci0 in my /dev folder. Is there a way to manually add it as a device?

---

### Post by Xamindar on 2007-07-26
> **sr20ve said:**
> I have an E1505 with this same problem. I can use and external dongle and it works fine, but I just can't get the internal to work.

The hciconfig hci0 reset command does not work because I don't have an hci0 in my /dev folder. Is there a way to manually add it as a device?

In your case it sounds like you don't even have the correct kernel module loaded.  Did you double check that?  

That's all I can think of.

---

### Post by Arne_M on 2007-10-01
hi 
I've got the same problem - what modules do I need for my internel device?

Arne

---

### Post by jsa13 on 2008-03-11
Mine worked fine immediately after the hardware install and flipping the wireless enable switch.  

I had already done the necessary "sudo apt-get install <blah>" and tweaks to get my [Belkin CF/PCMCIA card working]("http://ubuntuforums.org/showthread.php?t=711239").  I had my Dell D620's wireless switch turned off.  Once I enabled it the bluetooth indicator came on and up popped the notifier.  I'm using Ubuntu Gutsy 7.10.

---

### Post by Xamindar on 2008-03-12
> **jsa13 said:**
> Mine worked fine immediately after the hardware install and flipping the wireless enable switch.  

I had already done the necessary "sudo apt-get install <blah>" and tweaks to get my [Belkin CF/PCMCIA card working]("http://ubuntuforums.org/showthread.php?t=711239").  I had my Dell D620's wireless switch turned off.  Once I enabled it the bluetooth indicator came on and up popped the notifier.  I'm using Ubuntu Gutsy 7.10.



Yes it works.  As you can see, the last post in this forum was back in october of 2007.  Mine has been working for quite some time now without that command in startup.  I suspect they fixed the driver.

---

