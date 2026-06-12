---
title: "no outgoing net connection in new place"
date: 2005-08-23
forum: Hardware &amp; Laptops
---

### Post by vinthund on 2005-08-23
hello,

I have just started to use my laptop (hp compaq nx7000) in a new place, ie in a library. I plugged the cable and everything seemed to work fine (www, receiving mail)), however... certain services seem to be unavailable for me. For instance I cannot send mail (evolution, cannot connect to smtp server), I cannot use communicator (gnu-gadu, it just disconnects). Of couriosity I tried amule but it did not work either (connection lost, could re-connect but the arrows on the globe in right lower corner of the screen are yellow and there is no out or in connections). Under Windows I tried the communicator and it worked fine, so it is probaly something with my configuration? But what?

regards,

Marek

---

### Post by s_p_a_r_k_y on 2005-08-23
they are probably blocking certain outgoing ports. I was at a job where they didn't allow port 143 (IMAP) outgoing so I had to SSH tunnel it to my local laptop. Try this.

```
telnet SMTPSERVER 25
```

I get something like this
telnet mail.stefangeorg.net 25
Trying 82.165.238.196...
Connected to u15182239.onlinehome-server.com.
Escape character is '^]'.
220 u15182239.onlinehome-server.com ESMTP

which means I can connect to port 25 outgoing. If your connection seems to hang to a server you know is UP (via webmail or some other method) then they are blocking the ports.

---

### Post by vinthund on 2005-08-24
I got:

```

marek@ubuntu:~$ telnet post.pl 25
Trying 212.85.96.51...
telnet: Unable to connect to remote host: Connection refused

```

Does this mean that the library blocks outgoing connections? Can I do something about so that I could send emails directly from evoluton, not by www interface?



m

---

### Post by JLB on 2005-08-24
looks like it. my place of business does this too. only the ftp/http/https and ssh ports are open. looks like you are SOL. for mail i just ended up using gmail as a workaround when in a place like that taking care to CC myself.

if you need a gmail account, just let me know. I'd be happy to send you an invite.

---

### Post by s_p_a_r_k_y on 2005-08-24
if you have a shell account on the smtp server you could do the following (and if ssh outgoing is allowed)

sudo /etc/init.d/postfix stop
sudo ssh -L 25:localhost:25 [email]shelluser@smtp.server.com[/email]

Then setup your e-mail program to send through localhost

---

