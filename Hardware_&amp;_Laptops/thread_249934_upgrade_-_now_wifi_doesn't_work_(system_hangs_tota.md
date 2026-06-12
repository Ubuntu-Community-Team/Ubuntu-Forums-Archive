---
title: "upgrade - now wifi doesn't work (system hangs totally)"
date: 2006-09-03
forum: Hardware &amp; Laptops
---

### Post by dotdot on 2006-09-03
hi folks,
I've been using dapper (on my main laptop) for a while now and decided to upgrade another old laptop from breezy to dapper.

The old laptop is a vaio pcg x29 - my wireless usb box is a g122 dwl.

So i powered it up - connected to net - and upgrade flawlessly - took a few hours.

Now i find it simply won't enable connection to the driver without hanging the whole box.

It was configured with ndsiwrapper (rtsub ? ).
One thing i did notice in dmesg was
" rausb (WE) : Driver using old /proc/net/wirless support . please update driver" - followed by nothing - which from this angle doesn't exactly  inspire the average user.

Anyway - then deinstalled my wireless driver using ndiswrapper -e.
then re incorp it again.

So i'm at the prompt i type
lsusb it finds the dlink.
ndsiwrapper -l - says it's found the driver.
i start up networking.
For the wirelss connection it says.
The interface is not active. (i then check the properties - 
everything looks fine)

I then click on activate.

A couple of seconds go by then it hangs.....

Not great considering we're supposed to making ubuntu better not worse.

Any ideas people ?

..tia

---

