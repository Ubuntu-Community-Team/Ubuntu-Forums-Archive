---
title: "Installed - ran - now broken?"
date: 2005-12-09
forum: Installation &amp; Upgrades
---

### Post by Phreezzz on 2005-12-09
Hi community
this is a first post, and I have done a quick search in case the answer is lying in the archives somewhere, but so far, not found
Installed 5.10 on my wifes laptop for her, she was tired of XP!
Great first three days, then after an accidental shutdown due to power loss (she thought it was plugged in!) it now wont start
Fires up to X login, enter username and password but then displayes message that session lasted less than 10 seconds blah blah blah
Viewing /.xsession-errors  highlights are
/etc/gdm/Xsession: Beginning sessions stgartup
_IcetransTransNoListen: unable to find transport tcp
followed by about ten more lines of errors ending with
unable to read ICE authority file:  /home/cindy/.ICEauthority

I have no idea how to fix this problem, surely not another install?

Thanks in advance guys!
Phil

---

### Post by inhetep on 2005-12-09
Check this out

[http://ubuntuforums.org/showthread.php?t=98288&highlight=iceauthority](http://ubuntuforums.org/showthread.php?t=98288&highlight=iceauthority)

Hope this helps.

Alternative

```
$ sudo chown -R <username>:<group> /home/username>
```
eg
```
$ sudo chown -R cindy:cindy /home/cindy
```

---

