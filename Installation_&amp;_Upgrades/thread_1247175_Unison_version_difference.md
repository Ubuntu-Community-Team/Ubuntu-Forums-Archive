---
title: "Unison version difference"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by CptCapslock on 2009-08-22
Hi all,

I want to sync a folder between 4 Ubuntu computers and a Debian server. My idea was to sync all computers with the server via Unison through SSH, which I read about on the forums. 

I have two problems though:

[LIST=1]
[*]The version on the ubuntu computers is 2.27 the version at the server is 2.13. Therefore I get this error:```
Fatal error: Received unexpected header from the server:
 expected "Unison 2.27\n" but received "Unison 2.13\n\000\000\000\000", 
which differs at "Unison 2.1".
This can happen because you have different versions of Unison
installed on the client and server machines, or because
your connection is failing and somebody is printing an error
message, or because your remote login shell is printing
something itself before starting Unison.
```
So: how do I downgrade to 2.13, or how do I upgrade on the debian server to 2.27?
[*]I don't feel like entering my password all the time, because I want to do it via cron. How can I store my password? It doesn't have to be secure, since it doesn't contain sensitive information.
[/LIST]
Thanks.

---

### Post by drs305 on 2009-08-22
Although upgrading your server's version of unison would be preferable, if you cannot you can find old builds of ubuntu debs on the launchpad site. 

Go to the following page and type in *unison* and search for *successfully built* If you scroll down near the bottom you can find some of the 2.13 builds.

[https://launchpad.net/ubuntu/+builds?]("https://launchpad.net/ubuntu/+builds?")

---

### Post by CptCapslock on 2009-08-22
Thanks a lot! That worked perfectly. Now a solution to my second problem would be nice. Do you know how to store my password in some kind of way? This is the line I use:
```
unison -silent /home/user/folder ssh://[url]//home/user/folder
```

---

### Post by drs305 on 2009-08-22
I used to use unison with SSH. Accomplish the section for SSH Version 2, adding the public key to the second machine's $HOME/.ssh/authorized_keys.
[http://www.ece.uci.edu/~chou/ssh-key.html]("http://www.ece.uci.edu/~chou/ssh-key.html")

Once you have done that, you should be able to connect without a password. Here is a simplified command I used to sync with unison:
```

unison /home/drs1  ssh://drs2@192.168.0.2//home/drs2

```

---

### Post by CptCapslock on 2009-08-23
Thanks! All my problems are solved now.

To make things really easy for passwordless ssh, enter the following commands on the local machine:
```
$ ssh-keygen -t dsa
$ cat ~/.ssh/id_dsa.pub | ssh -l [REMOTE_USER] [REMOTE_SERVER] 'cat >> ~/.ssh/authorized_keys'
```

---

