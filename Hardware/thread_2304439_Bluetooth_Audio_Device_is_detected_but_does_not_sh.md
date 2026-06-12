---
title: "Bluetooth Audio Device is detected but does not show up in sound settings"
date: 2015-11-26
forum: Hardware
---

### Post by ubootfanat on 2015-11-26
Hi guys and gals,

After looking everywhere I finally have to ask for help. My issue concerns a bluetooth audio "headset" i.e. a audio receiver which one can connect to the TV or the Hifi Tower ([http://www.p4c.philips.com/cgi-bin/dcbint/cpindex.pl?slg=en&ctn=AEA2700/12]("http://www.p4c.philips.com/cgi-bin/dcbint/cpindex.pl?slg=en&ctn=AEA2700/12")).
[B]
The bottom line is:[/B]
it does not get recognized by pulseaudio i.e. the device is not listed in sound settings

**In detail:**
[LIST]
[*] the device is paired successfully
[*] the bluetooth settings says that it is an "audio device"
[*] pulseaudio (the sound settings) does not recognize the device
[/LIST]
here is the catch: I tried an old bluetooth headset I had hadn't used for a long time it is recognized as "headset" and is readily treated as headset voice gateway by bluetoothd

**Now the question:**
Is there a list of supported devices or connected devices for pulseaudio? Can I somehow convince pulseaudio to accept the device in question as an audio device? How can I debug into this more?

**subsequent info:**
syslog on pairing
```

Nov 26 21:11:22 mine bluetoothd[1079]: /org/bluez/hci0/dev_0C_A6_94_9A_39_E6/fd3: fd(22) ready
Nov 26 21:11:22 mine rtkit-daemon[1076]: Supervising 8 threads of 2 processes of 2 users.
Nov 26 21:11:22 mine rtkit-daemon[1076]: Successfully made thread 3620 of process 1075 (n/a) owned by '116' RT at priority 5.
Nov 26 21:11:22 mine rtkit-daemon[1076]: Supervising 9 threads of 2 processes of 2 users.
Nov 26 21:11:22 mine kernel: [ 2156.169827] input: 0C:A6:94:9A:39:E6 as /devices/virtual/input/input30
```

hcitool info output
```

Requesting information ...
	BD Address:  0C:A6:94:9A:39:E6
	OUI Company: Sunitec Enterprise Co.,Ltd (0C-A6-94)
	Device Name: Philips AEA2700
	LMP Version: 3.0 (0x5) LMP Subversion: 0x2578
	Manufacturer: Cambridge Silicon Radio (10)
	Features page 0: 0xff 0xff 0x8f 0xfe 0x9b 0xff 0x59 0x87
		<3-slot packets> <5-slot packets> <encryption> <slot offset> 
		<timing accuracy> <role switch> <hold mode> <sniff mode> 
		<park state> <RSSI> <channel quality> <SCO link> <HV2 packets> 
		<HV3 packets> <u-law log> <A-law log> <CVSD> <paging scheme> 
		<power control> <transparent SCO> <broadcast encrypt> 
		<EDR ACL 2 Mbps> <EDR ACL 3 Mbps> <enhanced iscan> 
		<interlaced iscan> <interlaced pscan> <inquiry with RSSI> 
		<extended SCO> <EV4 packets> <EV5 packets> <AFH cap. slave> 
		<AFH class. slave> <3-slot EDR ACL> <5-slot EDR ACL> 
		<sniff subrating> <pause encryption> <AFH cap. master> 
		<AFH class. master> <EDR eSCO 2 Mbps> <EDR eSCO 3 Mbps> 
		<3-slot EDR eSCO> <extended inquiry> <simple pairing> 
		<encapsulated PDU> <non-flush flag> <LSTO> <inquiry TX power> 
		<EPC> <extended features> 
	Features page 1: 0x01 0x00 0x00 0x00 0x00 0x00 0x00 0x00
```

can you hint me the right direction?

Thanks!

---

### Post by jeremy31 on 2015-11-26
Does ```
pactl list short
``` show module-bluetooth-discover?  If it doesn't
```
pactl load-module module-bluetooth-discover
```

You may have to delete the pairing and pair again

---

### Post by ubootfanat on 2016-01-02
Hi, thanks for the hint.

But as I said earlier, the device does pair quite nicely. It "only" does not show in the list of available sound devices.

```
% pactl list short | grep blue
8	module-bluetooth-policy		
9	module-bluetooth-discover		
10	module-bluez5-discover
```

This is how the gnome system settings presents me the remote device: [ATTACH=CONFIG]266507[/ATTACH]

Any other hints? How does the sound device list select suitable devices?

Thanks again!

---

