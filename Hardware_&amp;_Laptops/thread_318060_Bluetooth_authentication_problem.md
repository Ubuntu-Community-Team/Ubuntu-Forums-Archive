---
title: "Bluetooth authentication problem"
date: 2006-12-13
forum: Hardware &amp; Laptops
---

### Post by chiefofthejojos on 2006-12-13
Hi everyone,
I just got a new laptop, an HP Pavilion dv2000z and I'm trying to get the built-in bluetooth to work.  The hardware seems to be fine because I can scan and get all sorts of information out.  I'm just having trouble pairing.  When I run "hcitool auth" I get "HCI authentication request failed: Input/output error".  Here's a log:
```
brad@brad-laptop:~$ sudo hcitool dev
Devices:
        hci0    00:16:41:F2:D9:87
brad@brad-laptop:~$ hcitool scan
Scanning ...
        00:16:DB:19:D4:72       myphone
brad@brad-laptop:~$ hcitool cc 00:16:DB:19:D4:72
brad@brad-laptop:~$ sudo hcitool con
Connections:
        < ACL 00:16:DB:19:D4:72 handle 11 state 1 lm MASTER 
brad@brad-laptop:~$ sudo hcitool info 00:16:DB:19:D4:72
Requesting information ...
        BD Address:  00:16:DB:19:D4:72
        Device Name: myphone
        LMP Version: 1.2 (0x2) LMP Subversion: 0x512
        Manufacturer: Cambridge Silicon Radio (10)
        Features: 0xff 0xff 0x8f 0xf8 0x18 0x18 0x00 0x80
                <3-slot packets> <5-slot packets> <encryption> <slot offset> 
                <timing accuracy> <role switch> <hold mode> <sniff mode> 
                <park state> <RSSI> <channel quality> <SCO link> <HV2 packets> 
                <HV3 packets> <u-law log> <A-law log> <CVSD> <paging scheme> 
                <power control> <transparent SCO> <broadcast encrypt> 
                <enhanced iscan> <interlaced iscan> <interlaced pscan> 
                <inquiry with RSSI> <extended SCO> <AFH cap. slave> 
                <AFH class. slave> <AFH cap. master> <AFH class. master> 
                <extended features> 
brad@brad-laptop:~$ sudo hcitool inq
Inquiring ...
        00:16:DB:19:D4:72       clock offset: 0x3065    class: 0x500204
brad@brad-laptop:~$ sudo hcitool auth 00:16:DB:19:D4:72
HCI authentication request failed: Input/output error
```

any ideas?

EDIT:  Oh yeah, I'm running Edgy with the latest updates

---

### Post by christhemonkey on 2006-12-13
I think you need to be disconnected from the device before you can commence pairing with it, hence it throwing out an Input/output error.

So try disconnecting:
```
hcitool dc 00:16:DB:19:D4:72
```

And then try pairing:
```
sudo hcitool auth 00:16:DB:19:D4:72
```

---

### Post by chiefofthejojos on 2006-12-13
> **christhemonkey said:**
> I think you need to be disconnected from the device before you can commence pairing with it, hence it throwing out an Input/output error.

So try disconnecting:

Thanks for your help.  I tried that and received the simple message "Not connected."  To give you a bit of context, I'm attempting to setting up Bluetooth DUN on my laptop using the ubuntu community help guide [here]("https://help.ubuntu.com/community/BluetoothDialup").  I have done it on several different ubuntu computers before, but never with edgy, perhaps it simply hasn't been updated yet?

---

### Post by chiefofthejojos on 2006-12-13
happily for me, I just tried this on a different machine with a different bluetooth adapter (which worked with dapper before) and it also gives the same error message in edgy.  This supports my idea that my hardware works and there's only a software problem, I think.

---

### Post by fishwithapipe on 2006-12-14
I am guessing your running kubuntu, as most gnome users dont seem to be having any problems with this, and its been a while since i managed to get this working.

I installed the latest obex and bluez utils available from the universe, not main repo then downloaded the kdebluetooth 1.0beta2 source from kdebluetooth i think its moved to kmobiletools.org now then make && sudo make install over the software from the repos.

The current beta of kdebluetooth contains a fix for the pluez-pin app which was broken as they try to move the whole architechture to dbus, there was a bug on launchpad about this but nothing appear to have been done.

sorry i cant give perfect instructions but maybe this will help.

---

### Post by chiefofthejojos on 2006-12-15
actually no, I'm not using Kubuntu.  I'm actually a little perturbed at Edgy right now.  Why are all the guides missing steps?  I just downgraded to dapper, which the guide I was looking at was meant for, and I finally got it working -- AFTER making an extra tweak to the /etc/bluetooth/hcid.conf file.  This was on a perfectly clean new install.  I'm guessing there's probably one little undocumented tweak that needs to be made in Edgy before bluetooth pairing will work.  The tweak in dapper was to change the pin_helper to /usr/bin/bluepin, but Edgy doesn't have that file so I don't know what to do anymore.
You say gnome users aren't having any issues?  Are you saying because of lack of complaints, or because you have actually heard people say they have it working?  If it is the latter please kindly point the way for me.

---

### Post by chiefofthejojos on 2006-12-15
Ok, I finally got it working.  It was as "simple" as pasting this into my terminal:
```
dbus-send --system --dest=org.bluez /org/bluez/hci0 org.bluez.Adapter.SetMode string:discoverable
```
and then using the phone to pair with the computer.

---

### Post by Max Ischenko on 2006-12-24
> **chiefofthejojos said:**
> Ok, I finally got it working.
Good for you. I have been having exactly the same problem (I/O error on auth command) and cannot get it to work. I tried to initiated pairing from my phone (Nokia E61) but it says "unsupported device". I edited hcid.conf to use /usr/bin/bluepin -- didn't help either.

Any ideas what else should I try?

```
max@max-laptop$ hciconfig
hci0:   Type: USB
        BD Address: 00:0F:B3:90:16:B7 ACL MTU: 192:8 SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN
        RX bytes:2275 acl:37 sco:0 events:137 errors:0
        TX bytes:1673 acl:44 sco:0 commands:55 errors:0
max@max-laptop$ sudo hcitool auth 00:12:D2:2C:3B:FB
HCI authentication request failed: Input/output error

```


I am using 6.06 Dapper release.
PS:  The weird thing it used to work just fine! I still have some files on my phone transferred via Bluetooth.

---

### Post by Max Ischenko on 2006-12-24
> **Max Ischenko said:**
> 
I am using 6.06 Dapper release.
PS:  The weird thing it used to work just fine! I still have some files on my phone transferred via Bluetooth.

I got it working. The key was to delete /var/lib/bluetooth/* dir. After I did that and run cc command a popup appear asking for a pin on both pc and my phone.

Argh.

---

### Post by willywongi on 2006-12-26
ah, neither for me it's working- I've edgy. I got the same error from the shell (I/O error), and if I try to send a file from Nautilus it hang on searching devices but can't find a thing: note that "hcitool scan" works. But! if I try to send a file from the phone to pc it works flawlessly (and it doesnt ask for a pin). 

The thing I hate of those apps, applets and command line tools is that I can't find documentation or at least a config file. Where I've to look? Maybe I'm a complete n00b..??!!

---

### Post by elektronaut on 2007-01-07
[It's a known bug in gnome-bluetooth.](https://launchpad.net/bugs/70718) Look at Marcel's workaround. You have to call 'sudo hciconfig hci0 inqmode', if you write this in /etc/rc.local, it'll be executed during boot.

---

