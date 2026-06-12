---
title: "Remote-Control on /dev/input/eventX (Hauppauge,inputlirc)"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by nohu_ on 2007-12-08
Hallo,

After long time of experimenting with LIRC i finally got the Remote Control of my Hauppauge TV-Card working. But sadly not the way I want it.
I had to use the program "inputlirc" and at least it is now possible to assign some keys on the remote to do something (via lircrc).

But the Probelm is that some of the Buttons on the remote are assigned to functions (like volume-up/down/mute) by default (even if inputlirc is not running). The Numbers on the Remote are written on screen like you type it with the keyboard.

The Signals from Remote are sent to Event-Queue: /dev/input/event4

Here the output of **cat /proc/bus/input/devices**
```

#...........
I: Bus=0001 Vendor=0070 Product=3401 Version=0001
N: Name="cx88 IR (Hauppauge WinTV 34xxx "
P: Phys=pci-0000:02:06.0/ir0
S: Sysfs=/class/input/input5
U: Uniq=
**H: Handlers=kbd event4**
B: EV=100003
B: KEY=100fc312 214a80200000000 0 18000 41a800004801 9e168000000000 10000ffc
#...........

```


I think that the Handler kdb is interpreting this keys as Keyboard-Inputs. And handles them before they get to the event4 queue.

Is it possible to disable the KBD-Handler for this device?
I really wonder how to do that.

Thanks in advance
nohu_

---

### Post by rascal84 on 2008-01-06
> 
Here the output of **cat /proc/bus/input/devices**
```

#...........
I: Bus=0001 Vendor=0070 Product=3401 Version=0001
N: Name="cx88 IR (Hauppauge WinTV 34xxx "
P: Phys=pci-0000:02:06.0/ir0
S: Sysfs=/class/input/input5
U: Uniq=
**H: Handlers=kbd event4**
B: EV=100003
B: KEY=100fc312 214a80200000000 0 18000 41a800004801 9e168000000000 10000ffc
#...........

```


I think that the Handler kdb is interpreting this keys as Keyboard-Inputs. And handles them before they get to the event4 queue.

Is it possible to disable the KBD-Handler for this device?
I really wonder how to do that.

Thanks in advance
nohu_

I have the same output, and similar experience with my (Hauppauge A415-HPG) remote.  In mythtv, some of the buttons work, such as the directional buttons, the OK button, and the numbers. The rest of the buttons don't do anything.

I find it interesting though, that when my remote is "working", the output of  ps aux |grep lirc  returns nothing. In other words, lirc is not running, and my remote is "working".  There has to be some other module / app handling the input from that device.

I've tried several guides in an attempt to get this working, but to no avail.

[http://parker1.co.uk/mythtv_tips.php]("http://parker1.co.uk/mythtv_tips.php")  has some good information.

I think my next step is going to be to reinstall a plain jane Ubuntu 7.10 and load the mythtv packages manually. When I first installed this way, I was at least able to get the volume controls on the remote to work properly, so it might be a good starting point.

I'll happily share my lircd.conf, hardware.conf, .lircrc etc after my clean install if the results are better than those I've seen with Mythbuntu.  

I will give Mythbuntu some credit though, they have put together a nice kit that pretty much just works.

** EDIT **

simply starting lircd and then running irw to test capture from my remote will cause lircd to terminate.  However, starting lircd with the following command allows it to accept connections, although I am never able to see that I've pushed buttons on the remote.

lircd -H dev/input -d /dev/input/event4   # fill in your event / device here of course

In another terminal window, run irw, point your remote at your receiver, and push some buttons.  I don't see anything in irw when I do this, but your luck may be better than mine.

---

### Post by bonarez on 2008-01-19
> I have the same output, and similar experience with my (Hauppauge A415-HPG) remote
Yeah, me too, been trying with lirc on a knoppmyth installation over the last few days as you can see [here]("http://knoppmyth.net/phpBB2/viewtopic.php?p=105902#105902")

When working in X11 the remote works fine, but getting it to work in mythtv is a bit harder it seems..

I've just install inputlirc and I'm going to get it set up later, will look at [http://parker1.co.uk/mythtv_tips.php](http://parker1.co.uk/mythtv_tips.php) as well, seems very informative

if certain keys aren't working, it might be worth taking a look at [keyfuzz]("http://0pointer.de/lennart/projects/keyfuzz/"), a util to remap keycodes/scancodes

keep me up to date if you got things working any better, will do the same
grtz

---

