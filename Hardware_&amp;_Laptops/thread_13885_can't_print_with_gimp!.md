---
title: "can't print with gimp?!"
date: 2005-02-03
forum: Hardware &amp; Laptops
---

### Post by ming0 on 2005-02-03
I can print w/ open office and all of my other programs, but not gimp.

When I press print, my printer (a samsung ml-1430 laser printer) warms up like it usually does, and then nothing happens.

I get the following message at the bottom of /var/log/cups/error_log:
```
I [03/Feb/2005:08:16:55 -0500] Adding start banner page "none" to job 44.
I [03/Feb/2005:08:16:55 -0500] Adding end banner page "none" to job 44.
I [03/Feb/2005:08:16:55 -0500] Job 44 queued on 'ML-1430' by 'dean'.
I [03/Feb/2005:08:16:55 -0500] Started backend /usr/lib/cups/backend/ipp (PID 6832) for job 44.

```I just printed a test page to make sure the paper wasn't jammed, and it worked fine.

I've got all the foomatic stuff loaded, and all my cupsys stuff, plus the gimp-print packages.

I'm not really sure what to do??

(PS-In gimp, the printer is set as 'postscript level 2' printer, and if I try to find a driver from the gimp printer dialogue, there aren't any samsung options)

Thanks

---

### Post by ming0 on 2005-02-03
actually, I solved this one...

I just needed to remove the following part of the print command in the printer setup dialogue from inside gimp (just press print and then find 'printer setup')

Remove:
-oraw

and that's it!

---

