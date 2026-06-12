---
title: "problems with my burner"
date: 2005-07-15
forum: Hardware &amp; Laptops
---

### Post by daageep on 2005-07-15
Hi.

I'm getting pissed because my burner is not working correctly. I have a toshiba dvd/cdrw combo for my fujitsu s6120 laptop.

I tried to burn an iso image with gnome baker and it would start fixating at ~50%. this happens with different iso files. 

but my friend has successfully burned the same iso file with cdrecord (which I don't know how to use). I found a howto but i can't find my lun numbers, etc. i did a cdrecord -scanbus and I get the following:

"cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver." 

Then I tried using graveman. i *think* it worked burning an iso file that i gnomebaker had troubles with. it burned all the way but graveman quit immediately after fixating. in my gnome-terminal, it said segmentation fault.

even if graveman did do the job, i tried burning just an avi file but it failed at around 60%. 

guys, i don't know if its linux, cdrw progs, or my burner giving me problems. i'd appreciate some help. thank you!

---

