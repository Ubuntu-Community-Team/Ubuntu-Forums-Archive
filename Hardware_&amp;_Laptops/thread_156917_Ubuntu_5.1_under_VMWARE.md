---
title: "Ubuntu 5.1 under VMWARE"
date: 2006-04-08
forum: Hardware &amp; Laptops
---

### Post by nemiroff on 2006-04-08
Dear friends, 

I set up ubuntu under VMWare, or I tried to do it because X-server is not working and producing below error. 

[IMG]http://onfinite.com/libraries/850260/42c.jpg[/IMG]

It is obvious that, the problem comes from the wrong video card, ubuntu doesn't know what is VMWARE video card.

Does anyone know how can I fix this ?
where can I fix it ? (from Ubuntu or from VMWare ?)

Thanks. 
Alp

---

### Post by ranf on 2006-04-08
You fix it in Ubuntu (5._10_ by the way).
As root run:
```
dpkg-reconfigure xserver-xorg
```
and choose `svga' as graphics driver.

---

### Post by nemiroff on 2006-04-10
Thanks for your reply, however I did not set up a root password during install of ubuntu 5.10. 

At first, I thought that I forgot it, but I installed again but the installation did not ask for root password, are there any one for default ?

how can I find it ?

thanks

---

### Post by ranf on 2006-04-10
I saw "root@ubuntu" in your screenshot and assumed you had it enabled.
You don't have to. Just put "sudo " in front of the command above.

More reading on sudo vs. root:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

There is also a ready-to-run Ubuntu appliance at vmware.com:
[http://www.vmware.com/vmtn/appliances/ubuntu.html](http://www.vmware.com/vmtn/appliances/ubuntu.html)

---

### Post by jond01 on 2006-04-16
Hi, im using ubuntu appliance in VMWare server, but cant figure out what the password is for the ubuntu userid when im at the console.  It doesn't seem to be documented anywhere.  I didn't have to set up any account when installing.I'm a confused administrator!:(

---

### Post by crouton on 2006-04-17
Try 'vmware'?

---

