---
title: "t430 wifi problems"
date: 2012-09-17
forum: Hardware
---

### Post by alecbenzer on 2012-09-17
I just got a new thinkpad t430 and I'm having some wifi issues. I'm able to connect (in both windows and ubuntu) to mine and other people's personal wifi networks. In windows I'm able to connect to public wifi networks, but not in Ubuntu (I can usually temporarily get a connection but in a couple of minutes the connection will stop working).

How should I go about debugging this?

edit: If it helps, my lspci: [http://paste.ubuntu.com/1204994/](http://paste.ubuntu.com/1204994/) and my lsmod: [http://paste.ubuntu.com/1204993/](http://paste.ubuntu.com/1204993/)

---

### Post by alecbenzer on 2012-09-18
bump -- anyone have any ideas? It's been almost 2 weeks since I've gotten my t430 and I'm still not really able to use ubuntu on it...

---

### Post by afulldeck on 2012-09-18
> **alecbenzer said:**
> I just got a new thinkpad t430 and I'm having some wifi issues. I'm able to connect (in both windows and ubuntu) to mine and other people's personal wifi networks. In windows I'm able to connect to public wifi networks, but not in Ubuntu (I can usually temporarily get a connection but in a couple of minutes the connection will stop working).


I've been using ubuntu on a t430 for a while now and I'm not seeing the  same problem you are. Meaning, I connect to public or private it all  seems the same to me. And it should be. So sorry for the silly question,  but are you putting in the correct public password? Are you running on the 2G or 5G layer?

I should add, which wireless card did you order and have you updated to the latest drivers?

---

### Post by alecbenzer on 2012-09-18
Yeah I'd been hoping that going with lenovo I'd be avoiding the normal support issues I have with Ubuntu :/

I'm able to briefly connect to the wifi networks and access the internet but shortly after it disconnects (used to last maybe ~15mins, lately it seems even less, like <5) So yes, I'm putting in the correct password/using the right security/etc.

> Are you running on the 2G or 5G layer?

Not sure what this means :/

edit:

> I should add, which wireless card did you order and have you updated to the latest drivers?

Linked to my lspci and my lsmod above. I didn't specifically order any particular card but according to lspci it's a Realtek RTL8188CE. I've tried installing the manufacturer drivers and it seemed to be successful but I'm not sure if it actually worked or not.

---

### Post by afulldeck on 2012-09-18
Sorry for being obtuse. I was trying to understand if you where using the 2Ghz band or the newish 5Ghz band. However, your Realtek only uses the 2Ghz band and not the 5. Incidently, your problem also exists in windows see : 
[http://www.edugeek.net/forums/windows/72764-realtek-rtl8188ce-problems.html](http://www.edugeek.net/forums/windows/72764-realtek-rtl8188ce-problems.html)

That said, have you tried the solution explained here? 

[http://askubuntu.com/questions/95360/how-to-get-a-stable-wlan-connection-with-a-lenovo-x121e](http://askubuntu.com/questions/95360/how-to-get-a-stable-wlan-connection-with-a-lenovo-x121e)

---

### Post by alecbenzer on 2012-09-18
Interesting, I'm not experiencing this problem at all in windows.

Anyway, I'll try the solution from the AskUbuntu thread.

---

### Post by alecbenzer on 2012-09-19
Tried the solution (re-compiling the kernel driver). At first I thought it had helped but now I'm back to experiencing the same problems again...

---

### Post by alecbenzer on 2012-09-21
Bump -- anyone have any idea how to fix this? I've tried installing's Realtek drivers, compiling the linux drivers, nothing seems to help.

---

### Post by alecbenzer on 2012-09-27
Bump -- it's been 3 weeks since I've gotten this thing and I still can't get usable wifi in ubuntu :(

---

### Post by alecbenzer on 2012-10-01
Bump -- no wifi for almost a month :(

---

### Post by kucerovj on 2012-10-07
I am using thinkpad L430, which is pretty similar and had the same problems on linux 3.4 and 3.5, where I moved trying to get the trackpoint working. It didn't work at all, so I moved back to 3.2.0, where my wifi is fine. Which kernel are You using (command "uname -a"), which version of Ubuntu? And have you had any problems with your trackpoint?

---

### Post by alecbenzer on 2012-10-17
No problems with my trackpoint. I'm in the latest ubuntu (12.04), with I think a 3.4 kernel (not in ubuntu now so I can't check).

---

### Post by alecbenzer on 2012-10-18
Checked -- I was wrong, I'm already on a 3.2 kernel

```
~% uname -a
Linux alec-thinkpad 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

---

