---
title: "Jaunty Jackalope and encryption"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by cmistake on 2009-04-16
Hi.

I own a Samsung NC10 netbook, and I have it with me daily. I'm surprised that I haven't lost it yet, nor has it yet been stolen. That will propably happen in a month or so, so I thought it would be wise to encrypt my system. I want my files to be safe, becouse I have all my passwords and stuff saved in my Firefox profile etc. Also, if it gets stolen, I want to make my netbook as useless as possible to the guy who stole it.

So, if I undestand correctly, there's an option to encrypt /home/ directory during Jaunty installation. I want to make sure, becouse the stuff I've read about it all refer to Alpha version, and I've also read that it's no longer possible in beta. 
If it's simple and possible with Jaunty installation disk that solves the privacy issues - I can easily encrypt my /home/ directory and all my files would be safe. That would be great, but I want to go even further, becouse I'm paranoid and I wear a tinfoil hat everywhere to protect my thought from the evil government (We have one in Finland too).

Is there an easy way to encrypt the whole hard drive? If I did that, then protected my BIOS with a password, wouldn't it be impossible for anyone to get into my computer, or even install a new OS, without some skills with computer (removing the BIOS battery or something from a laptop this small). I know computer stores wont do that for anyone who comes with a laptop in their hands without a receit saying that they "forgot the password".

[SIZE="1"]Sorry if a similar post already exists. I tried to google around and browse the forums, but it just seemed that before Jaunty, encyption was done in so many different ways for so many different reasons that I wanted to find an answer that suits my situation best.
[/SIZE]

---

### Post by ahbart on 2009-04-16
I've read that there are some problems with encryption of home in Jaunty and that it would not be enabled in the final release. 
I've setup encryption on my home/username folder via encfs and libpam-mount and libpam-encfs. There was a very good howto for that on /www.ubuntu-eee.com.
But I can not find it over there. There is a copy of it here: [link](http://www.iterasi.net/openviewer.aspx?sqrlitid=x_watd9a70wbhh4rcl7jia)
If you use it, you should save it or print this page.

---

