---
title: "ssh + keychain"
date: 2008-08-13
forum: General Help
---

### Post by boblemur on 2008-08-13
hey this is kind of networking and kind of security so i didn't know where to put it...but i think general is suitable...

hey all, im not sure how the keychain manager works... or even if its the right tool to use for my problem:

i have 2 computers... laptop + desktop

desktop has a ssh server on it.
laptop :client(obviously) 

i have a dns so i can get my ip and i have port forwarded ssh port to my desktop.

i am trying to ssh into my desktop computer without a password, but instead use public key auth.. so i have my laptop's public key stored on the desktop in authorized_keys. and i have my private key on my laptop....


i want to know how to:

-not make keymanager for my password every time, but be unlocked at login.
-not have no password (so if my public key becomes compromised without me knowing people cant use it).

i was wondering if system > preferences > encryption and keyrings was able to achieve this.

thanks for any help in advance

---

