---
title: "Hardware failure? How to know? what to do?"
date: 2007-12-18
forum: Hardware &amp; Laptops
---

### Post by tacubuntuforums on 2007-12-18
Hello:

I've been experiencing some problems which I believe must be due to a hardware problem. But still don't know what may be working wrong. I'd like to know your opinion and if you know what tools could I use to detect it?

The most common thing that happens from time to time (sort of once every three hours) but very irregularly is that I see panel applets dying, especially the Monitor Applet and the Netspeed Applet. I suspect that is because they are refreshed more often. Two or three other applets have died in more than a month only. Moreover, the system sometimes freezes. In those cases usually everything freezes, sometimes moving the mouse works (or works a while). Typing Ctrl-Alt-Fx won't do anything and I have to turn off the computer with the power off button. A few times I'm logged out but experience problems when logging back.

Sometimes the system doesn't start properly: I log in graphically but not all things are loaded or they are but bash doesn't give me a prompt (or won't read the password in a different terminal) and I can't start new processes. So I have to reboot and then works fine. Normally one can experience none, one or two crashes in 14hrs. Maybe a bit more often this autumn, when the problem started, because it's much colder where it's working now.

It doesn't seem related to the load of the system or to using the Hard Disk. I can download a lot, browse the internet, watch videos, burn cd's, do certain computations, etc. It also happens when I'm not doing anything (with almost only the screensaver working or even without that, because I dissabled it) and it doesn't seem to be able to reproduce. It happens doing things that in a different moment would not happen. It vaguely seems to me that it happens sometimes  when it's going to start a new process or a process goes to running mode.

I have done the memtest86+ memory test 10 continuous hours plus other sessions.. a total of 14 hours aprox. And no error has been found with the standard test nor with a long period test (I don't remember its name)

This is a real example of the message displayed in all terminals a time when this happened a lot:


```
Message from syslogd@localhost at Wed Nov 14 14:44:39 2007 ...
localhost kernel: Recursive die() failure, output suppressed

Message from syslogd@localhost at Wed Nov 14 16:01:45 2007 ...
localhost kernel: Recursive die() failure, output suppressed

Message from syslogd@localhost at Wed Nov 14 16:18:34 2007 ...
localhost kernel: Recursive die() failure, output suppressed

Message from syslogd@localhost at Wed Nov 14 16:52:51 2007 ...
localhost kernel: Recursive die() failure, output suppressed

Message from syslogd@localhost at Wed Nov 14 17:16:51 2007 ...
localhost kernel: Recursive die() failure, output suppressed
```


An extract of 
 $ dmesg | tail -150

```
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hdb4, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
eth0: Media Link Off
eth0: Media Link On 100mbps full-duplex
NET: Registered protocol family 10
lo: Disabled Privacy Extensions
IPv6 over IPv4 tunneling driver
eth0: no IPv6 routers present
BUG: unable to handle kernel paging request at virtual address 0a742ea6
 printing eip:
c01ac43e
*pde = 00000000
BUG: unable to handle kernel paging request at virtual address 0a742ead
 printing eip:
c01ac43e
*pde = 00000000
BUG: unable to handle kernel paging request at virtual address 0a742ead
 printing eip:
c01ac43e
*pde = 00000000
Recursive die() failure, output suppressed
 <1>BUG: unable to handle kernel paging request at virtual address 0a742ea6
 printing eip:
c01ac43e
*pde = 00000000
BUG: unable to handle kernel paging request at virtual address 0a742ead
 printing eip:
c01ac43e
*pde = 00000000
BUG: unable to handle kernel paging request at virtual address 0a742ead
 printing eip:
c01ac43e
*pde = 00000000
Recursive die() failure, output suppressed
 <1>BUG: unable to handle kernel paging request at virtual address 0a742ea6
 printing eip:
c01ac43e
*pde = 00000000
BUG: unable to handle kernel paging request at virtual address 0a742ead
 printing eip:
c01ac43e
*pde = 00000000
BUG: unable to handle kernel paging request at virtual address 0a742ead
 printing eip:
c01ac43e
*pde = 00000000
Recursive die() failure, output suppressed
 <1>BUG: unable to handle kernel paging request at virtual address 0a742ea6
 printing eip:
c01ac43e
*pde = 00000000
BUG: unable to handle kernel paging request at virtual address 0a742ead
 printing eip:
c01ac43e
*pde = 00000000
BUG: unable to handle kernel paging request at virtual address 0a742ead
 printing eip:
c01ac43e
*pde = 00000000
Recursive die() failure, output suppressed
 <1>BUG: unable to handle kernel paging request at virtual address 0a742ea6
 printing eip:
c01ac43e
*pde = 00000000
BUG: unable to handle kernel paging request at virtual address 0a742ead
 printing eip:
c01ac43e
*pde = 00000000
```

Another day, just starting the session editing a text file it crashed
```
Dec  6 04:32:00 localhost -- MARK --
Dec  6 04:41:16 localhost kernel:  <1>BUG: unable to handle kernel paging request at virtual address 0a742ea6
Dec  6 04:41:16 localhost kernel:  printing eip:
Dec  6 04:41:16 localhost kernel: c01ac43e
Dec  6 04:41:16 localhost kernel: *pde = 00000000
Dec  6 04:41:16 localhost kernel: BUG: unable to handle kernel paging request at virtual address 0a742ead
Dec  6 04:41:16 localhost kernel:  printing eip:
Dec  6 04:41:16 localhost kernel: c01ac43e
Dec  6 04:41:16 localhost kernel: *pde = 00000000
Dec  6 04:41:16 localhost kernel: BUG: unable to handle kernel paging request at virtual address 0a742ead
Dec  6 04:41:16 localhost kernel:  printing eip:
Dec  6 04:41:16 localhost kernel: c01ac43e
Dec  6 04:41:16 localhost kernel: *pde = 00000000
Dec  6 04:41:16 localhost kernel: Recursive die() failure, output suppressed
```

The messages are almost always the same.

This PC is a Pentium4, 775MB RAM, almost 5 years old. A friend of mine told me that maybe I need to upgrade and flash the BIOS, but I think that if that were the problem then I would experience the failure doing the same things.

Anyone knows what could be done?

---

