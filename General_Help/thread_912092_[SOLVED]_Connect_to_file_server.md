---
title: "[SOLVED] Connect to file server"
date: 2008-09-06
forum: General Help
---

### Post by graabein on 2008-09-06
Hi, I have file server on the local network called "kafka". My main box is called "barbosa". How do I find it and connect with both SMB and SSH? I can do it easily from Windows XP (putty, windows explorer) on this box, but not with Ubuntu 8.04. Can I ping it?

---

### Post by WRDN on 2008-09-06
Using the name or IP of the server, you can connect.
Click Places > Connect to server, then select SSH or Windows Share (Samba) from the Service Type. Finally, fill in the details and click Connect.
You can connect to SSH from the Terminal using the command:

```
ssh [name/ip]
```

For example, when I connect, I type:

```
ssh -X [IP_Address] -p 1025
```

The "-X" directive ensures I can forward X11 and "-p 1025" is used as I connect on port 1025. You must set "X11Forwarding" to "yes" in the /etc/ssh/sshd_config file if you wish to forward X11.

---

### Post by graabein on 2008-09-06
```
$ **ssh kafka**
ssh: kafka: Name or service not known
```

How do I look for machines on my network?

---

### Post by pbotros1234 on 2008-09-06
> **graabein said:**
> ```
$ **ssh kafka**
ssh: kafka: Name or service not known
```

How do I look for machines on my network?
Do you have samba installed and everything? Make sure to edit your /etc/samba/smb.conf file for your network.

I used this tutorial [here]("http://www.linux.com/articles/58593"), and it works perfectly for me.

---

### Post by graabein on 2008-09-06
Thanks, I'll give it a shot when I find the time. Strange that it works from XP but not Ubuntu but it's probably some config issue or a missing program or something.

---

### Post by graabein on 2008-09-11
Still no go. I can connect from Windows XP partition but not from Ubuntu 8.04. What a let down!! :(

I don't need Samba to connect with ssh, right?

---

### Post by Iowan on 2008-09-11
> **graabein said:**
> I don't need Samba to connect with ssh, right?Correct! In fact, if server already has SSH installed, you could install use [SSHFS]("https://help.ubuntu.com/community/SSHFS").  SSH client is (usually) pre-installed. Sometimes, name resolution gets in the way - try ssh via IP address: **ssh 192.168.1.234**

---

### Post by milasch on 2008-09-11
you can edit your /etc/hosts file to point any name to an IP address...

this way ssh anything will work.

---

### Post by graabein on 2008-09-12
Is this strange? This is on the server from Putty on XP:
```
**$ ifconfig**
eth0      Link encap:Ethernet  HWaddr **<1>**
          inet addr:10.0.0.6  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: **<2>** Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:67 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7371 (7.1 KB)  TX bytes:10428 (10.1 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: **<3>** Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
Or should I try **ssh 10.0.0.6**? :confused:


Update: Oh yeah, that did the trick :)

---

### Post by graabein on 2008-09-15
Updated my **/etc/hosts** file adding:
```
10.0.0.6 kafka
```

So I can run **ssh kafka** to connect to my server. I like it!

---

