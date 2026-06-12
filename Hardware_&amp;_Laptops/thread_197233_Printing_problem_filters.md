---
title: "Printing problem: filters"
date: 2006-06-15
forum: Hardware &amp; Laptops
---

### Post by Fredo on 2006-06-15
Hello!

For quite a long time, I have a problem with my printer. And since I could find no help in the German forum, I decided to ask a wider audience at ubuntuforums.org.

I have a Lexmark X1150 which normally prints fine with the z600 driver. But some apps have problems. For a long time, all went well, but at a certain point of time somthing must have gone - I have no idea what.

[LIST][*]What works: Printing from GNOME Apps, OpenOffice.org, etc.
[*]What doesn't work: Printing from GtkLP, Scribus, lp(r) on the console.
[*]What happens: The printer symbol appears in the system tray, the job is shown in the queue as "printing", but it disappears after a while without actually printing.
[/LIST]

I had a look into the error log of cups, and it shows the following with a working job:

```
I [15/Jun/2006:19:03:30 +0200] Adding start banner page "none" to job 512.I [15/Jun/2006:19:03:30 +0200] Job 512 queued on "Z600-v1.0-1" by "frederik".
I [15/Jun/2006:19:03:30 +0200] Started filter /usr/lib/cups/filter/pstops (PID 20398) for job 512.
I [15/Jun/2006:19:03:30 +0200] Started filter /usr/lib/cups/filter/pstoraster (PID 20399) for job 512.
I [15/Jun/2006:19:03:30 +0200] Started filter /usr/lib/cups/filter/rastertoz600 (PID 20400) for job 512.
I [15/Jun/2006:19:03:30 +0200] Started backend /usr/lib/cups/backend/z600 (PID 20401) for job 512.
```

With a non-working job, I get the following:

```
I [15/Jun/2006:19:05:39 +0200] Adding start banner page "none" to job 513.I [15/Jun/2006:19:05:39 +0200] Job 513 queued on "Z600-v1.0-1" by "frederik".
I [15/Jun/2006:19:05:39 +0200] Started backend /usr/lib/cups/backend/z600 (PID 20500) for job 513.
```

So the filters are not applied and the printing doesn't start. But I have no idea why or what to do about it... :-( 


If anyone could help me with this, I would be really pleased. Printing without GtkLP is really no fun in some cases...

Kind regards,
Fredo

---

### Post by Fredo on 2006-07-01
No Ideas?

I was quite happy about having figured out where the problem is, but now I need some help to fix it.

Fredo

---

