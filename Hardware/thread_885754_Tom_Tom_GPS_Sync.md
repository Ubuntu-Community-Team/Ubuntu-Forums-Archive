---
title: "Tom Tom GPS Sync"
date: 2008-08-10
forum: Hardware
---

### Post by Databit on 2008-08-10
I have converted a few coworkers into Ubuntu users since Hardy Heron was released and they all seem to love it. Out of the 8 or 9 of them 2 people have had trouble. One I just simply told them "You are surprised that  doesn't support all the functionality of MICROSOFT messenger?" and they are happy now.

The other "dissatisfied customer" is about to call 1 issue a deal breaker. Her husband uses a Tom Tom GPS and tried to sync it. (No dual boot just straight up Ubuntu). They are upset at the right place "Why wouldn't Tom Tom have a download for Linux they have it for Windows and Apple?" which I found to be the perfect question. 

I've never used a GPS because I'm one of those look at a map for 5 or 10 minutes and know the city type people. I can't seem to find any instructions for getting it to work in Wine and I'm not sure if it will work there or not. Anyone know of anywhere I can look/send her way to get her happy again?
Thanks

---

### Post by flint_ on 2009-02-15
...and this is odd because the TomTom is, in fact a Linux device.

My only advice here is to watch my tomtom development page [http://docbox.flint.com:8081/tomtom](http://docbox.flint.com:8081/tomtom) or look at [http://www.opentom.org/](http://www.opentom.org/)
for more information.  Please post your research to this forum.

Regards,


Flint

---

### Post by FiReSTaRT on 2009-03-04
My research hasn't shown anything. Fortunately I can dust off one of the Windoze boxes or probably make it work under virtualization, but I'd prefer to do it under Ubuntu.

---

### Post by thavid on 2009-08-11
Hey. I've contacted TomTom about that same issue. Their reply to my e-mail was simply this:

"Sorry but tomtom doesn't support other systems than Windows and OSX, and there is no plan to support other platforms in a near future".

So, thank you TomTom, for my next SatNav I'll be choosing another brand, for sure...

---

### Post by quatrox on 2009-09-20
> **thavid said:**
> Hey. I've contacted TomTom about that same issue. Their reply to my e-mail was simply this:
 
"Sorry but tomtom doesn't support other systems than Windows and OSX, and there is no plan to support other platforms in a near future".
 
So, thank you TomTom, for my next SatNav I'll be choosing another brand, for sure...
 
It is people like you that makes the difference!
 
It looks like others had better luck:
[http://fixunix.com/ubuntu/535226-linux-distribution-tomtom-home.html](http://fixunix.com/ubuntu/535226-linux-distribution-tomtom-home.html)
 
I recommend people to stand up and ask. There are a lot of
GNU/Linux users with Tomtom devices but I assume most of
us don't actively ask for GNU/Linux software for it.
 
Let them know that they should not ignore a growing number of
their users/customers.

---

### Post by rodolphoarruda on 2010-04-15
> **thavid said:**
> I'll be choosing another brand, for sure...

Just wonder if someone has a list of Linux friendly GPS devices. Any URLs to point to in that regard.

tks

-RA

---

### Post by jsampaio57 on 2010-12-25
At last, a light at the end of the tunnel...
You should try [http://pytomtom.tuxfamily.org](http://pytomtom.tuxfamily.org)
Still in version 0.5, but at least, it can recognize a TomTom device connected to the usb port, and do some actions as GpsQuickFix, Backup and restore, and handle POI.
Download the pyTomTom.tar.gz file (the .deb didn't install in my machine), and extract it's folder. Connect the TT device; go to the folder extracted and execute pytomtom.sh

This is a long lasting, but promissing begin. Cheers, and Merry Christmas!

Jorge

---

### Post by trinitydan on 2010-12-25
Not to steer you away from open source alternatives, but have you tried running their software in Wine?  It is a bit of a long shot, but if the software runs ok, I think you can probably get that device to be recognized from the USB in wine.  I managed to get my DeLorme GPS working with DeLorme Windows software running in Wine anyway, so maybe the method would work.

Edit: Just noticed this thread is ancient so I guess the OP might not see this...

---

