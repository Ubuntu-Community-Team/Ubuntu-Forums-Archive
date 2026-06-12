---
title: "Bluez (bluetoothd) not sending DBUS method_call SelectConfiguration upon Connection"
date: 2014-03-21
forum: Hardware
---

### Post by (O) on 2014-03-21
[COLOR=#000000][FONT=Arial]***UPDATE:*** not solved yet, but part of a solution. See below.[/FONT][/COLOR]
This is my first post on UbuntuForums.  I read them a lot, but usually my problem has already been solved...even many times. So sorry if the question isn't as clear as it could be.

I am attempting to connect my iPod or other smart device to my laptop (Kubuntu 13.10) via bluetooth and stream a2dp-encoded music to a bluetooth speaker.  Never mind why I don't connect them directly.  I had a lot of trouble getting the devices to actually pair then connect at the same time, but now I'm able to do that.  I could never get PulseAudio to consistently load the sources and sinks, so I scratched that idea and started following this great post by James B:  [http://jamesbond3142.no-ip.org/blog/?viewCat=Bluetooth](http://jamesbond3142.no-ip.org/blog/?viewCat=Bluetooth)

I got the code compiled.  It uses the (newer?) DBus API for BlueZ. Following his instructions, I was able to pipe music into the a2dp "server" or out of it, but there is no sound.  In the code, he waits for two DBUS method_calls, SelectConfiguration and SetConfiguration in order to obtain the "transport", which I think is a handle or file descriptor that describes where the audio should go to/from.  However, the handlers for these events are never called.  I set up dbus-monitor to listen on the system bus for these calls using this guide: [https://wiki.ubuntu.com/DebuggingDBus](https://wiki.ubuntu.com/DebuggingDBus).  However, the method calls don't show.  Then again, I tried listening to ANY method calls on the system bus and there are some that don't show in dbus-monitor that I know are being called.  (i.e. [RegisterEndpoint]("http://git.kernel.org/cgit/bluetooth/bluez.git/tree/doc/media-api.txt?id=67ef3ac83752e3705fad55eb25586e1d21e44c2e"))

I see signals from org.bluez, but no method calls.  When running bluetoothd in verbose mode I get something like this when I connect my device:

bluetoothd[12118]: audio/a2dp.c:setup_ref() 0x7f9e8ffbdac0: ref=2
bluetoothd[12118]: audio/avdtp.c:avdtp_set_configuration() 0x7f9e8ffd03f0: int_seid=1, acp_seid=1
bluetoothd[12118]: audio/a2dp.c:setup_unref() 0x7f9e8ffbdac0: ref=1
bluetoothd[12118]: audio/avdtp.c:session_cb() 
bluetoothd[12118]: audio/avdtp.c:avdtp_parse_resp() SET_CONFIGURATION request succeeded
bluetoothd[12118]: audio/a2dp.c:setconf_cfm() Source 0x7f9e8ffa4600: Set_Configuration_Cfm
bluetoothd[12118]: audio/avdtp.c:avdtp_sep_set_state() stream state changed: IDLE -> CONFIGURED
bluetoothd[12118]: audio/avdtp.c:session_cb() 
bluetoothd[12118]: audio/avdtp.c:avdtp_parse_resp() OPEN request succeeded


but on another post I saw that someone had this:

bluetoothd[8315]: audio/a2dp.c:setup_ref() 0x7f1f8300b000: ref=2
bluetoothd[8315]: audio/avdtp.c:avdtp_set_configuration() 0x7f1f83012250: int_seid=2, acp_seid=1
bluetoothd[8315]: audio/a2dp.c:setup_unref() 0x7f1f8300b000: ref=1
bluetoothd[8315]: audio/avdtp.c:session_cb() 
bluetoothd[8315]: audio/avdtp.c:avdtp_parse_resp() SET_CONFIGURATION request succeeded
bluetoothd[8315]: audio/a2dp.c:setconf_cfm() Sink 0x7f1f82fc3210: Set_Configuration_Cfm
[COLOR=#ff0000]bluetoothd[8315]: audio/media.c:media_endpoint_async_call() Calling SetConfiguration: name = :1.65 path = /MediaEndpoint/A2DPSink[/COLOR]
bluetoothd[8315]: audio/avdtp.c:avdtp_sep_set_state() stream state changed: IDLE -> CONFIGURED
bluetoothd[8315]: audio/avdtp.c:session_cb() 
bluetoothd[8315]: audio/avdtp.c:avdtp_parse_resp() OPEN request succeeded[FONT=Verdana]
[/FONT]
[FONT=Verdana]At this point I have two theories:
1) [/FONT][FONT=Verdana]BlueZ[/FONT][FONT=Verdana] isn't sending this to the bus I'm watching when my device is connected[/FONT]
[FONT=Verdana]2) I'm not watching correctly (do method_calls also need to be added with [/FONT]dbus_bus_add_match () ?)[FONT=Verdana]

I find it hard to believe the second one, since James B's code worked for him and I didn't modify it.  [/FONT][FONT=Verdana]I'm using bluez version 4.101. (same as he, I think)
It's hard to find the exact conditions under which BlueZ calls these methods.

My syslog says something like this when I start the program: 
[/FONT][FONT=Verdana]
bluetoothd[8519]: Endpoint registered: sender=:1.166 path=/MediaEndpoint/A2DPSource[/FONT]
[FONT=Verdana]
and unregisters as well when the program exits.

I can't think of other details to add at the moment, but I'm happy to if I haven't provided enough.  Thanks in advance.

[/FONT]***&#8203;UPDATE: ***[COLOR=#333333][FONT=UbuntuRegular]A little embarrassing, but I racked my brain today about why a LINUX SYSTEM wouldn't get a file handle...hmmm...so I appended sudo to the program call (James B's a2dp-alsa program) and it worked. At least for the input device. Still nothing for the output (BT speaker), but I'll try to figure that out soon and post the result here.[/FONT][/COLOR]

---

