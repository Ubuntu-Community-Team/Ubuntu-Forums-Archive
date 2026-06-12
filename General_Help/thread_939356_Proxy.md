---
title: "Proxy"
date: 2008-10-05
forum: General Help
---

### Post by yousillygoose on 2008-10-05
Hello.  I need help to set something up on my college network.  I am tryign to set up some kind of server on my linux server so that my windows desktop can access it and browse websites through the  servers IP address.  Could anyone point me in the direction of how to do this.  Thank you.

---

### Post by mssever on 2008-10-05
Squid is the most popular proxy server. Tinyproxy is a lighter-weight proxy. Be sure you either require authentication, or make it only listen on localhost, then set up an SSH tunnel to connect to your server. The other advantage of an SSH tunnel is that all traffic between your client and your server is encrypted.

---

### Post by yousillygoose on 2008-10-05
Question though: when you do this and connect through ssh doesnt that require you to connect from a linux computer?  I'm currently on a windows computer but want to connect into my ubuntu server to do this....

---

### Post by mssever on 2008-10-05
> **yousillygoose said:**
> Question though: when you do this and connect through ssh doesnt that require you to connect from a linux computer?  I'm currently on a windows computer but want to connect into my ubuntu server to do this....
One of PuTTY's tools can do port forwarding. I did that when I was in college and running XP.

---

### Post by yousillygoose on 2008-10-05
So do you know exactly how I set that up?  Does this "squid" program work through putty.  If so, would you be able to explain or point me in the direction to do it.  Thanks.

---

### Post by yousillygoose on 2008-10-05
Just had a thought.  I am using this proxy as an automatic service (hopfully).  I have having a program automatically use this proxy (and hopefully others set up) to connect to websites so that I get credit for something.  I assume that using putty forces me to manually set my proxy status?  If not, GREAT!  If so is there another route I can take?

---

### Post by mssever on 2008-10-05
PuTTY and squid are completely separate programs. Squid is an industrial-strength proxy server (which means it can probably do whatever you want, but also that you have to be careful how you configure it--you don't want to leave an open proxy for spammers to use). There are a number of ways you can proxy through squid.

PuTTY is a Windows SSH client. It's useful if you decide to make squid only listen on localhost, then set up an SSH tunnel so you can connect to it.

Using squid directly would be easiest, but there's an important caveat: You need to make sure that only authorized people can proxy through your server. If you configure it wrong and someone uses it to do Bad Things, you'll get blamed and could find yourself blocked.

Using an SSH tunnel like I mentioned above avoids the risk of accidentally running an open proxy, since squid would only listen on localhost. Additionally, since the connection between the client and your server would be encrypted, it provides a bit of protection if you have to cross a hostile network between your client and server. (Of course, between the server and the Internet, there's no extra encryption layer.) The biggest drawback is having to ensure that an SSH session is active whenever you want to use your proxy. I created a QuickLaunch shortcut on my XP box that would start PuTTY and automatically setup port forwarding. I used Pageant (part of the PuTTY suite) to store my keys so I could have passwordless login (and key-based authentication is also more secure than password authentication). That meant that I just had to click an icon to set up my connection.

---

### Post by yousillygoose on 2008-10-05
so in either case I have to have squid set up to do this?  So it is not was possible to use putty solely without installing any other process?  I know this question is pretty opposite of my last question but I like learning the full spectrum of information on something before deciding on a path to take.

So the point of this reply: is it possible to ssh into a server with nothing special installed and use it's ip from my local windows computer.

---

### Post by mssever on 2008-10-06
> **yousillygoose said:**
> So the point of this reply: is it possible to ssh into a server with nothing special installed and use it's ip from my local windows computer.
It's possible, provided the browser or whatever is running on the server, not your local machine. That means you're either stuck with elinks or similar, or you have to set up an X server on your Windows machine (e.g., using Cygwin), and configure PuTTY to use X forwarding. Then you can start up Firefox or whatever **on your remote machine**.

However, I think that this approach would be problematic for everyday use, because the entire UI would have to travel through the SSH connection, in addition to the data, which would probably cause a significant slowdown unless you have an insanely fast network connection between the server and your local machine.

---

### Post by yousillygoose on 2008-10-06
yes, that may be a problem.  So the only way to do this is with a program like squid alone or squid plus ssh tunneling, correct?

---

### Post by mssever on 2008-10-06
> **yousillygoose said:**
> yes, that may be a problem.  So the only way to do this is with a program like squid alone or squid plus ssh tunneling, correct?
Yes, it's the only reasonable way. Although remember that squid isn't the only proxy server. Tinyproxy might be easier to handle if it can do what you want. And if you search synaptic, you'll probably find many different proxy servers.

---

