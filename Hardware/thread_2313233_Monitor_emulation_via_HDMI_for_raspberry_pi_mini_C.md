---
title: "Monitor emulation via HDMI for raspberry pi mini CPU via my laptop"
date: 2016-02-10
forum: Hardware
---

### Post by kayve on 2016-02-10
Thanks in advance.

I have a multiboot Sony VAIO running Ubuntu 14.04 LTS 

root@kayve-VIAO:~# uname -a
Linux kayve-VIAO 3.13.0-77-generic #121-Ubuntu SMP Wed Jan 20 10:50:42 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
root@kayve-VIAO:~# 

I misspelled VIAO in my machine name, I know.  Not an issue for me.  I have entered into a professional relationship that involves development for a small CPU called a Raspberry Pi Element 14

[https://www.raspberrypi.org/qsg](https://www.raspberrypi.org/qsg)
[https://www.element14.com/community/welcome](https://www.element14.com/community/welcome)

I have an SD card on which my colleague in this work has loaded a Raspbian OS

[https://www.raspberrypi.org/downloads/raspbian/](https://www.raspberrypi.org/downloads/raspbian/)

I currently have connected the raspberry pi device to power via a cell phone like power supply and have connected its HDMI port to my laptop HDMI port.  

My question is, in lieu of buying more hardware, i.e. some sort of monitor on which this Raspberry Pi device can output its graphical display, is it possible for me to configure my Ubuntu 14.04 LTS on my laptop to provide a software emulation that will not take over my workspace but instead will provide a subwindow that can act as a monitor device for the Raspberry Pi?

---

### Post by QIII on 2016-02-10
Your laptop's HDMI port is almost certainly *out*, not in, so connecting the HDMI out on your RPi to the HDMI out on your laptop is at best not going to damage either device.

You can install a remote desktop server on your Pi and a corresponding client on your laptop and, provided they are both on a network, remote from your laptop to your Pi's desktop.

---

### Post by kayve on 2016-02-10
OK.. so What is a monitor emulation client I should install on my laptop and how to I configure it to detect my pi?.. are you saying what I want is possible, or I need to perhaps use the pi's USB port instead and I have some USB devices that increase the number of ports.. I think they are .. well.. I need to check.. bridges or switches? Can I use that to build a network that accomplishes what I want?

CablesToGo USB 2.0 7port hub is one

I think I have a USB chord that is a two way wire

---

### Post by QIII on 2016-02-10
You need to have both devices on a network (wired or wireless) and install some sort of remote desktop application on each device.  I'm on my cell right now, so please excuse my brevity.

This might be helpful:  [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by kayve on 2016-02-10
oh wait it might be ethernet

the problem is I don't have a monitor to devote to the pi, so I was hoping to emulate a monitor with my laptop.. to change programs on the pi I guess one possibility is inserting it into my laptop and booting  my laptop from the pi SD card, but that is probably not possible because the SD card is configured to boot the pi device and not my laptop CPU, is this correct logic?

---

### Post by QIII on 2016-02-10
Not possible.  Raspbian and other OSes for SBCs are compiled for ARM architecture and will not boot or run on your laptop.

Remote desktop applications allow you to control and see another computer's desktop inside an application window that you can resize as you wish.  Once set up, you won't need a separate monitor.  But you will need to use one at least for a time to set up the Pi.  You can use the monitor just long enough to set up SSH and then log in to the Pi via the command line to set up the environment.

My Odroid is set up as a Server and does not have a monitor or desktop environment at all.  I interact with it in the command line over SSH.

But you will still need wireless or ethernet connectivity between the two on a network.

---

### Post by kayve on 2016-02-10
it just occurred to me I do not have a keyboard attached to the pi either.

---

### Post by QIII on 2016-02-10
A wireless keyboard and mouse using a wireless USB dongle can be used long enough to set up.

---

### Post by kayve on 2016-02-10
this guy seems to say you can change the direction of the port  [https://www.youtube.com/watch?v=uQBTn21214Q](https://www.youtube.com/watch?v=uQBTn21214Q)

the point is I don't have any of this hardware.

---

### Post by QIII on 2016-02-11
That isn't reversing the direction of the HDMI port.  That is creating a second desktop on one machine (Ubuntu already has multiple desktops, that is nothing new) and using that one to display the remote desktop on another machine on your LAN.  

TeamViewer is a remote desktop application, which is what I was suggesting above.

---

### Post by kayve on 2016-02-12
what would happen if I set my BIOS to boot from HDMI, plug the pi into the HDMI port and shutdown -r now?

---

### Post by gordintoronto on 2016-02-13
You're trying to do a lot of things which are impossible. Just to set up the pi, connect a keyboard, mouse and monitor, and set it up to host a remote desktop session. You can test it from your laptop. Once that is done, you can remove all the peripherals.

---

