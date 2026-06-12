---
title: "(First post) ATI mobility x1400 restricted driver not working"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by Durnus on 2007-11-01
Well, I just installed linux, and I have a problem.

I'm using a dell inspiron E1505, with a Radeon Mobility x1400 graphics card. After finding the official ATI driver for linux (fglrx), it doesn't work.

I try to let it run by enabling it from the restricted drivers manager, but it tells me:

"Could not apply changes! fix broken packages first."

I have checked everywhere, and none of my packages are broken, and it hasn't told me what to fix. I have enabled the source code downloading stuff, but this is as far as I can get without help. Please help, I'm stuck at an insanely low resolution until I can fix this. (It hurts my eyes!)

Thanks!

---

### Post by marcantonio on 2007-11-01
Try running ```
sudo apt-get -f install
``` and post the output here.

---

### Post by Durnus on 2007-11-01
I've only tried that too many times. :(

Anyway:
durnus@Galactic:~$ sudo apt-get -f install
[sudo] password for durnus:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
durnus@Galactic:~$

---

### Post by marcantonio on 2007-11-02
That error message is from synaptic.  If you run sudo synaptic, click on Custom Filters and then Broken is there anything listed?

---

### Post by Durnus on 2007-11-02
Does it run by default as sudo? I'm at school right now, so I can't check if I did it that way, but when I opened the package manager and looked for broken packages, none were broken.

Will give more info once I get home.

EDIT: None of my packages are broken. Anything else you need to help me with my situation?

---

### Post by Durnus on 2007-11-05
Please, this is a cry for help, I really don't want to use linux unless someone can fix it. (IE I hate low resolutions/really wanted to use desktop effects as a part of linux.)

Just ask me anything you need to know, and I will give you the info. I want linux to work!

EDIT: Good news! When I hit the "test" button in the Screen and Graphics manager, the resolution works great! When I try to apply the settings, though, it doesn't work. The resolution doesn't change, and there is no error message. No amount of reloading "X" or restarting will fix this. Hopefully this will help you understand what could be happening.

---

### Post by salviablue on 2007-11-20
Hi, I  hope you managed to get this problem sorted.
Any way I`m a complete Linux newb and I had the same problem. I found this post though that sorted out my problem! So if anyone else has a similar prob I hope this wil sort it.
[http://cybernetnews.com/2007/10/20/install-and-enable-restricted-drivers-in-ubuntu/](http://cybernetnews.com/2007/10/20/install-and-enable-restricted-drivers-in-ubuntu/)

---

