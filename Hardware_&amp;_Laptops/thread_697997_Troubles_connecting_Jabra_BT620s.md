---
title: "Troubles connecting Jabra BT620s"
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by Cyclops_ on 2008-02-15
Hey all!

I have the following configuration:

Ubuntu CE (Ubuntu 7.10 on kernel 2.6.22-14-386)
Gnome
Jabra BT620s
Motorola USB Bluetooth Connector PC850

I have downloaded and installed almost everything I can find on Bluetooth, including all the KDE apps and have been through all of the forum threads I can find with remote relation to my issue.  I even installed Bluetooth Manager called Blueman (which seemed to have gotten me a little farther)

I will put up any output anyone asks for anything, but here are the symptoms.

First of all, the headset is recognized ONLY when I put it in pairing mode.  If I run

```

hcitool scan

```with it on but not in pairing mode, I come up with nothing (even after I have had it in pairing mode, and connected to it).

So, i put it in pairing mode, scan, and there it is:

```

me@compy:/home/me$ hcitool scan
Scanning ...
        XX:XX:XX:XX:XX:XX       Jabra BT620s

```(Of course there are actually numbers where those XX's are)

So then I try this:

```

me@compy:/home/me$ hidd --connect XX:XX:XX:XX:XX:XX
Can't get device information: Success

```(It says successful, but I wouldn't count that a success...)

and then there's:

```

me@compy:/home/me$ sudo hcitool cc XX:XX:XX:XX:XX:XX
me@compy:/home/me$ sudo hcitool auth XX:XX:XX:XX:XX:XX
HCI authentication request failed: Connection timed out

```I can do this:

```

me@compy:/home/me$ hcitool dev
Devices:
        hci0    XX:XX:XX:XX:XX:XX

```When I run the btsco command:

```

me@compy:/home/me$ btsco -v XX:XX:XX:XX:XX:XX
btsco v0.42
Error: hwdep next device (hw:0): Operation not permitted
Error: control open (hw:1): No such device
Error: Can't find device. Bail

```Not sure what to do about that... but get the same thing when run with sudo.

so I try:

```

me@compy:/home/me$ sudo hciconfig hci0 reset
me@compy:/home/me$ hidd --connect 00:13:17:72:0D:24
Can't get device information: Connection timed out

```(All of this taking place in pairing mode)

I've also installed gbtsco, and when I try to connect to a device I get the following output in a terminal:

```

FATAL: Module snd_bt_sco not found.
Error: hwdep next device (hw:0): Operation not permitted
Error: control open (hw:1): No such device
Error: Can't find device. Bail
Error: hwdep next device (hw:0): Operation not permitted
Error: control open (hw:1): No such device
Error: Can't find device. Bail

```Here is an oddness...

With Blueman, I can see the headset (and my phone for that matter).  If I click "bond" it comes up with a dialog that asks for the passcode, which I enter, and I get a notification that it's bonded, and then a notification that the device is connected, and then half a second later, I get notified that the device has disconnected.

Sometimes, with hcitool, I can cc and then auth (or any other command, for that matter) if I do it quick enough... but normally cc will work OK but the next command will say "Not connected." if I'm not fast enough to enter it in.

I'm open to trying anything, outputting anything, whatever.

Can anybody assist?

Thanks in advance!!!!!!

---

### Post by Cyclops_ on 2008-02-18
*bump*  :)

---

### Post by jpeddicord on 2008-02-27
See [http://fosswire.com/2008/01/11/a2dp-stereo-linux/](http://fosswire.com/2008/01/11/a2dp-stereo-linux/), it's how I got mine working. :)

---

