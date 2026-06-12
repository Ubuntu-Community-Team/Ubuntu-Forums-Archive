---
title: "Wireless help"
date: 2006-07-14
forum: Hardware &amp; Laptops
---

### Post by landwomble on 2006-07-14
Hi All,
Linux noob here with Ubuntu Dapper on X31 thinkpad.
Can't get my 3com officeconnect wifi card to do very much under Ubuntu, although it is recognised it won't connect.
I'm going to try another spare card but have a few questions:

1) If I boot with another card in, will it be automatically detected if Ubuntu has the driver?  Don't want to reinstall if can help it.  If not, what do I need to do?

2) After tinkering with ndiswrapper with the 3COM, on boot now I get warning messages about ndiswrapper before Gnome starts.  If I remove the package for ndiswrapper via synaptics, will this remove it and the error messages?  If not, what config files do I need to look at to put it back the way it was before?

Cheers
Ric

---

### Post by encompass on 2006-07-14
For question one... yes.. it will jsut load it up with no question... you probably wont see anything as it loads the driver... jsut see if it is in the Network manager when your all done booting.

---

### Post by encompass on 2006-07-14
And question 2 it should... try to avoid ndiswrapper if you can.  They are not the best way to go because you would probably want to support an open driver.

---

### Post by landwomble on 2006-07-14
great, thanks.  Will try it out this weekend and see if it helps.
Bit of a steep learning curve, this, and having a two and a half year-old and another on the way means my experimental ubuntu-time is usually in the middle of the night!

---

