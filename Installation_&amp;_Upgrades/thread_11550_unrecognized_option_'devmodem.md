---
title: "unrecognized option '/dev/modem"
date: 2005-01-17
forum: Installation &amp; Upgrades
---

### Post by felixdzerzhinsky on 2005-01-17
When I run pppoeconf I get a working pppoe connection. After each reboot I get this error message:

tony@Perez ~ $ sudo mii-tool
Password:
eth0: negotiated 100baseTx-HD, link ok
tony@Perez ~ $ sudo pon
/usr/sbin/pppd: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem'



 I then have to run pppoeconf again to get the net running.

I should be able to start an internet connection with the command **pon** .


Is there somewhere I can put **pon**  so the connection starts at boot time.

Thanks

---

### Post by felixdzerzhinsky on 2005-01-21
I am still having trouble with this.

---

### Post by mrgardon on 2005-01-22
I'm getting the same message "unrecognized option, /dev/modem, but not from the terminal.  I haven't tried to access my modem from the terminal but will now since I see how you have done it and let you know if I have the same problems or find an answer.  Hopefully the latter.

---

### Post by felixdzerzhinsky on 2005-01-24
I am still stuck on this one. My ISP uses pptp. So I don't know if I can help you.

I've tried putting it in /etc/init.d/bootmisc.sh but that stops the computer for booting altogether.

I also tried using gksudo but that didn't work either.

Fortunately my girlfreind is smart enough to cope with cutting and pasting a script into a shell and typing in a password. 

Still there should be a way of making the net come up at boot time. :-k 

I prefer to make things invisible to users if possible.

---

