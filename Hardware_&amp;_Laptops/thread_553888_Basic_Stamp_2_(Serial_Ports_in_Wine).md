---
title: "Basic Stamp 2 (Serial Ports in Wine)"
date: 2007-09-18
forum: Hardware &amp; Laptops
---

### Post by JustAboutRealJAR on 2007-09-18
I'm having a problem with serial ports in wine... I think

I managed to get a CLI Basic Stamp programmer to work so I know the serial port works, and that the Basic Stamp works. But for some reason, the Parallax IDE isn't recognising the Basic stamp.

So I set up Test #1:
Plug in Basic Stamp, and click "Identify" (which just looks for devices and identifies them)

Result: No Device found... BUT! on Com2 we have (this is not code)
```
loopback: yes; echo:no
```

when I disconnect the Basic stamp from the serial port, it changes to 
```
loopback: no; echo:no
```

Test #2:
So I remove all the com ports from ~/.wine/dosdevices/ only to see the SAME RESULT!
Loopback:yes when it's plugged in Loopback:no when I disconnect it.

Why am I not getting something like... "No Com ports detected" ?

I am stumped... Please tell me anything at all that you know about wine!

Is there a way to reset the wineserver? or something like that?

Thanks,
Jim

---

### Post by barney_1 on 2008-01-17
Did you ever solve the problem?  I'm having the same issue.  Com1 reports Loopback: yes and echo: no

---

### Post by JustAboutRealJAR on 2008-01-19
> **barney_1 said:**
> Did you ever solve the problem?  I'm having the same issue.  Com1 reports Loopback: yes and echo: no

I just used the Parallax IDE to write the code, and then programmed the Basic stamp with the command line utility. Works great

---

### Post by m3tr0g33k on 2008-02-07
I have wine 0.9.54 and no config for serial ports. Just makinga link in dosdeviceS doesn't show any ports in my win apps. Could Someone help with what I'm missing?

Thanks in advance!

---

### Post by JustAboutRealJAR on 2008-02-10
I think this may be a bug... I was never able to get the serial ports working in wine... I eventually just gave up and used the command line utility to program my basic stamp.

Try contacting the WINE devs... see if they can steer you in the right direction

---

### Post by imog on 2008-07-01
> **JustAboutRealJAR said:**
> I think this may be a bug... I was never able to get the serial ports working in wine... I eventually just gave up and used the command line utility to program my basic stamp.

Try contacting the WINE devs... see if they can steer you in the right direction


I am working on a different serial port issue, and I came across information that may be applicable for your issue.

You need to configure sym links in the ~/.wine/dosdevices folder, something like this:

ln -s /dev/ttyS0 ~/.wine/dosdevices/com1


That way wine knows where to find your serial port.

---

