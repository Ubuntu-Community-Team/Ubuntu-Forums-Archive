---
title: "wi-fi not available after hibernate"
date: 2009-09-05
forum: Hardware
---

### Post by jds340 on 2009-09-05
I've been using Ubuntu 9.04 on my ASUS X58 Series laptop for months. Everything works fine except for one thing....

If I hibernate the laptop rather than closing it down, then when I restart it the Wi-Fi connection is lost and can't be re-connected. In the display of all Wi-Fi signals nothing shows up. It's a minor irritant, but one I'd like to get sorted out. When I get home after using my laptop I can't just open it up and start from where I left off, I have to restart the computer. Which can be very irritating if I then have to restart a slow to load application like Eclipse. 

Any suggestions, maybe a driver setting somewhere or something?

Ta

John Small

---

### Post by ImbaDaimon on 2009-09-05
I had the same problem.

Recently while i was searching for solution i click on **Network icon** and after **Connect to Hidden Wireless Network..** at the windows which apear **select your connection** and after press **Connect** button.

This should be work.

---

### Post by sergiom99 on 2009-09-05
sort of same thing happened to me, but I removed NetworkManager and installed Wicd and works much better.
Another way was to restart networking
```
sudo /etc/init.d/networking restart
```

---

