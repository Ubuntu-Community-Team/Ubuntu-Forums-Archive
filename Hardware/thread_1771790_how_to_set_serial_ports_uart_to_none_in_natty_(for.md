---
title: "how to set serial ports uart to none in natty (for lirc)?"
date: 2011-05-30
forum: Hardware
---

### Post by hachel on 2011-05-30
hello,

i'm trying to setup lirc.
Unfortunately I seem to be the only one still using it. I tried to google my problem and a lot of other people were having the same issues but all the proposed solutions (which worked eventually then) involved files that no longer exist because the most recent results where from 2008 or they were related to gentoo.

Anyway, the problem is that I cannot load the necessary lirc_serial module because my serial port is in use:
```
hachel@hachelbbd:~$ dmesg | grep serial
[    0.753005] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.840843] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   12.133310] lirc_serial: module is from the staging directory, the quality is unknown, you have been warned.
[   12.245857] lirc_serial: port 03f8 already in use
[   12.245862] lirc_serial: use 'setserial /dev/ttySX uart none'
[   12.245864] lirc_serial: or compile the serial port driver as module and
[   12.245866] lirc_serial: make sure this module is loaded first
```

Now if I type setserial... by hand lirc works perfectly until I reboot. I found solutions that said I should edit /etc/serial.conf or /etc/modprobe.d/lirc.conf, neither of which exist, to make it permanent. Or I should edit /var/lib/setserial/autoserial.conf which also didn't help.

What makes debugging this even more difficult is that logging seems to have changed completely in natty. I couldn't find anything related to lirc in any of the log-files (until I added lirc_serial to /etc/modprobe according to a thread about gentoo from 2005 which then at least provided me with above dmesg output).

Well, I hope somebody still uses lirc on a serialport, though I have little hope.

Thanks in advance,

hachel

---

### Post by hachel on 2011-05-31
hello, something I found out,

lirc seems to initiate before setserial frees the port. Therefore lirc complains it can't load but after boot I can modprobe lirc_serial without complaining.

I'm not too good with linux, but in /etc/rc0.d/ lirc comes before setserial if thats of any matter.

What would I have to do?

---

