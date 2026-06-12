---
title: "How to configure Linux machine as a time server?"
date: 2008-11-02
forum: General Help
---

### Post by Krupski on 2008-11-02
Hi all,

I'm running 8.10 Server 64 bit on a home file server. It's running the NTPD time daemon and it's working just fine (in that it synchronizes it's own time to NTP).

However, I have been unable to configure the "/etc/ntp.conf" file to make the server provide it's time to Windows clients on my local intranet.

I've Googled and tried all the examples... nothing seems to work. I edit the ntp.conf file, restart the NTPD daemon and test it - nothing is working.

My home intranet is using the 192.168.0.0 subnet... the router is 192.168.0.1 and the other computers and printers are 192.168.0.10 and up.

Can anyone help me out here? (and please, don't tell me "man ntpd"). I'm way beyond that point... and at my wits end.

It should not be so difficult... what am I doing wrong?

Thanks in advance!

-- Roger

---

### Post by jona7han on 2008-11-02
I use 8.04 server to sync my XP clients and did no configuration change to the ntp.conf file other than adding the time servers. I'm guessing your not blocking port UDP 123 on XP? This might help you, [Nettime]("http://nettime.sourceforge.net/") is a simple WIndows GUI tool for syncing time, it's designed for Win 2000 but works on XP, it might help give you some clues as to why it's not working.

---

### Post by Krupski on 2008-11-02
> **jona7han said:**
> I use 8.04 server to sync my XP clients and did no configuration change to the ntp.conf file other than adding the time servers. I'm guessing your not blocking port UDP 123 on XP? This might help you, [Nettime]("http://nettime.sourceforge.net/") is a simple WIndows GUI tool for syncing time, it's designed for Win 2000 but works on XP, it might help give you some clues as to why it's not working.

Well... the way I tested it was with 4NT (a 32 bit command processor for NT/2K/XP).

It's got a "time" command which will display or set time to an NTP server.

If I do "time /s real.ntp.server" it works fine.

If I do "time /s my.local.machine", it fails.

(Obviously the server names are descriptive and not *actually* what I typed).

I've tried a few other time clients... same thing - they work with NTP servers, they fail with my server.

I'm sure my problem is just an improperly configured "ntp.conf" file... but I've tried everything and nothing works so far. :(

-- Roger

---

