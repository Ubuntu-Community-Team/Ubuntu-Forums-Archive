---
title: "Printer help Samsung scx-1220a"
date: 2005-04-07
forum: Hardware &amp; Laptops
---

### Post by siphon232 on 2005-04-07
I am having problems printing from my samsung scx-1220a. Ok so I have googled around and read a few docs nothing helped so far. I may be doomed since this is a multifunction printer. OK so there is also another Huge catch this is a Korean printer only made and sold in Korea. So I cant find any linux help docs in English or Korean  for that matter. Its an inkjet using USB. Ubuntu detects it fine and it shows up in the print manager ..installs as a SI-630A. When I try to print test page or anything else the que is sent but the printer never moves and there is no error that I can detect. Even /var/log/cups/errors shows nothing. Any help or insight would be greatly appreciated.

---

### Post by jobezone on 2005-04-08
I have an hp printer, so this may be totally unrelated to your problem, but since I was having an exact problem, it went away when I executed:

sudo ptal-init setup

and answered the questions. My problem, i think, was that only after launching this setup did a necessary kernel module be loaded into memory.

---

### Post by siphon232 on 2005-04-08
Thanks for the suggestion.. I checked in to it but that is an HP specific driver .. I tried it any just to be 100% sure but .. it just said no HP printer detected so I am still out of luck ... right now I discovered I can work around the problem using vmware with xp on it to print that way ... but it kind of sucks to have to go all the way into vmware and boot up just to print something...

---

### Post by bugmenot on 2006-02-22
I've printer SCX-1220A but not driver for Win98/XP.
Thank any help!

---

