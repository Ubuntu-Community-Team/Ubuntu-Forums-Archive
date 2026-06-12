---
title: "Problem with connect to VPS"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by Python1288 on 2009-10-13
Hi I bought VPS Linux server, but i would like remote desktop thought NX Client. Firstly I installed on server ubuntu like this:
```
gpg --keyserver keyserver.ubuntu.com --recv-keys 493B3065 && gpg --export -a 493B3065 | sudo apt-key add -
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install kubuntu-desktop
```

Then I proceed as described in this tutorial:
```
http://forums.techarena.in/tips-tweaks/1191418.htm
```
but it's not work when I try loging to the server via NX Client. Then I try this tutorial:
```
https://help.ubuntu.com/community/FreeNX
```
but I don't receive public key (when I put this code sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2a8e3034d018a4ce) .. 
I am desperat. Please help me with this problem. Thanks. 
btw: sorry for my En and if I gave wrong section..

---

