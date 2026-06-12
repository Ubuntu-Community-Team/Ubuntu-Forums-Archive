---
title: "ipw2200 and airsnort"
date: 2005-09-21
forum: Hardware &amp; Laptops
---

### Post by ceph_systems on 2005-09-21
Has anyone been able to get airsnort to function with the ipw2200 driver? 

There was another Ubuntu thread where someone claimed that airsnort should "work flawlessly" with the latest ipw2200 drivers.

So I downloaded the latest firmware, ieee80211, ipw2200 tarballs, went through everything--removing the old drivers via the provided scripts, "make"-ing and "make install"-ing.  

I was able to successfully join my wireless network, so I know that the drivers are in place.  

Then I placed my wireless card into monitor mode:
"iwconfig eth1 mode Monitor"

Then started airnort as root user.  I hit "Start"  and nothing happens.  And there are definitely two or more wireless networks to chose from.

Any advice or comments would be greatly appreciated.

Thanks

---

### Post by ceph_systems on 2005-09-22
OOPS!

Got it working....just in case this helps someone else......

This is completely obvious in retrospect and will probably be for intermediate to advanced Linux users.....

Have your wireless interface up.  THEN switch the card to monitor mode:

iwconfig eth1 mode monitor

Then starting airsnort with "sudo" or as root does the trick.

What doesnt work is bringing the interface down, switching to monitor mode and then bringing the interface up.....
or it might if you know what config files are affected and what and when to start and stop.

---

### Post by gkoshra on 2006-10-11
Hi everybody.

I used this method to get my airsnort working ( thanks ceph_systems ) and then I couldn't see the tinterweb, so I did:

**sudo iwconfig eth1 mode managed**

To change the mode back to normal, once you've finished cracking for the day - saving your session in the process - and want to look at the net( if you are connecting to the internet via a wireless router, that is ).

I am a n00b and so don't really understand what I am doing.

---

