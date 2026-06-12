---
title: "Pixelview Play Tv Pro [BT878]"
date: 2005-09-24
forum: Hardware &amp; Laptops
---

### Post by fserve on 2005-09-24
i have this card, Playtv pro (bt878), and i cant hear anything, i use this line:
"sudo modprobe bttv card=37 tuner=2"
and the TVTime show the channel but without sound :/


i've tried others numbers on the 'card', but with no one i got sound...

---

### Post by fserve on 2005-09-26
how i can erase this post?

---

### Post by fserve on 2005-09-27
no one knows?

i've installed the playtv, but i cant hear sound...

---

### Post by pgoya on 2005-10-04
fserve, não sei como te ajudar. Mas caso você consiga resolver o problema, me avise OK? :D

---

### Post by burok on 2005-10-22
In Ubuntu 5.10 you only add 

options bttv radio=1 card=37 tuner=5

to /etc/modprobe.d/aliases

---

### Post by sefs on 2008-01-05
How can I install this card PixelView PlayTV Pro with a conexant bt878 chipset on gutsy.

Thanks.

---

### Post by d90 on 2008-05-10
> **sefs said:**
> How can I install this card PixelView PlayTV Pro with a conexant bt878 chipset on gutsy.

Thanks.


create new file in /etc/modprobe.d and give it name bttv


# i2c
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1
# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
# TV
options bttv card=70 tuner=5 radio=1 pll=1 adc_crush=0


restart ubuntu

if that is not it try to find out more about bttv card codes (probably you have to set other code eg 50...etc, use google if there is no help from this code to find out code you need)

---

