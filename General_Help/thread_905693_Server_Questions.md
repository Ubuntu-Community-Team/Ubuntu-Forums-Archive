---
title: "Server Questions"
date: 2008-08-30
forum: General Help
---

### Post by Viridia on 2008-08-30
Ok, here's  my situation:

I want to set up a server for myself. I'll be using my seven year old Sony laptop. Only one person will be using it at a time, and rarely at that. It will contain only documents normally, but mp3s and jpegs on occasions. It needs to be accessible from a web browser (I will most likely use it on the computers at school, to download docs from home plus it will be used across operating systems, so it needs to be done from the browser) It also needs to be easy to setup, since I have no prior experience with servers, and it needs to be *very* easy to download from, as my parents will be using it on occasion.

Will Ubuntu server edition fit my needs? Thanks

---

### Post by bodhi.zazen on 2008-08-30
From what you describe all you need is apache.

---

### Post by Viridia on 2008-08-30
How would I set that up?

---

### Post by bodhi.zazen on 2008-08-30
Installing is easy, 

sudo apt-get install apache2

then put your files in /var/www

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

See also any on line apache guide.

---

### Post by Viridia on 2008-08-30
Thanks

But could I upload files from my primary machine to the server?

---

### Post by cariboo on 2008-08-30
I think ssh, sftp and scp would serve your puposes better than going to the trouble of setting up apache2 on you laptop. Install openssh-server on you laptop and use sftp in Ubuntu and winscp in Windows.

Winscp is a free download and use sftp with Nautilus, in the location bar of Nautilus (Places-->Home Folder) type:

```
sftp://user@server
```

Where server is your server ip address or domain name. A window will pop up and ask for your password and you will be able to transfer files back and forth. If you are using a router, you should give your laptop a static ip address and then setup port forwrding to that ip address in your router. If you want a domain name you can go to:

[http://www.no-ip.com/](http://www.no-ip.com/)

To get a free domain name.

---

### Post by Viridia on 2008-08-31
Actually, my primary machine is an iMac. Are there any utilities for that?

---

