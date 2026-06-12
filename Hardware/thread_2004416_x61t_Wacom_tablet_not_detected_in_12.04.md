---
title: "x61t Wacom tablet not detected in 12.04"
date: 2012-06-15
forum: Hardware
---

### Post by goodman_m_w on 2012-06-15
Hi, I just did a completely fresh install (including formatting the home directory) of Ubuntu 12.04, and now my tablet does not work. It worked in the past. My computer is a Lenovo x61t tablet pc.

I see [this thread]("http://ubuntuforums.org/showthread.php?t=1780154") suggesting I install a new serial_wacom.ko, but it appears to be related to external serial tablets, and not ISDv4 tablet PCs, so I did not attempt the fix.

I did attempt, first, the solution described [here]("http://ubuntuforums.org/showthread.php?t=1862595") and at [ThinkWiki]("http://www.thinkwiki.org/wiki/Wacom_Serial_Tablet_PC_Stylus#Troubleshooting"), rebooted, and had no luck. I also tried some other settings (e.g. creating an xorg.conf) as described [here]("http://ubuntuforums.org/showpost.php?p=11363977&postcount=15"), but that doesn't help either.

The problem appears not to be about configuration so much as detection. It seems my laptop is not recognizing the hardware at all. See below:

```
$ sudo isdv4-serial-debugger -b 38400 /dev/ttyS4
^C$ xsetwacom list
$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=11	[slave  keyboard (3)]
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
```

Also for your info:
```
$ uname -a
Linux goodmami-tablet 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04 LTS
Release:	12.04
Codename:	precise
```

Any ideas what I can try?

---

### Post by goodman_m_w on 2012-06-15
Update: I do see some mention of the wacom hardware in /var/log/Xorg.0.log. It appears to load the module but then times out, and unloads the module:

```
$ grep -i wacom /var/log/Xorg.0.log
[    11.995] (II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS4)
[    11.995] (**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
[    11.995] (II) LoadModule: "wacom"
[    11.996] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    11.996] (II) Module wacom: vendor="X.Org Foundation"
[    11.996] (II) Using input driver 'wacom' for 'Serial Wacom Tablet'
[    11.996] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    11.996] (**) Serial Wacom Tablet: always reports core events
[    11.997] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[    11.997] (II) Serial Wacom Tablet: other types will be automatically added.
[    15.250] (WW) Serial Wacom Tablet stylus: Waited too long for answer (failed after 3 tries).
[    15.250] (WW) Serial Wacom Tablet stylus: Query failed with 38400 baud. Trying 19200.
[    18.504] (WW) Serial Wacom Tablet stylus: Waited too long for answer (failed after 3 tries).
[    21.757] (WW) Serial Wacom Tablet stylus: Waited too long for answer (failed after 3 tries).
[    21.757] (II) Serial Wacom Tablet stylus: serial tablet id 0x93.
[    21.757] (EE) PreInit returned 8 for "Serial Wacom Tablet stylus"
[    21.757] (II) UnloadModule: "wacom"
[    21.757] (II) Unloading wacom
```

At least it's trying!

---

### Post by Favux on 2012-06-15
Hi goodman_m_w,

After a reboot and getting the module unload message in Xorg.0.log try restarting X and see what that does.

---

### Post by goodman_m_w on 2012-06-25
Sorry for my slow reply---I am traveling.

Restarting X has no effect. The module is still being unloaded, according to the log.

---

### Post by Favux on 2012-06-25
It is sounding like the digitizer isn't responding to the queries from wacom_drv.so/wcmISDV4.c.  Your not seeing anything with isdv4-serial-debugger right?  How long ago was it working?  Does it work on another release or OS?

You could try to double checking the port:
```
sudo dmesg | grep ttyS
```

It doesn't look like it is using the new serio driver wacom_w80001.ko.  You could check in /lib/udev/rules.d/40-inputattach.rules if a rule is being applied.  You may want to try commenting it out anyway, even though it doesn't appear to be blocking the port.  Can also always go the other way and try the serio driver.

---

### Post by goodman_m_w on 2012-06-26
Thank you for your help.

It did not work for me in 11.10. I thought that was because I was using XMonad (with Gnome) instead of Unity, but maybe it wouldn't have worked anyway. I am now just using the default (Unity). I believe the digitizer last worked in 11.04.

Nothing about tty5 from dmesg:

```
$ sudo dmesg | grep tty5
$
```

I do see two rules in /lib/udev/rules.d/40-inputattach.rules:

```
$ cat /lib/udev/rules.d/40-inputattach.rules 
# Attach Wacom W8001 devices
SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="FUJ02e5", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 19200 --w8001 /dev/%k"
SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="WACf00c", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 38400 --w8001 /dev/%k"
```

In my debugging I had tried commenting out both of them, with no effect.

And sorry, but how would I check if the serio driver is being used (`locate wacom_w80001.ko`, at least, returns nothing), and if it is not, how to install/activate it?

---

### Post by Favux on 2012-06-26
> It did not work for me in 11.10. I thought that was because I was using XMonad (with Gnome) instead of Unity, but maybe it wouldn't have worked anyway.
My concern this is a hardware problem has increased.  Your not seeing a port in use with dmesg or with isdv4-serial-debugger.  We do have the ttyS4 from Xorg.0.log.  Did it auto-discover that or did you do some configuration to tell it to look on S4?

The serio driver/module wacom_w8001.ko would show up in **lsmod** as wacom_w8001.  That's what the inputattach udev rule is suppose to be invoking.  Although it doesn't seem to work so you might be better off putting it in rc.local as in:
```
inputattach --daemon --baud 38400 --w8001 /dev/ttyS4
```
although the input-wacom README for the inputattach/w8001 combo recommends:
```
inputattach --baud 38400 --wacom /dev/ttyS4
```
for /etc/rc.local.  I think it depends on which inputattach you have (input-wacom comes with its own version) and if you are trying to invoke the /lib/udev/inputattach script they've stuck in /lib/udev.  I think it's the script that isn't working.  Hmm, just looked at it and that's not how I remember it, I think they may have changed it.

---

### Post by goodman_m_w on 2012-06-28
I wouldn't be surpised if the hardware is breaking down---the laptop is now 5 years old.

I did set some config file with ttyS4 while following [this thread]("http://ubuntuforums.org/showpost.php?p=11363977&postcount=15"), but I had since removed or commented out the references to ttyS4 and rebooted before reporting Xorg.0.log. Maybe it was copied and persists somewhere else, though.

I commented out both lines in /lib/udev/rules.d/40-inputattach.rules, and put the line you suggested in /etc/rc.local, then rebooted. Still nothing.

Is there some way I can tell if it is a hardware, rather than configuration, error? I appreciate your help, but I don't want to waste your time if it's not going to work.

Thanks

---

### Post by Favux on 2012-06-28
Easisest way to detect a hardware problem is to check it on another Ubuntu release with a live CD if it isn't installed or better yet another OS where you know it worked.

Do you still have an xorg.conf with wacom sections in it?  They would be controlling things because xorg.conf runs after xorg.conf.d.  If you do have one in /etc/X11 please post it.

Yeah, ideally we would like to know the serial port it is on before we try to configure it.

---

### Post by goodman_m_w on 2012-06-29
Bad news. I booted the 10.10 live CD, and the stylus did not work. I'm quite certain it worked on that release 1.5 years ago, so I think you may be correct that there is a hardware problem.

I really appreciate your prompt and helpful responses. Unless you have another trick up your sleeve, perhaps we should declare this one dead.

---

### Post by Favux on 2012-06-29
Not sounding good.

It may be the digitizer to motherboard connection just got loose.  From what I've seen just like the video cable from the screen/LCD edge there should be a digitizer cable going to a connection on the motherboard.  The two might be bundled together.  The connection on either end may have loosened.  Not sure how all that works with the swivel hinge.

If it is something like a blown capacitor that's tougher.  Need good soldering skills and the right soldering iron and other tools.  Then hope you don't damage the motherboard.  If the actual serial chip or something is blown that's likely story over.

But I've heard folks say they just needed to push the connection back together and if at the screen edge tape it up.

---

### Post by goodman_m_w on 2012-06-30
Wow, thanks for the detailed information. And what you said about the connection being loose resonates with another issue I've been having: the screen flickers and scrambles at certain angles (and, strangely, as I press keys at some angles of the screen). I've had the swivel joint replaced in the past, and I wonder if something was knocked loose. When I get home from my travels I'll attempt to reconnect these cables.

I have replaced capacitors on my (external) lcd monitor, but I don't feel confident doing it on the laptop motherboard. I hope the capacitors are not the cause.

Cheers

---

