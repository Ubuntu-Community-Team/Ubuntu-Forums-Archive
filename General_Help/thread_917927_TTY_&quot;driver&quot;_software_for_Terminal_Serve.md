---
title: "TTY &quot;driver&quot; software for Terminal Server"
date: 2008-09-12
forum: General Help
---

### Post by mutnik on 2008-09-12
Hello,

I am looking for some software that will allow the RS232 ports on a terminal server to appear to be local TTYs on Linux.

I have a _Xylogics Micro Annex XL_ 16 port terminal server and would like full use of the RS232 ports.

If any one could point me in the right direction I would appreciate it.

Brett

---

### Post by cdenley on 2008-09-12
I think all you have to do is add a file like this for each port:

/etc/event.d/ttyS0
```

start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5

stop on runlevel 0

respawn
exec /sbin/getty 115200 ttyS0

```

I can't try it, though, since my computer doesn't have any serial ports.

---

### Post by mutnik on 2008-09-12
Yes.  The gettys will work to hook a serial terminal up to a local serial port on the PC.

However, my PC also does not have any serial ports.  I have a terminal server which is a separate piece of hardware.  It has 16 serial ports and 1 ethernet port.  The software I am looking for would connect to the terminal server over ethernet and allow communication with the 16 serial ports.  

The software would also take care of mapping each serial port on the terminal to a TTY device on Linux.

In the past I have seen such software for AIX and other UNIXes, but I am looking for an open source version for Linux.

---

### Post by cdenley on 2008-09-12
> **mutnik said:**
> Yes.  The gettys will work to hook a serial terminal up to a local serial port on the PC.

However, my PC also does not have any serial ports.  I have a terminal server which is a separate piece of hardware.  It has 16 serial ports and 1 ethernet port.  The software I am looking for would connect to the terminal server over ethernet and allow communication with the 16 serial ports.  

The software would also take care of mapping each serial port on the terminal to a TTY device on Linux.

In the past I have seen such software for AIX and other UNIXes, but I am looking for an open source version for Linux.

Did you try ttyd? What was the software called?
```

sudo apt-get install ttyd

```

---

### Post by mutnik on 2008-10-07
It looks like ttyd may be the solution I am looking for.  

The previous software that I encountered for AIX was part of the Remote Annex/Annex Manager package.  I am not exactly sure what the full capabilities of the Annex software were.  At the time we received the Micro-Annex terminal server from Xylogics to use for testing.  It was never rolled out into production and therefore I was never asked to support it.

I have just started looking at ttyd's documentation.  I am pretty sure it will work to receive the caller id info from my modem and to communicate with my X10 controller.  I am not yet certain how well it will work with my IR receiver.

Thanks for the info!

---

### Post by mutnik on 2008-10-07
Now that I know the name of the 'ttyd' package, I have quickly discovered the 'termnetd' package which appears to provide similar functionality as well.

Finding out about these serial communication packages was made somewhat difficult by the overload of information that I found regarding Linux thin clients whenever I used the search term "terminal server".  Even searching for terms like DTR, DSR, RTS, CTS, RS-232, RS-485 did not yield the results I was hoping for.

---

### Post by cdenley on 2008-10-07
> **mutnik said:**
> Now that I know the name of the 'ttyd' package, I have quickly discovered the 'termnetd' package which appears to provide similar functionality as well.

Finding out about these serial communication packages was made somewhat difficult by the overload of information that I found regarding Linux thin clients whenever I used the search term "terminal server".  Even searching for terms like DTR, DSR, RTS, CTS, RS-232, RS-485 did not yield the results I was hoping for.

Yes, thanks to windows, all the new linux users think terminal server is something a "remote desktop" client connects to.

---

