---
title: "Elo TouchScreen 4200L and Ubuntu 10"
date: 2011-10-12
forum: Hardware
---

### Post by scabezas on 2011-10-12
Hi. First time poster here. I've been searching and reading the forums for about one week now, but I simply can't find a solution to my display problem.

This is the situation:
We, at the company, are developing a web application to be used in computers arranged as a kiosk. These computers use a ELO TouchScreen 4200L USB, in vertical position. In Windows 7, these work practically out-of-the-box (not counting calibration and applying the characterization file).

Problems started when we decided we needed an OS better suited for long uptime periods. In this case, Ubuntu 10.04.

I have video, I can rotate the monitor via display settings, I even get drag and touch events working. But with the display in vertical position, it freaks out: when I drag in the X axis, it drags in the Y axis and viceversa.

I used the drivers provided by Elo [in this location]("http://www.elotouch.com/Support/Downloads/dnld.asp") (Linux 64 bit APR Driver), and followed the instructions provided [there]("http://www.elotouch.com/files/install/Elo-Linux-APR-v2.2.0_Installation-Instructions.txt") as well.

As I stated before, I've read most of the threads about this issue, threads such as [this one]("http://ubuntuforums.org/showthread.php?t=1460948&highlight=elo"), and [this other one]("http://ubuntuforums.org/showthread.php?t=1483778").

[FONT="Courier New"]**cat /proc/bus/input/devices**[/FONT] does not show my device.
[FONT="Courier New"]**/dev/input/by-id/**[/FONT] does not show my device either.

The weird thing is that I actually GET some response, not the desired one though.

Did I miss any thread?
Is it possible to get this display working on Ubuntu 10.04?

Thanks in advance!

---

### Post by spipe on 2011-10-13
Curious: are you testing this with a mouse attached, or no?  A kiosk station wouldn't normally have a mouse of course.

The reason I ask is that I'm seeing a similar problem on a "shuttle" all-in-one touchpad computer with the new Ubuntu 11.10.  The interesting thing is that if it boots with a USB mouse attached, the touchscreen works as expected, even if I unplug the mouse later.  If it boots without a mouse, the touchscreen seems to respond more or less randomly, even if I add the mouse later.

I'll probably start my own thread on this unless it turns out a USB mouse "fixes" your problem too.  Of course even then it's not really a fix, just maybe a clue that might help someone help us both.

---

### Post by scabezas on 2011-10-13
Wouldn't know about your issue, but in my case I finally got it to work properly. It was a really stupid thing, the thing is I was looking at the *wrong* stupid thing :P

According to the official documentation, in a certain point of the installation you have to copy a **[FONT="Courier New"].rules[/FONT]** file to **[FONT="Courier New"]/etc/udev/rules.d/[/FONT]**

You should edit that file, and should look like this:

```

ACTION=="add", ATTR{idVendor}=="04e7", MODE="0666"
ACTION=="add", ATTR{idVendor}=="04e7", RUN+="/sbin/start-stop-daemon --start --background --exec /etc/opt/elo-apr/eloapr -- --nobeepontouch [COLOR="Red"]--rotation 270[/COLOR] --aprmode_signature --custom_parameters"
BUS=="usb", ATTR{idVendor}=="04e7", MODE="0666"
BUS=="usb", SYSFS{idVendor}=="04e7", MODE="0666"
SUBSYSTEM=="usb", SYSFS{idVendor}=="04e7", MODE="0666"

```

The part in **[COLOR="red"]red[/COLOR]** is the one you should add.

What confused me is that in the official documentation they talk about **[FONT="Courier New"]--rotation, --rotate, -r, ...[/FONT]** and some different ways of doing this. The one I posted here is the one that worked for me.

Hope this helps anyone as clumsy as me!

Should I mark this as solved or is it a Moderator thing?

---

