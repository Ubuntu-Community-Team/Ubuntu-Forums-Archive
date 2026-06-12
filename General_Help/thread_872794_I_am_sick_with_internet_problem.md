---
title: "I am sick with internet problem"
date: 2008-07-28
forum: General Help
---

### Post by emigrant on 2008-07-28
hai, admins,moderators,staff and other members,

i couldnt find a solution for my problem for months. even here or in other fourms.
here it is the problem,

i have ADSL broadband conncetion(512kbps).
i connect to internet through adsl router throug network card.
i use dual OS. ubuntu 8.04 and windows vista.
internet connects and works perfectly in win vista.
i dont know why it doestnt conncet to internet in ubuntu.
i typed
```

sudo pppoeconf

```

and even
```

udo apt-get install pppoeconf

```

but it didnt connect at once. after some time or somedays it got connected. probably because i went through all the settings i thought would help me.
and then after i restarted it got disconnected. again after two or three days it again got connected.


now i have got fedup with ubuntu. but still i dont like to desert ubuntu.so please helppppppp me.
my previous posts didnt help me.:(:(:(:(:



thanks in advance.:popcorn:


btw: iam very very new to ubuntu.

---

### Post by UbuntuNerd on 2008-07-28
I notice that your previous post said you have Ubuntu 7.10 is that what you have currently using?

---

### Post by emigrant on 2008-07-28
no i am now usint 8.04. i have upgraded it.

---

### Post by Potatoj316 on 2008-07-28
Were you connected to the internet when you installed?  If you wernt DHCP might not be setup.  Some time when you dont have internet try this in the terminal
```
dhclient3
```
It may or may not work.  

Also try checking the restricted drivers manager under System->Administration->Hardware Drivers.  If there are any items listed here make sure their checkbox is checked.  You will have to be online to download the packages though.  

What is that pppoewhatever thing you were trying to install?

---

### Post by emigrant on 2008-07-28
ya i was connected to internet while i was upgrading.
as far as i can remember i enabled the restricted drivers when i was connected.

> 
What is that pppoewhatever thing you were trying to install?


i dont know what is that. but here only i found that.

[http://ubuntuforums.org/showthread.php?t=853243](http://ubuntuforums.org/showthread.php?t=853243)

---

### Post by emigrant on 2008-07-28
i cheked in network tools.

it wont connect to ethernet(0) interface.
it always connects to loopback(0) interface.

---

### Post by emigrant on 2008-07-28
I am now supposed to shift to another distro. what is your recommendation? please.

---

### Post by emigrant on 2008-07-29
i abondend ubuntu and now using fedora and working fine.
thanks for all your help

---

