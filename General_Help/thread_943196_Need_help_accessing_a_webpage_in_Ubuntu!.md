---
title: "Need help accessing a webpage in Ubuntu!"
date: 2008-10-10
forum: General Help
---

### Post by Albertkinng on 2008-10-10
ok, in my Mac I can access this page... in my Netbook with Ubuntu not. Can anyone tell me if this is a problem that can be solve or I'm in trouble. (I recently buy this ubuntu machine for work and this is one of my daily webpages I need to access.

This is the page: [http://207.30.10.251/](http://207.30.10.251/)

of course you dont know the name and pass, I just need to know if you can even click on the login botton. I can in Mac, I cannot in Ubuntu. Please help!

---

### Post by fictivetoast on 2008-10-10
Comes through for me - what exactly happens when you try to get at it in Ubuntu?  Does the address just not resolve?  I assume you're using FireFox?

---

### Post by BUSHYBOB on 2008-10-10
It's a flash movie. You need to get the flash plug-in.

---

### Post by sad1sm0 on 2008-10-10
I have the flash 9 plugin and I also can't press the submit button.

---

### Post by forger on 2008-10-10
$ apt-cache policy flashplugin-nonfree
flashplugin-nonfree:
  Installed: 10.0.12.10ubuntu1
  Candidate: 10.0.12.10ubuntu1
  Version table:
 *** 10.0.12.10ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages
        100 /var/lib/dpkg/status

can be pressed here :)

---

### Post by Albertkinng on 2008-10-10
> **forger said:**
> $ apt-cache policy flashplugin-nonfree
flashplugin-nonfree:
  Installed: 10.0.12.10ubuntu1
  Candidate: 10.0.12.10ubuntu1
  Version table:
 *** 10.0.12.10ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages
        100 /var/lib/dpkg/status

can be pressed here :)

ok, if you explain me how to get the new flash I can trash my Mac and continue wit6h my Ubuntu Machine for ever... thats the only thing that keep my Mac in my backpack.. Im new in Ubuntu, so please be gentle... How can I update the flash and access that page?? thanx in advance.

---

### Post by Albertkinng on 2008-10-10
Hey I did it! thanx for all your help. Now it can be pressed but I cannot access the page anyway, mmm I can send you a private messege and let you know my name and pass to help me here, I really need access to this page, it's very important.

---

### Post by forger on 2008-10-11
I am using Ubuntu 8.10 Intrepid Ibex beta currently.. I'm sorry, I won't accept the user/pass, I don't want to be blamed for anything, but I'll try and help you out without it :)

Reply and post the output of these commands:
```

lsb_release -a
uname -a
apt-cache policy flashplugin-nonfree

```

---

### Post by forger on 2008-10-11
Hm.. ignore the above post, I can't login to that page, or it doesn't show an error for wrong user/password

Have you tried with opera web browser:
[http://www.opera.com/download/](http://www.opera.com/download/)

edit: I tried it with opera, it doesn't work with opera.. well, at least not here :)

---

### Post by forger on 2008-10-11
No offense, but this webpage doesn't seem to do anything upon clicking that login button..
I used Internet Explorer in a virtual machine, and I tried to login with wrong user/pass and no errors.. is this normal?

Contact the support administrator of this page and mention this problem, since it's flash I think they ought to support a wealth of browsers. Be sure to mention your version of flash!

---

### Post by Albertkinng on 2008-10-12
Don't tell me that... oohh man,.. It's working on my Mac already.... I will try on other PC and see what happens... :confused:

---

