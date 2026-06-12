---
title: "HP nc8230 COM port problem (can't connect to routers)"
date: 2006-08-17
forum: Hardware &amp; Laptops
---

### Post by markrez on 2006-08-17
Hello -
I have an HP nc8230 laptop that I cant get any communication to/from the serial port (COM1).

I have done the "sudo chmod a+rw /dev/ttyS0" as suggested in another thread.  

```
mark@cptr:~$ dmesg | grep tty
[17179573.936000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.936000] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[17179573.940000] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
```

When I go into minicom or gtkterm I dont get the usual response I would in Windows Hyperterm when connected to a router or other similar device (packetshaper, access gateway)

any thoughts?  :confused:

---

### Post by markrez on 2006-08-19
> **markrez said:**
> Hello -
I have an HP nc8230 laptop that I cant get any communication to/from the serial port (COM1).

I have done the "sudo chmod a+rw /dev/ttyS0" as suggested in another thread.  

```
mark@cptr:~$ dmesg | grep tty
[17179573.936000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.936000] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[17179573.940000] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
```

When I go into minicom or gtkterm I dont get the usual response I would in Windows Hyperterm when connected to a router or other similar device (packetshaper, access gateway)

any thoughts?  :confused:
no ideas?

---

### Post by khughes on 2007-02-22
I know it has been a long time since you made this post but I just came acrossed it and thought I would give you an idea if you still hadnt figured it out.

I had this same issue and corrected it by going into minicom options. In the options somewhere you will find a section called init string and it will have a whole bunch of junk in there. Clear all of that out and save changes and then try to connect with your specific connection settings for that router.

Another problem I had that still goes uncorrected is if you suspend to ram or disk, when you come back out you will need to restart before you serial port works again.

---

### Post by whilenski on 2007-03-13
I'm having the same problem.  I've got a Dell Latitude D600 that claims it has a 16550A as well.  I've got it so that it will sometimes print output from the Cisco router/switch I'm connecting to, but I can't send commands to it or get proper output from the commands (if they are being sent).

Installing setserial seems to have allowed me to at least get that far, however, it's still being a bugger.  I've tried setting ttyS2 to irq 5 since it was on the same irq as ttyS0 (to see if that might help), however, it hasn't.

I'm fresh out of ideas, although I'm still looking for answers.  I've created a thread here as well not realizing this one was here.

Anyone have any answers on it?

(edit - I'm running 6.10.  This worked fine with Hoary Hedgehog, Breezy Badger, and Dapper Drake, but seems to have broken with this install)

---

### Post by whilenski on 2007-03-13
> **khughes said:**
> I know it has been a long time since you made this post but I just came acrossed it and thought I would give you an idea if you still hadnt figured it out.

I had this same issue and corrected it by going into minicom options. In the options somewhere you will find a section called init string and it will have a whole bunch of junk in there. Clear all of that out and save changes and then try to connect with your specific connection settings for that router.

Another problem I had that still goes uncorrected is if you suspend to ram or disk, when you come back out you will need to restart before you serial port works again.

I've actually tried this as it was suggested on another board, but clearing the init string did nothing.

And I don't suspend my machine - this occurs from a regular boot.

---

### Post by whilenski on 2007-03-13
> **whilenski said:**
> I've actually tried this as it was suggested on another board, but clearing the init string did nothing.

And I don't suspend my machine - this occurs from a regular boot.

I just fixed it.  I don't know if it's a combination of what I had done previously or not, but turning Hardware Flow Control to off in Minicom did the trick.

---

