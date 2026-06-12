---
title: "Problem with hardware (WiFi) after suspend / improper shutdown"
date: 2018-02-07
forum: Hardware
---

### Post by gde061-www on 2018-02-07
I've been using 16.04 with my Thinkpad L560 for years.  Recently I had power disconnect while the battery was out and the system experienced a improper shutdown (it wasn't a power surge or anything like that -- just got unplugged accidentally).  When it came back up something was messed up with the WiFi.  Now when it goes into suspend, either from shutting the lid or from timeout, the WiFi fails to connect, with the message "device not ready".   

Also the display would not come up at one point after shutting the lid, even though the various lights and sounds indicated the system had woken up... 

I attached the output of dmesg (didn't know what I should grep for... ) that has some ACPI and iwlwifi errors, but unfortunately I don't know what they mean or what I need to do.

Presumably there is a way to "uncorrupt" whatever got clobbered?

---

### Post by gde061-www on 2018-02-07
** UPDATE ** Problem appears to have resolved following advice found here: [https://appuals.com/ubuntu-16-04-to-17-10-wifi-and-ethernet-problem/](https://appuals.com/ubuntu-16-04-to-17-10-wifi-and-ethernet-problem/)

It may to have had something to do with the random MAC seeding, but after disabling that in the config file, and restarting the service, I removed that line and again restarted the service and now everything seems to be working as it was before, so it may have been as simple as just needing to manually restart the service with ```
$ sudo service network-manager restart
```.

I'm curious if something similar might have caused the video display service (don't know what it's called) to crap out ... but that issue hasn't reoccurred.

I have to say I'm quite put-off that there was nobody on the boards here who could offer advice.

---

