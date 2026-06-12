---
title: "thunderburd running but not responding"
date: 2008-08-02
forum: General Help
---

### Post by Silvernail on 2008-08-02
I have version 8.4 installed on my Presario lap top. All of the sudden, 
when I try to launch 'thunderbird' version 2.?, I get a message that "thunderbird' is already running but not responding.

It suggest I either kill the process or shut down my computer. I have done both to the extend of letting my system stay down several hours.

Boot up. Same message.

Anyone any thoughts?

TIA
Dave

---

### Post by p_quarles on 2008-08-02
Moved to General Help.

There is a lock file in the Thunderbird configuration directory causing this behavior. I can't tell you the exact file path and name, as I don't use Thunderbird any longer, but someone should be able to tell you if you can't find it yourself.

---

### Post by Silvernail on 2008-08-04
Not sure what I did but thank you for the trail to follow.But now the same sort of porblem pops up.

I try to send message: get error: "can not connect to SMTP server"

After the responce above and some digging I find this LOCK.
```
lrwxrwxrwx  1 root root      20 2008-08-04 14:00 lock -> 192.168.1.100:+28226

```

in
> SilverNail:~/.thunderbird/3ti0epll.default#

I know the 192.168.1.100 is my router and
is +28226 a port?

The timeing was interesting. It is in the future.

Would a trip to "Schields Up" tell me more?

TIA
Dave

---

### Post by wirelessmonkey on 2008-08-04
On my machine, I had to delete this file...   /home/me/.mozilla-thunderbird/blahblah.default/.parentlock, which fixed the issue.  Yours may be in .thunderbird instead of .mozilla-thunderbird

---

