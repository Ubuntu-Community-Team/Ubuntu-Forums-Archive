---
title: "USB Dongle Busy but can't tell why"
date: 2011-10-06
forum: Hardware
---

### Post by radiosgalore on 2011-10-06
ok this is a last ditch attempt here as everywhere else I've tried gets no reply or the users can't figure it out. My command line knowledge is very limited and i have to google to find the right commands normally. Anyway I have a T-Mobile Internet Dongle that will not connect despite manually configuring the details inc APN and having ejected it as initially the computer classed it as a hard drive. its the latest bit of code thats the most puzzling

[COLOR=#333333][FONT=Times New Roman][FONT=Lucida Grande]sudo wvdialconf 
Found an USB modem on /dev/ttyACM0.
Modem configuration written to /etc/wvdial.conf.
ttyACM0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2"
ttyACM1<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyACM1A<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

we see it finds the modem then the key part of the next command...

GNOME PPP: STDERR: ttyACM0<Info>: **Device or resource busy**
GNOME PPP: STDERR: Modem Port Scan<*1>: ACM0
GNOME PPP: STDERR: ttyACM1<Info>: **Device or resource busy**
GNOME PPP: STDERR: Modem Port Scan<*1>: ACM1
GNOME PPP: STDERR: ttyACM1A<Info>: **Device or resource busy**

it finds the modem then says its busy. Busy with what? I ejected the modem and we agree that blue flashing means the modem is saying everything is ok so what is it doing? It gets better as we see below
[/FONT][/FONT][/COLOR][COLOR=#333333][FONT=Times New Roman][COLOR=#000000][FONT=Lucida Grande]
sudo lsof /dev/ttyAMC1
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/guest/.gvfs
Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/andrew/.gvfs
Output information may be incomplete.

This last i believe should have told me what why the device was busy but obviously it did nothing of the sort. I read it the message could be suppressed by using -w but it didnt recognise the command[/FONT][/COLOR][/FONT][/COLOR]

I have the same issue on Ubuntu and Mint. I think if i recall the only difference is minor GUI variations though i could be wrong

---

