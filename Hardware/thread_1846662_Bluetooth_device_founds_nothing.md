---
title: "Bluetooth device founds nothing"
date: 2011-09-19
forum: Hardware
---

### Post by maarawoe on 2011-09-19
Hi,
I have a problem with bluetooth on my HP 4320s laptop running Ubuntu 11.10 beta (daily updated....) which is using some ralink bt device....

```
sudo hciconfig
hci0:	Type: BR/EDR  Bus: USB
	BD Address: E0:2A:82:26:00:DD  ACL MTU: 310:10  SCO MTU: 64:8
	UP RUNNING PSCAN 
	RX bytes:3392 acl:0 sco:0 events:153 errors:0
	TX bytes:3837 acl:0 sco:0 commands:137 errors:0

sudo hcitool dev
Devices:
	hci0	E0:2A:82:26:00:DD


lsmod | grep blue
bluetooth             166112  23 bnep,rfcomm,btusb

```

So the device is ok, module is loaded but when I try to discover any bt devices (using hcitool or the gnome/unity applet) I get no result - simply no devices were found even they are there and all of them are discoverable (I can see them on my second laptop and on my smartphone as well...)

```
sudo hcitool scan
Scanning ...
```



I have been messing around the forums whole day and tried various solutions (reinstalling bluez from the deb and from the repository, manual restarts of bluetoothd etc...) but it doesn't work...

Any idea?

Thanks

---

### Post by typhoon22 on 2011-12-15
I've got the same on 11.10. I've tried the hci tools, no luck.

Interestingly, sdptool browse <hwaddr of my phones bluetooth> returns all the stuff.

I have written a perl script, here is the code (hey I never said it was *good* :D):

> #!/usr/lib/perl

#includes
use Net::Bluetooth;
use strict;
my $addr;
my $rec_ref;
my $attr;


my $device_ref = get_remote_devices();
  foreach $addr (keys %$device_ref) {
        print "Address: $addr Name: $device_ref->{$addr}\n";
  }


#### search for a specific service (0x1101) on a remote device, 1132 is sms on an SGS2; 1101 is something else
  my @sdp_array = sdp_search($addr, "1132", "");

  #### foreach service record
  foreach $rec_ref (@sdp_array) {
        #### Print all available information for service
        foreach $attr (keys %$rec_ref) {
                print "Attribute: $attr Value: $rec_ref->{$attr}\n";
        }
  }


No returns for either.

I'm completely stuck. My laptop is discoverable from my phone, but my laptop cannot discover anything.

The device id is: 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter

---

