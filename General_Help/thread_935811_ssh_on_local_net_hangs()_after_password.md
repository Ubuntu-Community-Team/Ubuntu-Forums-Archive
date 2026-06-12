---
title: "ssh on local net hangs(?) after password"
date: 2008-10-02
forum: General Help
---

### Post by FourBrane on 2008-10-02
I'm running up-to-date Hardy Heron on my desktop and laptop, both connected to my local network. sshd is running on my desktop and ssh is installed on my laptop. I have the same user name on both systems.

From the laptop, if I run ssh 192.168.1.xxx (desktop's ip), I get the password prompt as expected. Bad passwords are bounced back properly with termination after three failures but the correct password produces...no response! The cursor sits there blinking until the desktop decides the session has timed out and I see:
Read from remote host 192.168.1.xxx: Connection timed out
Connection to 192.168.1.xxx closed.

Running ps on the desktop before that happens shows that the desktop has me logged in:

USER 	   STAT START   TIME	COMMAND
root	   Ss 	02:04   0:00 	sshd: fourbrain [priv] 
fourbrain  S    02:04   0:00 	sshd: fourbrain

If I run "ssh localhost" on the desktop, I can log in and I get the normal answering prompt, so sshd is working. Port 22 is open (of course, or the password traffic wouldn't happen).

Anyone have any ideas about what is causing me not to see the normal prompt?

---

