---
title: "apt-get update error"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by crazymoonboy on 2009-05-18
Hi,

I am trying to install one software from a https server and I already have my user name and password. BUT, Here

My user name is email id i.e., [email]abc@def.com[/email]
My password: password

and I am trying to get files from [www.example.net/somefile](www.example.net/somefile).

Now, I added the whole line in /etc/apt/sources.list file as below:

deb [https://abc@def.comassword@example.net/somefile](https://abc@def.comassword@example.net/somefile)
deb-src [https://abc@def.comassword@example.net/somefile](https://abc@def.comassword@example.net/somefile)

Now, I executed apt-get update command and it is giving the below error:
Couldn't resolve host 'def.comassword@example.net'

It is not taking my entire email id as my user name.

How can I give correctly in /etc/apt/sources.list file? Please help me.

Thanks in advance.

Regards,
Chandra.

---

### Post by aysiu on 2009-05-18
You shouldn't need a username and password to add a source to your /etc/apt/sources.list

What's the actual URL (not the example.net/somefile, the actual URL)?

---

