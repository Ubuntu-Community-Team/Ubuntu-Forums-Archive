---
title: "Help! sound not working on my lenovo n100"
date: 2007-05-15
forum: Hardware &amp; Laptops
---

### Post by LunatikOwl on 2007-05-15
I just installed ubuntu feisty on my lenovo n100 0768FLG and did almost any howto on the net to try to get the sound working

still, the silence is as loud as ever...

i attached here my lspci -vv  output and happily supply anything else.

---

### Post by zanjabeel5 on 2007-05-15
try this
[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG)

scroll down to the sound section

---

### Post by LunatikOwl on 2007-05-15
SUCCESS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

thanks a million!!! it's working like a candy.

now i have a 100% linux compatible laptop!!!!(more or less)

---

### Post by Shogun79 on 2007-05-15
This doesnt work for the C200, so don't try it if you have it.

---

### Post by zanjabeel5 on 2007-05-16
@Shogun79

not true. it works if you have this sound card.
I have the c200 and it fixed it.

anyway it is always a good idea to try.

---

### Post by LunatikOwl on 2007-05-17
> **zanjabeel5 said:**
> @Shogun79

not true. it works if you have this sound card.
I have the c200 and it fixed it.

anyway it is always a good idea to try.

last time i've tried to install a beta alsa driver it completly screwd up my snd-hda-intel, even 
"aplay -l" didn't recognize my card(while previously it did). lucky it was a fresh installation of Feisty, so i did reinstall.

p.s. 
i bought this laptop because i heard it was compatible with ubuntu but in-fact the compatibility test was on another 0768 model. the moral of this story always read the small letters...
p.p.s 
ubuntu community rocks! this is the second time i'm installing a linux, but the first time i'm staying with it(in the first time(suse) my sound and my 3d didn't work and i didn't have anyone to cry to help to...)

---

