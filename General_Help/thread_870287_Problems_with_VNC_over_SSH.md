---
title: "Problems with VNC over SSH"
date: 2008-07-25
forum: General Help
---

### Post by lsutiger on 2008-07-25
Hi all!
I am trying to use VNC + SSH to remote into my computer at home. I have SSH listening to port 5970. I left VNC on the default (5900). I have the ports forwarded on my router correctly.

I am trying to use the -via option. EX:
 vncviewer -via [email]linux-1501@antec.homelinux.net[/email] linux-1501:1

linux-1501 is my computer at home. antec.homelinux.net is the FQDN. The port forwarding is working correctly as I can ssh into the computer.

My question is, how, in the string given to the -via option do I set the port number?
From the man page:
>  The environment variable VNC_VIA_CMD can override the default tunnel command of
              /usr/bin/ssh -f -L "$L":"$H":"$R" "$G" sleep 20.  The tunnel command is executed with the environment variables L, H, R, and  G  taken  the
              values of the local port number, the remote host, the port number on the remote host, and the gateway machine respectively.


I am a little lost on this part.
Thanx for any instruction.

---

### Post by Darkade on 2008-07-25
Check this site, It helped me a lot! :D
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by Darkade on 2008-07-25
Check this site, It helped me a lot! :D
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

**EDIT:Sorry I don't know what happen, it said I couldn't post, and to try again, i tried again and I had already posted :S**

---

### Post by lsutiger on 2008-07-25
Thanx for the response! 

Thats where I started and went [to here]("https://help.ubuntu.com/community/VNCOverSSH") from that site. Neither one of them explained how to set the port when using the via option.

---

