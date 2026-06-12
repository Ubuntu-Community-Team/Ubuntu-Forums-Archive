---
title: "JBL flip 3 No sound from bluetooth audio device"
date: 2016-11-26
forum: Hardware
---

### Post by catalyst1987 on 2016-11-26
Hello,
    I am currently having issues with my JBL Flip 3 audio device.  I can connect the bluetooth speaker to my Ubuntu 16.04 desktop, but no sound comes out of it.  See attached pulseverbose log.  Any assistance would be greatly appreciated.

Many Thanks.

---

### Post by jeremy31 on 2016-11-26
I would try this in terminal after connecting
```
pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` off; sleep 2 ; echo -e "disconnect B8:69:C2:7F:5D:5A\n quit"|bluetoothctl;sleep 5; echo -e "connect B8:69:C2:7F:5D:5A\n quit"|bluetoothctl; sleep 5; pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` a2dp_sink
```

Then see if sound works

---

### Post by catalyst1987 on 2016-11-26
> **jeremy31 said:**
> I would try this in terminal after connecting
```
pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` off; sleep 2 ; echo -e "disconnect B8:69:C2:7F:5D:5A\n quit"|bluetoothctl;sleep 5; echo -e "connect B8:69:C2:7F:5D:5A\n quit"|bluetoothctl; sleep 5; pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` a2dp_sink
```

Then see if sound works

Tried it.  Unfortunately it doesn't work.  Terminal shows that it tries to connect to my speaker but then does a 'quit'.

---

### Post by jeremy31 on 2016-11-26
What version of pulseaudio do you have ```
dpkg -l | grep pulseaudio
```

The quit you see in terminal is for it to leave bluetoothctl.  Can you check to see if I got the MAC correct for your speaker?  I think it is B8:69:C2:7F:5D:5A

---

### Post by catalyst1987 on 2016-11-26
> **jeremy31 said:**
> What version of pulseaudio do you have ```
dpkg -l | grep pulseaudio
```

The quit you see in terminal is for it to leave bluetoothctl.  Can you check to see if I got the MAC correct for your speaker?  I think it is B8:69:C2:7F:5D:5A

Yes, the MAC address is correct.  In regards to pulseaudio I have the following output:

```

ii  gstreamer1.0-pulseaudio:amd64                               1.8.2-1ubuntu0.2                              amd64        GStreamer plugin for PulseAudio
ii  pulseaudio                                                  1:8.0-0ubuntu3.1                              amd64        PulseAudio sound server
ii  pulseaudio-module-bluetooth                                 1:8.0-0ubuntu3.1                              amd64        Bluetooth module for PulseAudio sound server
ii  pulseaudio-module-x11                                       1:8.0-0ubuntu3.1                              amd64        X11 module for PulseAudio sound server
ii  pulseaudio-utils                                            1:8.0-0ubuntu3.1                              amd64        Command line tools for the PulseAudio sound server
```

---

### Post by jeremy31 on 2016-11-26
Can you use Sound Settings to switch between HSP/HFP and A2DP?  You do have the latest updates to pulseaudio

You could also see this [bug report](https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1577197) and see if that workaround works

---

### Post by catalyst1987 on 2016-11-27
> **jeremy31 said:**
> Can you use Sound Settings to switch between HSP/HFP and A2DP?  You do have the latest updates to pulseaudio

You could also see this [bug report]("https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1577197") and see if that workaround works


Tried manually changing from [COLOR=#333333][FONT=monospace]A2DP to [/FONT][/COLOR][COLOR=#333333][FONT=monospace]HSP/HFP and then back to A2DP, but no such luck.  

I think something might actually be physically wrong with the device itself as I tried plugging in an audio cable from the speaker to my iPad mini and couldn't get any sound to come from it.  

[/FONT][/COLOR]

---

### Post by jeremy31 on 2016-11-27
There was also a link to a python script on github that worked for some people- I wasn't one of them as I had to use the command I posted

EDIT: It seems the newest version works for me

---

### Post by catalyst1987 on 2016-12-01
> **jeremy31 said:**
> There was also a link to a python script on github that worked for some people- I wasn't one of them as I had to use the command I posted

EDIT: It seems the newest version works for me

Did try running the script, but it errors for me.  

```
a2dp.py", line 118    print(d, end='')
                ^
SyntaxError: invalid syntax



```

---

### Post by catalyst1987 on 2016-12-01
> **jeremy31 said:**
> There was also a link to a python script on github that worked for some people- I wasn't one of them as I had to use the command I posted

EDIT: It seems the newest version works for me

Never mind on my last update.  Got the script to run and get the following output in the console, but still no sound from the speaker.

```
Connection MADESelecting device:
Device MAC: B8:69:C2:7F:5D:5A
Device ID: bluez_card.B8_69_C2_7F_5D_5A
Sink: bluez_sink.B8_69_C2_7F_5D_5A
Turning off audio profile.
Disconnecting the device.
Connecting again.
Setting A2DP profile
Device ID: bluez_card.B8_69_C2_7F_5D_5A
Updating default sink
Exiting bluetoothctl
Enjoy HiFi stereo music!
```

---

### Post by ricoter on 2017-04-21
I had the same problem and found a solution here:

[https://askubuntu.com/a/645072](https://askubuntu.com/a/645072)

Problem: Wifi and bluetooth interfere with each other

Solution:

   
[LIST=1]
[*]Run in terminal
[*]sudo tee /etc/modprobe.d/iwlwifi-opt.conf <<< "options iwlwifi bt_coex_active=N"

[*]Reboot
[/LIST]

Good luck

---

