---
title: "Latitude E6400 not cleanly resuming after standby"
date: 2013-07-06
forum: Hardware
---

### Post by socken23 on 2013-07-06
Hi all

I installed Kubuntu 13.04 (fresh install), since then my notebook won't cleanly resume after standby. This used to work on 12.10 so I guess it's a configuration issue.

When I resume from standby, KDE offers me the login window, but I can not type anything in the password box. 
I can then switch to the console by pressing Ctrl+Alt+F2. After killing the X server process, X restarts immediately. I can enter my username / password and it looks like KDE is starting again. However, the splash screen only shows the first three icons and then just halts.
The only option I then have, is a shutdown / restart from the console.

Any idea?

Thanks

---

### Post by gordintoronto on 2013-07-06
Is this from Suspend or Hibernate? Is it from closing the lid, several minutes of inactivity, or manually selecting it?

---

### Post by socken23 on 2013-07-07
> **gordintoronto said:**
> Is this from Suspend or Hibernate? Is it from closing the lid, several minutes of inactivity, or manually selecting it?

This is from suspend. I don't have Hibernate activated. And it's from manually selecting it (Fn + F1 on the Dell Latitude E6400). Same thing happens with closing the lid though.

---

### Post by gordintoronto on 2013-07-07
You might try the Dell forum here.

---

### Post by socken23 on 2013-07-10
> **gordintoronto said:**
> You might try the Dell forum here.

Well, it did work on 12.10. so I thought I have more luck here as it doesn't seem to be a general Dell problem. Maybe someone else experienced the same thing.

---

### Post by Toz on 2013-07-10
Can you post back the contents of your pm-suspend.log file like this (from a terminal window):
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

Also, can you post back the results of this command (also from a terminal):
```
cat /var/log/syslog | grep PM:
```
Maybe there is something in one of these files that can help pinpoint what the issue is.

---

### Post by socken23 on 2013-07-11
Sure I can:

Here is the pm-suspend.log
[http://paste.ubuntu.com/5866117/](http://paste.ubuntu.com/5866117/)

And here the part of syslog
[http://paste.ubuntu.com/5866125/](http://paste.ubuntu.com/5866125/)

Thanks for your time

---

### Post by Toz on 2013-07-11
Unfortunately, there are no errors in those logs.

Are you using any special peripherals (keyboard/mouse) instead of the laptop keypad?

Can you also post back a couple of more files? Post these after a resume attempt when you are at Ctrl+Alt+F2.
```
pastebinit /var/log/Xorg.0.log
sudo pastebinit /var/log/lightdm/lightdm.log
```

---

### Post by socken23 on 2013-07-12
No, nothing special. The only things I have connected are a Logitec Mouse (M705) with one of these universal USB connectors. But the mouse is responding, I can move the cursor around on the login screen after resume. The second thing attached is an external screen, but the same thing happens without the second screen.

Here are the files:
Xorg.0.log:  [http://paste.ubuntu.com/5867230](http://paste.ubuntu.com/5867230)
lightdm.log: [http://paste.ubuntu.com/5867231](http://paste.ubuntu.com/5867231)

---

### Post by Toz on 2013-07-12
There just don't seem to be any error messages that can help us. I do notice that you are using the opensource nouveau drivers. Have you tried enabling the proprietary nvidia driver?

---

### Post by socken23 on 2013-07-12
Thanks again. No, I didn't try that yet, will do this evening and report back.

---

### Post by socken23 on 2013-07-12
> **Toz said:**
> There just don't seem to be any error messages that can help us. I do notice that you are using the opensource nouveau drivers. Have you tried enabling the proprietary nvidia driver?

:guitar: 
Yes yes!! Installing the proprietary drivers solved the problem. Thank you so much for the tip!
Apparently I had these drivers active on 12.10 and didn't switch again after upgrading to 13.04.

---

### Post by Toz on 2013-07-12
Glad to hear. Can you mark this thread Solved following the instructions listed in my signature?
Thanks

---

