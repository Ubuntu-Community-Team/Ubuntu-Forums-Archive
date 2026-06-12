---
title: "Antec Veris Remote Control Power On Not Working"
date: 2011-06-13
forum: Hardware
---

### Post by eyesquare on 2011-06-13
I have been experiencing this problem after upgrading from 10.04 to 11.04 two weeks back. I'm no longer able to switch on my computer using the Antec Veris remote control, an IMON 0038 remote. 

I can however get it to work in the foloowing ways. If I boot from the 10.04 live CD and shutdown, the remote can switch on my computer. If I switch of the power and switch it back on, the remote works. This tells me it is most likely a change in 11.04 that is causing this behaviour.

I found a post on the Antec site saying that when you use the remote to power on the computer, the Antec hardware checks if the computer is actually powered off by checking for activity on the USB port. I'm not sure if this could be the problem, that in 11.04 the USB port is not powered down?

I'm at a total loss at what to check next. Any help will be appreciated!

---

### Post by RowanC on 2011-06-14
Hi, I'm also having this problem, and am wondering if it's due to the changes in the way Ir is now handled in the kernel ? anyone out there know how to make it work again??

---

### Post by danellisuk on 2011-06-23
I have the same issue, but unfortunately no solution yet :(

---

### Post by RowanC on 2011-06-25
Mine is going now - 

When I sat down to make the LCD go (as it didn't work by default) the power button magically started working!

To make the LCD go, all I had to do was install LCDproc (i did it via synaptic), and then change the line in /etc/LCDd.conf.

so...
```
sudo nano /etc/LCDd.conf
```
then change the driver line from 
```
Driver=curses

```
to
```
Driver=imonlcd

```
In this file you can also change some of the other default behaviours of the LCD

I hope this works for you guys too!

Edit:
This seemed to have helped, but only once. It's stopped working again. Looks like we get exercise.

---

