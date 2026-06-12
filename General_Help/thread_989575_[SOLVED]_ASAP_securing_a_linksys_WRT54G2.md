---
title: "[SOLVED] ASAP: securing a linksys WRT54G2"
date: 2008-11-21
forum: General Help
---

### Post by Stargazer989 on 2008-11-21
how do i secure a linsys wireless broadband ... thing ?

---

### Post by rlprice on 2008-11-21
Do you know how to log into your router? What firmware are you running?

---

### Post by Stargazer989 on 2008-11-21
firmware ?
if you mean Operating system; i'm running Ubuntu 8.04.
it came with a cd, but i can't seem to 'cd' to it's directory.

---

### Post by rlprice on 2008-11-21
No, on your router. You need to log into 192.168.1.1

with blank username and admin as the password.

---

### Post by newbee70 on 2008-11-21
> **Stargazer989 said:**
> how do i secure a linsys wireless broadband ... thing ?

When you first setup your router.

1. make sure you are connected via rj45 cable.
2. in your web browser enter 192.168.0.1 or 192.168.1.1
3. enter the user name and password that came with your router.
   I think it was admin when I got mine.
4. the router configurations will come up. and guide you through the setup.
5. change the user name and password as the first step.

---

### Post by Stargazer989 on 2008-11-21
is this where i enter the stuff to make it so that anyone who tries to connect with need a pass ? (image is attached)

---

### Post by Stargazer989 on 2008-11-21
ok... i've made it connect.. but now i can't get my Asus Eee PC 900a to connect. any other network i click on brings up the pass window but when i connect to mine it brings up some Wireless Connection with with a log tab and nothing happens.
any ideas ?

---

### Post by plucky on 2008-11-22
Try editing the wireless networks information and deleting the connection information for your network so that when it reconnects,it will have to ask for a passphrase.Then restart networking with ```
sudo /etc/init.d/networking restart
```


Hope this helps

Good Luck

---

### Post by newbee70 on 2008-11-22
> **Stargazer989 said:**
> ok... i've made it connect.. but now i can't get my Asus Eee PC 900a to connect. any other network i click on brings up the pass window but when i connect to mine it brings up some Wireless Connection with with a log tab and nothing happens.
any ideas ?

left click on the network connection icon "upper right toolbar" and see if your wireless connection is activated.

---

### Post by Stargazer989 on 2008-11-22
you guys must be talking about Ubuntu-eee... i wish i could use it on my Eee pc 900a, but i can't get it to boot from Flash drive (may have something to do with the flash drive having u3(google, if you don't know))

screenies attached (i'm BigBear)

---

### Post by Stargazer989 on 2008-11-22
i retract my previous statement of not being able to get my asus eee pc 900a unbootable. i hadn't realized that i had to hold the power button plus the esc button whilst it boots. even with this being said, i can't seem to figure out what to do and how to boot my asus eee pc 900a.

---

