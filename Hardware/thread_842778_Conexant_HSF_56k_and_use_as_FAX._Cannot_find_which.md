---
title: "Conexant HSF 56k and use as FAX. Cannot find which fax class modem supports"
date: 2008-06-27
forum: Hardware
---

### Post by iosifidis on 2008-06-27
Hello,

I'm new to this forum. I use the mailing list in my country (Greece).
I have Hardy Heron installed and I want to use the modem as fax.
Modem is Conexant HSF 56k. I installed it using the driver conexant_192-1ubuntu-1.tar.gz (or newer). I found on-line that it can be used as 14400 for free. I checked it with a friend from the Greek list and the modem was installed OK.
My lspci gives 02:02.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)

Well, now I try to send fax using efax-gtk.
My serial device is ttySHSF0
On the 3rd line (it's in Greek and I cannot remember the english word) I was told in the past to add 1,1,0,2,0,0,0,0
Class automatic.

On the parameters tab I was told to put
Init: Z &FE&D2S7=120 &C0 M1L0
Other parameters: -ozzzz

Those are the "strange" things I have.
When I'm trying to send a fax (file.ps) it returns:

Error: cannot find which fax class the modem supports

This is in short what it writes since it's in Greek.

Does anyone know what to do?
Thanks in advance
Stathis

---

### Post by iosifidis on 2008-06-27
Hello again,

I found this link:

[http://ubuntuforums.org/showthread.php?t=94448&highlight=Conexant+HSF+56k](http://ubuntuforums.org/showthread.php?t=94448&highlight=Conexant+HSF+56k)

at the bottom it says that free driver doesn't support fax.

So I got out my old USR Sporster 33600 on serial port. And I put ttyS0 as device. Well it worked until:

efax-0.9a: 00:46:04 Warning: bit-reversed HDLC frame, reversing bit order
efax-0.9a: 00:46:05 Warning: frame error
efax-0.9a: 00:46:08 Error: timed out reading frame data

and it ends the transmition. It has all above options.

Is there an idea?

---

