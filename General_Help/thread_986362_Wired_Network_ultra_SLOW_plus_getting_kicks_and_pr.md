---
title: "Wired Network ultra SLOW plus getting kicks and problem COMPILING"
date: 2008-11-18
forum: General Help
---

### Post by UbunistWarrior on 2008-11-18
Idk if this is the right place to post but i see it as "General help"? xd
Anyway heres my problem when i had 8.4 all was ok 10000 times more faster than windows in all the things, But when i upgraded to 8.10 i start having problem the first was compiling, For some rason on ubuntu 8.10 i can't use a simply function on c++ wich is "fread" for read things on the binary wich is really used on programs, The error is 
```
ignoring return value of &#8216;size_t fread(void*, size_t, size_t, FILE*)&#8217;, declared with attribute warn_unused_result

```
For some reason on ubuntu 8.10 is ignoring the return value of fread, I had to use Windows to compile it and then i formated another HD with Debian for compile it and all worked ok, But i want ubuntu because i think ubuntu is more user friendly and got more support like this great forum, Anyway the other problem i have is the internet, When i upgraded i start having problem with the connection i suppose to have 10 mb internet and when i'm navigating i saw the internet is so damn slow, so i decide to make a speedtest and it tell me i got 1.6mb LOL? It's so damn annoying, And thats not all, I host a small game and all the persons are getting mass kicks so i want to know if theres any fixes for that or i have to downgrade to 8.4 forever? Thanks on advance hope a fast reply...

BTW Here my ifconfig -a of the connection i use "eth0"
```

eth0      Link encap:Ethernet  HWaddr 00:1a:4d:9e:e8:41  
          inet addr:--.---.---.---  Bcast:--.---.---.---  Mask:---.---.---.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:1045948 errors:0 dropped:0 overruns:0 frame:0
          TX packets:793566 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:451503931 (451.5 MB)  TX bytes:78987240 (78.9 MB)
          Interrupt:254 Base address:0x4000 

```

Im not so linux expert but i think theres a problem, When i had 8.4 i never get that line
```
Interrupt:254 Base address:0x4000 
```
P.S. I'm using a Motorola modem Version SBV5120

---

### Post by UbunistWarrior on 2008-11-18
bump

---

### Post by Yellow Pasque on 2008-11-18
The gcc 4.3 in Ubuntu 8.10 is very strict. You can install gcc 4.2 and change the gcc symlink in /usr/bin/ to point to gcc-4.2

BTW, are you using fread properly and not ignoring its return value?

---

### Post by UbunistWarrior on 2008-11-18
> **Temüjin said:**
> The gcc 4.3 in Ubuntu 8.10 is very strict. You can install gcc 4.2 and change the gcc symlink in /usr/bin/ to point to gcc-4.2

BTW, are you using fread properly and not ignoring its return value?

Ye im using the fread properly, I got it working on windows and on Debian :/ anyway ill try with gcc 4.2 and edit this post...

EDIT:
Worked great thanks, Now i just have the internet problem...

---

