---
title: "How to remotely restart ubuntu"
date: 2008-08-11
forum: General Help
---

### Post by jcapinc on 2008-08-11
Hello,

Alright, I have set up VNC, been using it on vacation for the past couple days and it has been working great!  I love how well it works!

I have been accessing my home desktop Dell (my production machine) successfully and smoothly, but only one time I forgot to enter in the correct password (I set it up for a password, also worked great).  After that one time, I have been getting code 111 when trying to connect, resulting in failure at the point at which the machine should have asked for the password.  I looked up VNC's code 111 and I could net get good information.  

So any help in this would be great. My initial response would be to simply restart the machine or look to see ](*,).  

any help would be great!
k/thx/cya l8r/ttyl

---

### Post by jerome1232 on 2008-08-11
Does the remote machine have openssh-server installed?

If so you can ssh in, reboot the machine or have a look at settings etc.
```
sudo reboot
```

edit: I've seen a few things mentioning to try adding a :1 after the ip address

---

### Post by jcapinc on 2008-08-11
> **jerome1232 said:**
> Does the remote machine have openssh-server installed?

If so you can ssh in, reboot the machine or have a look at settings etc.
```
sudo reboot
```

edit: I've seen a few things mentioning to try adding a :1 after the ip address

yea cant get in via ssh, I did not install that myself, and it is not comming pre-loaded.

Part of my woes also is that I have a buggy netgear router that wont let me remotely manage it.  This means I cannot set it to forward new port numbers to my computer.  I managed to get it set up for vnc (port 5900).  But other than that I only have port 80, which gives me access to my Apache dev server.

so thanks for the idea.  Ive tried telnet and such but the blasted router is a pain.

Thanks for the quick response!

---

### Post by Hyper Tails on 2008-08-11
i think this one also works

```
sudo poweroff
```

---

