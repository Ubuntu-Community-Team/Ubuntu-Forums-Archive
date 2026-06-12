---
title: "lirc ir blaster troubles"
date: 2009-02-15
forum: Hardware
---

### Post by Shu3636 on 2009-02-15
I had a working system, but am upgrading to a newer PC and Ibex.  I have an IRMan and a homebrew serial IR blaster.  They worked great under Feisty.

Got lirc configured to where everything looks good, IRMan is receiving signals, but the blaster is not emitting any signals.  Device used to work, and when I cat some random file to /dev/ttyS1, it lights up under a digital camera, so hardware seems valid.

There are no error messages, lirc seems to think everything is good, but the results aren't there.

I've tried to simplify the sequence, removing config files from the equation, doing stuff from the command line.  Device is on COM2.

In terminal 1:
```
~$ sudo setserial /dev/ttyS1 uart none
~$ sudo modprobe lirc_serial irq=3 io=0x2f8
~$ sudo lircd -n -d /dev/lirc1 -o /dev/lircd1 /etc/lirc/lircd.conf
```

In terminal 2:
```
~$ ls -l /dev/lirc*
crw-rw---- 1 root root 61, 0 2009-02-14 14:05 /dev/lirc0
crw-rw-rw- 1 root root     0 2009-02-14 14:05 /dev/lircd
crw-rw-rw- 1 root root     0 2009-02-14 14:05 /dev/lircd1

~$ ./channel.pl 123
```

The response in terminal 1 is:
```
lircd-0.8.3[13045]: accepted new client on /dev/lircd1
lircd-0.8.3[13045]: removed client
lircd-0.8.3[13045]: accepted new client on /dev/lircd1
lircd-0.8.3[13045]: removed client
lircd-0.8.3[13045]: accepted new client on /dev/lircd1
lircd-0.8.3[13045]: removed client
lircd-0.8.3[13045]: accepted new client on /dev/lircd1
lircd-0.8.3[13045]: removed client
```
(send the three numbers then 'enter')

Seemed to go exactly as planned.  However, no signals were emitted from the blaster.

I've tried loads of stuff, a wide variety of different options and config changes, all to no avail.

Can any kind soul lend a helping hand?

Thank you.

---

### Post by Shu3636 on 2009-02-15
I resolved this on my own, updating here in case anybody runs into something similar.

I failed to add 1 important detail in my original post, that I'm not using on board COM ports, they are from a Rosewill PCI serial card.

That changes the address and irq values from the deaults for the serial ports.

Changing the module to load with the correct values led to lircd complaining "device or resource busy".

Adding the parameter "share_irq=1" to the load module solved that.

Now everything works perfectly.

---

