---
title: "HPIJS segfaults when printing SVG from Inkscape"
date: 2009-01-18
forum: Hardware
---

### Post by worldgnat on 2009-01-18
I'm trying to print an 8.5"x11" svg image in Inkscape (Ubuntu 8.10, HPIJS v2.8.7) and whenever I do I get a message saying the printing failed, and when I look at the printer in cups (localhost:631) I see: "/usr/lib/cups/filter/foomatic-rip failed". This error by itself is common enough on the internet, and I tried foomatic-cleanupdrivers which didn't work. Then I looked at dmesg and I saw this: 

[ 1175.091105] type=1503 audit(1232323317.272:49): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=7311 profile="/usr/sbin/cupsd"
[ 1176.167333] hpijs[7314]: segfault at 0 ip 0000000000435e47 sp 00007fff014eedb0 error 6 in hpijs[400000+59000]

I've tried exporting to PDF, which gives me a different error:

[ 1136.296630] type=1503 audit(1232323278.477:48): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=7286 profile="/usr/sbin/cupsd"
[ 1137.418490] gs[7286] trap divide error ip:7f780cb389a2 sp:7fff1573a510 error:0 in libgs.so.8.63[7f780c9e7000+4f0000]

The interesting part is that if I export to PNG it prints all the alpha as black, but when I put a white background layer behind it it gives me the same "trap divide error...". 

I'm trying to print pages for a DayRunner calendar, and when I print one of the DayRunner pages on it's own (about 170mmx95mm), it prints fine, but when I print all three together on an 8.5"x11" or even on 10"x7.2" I get the above errors. 

I should also mention that I have never had problems with this printer or computer before, and I've been using it as is for at least 5 months. I haven't made any major changes to my system, and this occurrence does not appear to have happened after any particular update.

Googling gave me nothing, not even bug reports, and I have no idea what to do. Suggestions? 

Cheers,
-Peter

---

