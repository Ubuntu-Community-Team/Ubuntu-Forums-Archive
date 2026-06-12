---
title: "&quot;urb failed&quot; lirc Novat500 &quot;dosent exist dev/lirc0&quot;"
date: 2010-12-10
forum: Hardware
---

### Post by neco on 2010-12-10
At boot appears a "rc submit urb failed"

> dib0700: rc submit urb failed

> ```
uname -r
```
2.6.35-23-generic-pae

And i think my lirc configuration issues  must be related with that message. Because only 2 times of a lot of trys i succesfully have my remote working (the one that comes with my card tuner).

Data:

> ```
dmesg | grep DVB
```
dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
DVB: registering adapter 0 frontend 0 (DiBcom 3000MC/P)...
DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
DVB: registering adapter 1 frontend 0 (DiBcom 3000MC/P)...
input: IR-receiver inside an USB DVB receiver as /devices/pci0000:[LIST]
[/LIST]00/0000:00:08.0/0000:01:08.2/usb3/3-1/input/input5
dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.

> ```
cat /proc/bus/input/devices
```
I: Bus=0003 Vendor=2040 Product=9950 Version=0100
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:01:08.2-1/ir0
S: Sysfs=/devices/pci0000:00/0000:00:08.0/0000:01:08.2/usb3/3-1/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=14afc336 294284f 0 0 0 4 80158000 2190 40000801 9e96c0 0 900240 10004ffc

> ```
sudo aptitude install lirc lirc-x
```
I select: Hauppauge novaT500, transmitter none and input event5


> ```
lsmod | grep ir
```
nf_nat_irc              1168  0 
nf_conntrack_irc        3348  1 nf_nat_irc
nf_nat                 16289  4 ipt_MASQUERADE,iptable_nat,nf_nat_irc,nf_nat_ftp
nf_conntrack           63258  9 ipt_MASQUERADE,iptable_nat,xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp

> ```
ps -A | grep lirc
```
3102 ?        00:00:00 lircd

It is running but no ir module loaded, even not /dev/lirc0 . Anyway i try:
> 
```
sudo irrecord novaT500 -H devinput -d /dev/input/event5
```
....
Hold down an arbitrary button.
*(I press any button)*
irrecord: gap not found, can't continue
irrecord: closing '/dev/input/event5'

So its not working, i have been around this issue for weeks, and i claim for help, it is so frustrating for me, weeks reading but nothing works ](*,) :cry: Any help would be very apreciated

Neco

---

