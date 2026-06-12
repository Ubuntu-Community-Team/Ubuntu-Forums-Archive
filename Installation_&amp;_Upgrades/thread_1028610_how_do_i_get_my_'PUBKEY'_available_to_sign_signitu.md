---
title: "how do i get my 'PUBKEY' available to sign signitures??"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by shadako17 on 2009-01-02
Hi, im pretty much completely new to Ubuntu, and linux for that matter,and have Ubuntu 8.10, and was wondering how to get this PUBKEY thing working to get signitures, in turn to get apt-get update to work, in turn to get my Java working properly.:confused:. maybe i should title this 'how to get my java working', but this seems more realible to me. right now i found out a little from a friend and in the terminal I typed...

shadako@shadako-desktop:~$ sudo apt-get update

...and got a lot of stuff looking good...
but then got this...

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems

is there any way for anyone to help me? if there is, i would be very grateful :D

---

### Post by Partyboi2 on 2009-01-02
You should be able to add the key from the terminal.
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
then
```
sudo apt-get update
```

---

### Post by shadako17 on 2009-01-02
thank you very much! but i stil cant use java, can you help me? (im bad at doing stuff by my self) :)

---

### Post by Partyboi2 on 2009-01-02
What problem are you having with java?

---

### Post by shadako17 on 2009-01-02
i can download java over and over again and get new versions, but it just wont work with my games and assuming my hard drive (which cant be mounted)

it happend when my comp crashed one day...so yeah :(

---

