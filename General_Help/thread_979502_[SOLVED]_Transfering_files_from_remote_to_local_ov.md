---
title: "[SOLVED] Transfering files from remote to local over SSH"
date: 2008-11-12
forum: General Help
---

### Post by echo314 on 2008-11-12
What am I doing wrong here? 
```
fleetadmiral73@sdesktop:~$ scp test.file echo@localhost:/home/echo/
ssh: connect to host localhost port 22: Connection refused
lost connection
fleetadmiral73@sdesktop:~$ 

```

How do I open 22? I've tried a bunch of stuff, my friend is even connected to me on that port, yet I cant get a file from his comp to mine?

---

### Post by Crafty Kisses on 2008-11-12
You probably need the **openssh-server** package (which is provided by transitional ssh package). This would be true on both computers, and make sure you installed it correctly on both computers.
```
sudo aptitude install ssh
```

---

### Post by blackened on 2008-11-12
> **echo314 said:**
> What am I doing wrong here? 
```
fleetadmiral73@sdesktop:~$ scp test.file echo@localhost:/home/echo/
ssh: connect to host localhost port 22: Connection refused
lost connection
fleetadmiral73@sdesktop:~$ 

```

How do I open 22? I've tried a bunch of stuff, my friend is even connected to me on that port, yet I cant get a file from his comp to mine?

Are you doing this on a LAN or over the net?

---

### Post by baeksu on 2008-11-12
Can you make an ordinary ssh connection to his machine?

Connection refused tells that either he has a firewall blocking the port, or there's no ssh server listening on his machine for remote connections.

Until you can connect to his machine through ssh, scp won't work.

Of course, if he can connect to you via ssh, he can always set up a "reverse ssh tunnel". Example can be found here: [http://articles.techrepublic.com.com/5100-10878_11-5779944.html?tag=nl.e011](http://articles.techrepublic.com.com/5100-10878_11-5779944.html?tag=nl.e011)

---

### Post by echo314 on 2008-11-12
It is installed though, right? Since I can connect to him, and he to me, we both should have the server installed. I can run commands on his system, I just cant figure out how to make the destination dir back to MY own computer, its stuck in his. or I get that port 22 error, but he is connected to my comp on that port, and can run commands, so obviously its open..

THank you for your response

---

### Post by echo314 on 2008-11-13
> **blackened said:**
> Are you doing this on a LAN or over the net?

Over the net. I can obviously SSH into his box, and he can successfully SSH into mine. The problem is I when taking files of his comp, and routing them back to *mine*, it can't get in, saying the port is blocked.

I can make an ordinary connection to his machine, the test.file is in a folder on his comp i created over ssh.

---

### Post by blackened on 2008-11-14
> **echo314 said:**
> Over the net. I can obviously SSH into his box, and he can successfully SSH into mine. The problem is I when taking files of his comp, and routing them back to *mine*, it can't get in, saying the port is blocked.

I can make an ordinary connection to his machine, the test.file is in a folder on his comp i created over ssh.

Can your friend do the reverse of this process using scp via the same command?

Also, have you tried using **uname@ipaddress** instead of **uname@hostname**?

---

### Post by echo314 on 2008-11-14
Trying scp with username@IP worked. Thank you all for helping me figure this out.

ps. Why is the terminal choppy when logging into his machine? Is that a result of the Internet being slow, or his machine? I just remember it was not always laggy, and now even when I type in some characters, its slower.

---

### Post by blackened on 2008-11-14
> **echo314 said:**
> Trying scp with username@IP worked. Thank you all for helping me figure this out.

ps. Why is the terminal choppy when logging into his machine? Is that a result of the Internet being slow, or his machine? I just remember it was not always laggy, and now even when I type in some characters, its slower.

Likely just net lag. Is it always slow, or does the speed and reactivity vary?

---

