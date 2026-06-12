---
title: "Choice of CPU for Ubuntu Server"
date: 2016-09-11
forum: Hardware
---

### Post by petenoob on 2016-09-11
So I am trying to decide on a laptop which will run a ubuntu apache webserver, which does not break the bank and I am not sure if I should go for a better processor.


I am using the webserver as a kind of quiz machine with 50 wireless clients connected concurrently answering questions and submitting answers. Nothing heavy like streaming videos, but each user requests is around 10-30 kb, static pages, one question per page, one jpeg. The users could be using the server all at once.


Anyway, for a webserver, I hear that RAM is very important over anything else so I am going to get 16GB, and to make sure I am going to get a SSD drive. The model I am thinking about Lenovo L460:


[http://i.stack.imgur.com/VOQO7.png](http://i.stack.imgur.com/VOQO7.png)


[http://i.stack.imgur.com/6O7Uj.png](http://i.stack.imgur.com/6O7Uj.png)

So with performance in mind, should I upgrade to i5 or even i7? Does it matter?

---

### Post by mörgæs on 2016-09-12
It sounds like a light work load and I suggest that you begin with whatever hardware you have available already. 

Don't go buying new stuff unless you have hard proof (that is, test results) that the old one is too weak.

---

### Post by mastablasta on 2016-09-12
why a laptop? does server need to be portable or something? 
why i5? why 16GB RAM? Why SSD?

the latest Raspberry pi could probably run what you plan to run. not sure aboout concurrent connections. in any case of not the Pi, then a miniPC would definitelly run it easilly.

---

### Post by petenoob on 2016-09-12
Yes, it must be highly portable as I need to move location everyday. And since I have no experience with so many users all at once, I rather line all my ducks up because the project will be used in a commercial setting so everything must be smooth with no bottlenecks. Hence SSD, and 16GB ram. 

To add more information, I will have two bridge APs to work with so many clients.

---

### Post by mörgæs on 2016-09-12
> **petenoob said:**
> Since I have no experience with so many users all at once...

...I suggest that you get experienced by doing some real-life testing.

Better to base your decision upon facts than upon presumptions. Can't give you advice beyond that at this early stage.

---

### Post by petenoob on 2016-09-12
Yes, you are right, I need experience.

I do have a working prototype with one router, one web-server, and some tablets, works fine. But i still need a benchmark where to start because I still need 50 concurrent users, and I still need to plan to buy what I need. 

Which is theory-craft, which is why I posted my question. So give me an possible theoretical answer based on YOUR experience. :-k If there is someone who has done something similar wouldn't it be prudent to ask first?

---

### Post by mörgæs on 2016-09-13
My experience is that a webserver serving only static pages puts very little workload on the hardware. Moreover, 50 concurrent users are not truly concurrent, as their mouse clicks do not appear in the exact same moment. 

This gives low hardware requirements.

Do you have the option to test your present hardware in a 50 user setup?

---

### Post by mastablasta on 2016-09-13
i still think your machine will be an overkill, but if you were given the budget for it, then go for it. 

the bottleneck i see could be the wi-fi connection, since it is not optmised on laptops for what you intend it to do. i would seriously think about mini iTX board (e.g. something like intel NUC) with some professional wi-fi PCI card added or some other type of wi-fi expansion on the laptop (if you go the laptop way). that it unless you intend to use a good wireless router to do that. then you can use cheaper PC. 

SSD is not necessary. 16GB ram - i haven't seen your page, but from what you described i doubt you will go over 1 GB. but if you have the money, go for it.

you can probably use pentesting tools (check out Kali or Backbox Linux for some guides and tools) to try and log 100 user concurently and see how it goes.

i have for 5 or 6 users a 4GB microserver with Apache, Owncloud, Ajenti, various security services, SSH and few other things. i never went over 350 MB ram. i think i need to start playign with virtual machines as this server is not being used much... it was meant as a backup & file server. i added RAID1, but in retrospect that might not have been necessray. oh and the os is on a USB key. the only bottleneck is network.

---

### Post by petenoob on 2016-09-13
> **mörgæs said:**
> My experience is that a webserver serving only static pages puts very little workload on the hardware. Moreover, 50 concurrent users are not truly concurrent, as their mouse clicks do not appear in the exact same moment. 

This gives low hardware requirements.

Do you have the option to test your present hardware in a 50 user setup?

No, not with 50 users. To test it, I am going to buy 30 cheap computer tablets and auto-reload a browser page with some data to the server (... and hope if doesn't blow up :D ). I think this method could possibly answer the biggest question which is the performance of 1 host and 'many' clients. Maybe there is a better way to test but I think well beyond the scope of my skills.

Cheers!

---

### Post by petenoob on 2016-09-13
> **mastablasta said:**
> i still think your machine will be an overkill, but if you were given the budget for it, then go for it. 

the bottleneck i see could be the wi-fi connection, since it is not optmised on laptops for what you intend it to do. i would seriously think about mini iTX board (e.g. something like intel NUC) with some professional wi-fi PCI card added or some other type of wi-fi expansion on the laptop (if you go the laptop way). that it unless you intend to use a good wireless router to do that. then you can use cheaper PC. 

SSD is not necessary. 16GB ram - i haven't seen your page, but from what you described i doubt you will go over 1 GB. but if you have the money, go for it.

you can probably use pentesting tools (check out Kali or Backbox Linux for some guides and tools) to try and log 100 user concurently and see how it goes.

i have for 5 or 6 users a 4GB microserver with Apache, Owncloud, Ajenti, various security services, SSH and few other things. i never went over 350 MB ram. i think i need to start playign with virtual machines as this server is not being used much... it was meant as a backup & file server. i added RAID1, but in retrospect that might not have been necessray. oh and the os is on a USB key. the only bottleneck is network.

Actually you may be correct that my setup is an overkill. Even though I think a lesser spec should be ok, I am still not sure, plus, and this is the most important, I need to show others that it works and works very well without any 'lag', so it is ok to invest in better hardware. And besides, this server right now is on my home laptop so I have to buy a new work laptop anyway to run a dedicated web-server.

Yes, the bottleneck is the wifi. I think I got that sussed, add 2 hardwired APs and bridge them. The APs OEM said it should be fine with what I am trying to do but if there is a problem, just add another AP. Like I said before, the system is portable so lugging around 2-3 APs and 1 laptop, plus setup and wires is not ideal but get some experience first and go from there.

Thanks for the heads up on the testing, I am going to read about it now.

---

