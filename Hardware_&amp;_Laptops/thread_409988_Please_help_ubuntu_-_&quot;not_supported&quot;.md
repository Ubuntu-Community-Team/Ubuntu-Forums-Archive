---
title: "Please help: ubuntu - &quot;not supported&quot;"
date: 2007-04-15
forum: Hardware &amp; Laptops
---

### Post by enchesss on 2007-04-15
AAAAAAAAAAAHHHHHHHHHHHHHHHH!!!!!!!!!!!!!!!!!!!!!!


Not exactly sure why but when unstalling 6.10 ubuntu and kubuntu i get black screen with yellow text "not supported".

Frustrating experience becuase used to love using kubuntu dapper on amd64. now there seem to be no ubuntu versions that work with my new system. NOT GOOD!

Have this system:
AMD2 athlon X2 cpu
Asus m2v mainboard
nvidia 6200 turbocache graphics
1gb
250gb

Attempted these isos:
kubuntu 6.06 dapper x386 (works on sempron) - stalls when trying to detect ethernet.
kubuntu 6.10 cd version - blue screen "NOT SUPPORTED"
kubuntu 6.10 dapper dvd alternate - stalls on boot option
kubuntu 6.10 dapper dvd german alternate - could not understand
ubuntu 6.10 live version - "NOT SUPPORTED"


I would love to participate and develop a patch for these installs but need help.


Cheers


SUPPORT AUSTRALAIN WORKING FAMILIES AND GO TO ROCKING FOR YOUR RIGHTS AT SYDNEY HYDE PARK 11:00AM SUNDAY 28TH APRIL 2007.
HEAPS OF AWSOME BANDS - MIDNIGHT OIL AND SOMETHING FOR KATE $5 ONLY.
JOHN HOWARD NEEDS TO CHANGE REPRESSIVE POLICIES ON ORDINARY AUSSIES!!!!

---

### Post by kidders on 2007-04-16
Hi there,

I have a similar system that works well. :confused: I wonder what the cause of your troubles is. Unfortunately, your post is a low on detail, so it's hard to know what might be going on.

If none of the CD images you tried boots successfully, perhaps you are having kernel troubles ... which I have started having recently. If you could post system logs, boot messages, etc. it would be a great help.

---

### Post by enchesss on 2007-04-17
sorry there are no system logs becuase non of these os's actually boot. The installations all fail. Any message such as "not supported" is out of the ordinary. Usually there is just a blank black screen when installing.

---

### Post by kidders on 2007-04-17
Yeah... If you can't *see* anything, there's no way to report any messages that might be popping up! ](*,)

I wonder if your problems have anything to do with your graphics card. On my system, for instance, if I don't disable the boot-time splash image, nothing happens. (It took me some time to figure out what the cause of that particular problem was ... it has to do with a minor usplash design limitation). The issue only affects me if I use a DVI cable and a 16:9 monitor. Is it possible that you are encountering the same problem?

I've only ever installed a Ubuntu desktop system two or three times, so I can't remember much of the detail of how it works ... does the CD's bootloader let you modify boot-time kernel parameters? What about an alternate install CD?

---

### Post by snoop on 2007-04-17
I am not sure if you have tried this or not, but have you checked the checksum of the iso's?

If the checksum is fine, try what kidders suggested and try the alternate cd, it might work out.

---

