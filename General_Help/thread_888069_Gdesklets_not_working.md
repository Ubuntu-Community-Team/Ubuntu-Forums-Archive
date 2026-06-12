---
title: "Gdesklets not working"
date: 2008-08-12
forum: General Help
---

### Post by sofasurfer on 2008-08-12
I installed gdesklets. Ran it from gui and it freezes up. Ran from terminal and got a message that it was "unable to connect to daemon. Then when I tried again from terminal I got this...


```
 
daryl@daryl-desktop:~$ gdesklets
Starting gdesklets-daemon...
Connected to daemon in 503 milliseconds.

==========================================================[08/12/08-18:42:30]===
=== Unhandled error! Something bad and unexpected happened. ===

[EXC]
in /usr/bin/gdesklets: line 393 <module>
in /usr/bin/gdesklets: line 268 parse_command
in /usr/bin/gdesklets: line 177 __open_profile
in /usr/bin/gdesklets: line 167 __client_daemon
in /usr/lib/gdesklets/main/client.py: line 208 set_remove_command
in /usr/lib/gdesklets/main/client.py: line 38 __send
in /usr/lib/gdesklets/utils/xdr.py: line 75 recv
[EXC]/usr/lib/gdesklets/utils/xdr.py

[---]   70     chunk = ""
[---]   71     while (True):
[---]   72         try:
[---]   73             length = ord(s.recv(1))
[---]   74         except:
[ERR]>  75             raise XDRError
[---]   76 
[---]   77         if (length): chunk += s.recv(length)
[---]   78 
[---]   79         flag = s.recv(1)
[---]   80         if (flag == _CONT): continue
[---]   81 


```

This happened on 2 differant Hardy systems.

Any ideas why?

---

### Post by tuxxy on 2008-08-12
Is there a reason you choose gdesklets or have you not tried screenlets? that should come by default in applications > accessories > screenlets , I prefer these to gdesklets and dont think they have been updated for a while either unlike the screenlets

[http://packages.ubuntu.com/hardy/gnome/screenlets](http://packages.ubuntu.com/hardy/gnome/screenlets)

---

### Post by rainwalker on 2008-08-12
+1 for Screenlets, so much better than Gdesklets

---

### Post by sofasurfer on 2008-08-12
Woops! Now I'm confused. I just heard about either gdesklets or screenlets. Which ever it was (I think gdesklets) I did not know about the other.
My reason for wanting a *lets anything is that I tried cairo-clock and could not get it to stay put in the screen location that I placed it. Odd, since I was successful with it a couple weeks ago. Anyway, I heard that this other thing, gdesk or screenlets had a good looking clock. So I will go try screenlets now.
I'll let you know.

---

### Post by sofasurfer on 2008-08-12
Well, the screenlets clock isn't near as nice as the cairo-clock. Are any one you guys proficiant in fixing cairo-clock problems?

---

### Post by ranjith19 on 2010-11-24
[http://ubuntuforums.org/showthread.php?p=10156439#post10156439](http://ubuntuforums.org/showthread.php?p=10156439#post10156439) has the solution

---

