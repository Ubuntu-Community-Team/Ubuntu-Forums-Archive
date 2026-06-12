---
title: "Apache2 multiple site hosting"
date: 2008-08-22
forum: General Help
---

### Post by idipous on 2008-08-22
Hi everybody,

I tried to configure apache2 on ubuntu 8.04 today so as to host multiple sites over the same ip. I have succeeded partially.

Following some instruction I found online ([http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2](http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2)) I have managed to have multiple sites. The problem is this:

On some computers typing [http://www.otecorporategames.gr/hello.html](http://www.otecorporategames.gr/hello.html) works fine but again typing  [http://otecorporategames.gr/hello.html](http://otecorporategames.gr/hello.html) it outputs an error saying that the file cannot be found.

On other computers the exact opposite is happening. Why is that?

I need it to work both ways and I am sure that the dns record are correct. Should I try another configuration than the one proposed in the above link?

My file in the /etc/apache2/sites-available directory is called otecorporategames.gr and has the following content:

```
<VirtualHost myip:80>
ServerName otecorporategames.gr
ServerAlias www.otecorporategames.gr
ServerAdmin andreas.s@arcww.gr
DocumentRoot /var/www/otecorporategames/docs
</VirtualHost>

```

I am really confused here and any help would be much appreciated.
Thanks in advance
idipous

---

### Post by kidders on 2008-08-24
Hi there,

> **idipous said:**
> I am sure that the dns record are correct.

It doesn't look that way ... otecorporategames.gr and www.otecorporategames.gr don't point at the same machine. One is an Ubuntu/Apache box, and the other is running Windows/IIS6.

```
Starting Nmap 4.03 ( http://www.insecure.org/nmap/ ) at 2008-08-24 10:35 BST
Interesting ports on www.fastnet.gr (193.58.186.29):
(The 1670 ports scanned but not shown below are in state: filtered)
PORT    STATE  SERVICE  VERSION
25/tcp  closed smtp
80/tcp  open   http     Microsoft IIS httpd
110/tcp closed pop3
443/tcp open   ssl/http Microsoft IIS httpd 6.0
Service Info: OS: Windows
```

```
Starting Nmap 4.03 ( http://www.insecure.org/nmap/ ) at 2008-08-24 10:35 BST
Interesting ports on lion.fastnet.gr (193.58.186.63):
(The 1666 ports scanned but not shown below are in state: closed)
PORT    STATE    SERVICE      VERSION
22/tcp  open     ssh          OpenSSH 4.7p1 Debian-8ubuntu1.2 (protocol 2.0)
80/tcp  open     http         Apache httpd 2.2.8 ((Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch)
111/tcp open     rpcbind       2 (rpc #100000)
135/tcp filtered msrpc
137/tcp filtered netbios-ns
138/tcp filtered netbios-dgm
139/tcp filtered netbios-ssn
445/tcp filtered microsoft-ds
```

---

### Post by qstraza on 2008-08-24
port scanning is illegal in our country :/ :p

---

### Post by Vishal Agarwal on 2008-08-24
> **qstraza said:**
> port scanning is illegal in our country :/ :p


:)

---

### Post by idipous on 2008-08-26
Well intentioned scans are not illegal...

Thanks

---

### Post by qstraza on 2008-08-26
owner has to allow you first ;)

---

### Post by kennedy7 on 2008-12-06
Aah someone didnt search long enough on the forum as it turns out i have a post that teaches you exact virtrual-hosting setup that works fine. here is the link [http://ubuntuforums.org/showthread.php?t=978659&highlight=virtual+hosting](http://ubuntuforums.org/showthread.php?t=978659&highlight=virtual+hosting)

You will be able to host more than one site with vhosting.

---

