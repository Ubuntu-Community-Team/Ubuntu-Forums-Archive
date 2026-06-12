---
title: "Ubuntu 32 bit recognizes only one 2gb memory stick but ovlerlooks the other one"
date: 2010-11-15
forum: Hardware
---

### Post by kerala on 2010-11-15
I use ubuntu in a 32 bit architecture with a amd64 processor. My problem is that ubuntu only recognizes one of two 2 gb memory sticks. Therefore I can only work with 2 gb. Is this normal for a 32 bit architecture and how can I change it?

---

### Post by irv on 2010-11-15
I am running 34 Bit Ubuntu and have two 2 Gb memory sticks and I am recognizing 3.8 Gb.
[ATTACH]175673[/ATTACH]

---

### Post by TBABill on 2010-11-15
No it is definitely not normal. You can have up to about 3.8GB or so appear out of the 4. That's the upper limit so if you had more you would need a 64 bit system or the PAE kernel. But yours could be as simple as one of the RAM chips coming out of the slot a little bit. 
 
Do you have Windows or another distro on another partition to check? What does your BIOS say you have (if it looks at the RAM)?

---

### Post by kerala on 2010-11-15
Okay, it is not normal, good to know. I ve made a memtest and the result was over 13000 errors so I removed the damaged memory stick. But I dont know when I buy a second memory stick if this stick will be recognized. I will take a look into my bios.

---

### Post by irv on 2010-11-16
> **kerala said:**
> Okay, it is not normal, good to know. I ve made a memtest and the result was over 13000 errors so I removed the damaged memory stick. But I dont know when I buy a second memory stick if this stick will be recognized. I will take a look into my bios.

Just match the one good one. I had my memory go bad in a laptop a few years ago, and the memory manufacture sent me new memory at no charge, they even paid the shipping, and the laptop was over 4 years old. They told me it had a life time warranty. And don't forget call the manufacture they should stand by their product. 
Also have you tried to re-seat the memory stick? maybe is is not set in right and not making contact with the socket.

---

