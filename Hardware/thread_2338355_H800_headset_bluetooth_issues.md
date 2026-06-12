---
title: "H800 headset bluetooth issues"
date: 2016-09-27
forum: Hardware
---

### Post by bernie9998 on 2016-09-27
I am having trouble getting full bluetooth support for my logitech H800 headset on Xenial 16.04.

When paired in bluetooth mode, I am only able to use the A2DP Sink profile.  Attempting to switch to the HSP/HFP profile results in this error message:

```

[pulseaudio] module-bluez5-device.c: Refused to switch profile to headset_head_unit: Not connected

```

Checking the pulseaudio details, I can see both profiles (a2dp and the headset), but only a2dp is listed as availble:

```

        Name: bluez_card.88_C6_26_31_DF_F0
        Driver: module-bluez5-device.c
        Owner Module: 28
        Properties:
                device.description = "H800 Logitech Headset"
                device.string = "88:C6:26:31:DF:F0"
                device.api = "bluez"
                device.class = "sound"
                device.bus = "bluetooth"
                device.form_factor = "headset"
                bluez.path = "/org/bluez/hci0/dev_88_C6_26_31_DF_F0"
                bluez.class = "0x240404"
                bluez.alias = "H800 Logitech Headset"
                device.icon_name = "audio-headset-bluetooth"
                device.intended_roles = "phone"
        Profiles:
                a2dp_sink: High Fidelity Playback (A2DP Sink) (sinks: 1, sources: 0, priority: 10, available: yes)
                headset_head_unit: Headset Head Unit (HSP/HFP) (sinks: 1, sources: 1, priority: 20, available: no)
                off: Off (sinks: 0, sources: 0, priority: 0, available: yes)
        Active Profile: a2dp_sink
        Ports:
                headset-output: Headset (priority: 0, latency offset: 0 usec)
                        Part of profile(s): a2dp_sink, headset_head_unit
                headset-input: Headset (priority: 0, latency offset: 0 usec, not available)
                        Part of profile(s): headset_head_unit

```

I have queried this device with bluetoothctl info:

```

Device 88:C6:26:31:DF:F0
        Name: H800 Logitech Headset
        Alias: H800 Logitech Headset
        Class: 0x240404
        Icon: audio-card
        Paired: yes
        Trusted: yes
        Blocked: no
        Connected: yes
        LegacyPairing: no
        UUID: Audio Sink                (0000110b-0000-1000-8000-00805f9b34fb)
        UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
        UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
        UUID: Handsfree                 (0000111e-0000-1000-8000-00805f9b34fb)

```

Apparently, most headsets provide both the Handsfree and Headset types in bluetooth, but this one only provides the Handsfree type.  Is it possible that pulseaudio won't connect because pulseaudio only supports HSP and does not support HFP?

I have tried installing ofono to get HFP support, but it appears that ofono is intended only for implementing a handsfree device, not for connecting to one.

The closest issue I can find regarding this is this question on askubuntu:

[http://askubuntu.com/questions/531862/h800-logitech-headphones-not-working-properly](http://askubuntu.com/questions/531862/h800-logitech-headphones-not-working-properly)

In that case, the user simply responded that it now works on 15.04.  If that is the case, it appears to have regressed in 16.04.

I wonder if it has something to do with the upgrade from bluez4 to bluez5 and the change that caused the HSP/HFP implementation to move from bluez to pulseaudio.

Has anyone else experienced this issue?  Has anyone found a workaround to this?

Thanks for your assistance.

---

### Post by jeremy31 on 2016-09-27
In pulseaudio control try switching to the off profile before switching to headset
There are other posts here about bluetooth audio problems but most have the opposite issue, we have problems switching to A2DP mode.  If you look at my recent posts you will find a couple of these threads.  I also think it is a pulse issue

---

### Post by bernie9998 on 2016-09-28
No, that still didn't help.  Still get the same Not Connected error in the logs:

```

[pulseaudio] module-bluez5-device.c: Refused to switch profile to headset_head_unit: Not connected

```

With the off profile selected, the headset profile is still listed as not available in pulse audio:

```

        Name: bluez_card.88_C6_26_31_DF_F0
        Driver: module-bluez5-device.c
        Owner Module: 27
        Properties:
                device.description = "H800 Logitech Headset"
                device.string = "88:C6:26:31:DF:F0"
                device.api = "bluez"
                device.class = "sound"
                device.bus = "bluetooth"
                device.form_factor = "headset"
                bluez.path = "/org/bluez/hci0/dev_88_C6_26_31_DF_F0"
                bluez.class = "0x240404"
                bluez.alias = "H800 Logitech Headset"
                device.icon_name = "audio-headset-bluetooth"
                device.intended_roles = "phone"
        Profiles:
                a2dp_sink: High Fidelity Playback (A2DP Sink) (sinks: 1, sources: 0, priority: 10, available: yes)
                headset_head_unit: Headset Head Unit (HSP/HFP) (sinks: 1, sources: 1, priority: 20, available: no)
                off: Off (sinks: 0, sources: 0, priority: 0, available: yes)
        Active Profile: off
        Ports:
                headset-output: Headset (priority: 0, latency offset: 0 usec)
                        Part of profile(s): a2dp_sink, headset_head_unit
                headset-input: Headset (priority: 0, latency offset: 0 usec, not available)
                        Part of profile(s): headset_head_unit

```

I think the issue that has to be addressed is why the headset profile is not available in pulse audio.

---

### Post by jeremy31 on 2016-09-28
Try using ```
bluetoothctl
```
It will list the MAC addresses of devices that you have paired to, then find the MAC address of your headset
```
connect [device MAC address
```
Then see if pulse will allow you to switch profiles and there is a chance that modifying the following to include your headsets MAC instead of mine might work
```
pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` off; sleep 5 ; echo -e "disconnect AC:9B:0A:4F:CA:FF\n quit"|bluetoothctl;sleep 5; echo -e "connect AC:9B:0A:4F:CA:FF\n quit"|bluetoothctl; sleep 5; pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` headset_head_unit
```

---

### Post by bernie9998 on 2016-10-04
I've tried switching profiles many times from many different methods without success.

I just tried this method, switching by the command line and disconnecting and reconnecting the device from bluetooth inbetween.  However, it still fails:

Failed to set card profile to 'headset_head_unit'.

As I had mentioned previously, I don't think this is the typical issue seen where other bluetooth devices cannot connect as A2DP sink.  As mentioned in my initial post, most devices expose both a headset and handsfree interface in bluetooth.  However, my device appears to only provide a handsfree interface.  I think the issue is in the handsfree support, or lack thereof in pulse audio.

---

