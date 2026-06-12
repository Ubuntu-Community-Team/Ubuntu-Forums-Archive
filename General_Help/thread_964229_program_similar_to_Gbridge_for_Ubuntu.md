---
title: "program similar to Gbridge for Ubuntu?"
date: 2008-10-30
forum: General Help
---

### Post by xanfantasy on 2008-10-30
Recently I found a program called [Gbridge]("http://http://www.gbridge.com/"). Gbridge is a secure file share and VNC server/client that used a gmail account to connect computers. I have played with in in windows XP and was wondering if there is a similar program for Ubuntu. 

The features I like about it is the Remote Desktop and file sharing. Also, you do not need an IP to connect to the other computer. This is very helpful since I have Verizon DSL and they occasionally change the IP to prevent servers. The program would also have to be able to have the server on ubuntu and a windows client to connect.

If not, is there a way to write a script their either mails out the external IP every so often or look for a special Email from a gmail account and then send out the email? That way I would be able to get the IP when ever I would need it and I could just use one of the VNC clients/servers already in the repositories.

Thanks
Xan Fantasy

---

### Post by xanfantasy on 2008-11-06
I'm guessing there isn't any program similar to this, but is there a way to email the ip? Is it possible through bash and/or python?

---

### Post by jeffrey8chang on 2009-06-27
You can try Remobo, which can be run on Linux, Mac, and Windows:

[http://www.remobo.com](http://www.remobo.com)

It assigned Virtual IP to the machines in your Instant Private Network, and provide dynamic-DNS mapping between <machine>.<userID>.remobo.com and your Virtual IP.

--- Jeffrey

---

### Post by xanfantasy on 2009-06-28
Thanks, That's exactly what I was looking for.

Xan Fantasy

---

