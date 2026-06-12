---
title: "Ubuntu 10.04 and Nokia Booklet 3G"
date: 2010-05-27
forum: Hardware
---

### Post by Infra on 2010-05-27
Hello

Any users here who own the Nokia Booklet 3G and are using it with Ubuntu installed (10.04 preferred).

How well does it work, or does it work at all?

What would be the biggest drawbacks and what would i be missing if I installed Ubuntu on this nice piece of hardware?

What I have read, is that the biggest problem is the Poulsbo chipset (GMA500 etc), am I correct?

I'm using W7 Pro and Jolicloud at the moment. The problem with Jolicloud is the horrible battery life it gives (like 5hours max). Would the situation be better with Ubuntu?

---

### Post by Ranko Kohime on 2010-05-27
5 hours is pretty good for a laptop, but I guess when they advertise 12 it's not so hot.  :P

Still, I'd kill for 5 hours myself.  I've got 2/3 the battery capacity of yours.

---

### Post by Infra on 2010-05-27
> **Ranko Kohime said:**
> 5 hours is pretty good for a laptop, but I guess when they advertise 12 it's not so hot.  :P

Still, I'd kill for 5 hours myself.  I've got 2/3 the battery capacity of yours.

Well yeah it's pretty good but it's almost 50% less than with windows, so I'm not very happy :-)

---

### Post by chenga91 on 2010-07-01
Ubuntu 10.04 is pretty awesome on the Nokia Booklet. It's a lot faster than Windows and I'm averaging about 8 hours on it. When installing it, make sure you use the desktop version so that when you try to fix the screen resolution, it actually works. I tried doing it on the netbook remix, and every time i tried fixing it, after rebooting the computer, the screen would just be white.

The only other problem I'm having with the Nokia Booklet is that the wifi connection tends to disconnect after every 30 minutes or so. It gets to be a pain to reset the connection every time. Hopefully a fix will come out for it. :/

---

### Post by armika on 2010-07-28
Yep, got my booklet a month ago and running Ubuntu 10.04 on it. Battery lasts about one working day (~8 hours). The display driver thingy is a disappointment, since it also prevents me from using MeeGo; I hope it gets 'fixed' soon. Wifi and 3G work fine, haven't experienced disconnections and today I also managed to get the GPS working.

---

### Post by jxie90 on 2010-09-17
Anybody got the mic or webcam working on the Booklet?

---

### Post by nic4m on 2010-09-26
> **armika said:**
> Yep, got my booklet a month ago and running Ubuntu 10.04 on it. Battery lasts about one working day (~8 hours). The display driver thingy is a disappointment, since it also prevents me from using MeeGo; I hope it gets 'fixed' soon. Wifi and 3G work fine, haven't experienced disconnections and today I also managed to get the GPS working.

any hint how you got the GPS working? :)

---

### Post by armika on 2010-09-26
> **nic4m said:**
> any hint how you got the GPS working? :)

To enable the GPS write AT_OGPS=2 to /dev/ttyHS4 and to disable it write AT_OGPS=0

- Arto

---

### Post by tschakram on 2011-08-02
Hello

I am new with ubuntu.did you know how to insert the order?

I tested it with C-Kermit. But it doesnt works. 


~/bin/gps_on.sh:
#!/usr/bin/kermit

def port /dev/ttyHS4
def speed 115200
def carrier-watch off

set port \m(port)
if fail exit 1 Can't open \m(port)
set speed \m(speed)
set carrier-watch \m(carrier-watch)

output AT_OGPSP=7,2\13
input 3 OK

output AT_OGPSCONT=1,"IP","prointernet"\13
input 3 OK

output AT_OGPSLS=1, "http://supl.nokia.com"
input 3 OK

output AT_OGPS=2
input 3 OK

exit


For turning GPS off:


~/bin/gps_off.sh:
#!/usr/bin/kermit

def port /dev/ttyHS4
def speed 115200
def carrier-watch off

set port \m(port)
if fail exit 1 Can't open \m(port)
set speed \m(speed)
set carrier-watch \m(carrier-watch)

output AT_OGPS=0\13
INPUT 3 OK

exit

Sorry for my bad english.

thanks for answer
tschakram

---

### Post by vickoxy on 2011-08-02
I won´t open new thread, so i will post my questions here:
1) is there any Ubuntu Distribution that support GMA 500 and native Resolution?
2) is it possible to use Booklet via HDMI with external Display 1920x1080?
3) does Suspend or HIbernation work?

---

