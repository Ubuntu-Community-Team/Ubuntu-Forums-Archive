---
title: "Getting the treo to sync via bluetooth"
date: 2007-01-27
forum: Hardware &amp; Laptops
---

### Post by stephentyler20 on 2007-01-27
So after tinkering around with various settings on linux/treo, I finally was able to get the treo 650 to add the laptop to the trusted devices list. However, that's as far as it goes. After reading the various "How-to's" out there, I still can't get the treo to synchronize with the computer, and transfer files. All I'm looking to do is get my datebook sync'd up with the PC right now, more advanced stuff can come later. 

The farthest I can get is an error that says the Modem is not working properly. Any advice?

---

### Post by stephentyler20 on 2007-01-27
Nevermind, found another Howto and followed those instructions, now seems to work fine. Finally!

---

### Post by firstc624 on 2007-01-27
share what  you found please.  i have been tryign to get my treo 700w to sync and it sucks

---

### Post by gtratter on 2007-02-12
> **stephentyler20 said:**
> Never mind, found another Howto and followed those instructions, now seems to work fine. Finally!

I am unable to sync with any regularity via USB/Cradle (using either gpilot or jpilot), and am not able to sync via bluetooth at all. I have a Treo 650p.

I would be very interested in learning how you are able to sync. I searched this forum and followed all instructions I could find - to no avail. Being able to sync calendars and to-do's is vital to me and sadly, this is the only reason Windows still sits on a partition.

---

### Post by Elijah on 2007-02-22
try this howto I made: (bluetooth only)
[http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html](http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html)

---

### Post by gtratter on 2007-02-22
Thanks - I will give it a try on Friday and report back

---

### Post by wormeyman on 2007-04-21
> **Elijah said:**
> try this howto I made: (bluetooth only)
[http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html](http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html)
I tried your guide but my pc doesn't show up when i try to add devices but when i type hcitool scan i can see my 650 any advice from anyone would be much appreciated

---

### Post by Rescue9 on 2007-05-23
:-( I tried The howto listed above, but every time I get to the the network section and try to connect I get the error 0x0305. Any clues?

---

### Post by Rescue9 on 2007-05-24
WOOOHOOOO!!!!! I got it to work and it syncs with Evolution via Bluetooth!!!!

The problem was the line

```
sudo /etc/init.d/bluetooth restart
```

For some reason restart[ing] the connection didn't work. HOWEVER< if you stop then start the connection after a few seconds it works like a charm!

Keep following the instructions as provided.

---

### Post by macgar32 on 2007-06-10
> **Elijah said:**
> try this howto I made: (bluetooth only)
[http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html](http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html)

I Love you man:p

---

