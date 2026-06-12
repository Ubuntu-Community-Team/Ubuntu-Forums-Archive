---
title: "v470 bluetooth problems (doesn't reply)"
date: 2008-07-13
forum: Hardware
---

### Post by crashanddie on 2008-07-13
Hi everyone,

I've been asking around in #ubuntu about this problem, but not a lot of replies (not any, in fact).

I recently acquired a Microsoft Bluetooth Notebook Mouse 5000. It worked fine under Ubuntu, click and register, no problem. I had to return it though, because the scrollwheel was faulty (I couldn't scroll up without pasting stuff). So I got a Logitech v470 Bluetooth Notebook Mouse.

Yes, I have read all the threads about this mouse working fine, but the fact is, it doesn't work with me. I would like to point out that I have been able to pair it, and have it working no problem with my PS3, my Nokia n810 (only pairing, no mouse supported), and a MacBook with OS X. It pairs no problem, it's spotted right from the start, and it works fine.

Here's a bit of information about my laptop:

```

$ lsusb | grep -i broadcom
Bus 003 Device 002: ID 0a5c:2101 Broadcom Corp. 

```

```

$ uname -a
Linux thecrasher 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

```

```

$ dpkg -l | grep blue
ii  bluez-audio                                   3.26-0ubuntu6                                              Bluetooth audio support
ii  bluez-cups                                    3.26-0ubuntu6                                              Bluetooth printer driver for CUPS
ii  bluez-gnome                                   0.25-0ubuntu1                                              Bluetooth utilities for GNOME
ii  bluez-hcidump                                 1.40-0ubuntu1                                              Analyses Bluetooth HCI packets
ii  bluez-utils                                   3.26-0ubuntu6                                              Bluetooth tools and daemons
ii  gnome-bluetooth                               0.11.0-0ubuntu1                                            GNOME Bluetooth tools.
ii  libbluetooth2                                 3.29-0ubuntu1                                              Library to use the BlueZ Linux Bluetooth sta

```

/etc/default/bluetooth:

```

$ cat /etc/default/bluetooth | grep -i hidd
############ HIDD
HIDD_ENABLED=1
HIDD_OPTIONS="--master --server"

```


Description: I put it in "pairing mode" (by holding the button underneath it for a second), it starts flickering, no problem there. I try to connect using the bluetooth-properties application. I go into services, Input Device, and click Add. The list shows the MAC address of my mouse, but no name. When I try to click "connect", it says "Connecting to the device", and after a few seconds, times out, and the whole application quits.

This is the message I get:

```

$ bluetooth-properties 
process 10540: arguments to dbus_message_new_method_call() were incorrect, assertion "_dbus_check_is_valid_path (path)" failed in file dbus-message.c line 1074.
This is normally a bug in some application using the D-Bus library.

** ERROR **: Out of memory
aborting...
Aborted

```

When I use hcitool scan, this is the output I get:

```

$ sudo hcitool scan
Scanning ...
	00:16:B8:8F:D8:F8	Z530i
	00:12:47:BD:F7:79	L'Oursomobile
	00:1D:6E:D9:5C:69	Mercurio
	00:07:61:A6:CE:0D	n/a.

```

The first 3 are two mobiles phones, and a Nokia Internet Tablet. The last one is my mouse. Please note that the mouse "takes it time" before appearing on that list. Again, probably because it times out.

This is the output of hcidump during this scanning:

```

$ sudo hcidump
[sudo] password for crashanddie: 
HCI sniffer - Bluetooth packet analyzer ver 1.40
device: hci0 snap_len: 1028 filter: 0xffffffff
< HCI Command: Inquiry (0x01|0x0001) plen 5
> HCI Event: Command Status (0x0f) plen 4
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Complete (0x01) plen 1
< HCI Command: Remote Name Request (0x01|0x0019) plen 10
> HCI Event: Command Status (0x0f) plen 4
> HCI Event: Remote Name Req Complete (0x07) plen 255

```

This is the output of /var/log/syslog:

```

$ tail /var/log/syslog
Jul 13 16:25:42 thecrasher audio[6039]: /org/bluez/audio: org.bluez.audio.Manager.ListDevices()
Jul 13 16:25:42 thecrasher input[6067]: /org/bluez/input: org.bluez.input.Manager.ListDevices()
Jul 13 16:25:56 thecrasher input[6067]: /org/bluez/input: org.bluez.input.Manager.CreateSecureDevice()
Jul 13 16:25:56 thecrasher NetworkManager: <debug> [1215959156.174449] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_761a6ce0d'). 
Jul 13 16:26:21 thecrasher input[6067]: GetRemoteServiceHandles: org.freedesktop.DBus.Error.NoReply(Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Jul 13 16:26:21 thecrasher hcid[6011]: remove_name_listener: no listener for :1.741
Jul 13 16:26:28 thecrasher hcid[6011]: connect(): Function not implemented (38)
Jul 13 16:26:28 thecrasher NetworkManager: <debug> [1215959188.679965] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_761a6ce0d'). 

```

When trying hidd --search, this is what I get:

```

$ sudo hidd --search
Searching ...
	Connecting to device 00:07:61:A6:CE:0D
Can't get device information: Function not implemented

```

```

$ sudo hcidump 
HCI sniffer - Bluetooth packet analyzer ver 1.40
device: hci0 snap_len: 1028 filter: 0xffffffff
< HCI Command: Inquiry (0x01|0x0001) plen 5
> HCI Event: Command Status (0x0f) plen 4
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
> HCI Event: Inquiry Complete (0x01) plen 1
< HCI Command: Create Connection (0x01|0x0005) plen 13
> HCI Event: Command Status (0x0f) plen 4
> HCI Event: Connect Complete (0x03) plen 11
< HCI Command: Create Connection (0x01|0x0005) plen 13
> HCI Event: Command Status (0x0f) plen 4
> HCI Event: Connect Complete (0x03) plen 11

```

```

$ tail /var/log/syslog
Jul 13 16:33:20 thecrasher NetworkManager: <debug> [1215959600.332299] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_761a6ce0d'). 
Jul 13 16:33:52 thecrasher NetworkManager: <debug> [1215959632.430816] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_761a6ce0d'). 
Jul 13 16:33:52 thecrasher NetworkManager: <debug> [1215959632.437268] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_761a6ce0d'). 
Jul 13 16:34:28 thecrasher NetworkManager: <debug> [1215959668.055235] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_761a6ce0d'). 

```

I would like to point out that adding the device information in /etc/bluetooth/hcid.conf has no effect. Also, adding -i BTADDR in the HIDD_OPTIONS doesn't have an effect.

Thanks for reading, all help is appreciated.

S.

---

### Post by crashanddie on 2008-07-13
bump

---

### Post by steveneddy on 2008-07-13
Bumping doesn't help. Very often.

Make sure that you have the Bluetooth icon in your upper toolbar.

[IMG]http://www.bidorbuy.co.za/user_images/889/138889_bluetooth_icon50.jpg[/IMG]

If so, right click and select [COLOR="Blue"]**Preferences**[/COLOR].

Click the [COLOR="Blue"]**Services**[/COLOR] tab.

Click the [COLOR="Blue"]**Input Service**[/COLOR] line.

Now, turn on the mouse and turn it over. There is a Connect button on the bottom. Press this button and the light on top will start blinking.

Now, back to the computer, click the [COLOR="Blue"]**Add**[/COLOR] button.

It should auto detect the mouse and add it to the list.

It really should be that easy.

I use the same mouse and after a fresh reinstall of Hardy, this is all I did to get it to connect.

You may need to try this a couple of times.

Restart with the mouse in connect mode may also help the Bluetooth find it.

After that it will connect every time.

EDIT

Try this also:

Remember to push the Connect button on the bottom of the mouse when you try these commands.

```

## to connect to my mouse, in terminal type

sudo hidd --connect [COLOR="Red"]**00:07:61:96:6C:B7**[/COLOR] [COLOR="Blue"]**use your mouse's address here**[/COLOR]

##  If you want to quickly connect a Bluetooth keyboard or mouse to your computer, but don’t need to make it permanent, just open a GNOME Terminal and type

sudo hidd --search

```

Just don't forget to push the connect button on the bottom of the mouse for this to be effective.

---

### Post by crashanddie on 2008-07-13
Thank you for your reply steveneddy,

Still, I have tried all that, as you can see by my all the data that is in the first post. And yes, each and every time, the mouse was in connect mode, flashing light and all, this was also noted in the first post.

Again, like I said in the first post, if I try to add the mouse via the right click on the bluetooth icon (equal to bluetooth-properties), then services, and input service, the application will only see the MAC address of my mouse, and not its name (which is already weird). After trying to connect to it, it will sit there, and after a while, the program will just crash. All of this has been noted in the first post.

Still, thank you for your interest.

---

### Post by scotcella on 2008-07-19
I have the same mouse. I just managed to get it working...

Do you still need help with this? I can help you with this, so I am assuming you are using the Hardy version.

You'll need to downgrade your blue utiliz package to the older gutsy version v3.19 I think..  please refer to [this thread]("http://ubuntuforums.org/showthread.php?t=863815") for downgrading.

Make sure you have gnome-bluetooth installed as well...  and you may need to uninstall the audio package.

And then restart to make sure it's working effectively..  etc etc..

Do the normal configurations etc and follow steveneddy's post.

At the moment I have my mouse connected via the command

> 
sudo hidd --search

Still trying to find out how to make the first command work using my mouse address..  still trying to find it! 

Now I'm off to try and get Evolution work :)

please let me know if this worked for you :o)

---

### Post by stubelston on 2008-07-23
I have the v470 mouse also.  Have never had a problem with it when booted to the Windoz side of my laptop.  

But I went through agony similar to that of Crashanddie when I first installed Ubuntu.  After a lot of thrashing, it finally worked, but because of confusion of try this, try that, try the other thing, it was never clear what got it going in the first place.  Some combination of the various tricks suggested by Steveneddy, as I recall.

Often when there is an update applied by synaptic (I think mostly, but not always, when it involves a kernel upgrade), the "system" seems to lose the connection to the mouse and also to forget how to connect to the mouse at boot time (or when I remember to switch the mouse on . . .).  In the past, I paniced and repeated the "thrash" process --- not very scientific.

This (the update disconnect) happened a few days ago (there was an update automagically applied with a little intervention on my part) and I tried to survive by using the touch pad (ack) because I had work to do.  Tonight I decided to go at it more systematically.

BTW, when this disconnect happens, I still do not have a problem if I decide to boot WinXP.  So it ain't the hardware . . .

I tried the procedure outlined by Steveneddy above, the part that involves incantations over the Bluetooth manager properties dialog.  That produced a partial result - after selecting 'Input Service', then pressing the connect button on the bottom of the mouse and then clicking 'Add' on the services tab, a dialog pops up saying that it is connecting to the mouse, and then it reports having connected.  There is also an icon to the right of the 'Bluetooth Laser Travel Mouse' entry in the 'Services' dialog that resembles an RS232 connector.  It disappears after a few seconds.  If I move the mouse or click one of the buttons, that connector icon reappears, but goes away again if there is no continued mouse activity.  __I notice that the mouse is not really working__ , i.e. there is no corresponding cursor motion (I have to use the touchpad) and I can't click on anything (after positioning the cursor with the touchpad).  So I sort of have a connection (the connector icon that comes and goes with mouse activity) but it does not translate into cursor/clicking action.

If I do the above and __then__ execute 'sudo hidd --search', BANG, the flaky/partial connection becomes complete, that connector icon is there and it is 'on' solid and doesn't disappear after a few seconds, and the system autodetects the mouse on restarts.

I guess it is possible that 'sudo hidd --search' might have worked on its own, but this evening's episode was too traumatic to go into the manager, delete all references to the mouse to try to break the connection, and then do the hidd thing only.  I'll try that next time . . .

Sorry about the long winded story, but this problem seems to involve very complex behavior, and although a number of people seem to have a problem with this mouse, the details of the problems seem to vary tremendously, and the solution for one case doesn't seem to work without fail in another.  So here is a little more data.

---

### Post by devill on 2008-08-16
#3 is a great how to, but I got stuck at the point where the device should show up in the list of input devices. The mouse is bound to the laptop, but it just won't show up in the list.

I have "Trust Bluetooth Optical Mini Mouse" and a Sony VAIO AR series laptop, installed with Ubuntu Studio 8.

Do you have any ide what could be wrong?

---

