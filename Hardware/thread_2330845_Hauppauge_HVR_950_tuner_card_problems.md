---
title: "Hauppauge HVR 950 tuner card problems"
date: 2016-07-15
forum: Hardware
---

### Post by 4kh3RAm on 2016-07-15
I have a Hauppauge HVR 950 tuner card.

I can not get it to get TV channels using either MythTv or VLC.

MythTv froze when it got to selecting country.

Using VLC

When I ran

```
w_scan -c US -X > channels.conf
```

I got this.
> 
ERROR: Sorry - i couldn't get any working frequency/transponder
 Nothing to scan!!

Can someone help me.

Thanks.

---

### Post by deadflowr on 2016-07-15
Moved to ***Hardware***

If by "MythTv froze when it got to selecting country."
you mean during the initial setup, then that might be an error with the database's username or password setting.
fwiw

---

### Post by 4kh3RAm on 2016-07-15
How can I fix that ?

Latest attempt to scan for channels.

> w_scan -c US -X 
w_scan version 20141122 (compiled for DVB API 5.10)
using settings for UNITED STATES
ATSC
VSB US/CA, DVB-T TW
scan type TERRCABLE_ATSC, channellist 1
output format czap/tzap/szap/xine
WARNING: could not guess your codepage. Falling back to 'UTF-8'
output charset 'UTF-8', use -C <charset> to override
Info: using DVB adapter auto detection.
main:3904: FATAL: ***** NO USEABLE TERRCABLE_ATSC CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.


lsusb is mis-identifying my card.

> Bus 001 Device 002: ID 2040:6513 Hauppauge WinTV HVR-980

I have a HVR 950 ??

---

### Post by deadflowr on 2016-07-16
No it's properly identified:
see: [https://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950]("https://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950")

As far as fixing mythtv, well it's probably easier to reinstall mythtv.
But I would only reinstall if mythtv was a standalone OS, and not added as an extra to a regular system.
Myth is huge and will eat up a regular system resources, as the backend will always be running.

And learning myth really requires you to go all in.
I feel it's a 3rd times the charm OS, where as if you're lucky, the 3rd time you install it, it might actually function proper; for the first time.
/me rambles


So instead, I'd recommend, me-tv or kaffeine. Both are/have excellent TV players built into them.
Both are in the Ubuntu repositories.

Hope it helps, or makes sense.
Sorry for the rambling on myth...

---

### Post by 4kh3RAm on 2016-07-16
MeTV  could not find any channels. :-(

I will try kaffeine next.

No available device from Kaffeine. :confused:

Tuner card may be un-usable.

---

### Post by deadflowr on 2016-07-16
The link I posted earlier has a make it work section, though it seems that card only has support for ATSC and not QAM, for what it's worth.
Looking at it from this page:
[https://www.mythtv.org/wiki/Digital_Tuner_Cards]("https://www.mythtv.org/wiki/Digital_Tuner_Cards")

ATSC would be for broadcast/antennae  
QAM for cable.

---

### Post by 4kh3RAm on 2016-07-16
Yes, all I use is over the air channels.

My regular TV gets over 50 channels, many of which are high def.

No cable or dish.

> **deadflowr said:**
> The link I posted earlier has a make it work section, though it seems that card only has support for ATSC and not QAM, for what it's worth.
Looking at it from this page:
[https://www.mythtv.org/wiki/Digital_Tuner_Cards](https://www.mythtv.org/wiki/Digital_Tuner_Cards)

ATSC would be for broadcast/antennae  
QAM for cable.

I tried the make it work section.

Got as far as getting the .sys file.

Could not get any further.

There is no such directory. (linux/Documentation/video4linux)

run the extract_xc3028.pl script found in : 

 ./extract_xc3028.pl
copy the generated file so it can be picked up by the Linux kernel: 
 cp xc3028-v27.fw /lib/firmware

> **deadflowr said:**
> The link I posted earlier has a make it work section, though it seems that card only has support for ATSC and not QAM, for what it's worth.
Looking at it from this page:
[https://www.mythtv.org/wiki/Digital_Tuner_Cards](https://www.mythtv.org/wiki/Digital_Tuner_Cards)

ATSC would be for broadcast/antennae  
QAM for cable.

SOLVED

Thanks a lot deadflowr. :-)

I got the card receiving TV channels.

MeTV is picking up about 20 channels out of about 60 available.

Looking to get a better antenna than the 16 inch one I have now.

It's just a simple antenna you would have on a radio.

---

