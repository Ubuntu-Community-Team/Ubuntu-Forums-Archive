---
title: "Ubuntu 8.10 on HP dv4t with Intel Wifi Link 5100"
date: 2008-11-26
forum: Hardware
---

### Post by Yankee_Fan on 2008-11-26
I've been browsing through the messages and can't seem to find the answer anywhere. I'm running 8.10 x86_64 and I can't figure out how to make the wireless card run in 802.11n mode. It's only working in 802.11g mode. Has anyone been able to make this work in 802.11n mode? Thanks for any info you can provide.

---

### Post by Yankee_Fan on 2008-11-26
Doesn't anyone around here use 802.11n?????

---

### Post by Yankee_Fan on 2008-11-27
Bump??

---

### Post by Yankee_Fan on 2008-12-04
Bump again!  I can't find any info anywhere on how to make this card work in 802.11n mode.....and according to Intel's website...it should work in N-mode using the *iwlagn* driver.

---

### Post by davehardy20 on 2008-12-17
I have a Lenovo W500 with the same issue, wireless 'n' does not appear to be working. Anybody any clues???

---

### Post by punkybouy on 2008-12-17
Isn't the speed set at the router level and not at the host level?  Is your router set to "n"?

---

### Post by Yankee_Fan on 2008-12-17
Yes, the router is set to "N" mode....my wife's Winblows laptop connects at "N" speeds to it and the router reports the type of connection.  Right now it reports my wife's laptop as an "N" connections whereas my laptop running Ubuntu Intrepid shows up as a "G" connection.  When I had Winblows on this laptop, it connected as "N".

---

### Post by stan01 on 2008-12-25
Same story here with a dell e4200 with an intel 5100 agn card: it won't go faster than g. A Draytek vigor N61 usb stick works fine in n mode however. In my case it might have to do with the wireless router i am using (draytek 2820).

---

### Post by avilella on 2009-01-25
Hi,

I took the liberty of creating a launchpad team for the people who own or develop for the Dell Latitude E4200/E4300 laptops, so that we can have more visibility upstream when having to ask for patches or support.

[https://launchpad.net/~e4200-e4300](https://launchpad.net/~e4200-e4300)

I'll be sending a couple of messages to ubuntuforums and notebookreview forums to gather the ~15 users I've identified so far.

Cheers,

Albert.

> **stan01 said:**
> Same story here with a dell e4200 with an intel 5100 agn card: it won't go faster than g. A Draytek vigor N61 usb stick works fine in n mode however. In my case it might have to do with the wireless router i am using (draytek 2820).

---

### Post by JDahl on 2009-01-25
The missing 802.11n capabilities of the Intel Wifi 5100 card is a very
well known problem, and trying to connect to a 802.11n network most
likely causes kernel panics on Ubuntu 8.10:

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/276990](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/276990)

It's also mentioned under "known problems" of the Ubuntu 8.10 release notes.

Supposedly, the 2.6.28 kernel will fix this.

---

