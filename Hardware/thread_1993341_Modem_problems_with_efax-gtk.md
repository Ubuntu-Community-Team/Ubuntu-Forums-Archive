---
title: "Modem problems with efax-gtk"
date: 2012-06-02
forum: Hardware
---

### Post by RogerDavis on 2012-06-02
I upgraded from Ubuntu 10.04 to 12.04. All WAS WORKING in 10.04. I suspect I need to enter different commands in the init string, but not sure what to change. Maybe ttyS1 to ? something for internal connections? Current init string is Z &FE&D2S7=120 &C0 M1L0 

Modem is USR V.90 / V.92 Model 5610C Performance Pro Modem, _using all standard command sets_ - INTERNAL, NOT WINMODEM!!!

sudo lspci gets the below modem info:
06:02.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01)

Using ttys0 gets the following messages: 
Socket running on port 9900 
efax-0.9a: 20:23:57 opened /dev/ttyS0 
efax-0.9a: 20:24:03 sync: dropping DTR efax-0.9a: 20:24:08 sync: sending escapes efax-0.9a: 20:24:13 Error: sync: modem not responding 
efax-0.9a: 20:24:13 failed page /home/roger/Downloads/VSP Benefits 2010.pdf.001 efax-0.9a: 20:24:13 finished - no response from modem

For ttys1
Socket running on port 9900
efax-0.9a: 21:12:23 opened /dev/ttyS1
efax-0.9a: 21:12:23 failed page /home/roger/Downloads/VSP Benefits 2010.pdf.001
efax-0.9a: 21:12:23 Error: tcgetattr on fd=8 failed: Input/output error
efax-0.9a: 21:12:23 Error: fax device write: Input/output error
efax-0.9a: 21:12:25 Error: tcgetattr on fd=8 failed: Input/output error
efax-0.9a: 21:12:27 Error: fax device write: Input/output error
efax-0.9a: 21:12:29 sync: dropping DTR
efax-0.9a: 21:12:29 Error: tcgetattr on fd=8 failed: Input/output error
efax-0.9a: 21:12:30 Error: tcgetattr on fd=8 failed: Input/output error
efax-0.9a: 21:12:30 Error: tcgetattr on fd=8 failed: Input/output error
efax-0.9a: 21:12:32 Error: fax device write: Input/output error
efax-0.9a: 21:12:34 sync: sending escapes
efax-0.9a: 21:12:34 Error: tcgetattr on fd=8 failed: Input/output error
efax-0.9a: 21:12:34 Error: fax device write: Input/output error
efax-0.9a: 21:12:34 Error: fax device write: Input/output error
efax-0.9a: 21:12:34 Error: tcgetattr on fd=8 failed: Input/output error
efax-0.9a: 21:12:34 Error: fax device write: Input/output error
efax-0.9a: 21:12:34 Error: fax device write: Input/output error
efax-0.9a: 21:12:36 Error: fax device write: Input/output error
efax-0.9a: 21:12:38 Error: fax device write: Input/output error
efax-0.9a: 21:12:40 Error: sync: modem not responding
efax-0.9a: 21:12:40 Error: tcgetattr on fd=8 failed: Input/output error
efax-0.9a: 21:12:40 finished - unrecoverable error

Can anyone help!?!

---

### Post by antmenj on 2012-09-13
I also had a fault getting this working but I suspect its different from the above.

I am using a full external hardware modem.  It seemed as if the program could not find the com port aka ttyS0.

The fix:

```
gksudo gedit /etc/group
```

Look for the line that says:

```
dialout:x:20:
```

So lets say your log in name is john.  Add to the line as follows.

```
dialout:x:20:john
```

Save the file and exit.  I can't remember if any rebooting was required or not.

Should keep the fax spammers at bay for a little longer.

---

### Post by RogerDavis on 2012-11-05
Switched to ttyS4, and now when I try to send, I get :
Socket running on port 9900
efax-0.9a: 12:49:40 opened /dev/ttyS4
No sounds, no nothing. It will sit there forever that way.

Also - the "light" always remains red, so I think DTR is never raised
and
roger@roger-desktop:~$ dmesg | grep tty gets
[ 0.000000] console [tty0] enabled
[ 1.448980] 0000:04:01.0: ttyS4 at I/O 0xd000 (irq = 17) is a 16550A

---

### Post by fhqiihcy on 2012-11-05
you can search it with google.com [IMG]http://allkindsofpic.info/images/giai.gif[/IMG]

---

