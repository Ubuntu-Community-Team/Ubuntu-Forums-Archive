---
title: "Logging user activity"
date: 2005-11-20
forum: General Help
---

### Post by vDave on 2005-11-20
Hello,

I have recently setup an Ubuntu 5.10 box, and have added user accounts for some members of my family.

Specifically, I have given them access to some shared files - but I would like to record which files they access and at what times.

They login remotely to my machine using scp/ssh via WinSCP from their home WinXP machine.

Using this program, they are able to download the files that I have given them access to. 

I would like to be able to determine:
1) Which of them is logged in at the moment (i know that 'ps ax | grep sshd' will tell me this, but it would be nice to have it logged)
2) Which files are currently being, or have recently been, accessed.
3) What bandwidth is being consumed by a given user.

Can anyone help a linux newbie here?  
I had mrtg setup on my previous linux distro, but that only showed per-IP address bandwidth usage (at least, as far as I could tell) and not per-user or per-session usage.

Also, I would like:
4) A convenient way to limit or reduce on-the-fly the bandwidth allocated to a given session, so I can use it locally, if required.

Thanks in advance,

    -dave-

---

### Post by vDave on 2005-11-21
Noone has an answer?

---

### Post by feign on 2005-11-21
vDave I would be interested in seeing what others say, because some of your questions are of interest to me.

*4) A convenient way to limit or reduce on-the-fly the bandwidth allocated to a given session, so I can use it locally, if required.*

I am not certain that this is the solution you are looking for but I have a Linksys WRT54G router.  It comes with QoS feature that lets you limit bandwidth for certain addresses or set priorities for certain ports.

---

### Post by ranf on 2005-11-22
[QUOTE=vDave]
They login remotely to my machine using scp/ssh via WinSCP from their home WinXP machine.

I would like to be able to determine:
1) Which of them is logged in at the moment (i know that 'ps ax | grep sshd' will tell me this, but it would be nice to have it logged)
[/QUOTE]
Type `w' or `who' to see who currently is logged in.
`last' is also nice.

---

