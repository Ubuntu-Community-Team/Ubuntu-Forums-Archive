---
title: "[SOLVED] terminal chat with IP"
date: 2008-09-01
forum: General Help
---

### Post by tsikis on 2008-09-01
Hello there i have a question that i cannot find the answer anywhere.
I want to be able to chat through terminal with a friend of mine but we do not want to use any kind of messenger so my question is :
Is there anyway , package to use so we can chat through terminal by using our ip (either me connecting to him or opposite) or any other way possible but just by using the other ones IP.
By asking that i do not mean using any kind of ssh to connect to him by a username and talk from user to user.
Just using his ip and if needed a password of some kind.
Thanks in advance

---

### Post by Oldsoldier2003 on 2008-09-02
Moved from Tutorials and Tips moderation queue. To avoid delays in resolving your problem, please don't post support questions to T&T .

---

### Post by Vivaldi Gloria on 2008-09-02
Probably there are better tools for the job but you can easily achieve cli chat with netcat:

[http://www.hackosis.com/2007/12/01/diy-simple-chat-server-with-netcat/](http://www.hackosis.com/2007/12/01/diy-simple-chat-server-with-netcat/)

Netcat is #4 here:

[http://sectools.org/](http://sectools.org/)

In the first computer give the command

```
netcat -nvlp <port_number>
```

and in the second give the command

```
netcat -nv <ip_number> <port_number>
```

and start chatting. Of course you should forward the ports in the routers first.

While chatting I prefer that one sides starts his lines with the plus sign so they are easier to see. Actually it shouldn't be hard to write a script which does this automatically. 

Note that netcat sends in the open so it could be sniffed. You can tunnel it through ssh or try cryptcat

[http://sourceforge.net/projects/cryptcat/](http://sourceforge.net/projects/cryptcat/)

I haven't tried cryptcat so I cannot comment on it.

If you find a dedicated tool for chatting please let me now.

---

### Post by Vivaldi Gloria on 2008-09-02
I experimented with cryptcat a bit. First install it:

```
sudo apt-get install cryptcat
```

In the first machine use

```
cryptcat -nvlp <port_number> -k <password>
```

and the in the second use

```
netcat -nv <ip_number> <port_number> -k <password>
```

Works similarly to netcat. 

Note that there is also socat which can use openssl:

[http://www.dest-unreach.org/socat/](http://www.dest-unreach.org/socat/)
[http://www.dest-unreach.org/socat/doc/socat-openssltunnel.html](http://www.dest-unreach.org/socat/doc/socat-openssltunnel.html)
[http://www.dest-unreach.org/socat/doc/socat.html](http://www.dest-unreach.org/socat/doc/socat.html)

---

### Post by Thyagaraj on 2011-06-11
I don't want to start telling it's an old post, but really it's Useful+Entertainment which I was looking for. I really liked your image, it's very cute but a bit of sadness appears on it and perhaps it may be related to your personal life. Thanks!

---

