---
title: "Maverick - Synaptics Touchpad fails on resume on Dell XPS Studio"
date: 2010-11-03
forum: Hardware
---

### Post by steenbras on 2010-11-03
Since upgrading to Maverick, I occasionally (around 10% of the time) experience a failure of the Synaptics Touchpad to initialise on suspend after a resume. This is on a Dell Studio XPS laptop.

Before Maverick this happened occasionally (much less frequently) and could always be overcome with 

```
sudo modprobe psmouse
sudo modprobe -r psmouse
```

However, on Maverick this has no effect.

Here is some log output from dmesg:
```
$ dmesg | grep -i synaptics
[   20.710358] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000/0xa0000
[   20.755959] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input13
[ 5217.488036] Unable to query Synaptics hardware.
```

and from Xorg:
```
$ cat /var/log/Xorg.0.log | grep -i synaptics
[    32.276] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event12)
[    32.276] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    32.276] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    32.276] (II) LoadModule: "synaptics"
[    32.277] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    32.277] (II) Module synaptics: vendor="X.Org Foundation"
[    32.277] (II) Synaptics touchpad driver version 1.2.2
[    32.305] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5576
[    32.359] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4684
[    32.359] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    32.359] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    32.359] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[    32.400] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    32.400] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    32.416] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    32.416] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    32.416] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    32.416] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    32.416] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    32.448] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    32.448] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[  5218.735] (II) config/udev: removing device SynPS/2 Synaptics TouchPad
[  5218.736] (II) UnloadModule: "synaptics"

```

Any help appreciated!

---

### Post by manzdagratiano on 2010-11-08
I had the same issue on Maverick on my Dell Vostro V13 - it started recently after a kernel upgrade. I finally figured out the solution after a combination of solutions a few minutes ago.

Create a file /etc/pm/sleep.d/71input-reset and paste in it:

```
#!/bin/sh
#
# Reload the AT keyboard interface.

case "$1" in
        hibernate|suspend)
                rmmod psmouse
                ;;
        thaw|resume)
                modprobe psmouse
                ;;
        *)
                ;;
esac
```

Make it executable:

```
sudo chmod +x /etc/pm/sleep.d/71input-reset
```

and we're done! :guitar:

I must mention that there was always a lag in resuming the mouse on my laptop, but it always did work after a few seconds - until recently when it completely stopped working.

---

### Post by nedosa on 2010-11-21
I have the same problem on a Dell XPS 16. Tried the above solution but didn't help unfortunately. Would anyone know if there is a bug that links to this problem ?

---

### Post by Chilly_Willy on 2010-12-01
I too have this problem with my Dell XPS16. I found this old bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317270](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317270)

---

### Post by Chilly_Willy on 2010-12-05
When I use 2.6.35-22, I have yet to experience this problem. Now there is a new 2.6.35-26 kernel, will try that for a while.

---

### Post by linaux on 2010-12-22
For what it's worth, I had the same problem on a zareason laptop, and that's how I found this thread. I'm running linux mint 10, which I believe is based on Maverick. Got an error message stating,
> unable to query Synaptics hardware
I just got this machine last night, and it's my first experience with Linux save for a live CD of Ubuntu. The problem occurred after my first attempt with Hibernate. Prior to that, I used Suspend.

anyway, now I see that it's not a zareason hardware issue, and you see it's not a dell issue. Cheers.

---

### Post by Chilly_Willy on 2010-12-22
I get the same error message.

I've had this laptop with Jaunty, Karmic, Lucid and now Maverick and have never had any problems before Maverick.

---

### Post by linaux on 2010-12-22
> **Chilly_Willy said:**
> I get the same error message.

I've had this laptop with Jaunty, Karmic, Lucid and now Maverick and have never had any problems before Maverick.

Not to go too far off topic, but I'm grateful for this thread because it reassured me that I don't need to return this brand new computer. If you've been doing this since Jaunty, I take it you're happy with Linux in general. I guess I'll just avoid Hibernate, use Suspend, and stick with it.

---

### Post by steenbras on 2011-01-17
So a few of us are having this issue - but no-one's any clearer as to the root cause?

Just for the record - mine happens after a suspend, not hibernate. A USB mouse works fine - the touchpad is the issue. I also notice the "unable to query Synaptics hardware". 

I've also noticed a module called synaptics_i2c.ko from modprobe -l, but removing and reprobing for it has no effect.

Must say that Maverick to me seems the least stable Ubuntu release I've come across (been using it since Jaunty). I have issues with the trackpad, but far more worryingly I notice that X restarts itself sometimes after switching monitor configurations. I bit of a problem when you're running a VM.

---

### Post by GarvBuntu on 2011-01-18
Same here. My Studio XPS 16 touchpad fails after suspend. The USB mouse has no problems. I've been unsuccessfully chasing this one for a while. This has occurred on my system while running either 32 or 64 bit Maverick.

---

### Post by Chilly_Willy on 2011-02-04
I was so fed up with this problem. I have this every suspend/resume. I tried the maverick live-usb and there suspend/resume worked like it should.

So I've reinstalled Maverick and the touchpad is working again after resume.

---

### Post by izzaboo on 2011-02-09
I've been having a similar problem on resume from hibernate (not so much with suspend from resume) with recently purchased Lenovo G560 (cheapo officeDepot model).  A restart always seems to reset it.  The only time this machine hibernates, though, is when the battery is critically low and I don't get to a power supply fast enough.

My problem seems to be more with the trackpad buttons than with the trackpad itself.  That is, clicking menus, dragging things, etc fail.

I also can't get the disable trackpad while typing feature to really be effective in any way at any time. If that might be related...

Otherwise everything seems pretty well functional on this machine, even after hibernate.

edit: I should probably clarify that on this Lenovo xinput list indicates I am using an "ETPS/2 Elantech Touchpad" and a "Virtual core XTEST pointer". I don't know enough about hardware to *know* if that matters for this discussion but it seemed relevant to me.

---

