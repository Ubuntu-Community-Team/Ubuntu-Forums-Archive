---
title: "ssh help with public keys"
date: 2008-11-10
forum: General Help
---

### Post by Roque2 on 2008-11-10
okay this is my problem, I am using a windows xp computer at work at access my linux computer at home. On the windows xp computer I am using putty and tightvnc. I have been reading tons of howto's to try and get this ssh server secure, but all the how to's have both computers using linux and are a bit confusing. Would somone pls be able to show me how to generate a private public key on my windows computer and send it to my linux server at home.

---

### Post by Roque2 on 2008-11-10
Okay I have used putty gen to create the pairs of keys, and have used pageant to add my private key. But I am having problems with the public key. Since I am sitting next to the linux computer I am adding the public key to a usb drive and adding it to the .ssh folder in my home directory, and editing the private key so that it can be used in linux so a tutorial has stated. [http://kutzooi.co.uk/howto.php?005]("http://kutzooi.co.uk/howto.php?005") Now it also says to secure your server up by not allowing passwords, so i do that and restart the ssh server. Now when I use putty to log onto the server it just askes me for login then the password. Whats the deal, I am lost.

---

### Post by chk9 on 2008-11-12
> **Roque2 said:**
> I am adding the public key to a usb drive and adding it to the .ssh folder in my home directory

Did you add the public key in .ssh/authorized_keys ?

---

