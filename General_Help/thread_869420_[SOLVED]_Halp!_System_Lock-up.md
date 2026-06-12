---
title: "[SOLVED] Halp! System Lock-up"
date: 2008-07-24
forum: General Help
---

### Post by slugicide on 2008-07-24
Hey, I need some help, for sure.  My system (Dell E1505, Hardy) has locked up 5 times in the last couple of days.  I can't even do that REISUB trick I'm supposed to be able to.  At the same time, sound has quit playing in Flash.  I don't know if these are related, or if they are each/both related to the kernel update, although both problems started around then.  What do I need to do to help you help me?  Thanks!!

---

### Post by iaculallad on 2008-07-24
> **slugicide said:**
> Hey, I need some help, for sure.  My system (Dell E1505, Hardy) has locked up 5 times in the last couple of days.  I can't even do that REISUB trick I'm supposed to be able to.  At the same time, sound has quit playing in Flash.  I don't know if these are related, or if they are each/both related to the kernel update, although both problems started around then.  What do I need to do to help you help me?  Thanks!!

For the REISUB trick that did not work, had you tried using the Ctrl+Alt+Backspace combo keys?

For the Flash sound: Try installing the audio support wrapper for non-free flash plugin.

```
sudo apt-get install libflashsupport
```

If that does not work, try installing your linux-generic file:

```
sudo aptitude install linux-generic
```

---

### Post by slugicide on 2008-07-24
libflashsupport fixed sound in flash.  Thanks.

As to the locking up: yes, I tried ctrl+alt+bksp.  First thing I did.

---

### Post by slugicide on 2008-07-24
Make that 6 times.

edit: 7 and 8.  The last time it locked up as soon as I restarted.  I'm in the old kernel now, in case that will help.  Any advice?

---

### Post by slugicide on 2008-07-25
Bump, 'cause I really need help.

---

### Post by avtolle on 2008-07-25
The kernel update has been the subject of many threads over the past two days. There is a bug, which has been reported. For now, continue to boot into the older kernel. 

BTW, that update came from the proposed repository, the intent of which is to provide packages for testing. Obviously, these packages can have bugs; so if you don't want to be involved in testing, disable the proposed repository, which, for good reason, is disabled by default.

---

### Post by slugicide on 2008-07-25
> **avtolle said:**
> The kernel update has been the subject of many threads over the past two days. There is a bug, which has been reported. For now, continue to boot into the older kernel. 

BTW, that update came from the proposed repository, the intent of which is to provide packages for testing. Obviously, these packages can have bugs; so if you don't want to be involved in testing, disable the proposed repository, which, for good reason, is disabled by default.
Oh, thanks!  
This is the first time I've added "proposed."  I keep forgetting I've done so and am testing.  I'll look at those threads.

---

