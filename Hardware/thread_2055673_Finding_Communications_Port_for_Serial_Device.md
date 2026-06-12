---
title: "Finding Communications Port for Serial Device"
date: 2012-09-09
forum: Hardware
---

### Post by dodle on 2012-09-09
I don't know all of the terminology for what I am trying to do so please excuse me if there is some confusion.  I am trying to connect to an SATA hard drive via PUTTY in an attempt to unbrick it. I have it connected from the ground/tx/rx cables to a USB port. [According to the tutorials]("http://www.overclock.net/t/457286/seagate-bricked-firmware-drive-fix-with-pics"), on Windows, I should use a communications port (e.g. COM9). But I am not sure how to detect through which port my device is connected. By default PUTTY is set to /dev/ttyS0, but that does not work.

**----- Note -----**

I was attempting to do this earlier but when I got to where I needed to press "Ctrl-Z", putty did nothing. No prompt appeared.

---

### Post by dandnsmith on 2012-09-10
I found that that tutorial doesn't show all the words, and couldn't find how much was missing. However, I managed to salvage enough to work out that the author was using a connection from the drive (SATA) to a modem port (he says he was using a telephone cable, and had obviously organised the connections - which would get him using a serial port /dev/ttySx.

You are talking about using a USB port, and you wouldn't have the same connections to wire, and not the same port configurability.

I hope this helps

---

### Post by dodle on 2012-09-11
I figured out how to find the port using the following command sequence:

```
# Without hard drive connected
[****@****]$ ls -l /dev > f1
# With hard drive connected
[****@****]$ ls -l /dev > f2
[****@****]$ diff f1 f2
8c8
< drwxr-xr-x. 2 root root        3320 Sep 11 13:21 char
---
> drwxr-xr-x. 2 root root        3280 Sep 11 13:25 char
54c54
< crw-rw-rw-. 1 root tty       5,   2 Sep 11 13:24 ptmx
---
> crw-rw-rw-. 1 root tty       5,   2 Sep 11 13:25 ptmx
76d75
< drwxr-xr-x. 4 root root          80 Sep 11 13:21 serial
158d156
< crw-rw----. 1 root dialout 166,   0 Sep 11 13:21 ttyACM0
```

I was able to determine that it was connected at /dev/ttyACM0.

But I am running into the same problem I was having in Windows: The PuTTY terminal opens like it is connected but I can't type anything. 'Ctrl-Z' should bring up a prompt but it doesn't. The loopback test worked so there should be nothing wrong with the cable.

**----- SOLVED -----**

Ah!!! I had the TX and RX cables reversed, doh!

---

### Post by drdos2006 on 2012-09-11
That was a interesting post. 

Can I ask "Did you need to convert the 5 volts to a lower voltage ?"

Do you know what bricked the drive in the first place ?

regards

---

### Post by dodle on 2012-09-11
These Seagate Barracuda 7200.11 drives are prone to bricking because of a firmware issue. Unfortunately that is not the only problem. Apparently there is also a faulty heads issue, which this drive seems to be suffering from as well.

I'm not sure what you mean by converting the 5v. It was recommended to use a 3v battery to power the ca-45 cable but I was able to do it with two 1.5v AA batteries. That was one thing that was missing in many of the tutorials, the cable needs to be hooked up to a battery using the two extra wires. On mine they were yellow (negative) and red (positive).

---

### Post by drdos2006 on 2012-09-11
Thanks for that.

How did you connect the 3 volts, was it on the Power Connector on pins 1,2,3 and 4 for ground ?

USB normally delivers 5 volts.


regards

---

