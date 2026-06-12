---
title: "Magicolour 2430dl printing problem"
date: 2006-01-11
forum: Hardware &amp; Laptops
---

### Post by rgilham on 2006-01-11
Hi there,

I recently purchased a magicolor 2430dl and installed it for network printing. The problem that I am experiencing with breezy is that the first print job prints correctly but after this the printer stops with a file sent to printer waiting to finish followed by a broken pipe error. Restarting cups does not seem to fix the problem. Erasing the /var/spool/cups files restarting seems to help. I have tried enabling logging on cups but that does not shead any light on the problem.

Any suggestions
Robin

I have found that the problem occurs when printing from gimp, it seems that a process that the cups subsystem goes into a loop and crashes, blocking the queue. The problem occurs with Debian 3.1 and Suse 9.1 so it might be a printer problem can someone please try print an image b/w or colour from gimp to this printer and report there success or problems. I have logged this problem it Minolta who are investigating. Will continue to find the course myself.

Robin

---

