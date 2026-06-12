---
title: "Bluetooth headphones paired but only mono and poor quality"
date: 2016-09-24
forum: Hardware
---

### Post by teafan on 2016-09-24
Hello,
I Bought a new pair of bluetooth headphones the other day (Bluedio T2 Bluetooth Stereo Headphones), however I cannot get them to work properly with Ubuntu. I can connect and pair however they only play in mono and the sound is poor, which im putting down to the mono. When I open up sound settings they up as mono also. 

Perhaps this is because of the bluetooth adapter I'm using which maybe does not support Bluetooth 4.1 (the headphones). The headphones work great with my other devices; tv - and I also don&#8217;t want to shell out more money on a new adapter without knowing if this is actually the fault.

So this is my bluetooth adapter information...
```
hciconfig -a hci0
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 5C:F3:70:14:12:22  ACL MTU: 1022:8  SCO MTU: 121:3
    DOWN 
    RX bytes:4470 acl:42 sco:0 events:325 errors:0
    TX bytes:215303 acl:258 sco:0 commands:159 errors:103
    Features: 0xff 0xfe 0x0d 0xfe 0x98 0x7f 0x79 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF 
    Link mode: SLAVE ACCEPT 


```



Please help figure this out and allow me to enjoy music. **Thanks**. :)

---

### Post by jeremy31 on 2016-09-25
Are you using Ubuntu 16.04?  If so watch [https://ubuntuforums.org/showthread.php?t=2335154](https://ubuntuforums.org/showthread.php?t=2335154)

The only way I can get my headphones to switch to A2DP(high quality audio) is to
```
pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` off; sleep 2 ; echo -e "disconnect AC:9B:0A:4F:CA:FF\n quit"|bluetoothctl;sleep 5; echo -e "connect AC:9B:0A:4F:CA:FF\n quit"|bluetoothctl; sleep 5; pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` a2dp_sink
```

Replace AC:9B:0A:4F:CA:FF with the MAC address of your headset, the MAC is in the command twice

---

### Post by teafan on 2016-09-25
Thanks jeremy31. I will keep an eye on that thread, .. sortof nice to see other people in the same boat, but still annoying. ](*,)

Infact, this is my temporary computer running 15.10. I should be using my other computer later this week (16.04), but i suspect the fault will be the same on that too.

BTW, Does this command work if you add it to startup applications?



Also, as anyone tried buying one of those bluetooth to Transmitter/Receiver adapters which connect to the stereo (AUX), and use one of them instead of other conventional bluetooth. Because perhaps that when you connect to the bluetooth Transmitter/Receiver it will connect to the stereo port without the operating system bugging out.

---

### Post by jeremy31 on 2016-09-26
The bluetooth that plugs into an audio jack should work.  I haven't tried adding the command to startup applications as I have sound muted 90% of the time

I don't remember having these issues on 15.10 but I updated to 16.04 very soon after release and there is a chance a later update caused the issue in 15.10

---

### Post by teafan on 2016-09-26
I would love to know if anyone has tried using a bluetooth audio jack adapter and whether it can bypass this issue before I spend money buying one. Sadly i know nobody with one so I can test it out.

Do you know if this is a bug related to the sound card, bluetooth adapter, or the actual heaset? I'm hoping maybe it will work fine on my other computer with different hardware, when it comes back. - being a different sound card, bluetooth, ect.

Also, my bt headphones have a mic and volume control.

Sorry to double post. But I’ve tried the headphones on my laptop using the bluetooth built in (different adapter) on 16.04 and they work perfectly. - So I can rule out the headphones, so I'm thinking its either the bluetooth adapter or the software on 15.10.

I think I will just wait until my main computer comes back from fixing and just cross my fingers... perhaps even get a new adapter if necessary. :)

---

### Post by jeremy31 on 2016-09-26
Recent reports make me think it is related to Pulse Audio 8 that is used in Ubuntu 16.04.  My own experience with a Logitech headset with its own dongle seem to reinforce this idea as I have issues with sound from them and nothing in Ubuntu can see it as a bluetooth device when it is plugged in

---

