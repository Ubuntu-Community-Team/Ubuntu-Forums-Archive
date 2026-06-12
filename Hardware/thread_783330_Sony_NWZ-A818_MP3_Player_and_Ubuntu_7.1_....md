---
title: "Sony NWZ-A818 MP3 Player and Ubuntu 7.1 ..."
date: 2008-05-05
forum: Hardware
---

### Post by drewb93 on 2008-05-05
Hey everyone,

I'm planning on purchasing a new MP3 player, Sony's NWZ-A818. I've searched around about how it and Ubuntu 7.1 works together. I've read I can just drag and drop files into, no problemo, done. However, this is a substantial investment on my part, and I just wanted to be sure I'll be able to put music on it with all the track information correct and whatnot. So, if there's anyone here who has the NWZ-A818 (or something similar to it), and can tell me if it works out well, please let me know! Thanks in advance!

---

### Post by lolobu on 2008-06-14
I've got one and it works perfectly with Gutsy (7.10). It seems that there is a bug in HAL with Hardy 8.04 at the moment (it won't mount automaticaly) but I supposed that it should be fixed shortly so stick with Gutsy for the time being.
You can transfer your files out of the box with nautilus. However if you want it to be recognized by Quodlibet, Rhythmbix and the likes, just do this :
```

cd
wget http://www.delagoutte.net/sony-nwz-a818.diff
sudo -s
cd /usr/share/hal/fdi/information/10freedesktop
patch -p0 < ~/sony-nwz-a818.diff

```

And the last thing is that if you're using EasyTag to tags your mp3, you should configure it to use ID3v2.3 (and not ID3v2.4 as it is by default) since the Sony NWZ doesn't support v2.4

---

### Post by fuzzmo on 2008-06-17
Great player - best I have ever had.  However it doesn't mount properly on Hardy (as the above poster said).  Not a problem though - I can transfer music via Rythmbox easily without modification.

I hope they solve the HAL problem though - I miss dragging and dropping :(

---

### Post by Interpreter on 2008-09-16
> **fuzzmo said:**
> Great player - best I have ever had.  However it doesn't mount properly on Hardy (as the above poster said).  Not a problem though - I can transfer music via Rythmbox easily without modification.

I hope they solve the HAL problem though - I miss dragging and dropping :(

Any updates on this?

---

### Post by lolobu on 2008-09-16
Nothing new on hardy but it does work again with the new kernel in Intrepid Ibex (currently alpha 5, released end of October)

---

### Post by Interpreter on 2008-09-16
> **lolobu said:**
> Nothing new on hardy but it does work again with the new kernel in Intrepid Ibex (currently alpha 5, released end of October)

Well if that is the case: thank you for the fast and down to the point reply, I appreciate it, im somewaht torn between using my sisters laptop for the time being or trying the amarok/rhythmbox combo... ))

Anyway thanks!

---

### Post by regalrecaller on 2008-11-29
> **fuzzmo said:**
> Great player - best I have ever had.  However it doesn't mount properly on Hardy (as the above poster said).  Not a problem though - I can transfer music via Rythmbox easily without modification.

I hope they solve the HAL problem though - I miss dragging and dropping :(

any updates on this yet?

---

### Post by Interpreter on 2008-12-01
It works with 8.10 as promised.

---

