---
title: "How to know if Tx buffer empty in USB-SERIAL"
date: 2008-10-16
forum: General Help
---

### Post by Ebc1de on 2008-10-16
Hi,

I am looking for a way to figure out if all data written to a virtual serial port has been transmitted so that I can switch the modem to Receive mode. I was using a real serial port earlier (/dev/ttySN) and was able to query the status via the LSR, i.e.
ioctl(fd, TIOCSERGETLSR, &lsr);
and wait till lsr was empty.

Now, I am using a USB port (/dev/ttyUSB0) to emulate a serial port and looking for a way to know when the written data has gone out on the line (the above ioctl() call doesn't work).
The functions wait_until_sent() and tty_wait_until_sent() which seem to be an option don't seem to be available to non-driver code.
At least, the files I have #included don't seem to work or exist.

I am using ubuntu 7.10.

Thanks for any pointers.

Ebc

---

