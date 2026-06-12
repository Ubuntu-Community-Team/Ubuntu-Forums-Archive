---
title: "Bluetooth pairing problem"
date: 2005-12-15
forum: Hardware &amp; Laptops
---

### Post by ggore on 2005-12-15
My Ubuntu machine's Bluetooth setup works pretty much OK, I can transfer files back & forth from it to a Powerbook and a SUSE machine on my network.  But when I try to pair my Motorola HS850 headset with it using Kbluetooth I get a message from Kbluetooth "Pairing not allowed".    The box never pops up to enter the passcode either.   What am I doing wrong, I can't find a single article on the internet that tells how to set up and use Kbluetooth, not even on their site!

---

### Post by hscottyh on 2006-01-02
I would like to know too, getting the exact same problem with the exact same headset.

---

### Post by hscottyh on 2006-01-02
Ok, still not hearing audio. I just issued the command btsco -v 00:00:00:00:00:00 where the zero's are the mac address of the device. Without  kbluetoothd running. It asked for a password, I entered 0000 and everything seems to connect. 

But still not hearing any sound, but I do here a beep when I try to send music to it with xmms and a beep when I stop it.

I'll post an update when it's actually usable.

---

### Post by hscottyh on 2006-01-03
Udate: Tried it with gnomemeeting and the mic works, I just don't get audio back. Anybody got any ideas?

---

### Post by hscottyh on 2006-01-04
Everything is now working great! It ended up being the dongle. To get audio working in both directions in linux, it seems you have to have a bluetooth adapter with the CSR chipset, 'Cambridge Silicon Radio'.

If you execute: 
**sudo hciconfig hci0 revision**

and don't have this line in the output:

**SCO mapping:  HCI**

then, it's almost certain it won't work.

I'm now using a DLINK DBT-120 dongle. 
I hope this saves someone some time.

---

### Post by Tavathlon on 2006-03-03
hscottyh, so you do use this dongle (DBT-120) for bluetooth headsets? I have an Ericsson headset, and the first dongle I bought (from MSI; I don't remember the exact model, since I returned it to the store today) did not work very well. As I have understood it, the model of the headset is a minor problem, it is more about the dongle. Am I right?

---

### Post by anders.ostling on 2006-03-28
I do have an usb dongle, and the same problem as you mentioned (beeps instead of music). Here is my config

anos@zoolog:~$ sudo hciconfig hci0 version
hci0:   Type: USB
        BD Address: 00:10:60:A4:F6:CC ACL MTU: 192:8 SCO MTU: 64:8
        HCI Ver: 1.1 (0x1) HCI Rev: 0x460 LMP Ver: 1.1 (0x1) LMP Subver: 0x460
        Manufacturer: Cambridge Silicon Radio (10)

anos@zoolog:~$ sudo hciconfig hci0 revision
hci0:   Type: USB
        BD Address: 00:10:60:A4:F6:CC ACL MTU: 192:8 SCO MTU: 64:8
        HCI 17.11
        Chip version: BlueCore02
        Max key size: 128 bit
        SCO mapping:  HCI

anos@zoolog:~$ sudo hciconfig hci0 features
hci0:   Type: USB
        BD Address: 00:10:60:A4:F6:CC ACL MTU: 192:8 SCO MTU: 64:8
        Features: 0xff 0xff 0x0f 0x00 0x00 0x00 0x00 0x00
                <3-slot packets> <5-slot packets> <encryption> <slot offset>
                <timing accuracy> <role switch> <hold mode> <sniff mode>
                <park state> <RSSI> <channel quality> <SCO link> <HV2 packets>
                <HV3 packets> <u-law log> <A-law log> <CVSD> <paging scheme>
                <power control> <transparent SCO>

If you have any hints on how to replace the beeps with nice music, please let me know!

Anders

---

### Post by hartogvdb on 2006-06-19
I have an Acer Ferrari with built in bluetooth that doesn't want to know about pairing my headset. 
Does anybody understand what is missing. My friend has many more features on his Dell. 
Is there any documentation of what these features do or represent?

It shows the following details:
hartog@ferrari:~$ sudo hciconfig hci0 revision
hci0:   Type: USB
        BD Address: 00:0B:6B:91:50:62 ACL MTU: 377:10 SCO MTU: 64:8
        Firmware 105.105 / 74
hartog@ferrari:~$ sudo hciconfig hci0 features
hci0:   Type: USB
        BD Address: 00:0B:6B:91:50:62 ACL MTU: 377:10 SCO MTU: 64:8
        Features: 0xff 0xff 0x0d 0x38 0x08 0x08 0x00 0x00
                <3-slot packets> <5-slot packets> <encryption> <slot offset>
                <timing accuracy> <role switch> <hold mode> <sniff mode>
                <park state> <RSSI> <channel quality> <SCO link> <HV2 packets>
                <HV3 packets> <u-law log> <A-law log> <CVSD> <power control>
                <transparent SCO> <enhanced iscan> <interlaced iscan>
                <interlaced pscan> <AFH cap. slave> <AFH cap. master>
hartog@ferrari:~$ sudo hciconfig hci0 version
hci0:   Type: USB
        BD Address: 00:0B:6B:91:50:62 ACL MTU: 377:10 SCO MTU: 64:8
        HCI Ver: 1.2 (0x2) HCI Rev: 0x69 LMP Ver: 1.2 (0x2) LMP Subver: 0x694a
        Manufacturer: Broadcom Corporation (15)

---

### Post by mimsmall on 2007-02-02
DBT120 works for me on my hp pavilion ze4400. I would try this dongle before tearing hair out.

---

