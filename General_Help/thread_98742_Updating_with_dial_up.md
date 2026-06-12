---
title: "Updating with dial up"
date: 2005-12-04
forum: General Help
---

### Post by Jjohn on 2005-12-04
Hello Everyone.
                      I have succeeded in installing breezy onto my old Dell laptop with quite a good result (most things work)  From a terminal I ran "sudo apt-get update" and ended up with 300 updates to install (approx 230mg) because I am on dial up I went slowly through the update gui screen and edited the list to fifty updates, it took a long time.
                     Is there a command line that I can use to tell how many updates to load? My preference is approx 30 then 30 then 30 etc
Just to make things a little more difficult my isp resets the modems every three or so hours.
Regards   John:)

---

### Post by psyguy92 on 2005-12-04
[QUOTE=Jjohn]Hello Everyone.
                      I have succeeded in installing breezy onto my old Dell laptop with quite a good result (most things work)  From a terminal I ran "sudo apt-get update" and ended up with 300 updates to install (approx 230mg) because I am on dial up I went slowly through the update gui screen and edited the list to fifty updates, it took a long time.
                     Is there a command line that I can use to tell how many updates to load? My preference is approx 30 then 30 then 30 etc
Just to make things a little more difficult my isp resets the modems every three or so hours.
Regards   John:)[/QUOTE]

Why not just mark 1/3 of the total downloads each night in synaptic?

230 MB = 235520 KB total update size.
Assuming 3 hours per night...
3 hrs -> 180 min -> 10800 sec. 
Assuming average d/l speed of 7.5 kbps, in one night you download 81000 kb or 79.1 MB
3 overnight download sessions at 3 hrs each, you have 237.3 MB (assuming the stars are in correct alignment etc).

I don't know about all the command line options for apt-get, which is what you asked about.  Just thought this idea might work. :)

---

### Post by Jjohn on 2005-12-04
Yes, That is what I would like to do. Sadly my dialup speeds are only 4.5 kbs. but I could change the numbers to equal 5 sessions if I had a command line.
Regards John

---

