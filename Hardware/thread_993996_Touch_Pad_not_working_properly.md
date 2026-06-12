---
title: "Touch Pad not working properly"
date: 2008-11-26
forum: Hardware
---

### Post by tmaple on 2008-11-26
I have just installed 8.10 on my Dell D830 Laptop and all is working well except the touch pad. It does work but it is very slow to respond. I moved the speed adjustment up in the System --> preferences --> mouse settings and that has helped. If I have a mouse plugged in it work flawlessly. I have used openSuse and CentOS before on this box trying to decide which distro to use and the touch pad work as it should. Any help would be appreciated. ](*,)

---

### Post by rHBa on 2009-03-23
I had similar problems running Intrepid on a Dell Latitude 110L.

[[COLOR="Blue"]This thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=365683") was very useful for checking that your settings aren't out of whack but what fixed it for me was, using synclient, setting GrabEventDevice to 0/false like this:

```

me@comp:~$ synclient GrabEventDevice=0
me@comp:~$
```
Hope this helps...

---

