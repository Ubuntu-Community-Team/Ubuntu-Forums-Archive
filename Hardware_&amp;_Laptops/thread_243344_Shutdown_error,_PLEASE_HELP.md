---
title: "Shutdown error, PLEASE HELP"
date: 2006-08-24
forum: Hardware &amp; Laptops
---

### Post by chris86wm on 2006-08-24
I have been using Ubuntu on my laptop (inspiron 6000) for about a year now without problems. I recently installed Dapper and everything worked well out of the box. Then after about a month I started getting this error at shutdown.

**unregister_netdevice: waiting for eth1 to become free. Usage count = 1**

The error continues to scroll and I have to turn the laptop off with the power button. I uninstalled Ubuntu and installed Xubuntu. After a months use, the same error.

**unregister_netdevice: waiting for eth0 to become free. Usage count = 1**

eth1 is my wireless card (ipw2200) which is currently still working fine until shutdown. Someone PLEASE help me ](*,)

---

### Post by chris86wm on 2006-08-25
bump, man is this problem annoying :-?

---

### Post by chris86wm on 2006-08-27
I am thinking this may have something to do with the kernel?
Any help would be GREATLY appreciated

---

### Post by chris86wm on 2006-08-28
Please dont make me bump this again [-o<

---

### Post by alexwalkey on 2006-08-29
Getting the exact same thing, been looking everywhere for a solution. Just suddenly started happening to me yesterday.

Was great actually, I closed my laptop as it was shutting down (assuming it would go smoothly - as it always has) and ending up baking it in it's neoprene cover cos it couldn't shutdown.

Anyone out there know what's going on?

---

### Post by alexwalkey on 2006-08-29
Ok sorted my prob out.:KS 

[http://ubuntuforums.org/showthread.php?t=213598&highlight=%22waiting+eth1%22](http://ubuntuforums.org/showthread.php?t=213598&highlight=%22waiting+eth1%22)

It's a kernel problem, you need to go back to a previous version.

Just search for "linux-image" in synaptic package manager and choose an earlier one or, better, the exact one the guy/girl (chrismyers) mentions in the above post - that worked for me.

---

### Post by chris86wm on 2006-08-29
giving it a try

edit: seems to work. THANK YOU so much for helping me

---

### Post by chris86wm on 2006-08-31
Nope, after using it for a bit. That didnt work. I have tried kernel 2.6.15-26-386 & kernel 2.6.15-23-386. I tried re-installing before and that didnt work. This is becoming really annoying, and I am completely out of ideas on what to do about this.

---

