---
title: "Hard Drive Data Encryption"
date: 2005-12-02
forum: General Help
---

### Post by eli_d on 2005-12-02
Hey, everyone.  Just wanted to first say thanks for the great distribution and the excellent forums/wiki.  To this point, they've helped me solve every problem I've had.

I read the Wiki articles on encrypting hard drives and file systems, but they were unfortunately too much for a somwhat newbie like me to handle.  

I was wondering if anyone could point me in the direction of any sort of SIMPLE solution for encrypting at least one directory or partition under linux/ubuntu.

I would really like a place to store information that would be a little more difficult to get to than just removing my hard drive from my system and putting it into another machine, should it be stolen (I've already had two computers stolen in the last three years). 

I don't need a "world government proof security vault."  Just something that will deter most slightly computer literate theives from spending the time it takes to get to my data.

Any direction would be greatly apprectiated...

:confused: Eli

---

### Post by cgjones on 2005-12-02
You might want to check out Seahorse at [http://seahorse.sourceforge.net/](http://seahorse.sourceforge.net/) . It should be available through Synaptic.

---

### Post by docomo on 2005-12-02
I use cryptsetup myself but perhaps that is not as simple as you want it. It's not quite as hard as it seems though.

The new version of truecrypt has a linux version and you can get it compiled for Ubuntu on their website. I have only used it in Windows but found it relatively easy and it worked well. [http://www.truecrypt.org/]("http://www.truecrypt.org/")

---

### Post by eli_d on 2005-12-02
hmmmm... i've done a little more research on cryptsetup and think i can handle it... also truecrypt looks promising.

thanks...

eli

---

### Post by arpunk on 2005-12-02
take a look at: [http://loop-aes.sourceforge.net/loop-AES.README](http://loop-aes.sourceforge.net/loop-AES.README), ive used it on my laptop when hd was still alive.

---

### Post by docomo on 2005-12-02
Depending on your level of paranoia you might want to encrypt swap as well. If you install cryptsetup you can find instructions in /usr/share/doc/cryptsetup/CryptoSwap.HowTo

I find cryptsetup easier to use than loop-aes.

---

### Post by arpunk on 2005-12-02
Indeed, cryptsetup its a lot easier and faster to setup, however you might want to take a look at this:

[http://deb.riseup.net/storage/encryption/benchmarks/dmcrypt-v-loopaes/](http://deb.riseup.net/storage/encryption/benchmarks/dmcrypt-v-loopaes/)

For comparison between them.

---

