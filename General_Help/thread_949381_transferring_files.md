---
title: "transferring files"
date: 2008-10-16
forum: General Help
---

### Post by mmbathan on 2008-10-16
Hi all,

I am a beginner in linux and I have a project to measure the network performance by transferring files over the network 

I use now two virtual machines , one as server and the other as client.

I tried two ping the two machines and it works fine.

and I tried to use scp command to copy file from clients to server and I got this message : 
```
bagside@bagvapp:~/Desktop$ scp mm.txt bagside@192.168.150.132:/home/user/scpm.txt
bagside@192.168.150.132's password: 
Permission denied, please try again.
bagside@192.168.150.132's password: 
Permission denied, please try again.
bagside@192.168.150.132's password: 
Permission denied (publickey,password).
lost connection
bagside@bagvapp:~/Desktop$ 

```

I tried to ssh the server and it is working fine 
```
bagside@bagvapp:~/Desktop$ sudo ssh -L123:localhost:321 user@192.168.150.132
user@192.168.150.132's password: 
Linux ubuntu8041server 2.6.24-19-server #1 SMP Sat Jul 12 00:40:01 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
Last login: Thu Oct 16 04:46:37 2008 from 192.168.150.130
user@ubuntu8041server:~$ 

```


from the server side I tried to ssh the client and I got: 

```
user@ubuntu8041:~# ssh -L123:localhost:321 bagside@192.168.150.130
ssh: connect to host 192.168.150.130 port 22: Connection refused

```

So what is the problem with scp? 

pleas help me 

thanks alot

---

### Post by pedro_orange on 2008-10-16
You're using virtual machines to test network speed? I hope they are on separate hosts lol!

scp uses ssh to connect and copy. It also uses the same authentication. However it should prompt you for these if you're not providing credentials. 
You can run scp with the -v flag to help you debug what the problem is. But I would say it's probably that you're logging in as an incorrect user.

I find it interesting you can't connect to the client from the server, but you can visa versa. I would imagine you've not configured the client to accept ssh connections, which on the server you have.

---

### Post by mmbathan on 2008-10-16
thank you pedro_orange for your reply 

as I said I am a beginner, can you help me to fix this problem

Regards,

---

### Post by hyper_ch on 2008-10-16
install on bagvapp sshfs and use that to mount the other computer into your local file system.

---

### Post by sparky-steve on 2008-10-16
Hi

You said:

> I tried to ssh the server and it is working fine:

bagside@bagvapp:~/Desktop$ sudo ssh -L123:localhost:321 user@192.168.150.132
user@192.168.150.132's password: 
Linux ubuntu8041server 2.6.24-19-server #1 SMP Sat Jul 12 00:40:01 UTC 2008 i686

But you had problems with:

> bagside@bagvapp:~/Desktop$ scp mm.txt [email]bagside@192.168.150.132:/home/user/scpm.txt[/email]

My first comment (as per pedro_orange) would be about usernames; specifically in the above examples you give, when you SSH you're using the remote username "user" but on scp you're using the remote username "bagside".  Is there a username of "bagside" on the server?

Have you tried

```
bagside@bagvapp:~/Desktop$ scp mm.txt user@192.168.150.132:/home/user/scpm.txt
```

Or am I missing something?

---

### Post by mmbathan on 2008-10-16
thank you guys for your advics

I used the code as sparky-steve advice me 

```
bagside@bagvapp:~/Desktop$ scp mm.txt user@192.168.150.132:/home/user/scpm.txt
```

and it is working fine, but from the server side I am still could not ssh  or scp to the client.

Regards,

---

### Post by Sam on 2008-10-16
> **mmbathan said:**
> and it is working fine, but from the server side I am still could not ssh  or scp to the client.

If you want to connect in both ways, then you must install the ssh daemon (server) on both hosts.

---

### Post by sparky-steve on 2008-10-17
> **mmbathan said:**
> thank you guys for your advics

I used the code as sparky-steve advice me 

```
bagside@bagvapp:~/Desktop$ scp mm.txt user@192.168.150.132:/home/user/scpm.txt
```

and it is working fine, but from the server side I am still could not ssh  or scp to the client.

Regards,

on the client, install sshd, either in synaptic package manager (search for openssh-server) or at the command line:

```
sudo apt-get install sshd
```

If you have any firewalls (unlikely from a fresh install of ubuntu) you will need to open port TCP/22

SS

---

### Post by mmbathan on 2008-10-18
hi all,

I tried to install ssh in a client and I got:

```
bagside@bagvapp:~$ sudo apt-get install sshd
[sudo] password for bagside:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

---

### Post by sparky-steve on 2008-10-18
Hi

What happens if you run

```
sudo dpkg --configure -a
```

?

---

### Post by mmbathan on 2008-10-19
Hi sparky-steve,

nothing it's happen

---

