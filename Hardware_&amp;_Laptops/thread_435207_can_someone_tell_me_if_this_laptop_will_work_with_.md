---
title: "can someone tell me if this laptop will work with linux?"
date: 2007-05-06
forum: Hardware &amp; Laptops
---

### Post by ice60 on 2007-05-06
hi, i want to get this laptop tomorrow but i have no idea if it's compatible with linux, how can i find out if everything will work OK?
[http://www.dixons.co.uk/martprd/product/seo/673381/?int=hphot4](http://www.dixons.co.uk/martprd/product/seo/673381/?int=hphot4)

---

### Post by K.Mandla on 2007-05-06
Is it in a store? or is it Internet-order only? I was thinking you could take the live CD to the store and try it out.

---

### Post by FishRCynic on 2007-05-06
how similar is the chipset to the HP DV9205 ?

---

### Post by tyler22 on 2007-05-06
> **K.Mandla said:**
> Is it in a store? or is it Internet-order only? I was thinking you could take the live CD to the store and try it out.


Thats what I would recommend. Also, many stores have a 14 day return policy. So if you get the laptop and you find that something just will not work running ubuntu you may return it.

---

### Post by ice60 on 2007-05-06
thanks for the help :)  there are a few places that are selling that model at a discount tomorrow, at least i think they are lol.

i have given wireless a 'wide berth' and just used wired connections mostly so i have no idea what i'll need to do to test it if i take a livecd :confused: 

is it likely i won't need to download anything and the driver will be included with the livecd? or will i have to take a list of chipsets and see what it's using? i have no idea. can i just run iwconfig :|

can someone tell me in simple steps how i'll know if it will work with a livecd? or is there a link i can read that will explain it? thanks.

[color=blue]EDIT[/color] btw, i've got loads of livecds, would it be better to try with knoppix first - is there a livecd that's easy to get working with laptops? it's the wireless i'm worried about incase i haven't made it clear lol

---

### Post by K.Mandla on 2007-05-07
Take two or three; what works with one live CD might not with another.

In general, *iwconfig* and/or *ifconfig* from the terminal should at least tell you if it recognizes the card. You could also look inside /etc/network/interfaces and /etc/iftab, once you're in a live environment. 

Ideally you could take a USB drive with you and pipe the output from all those commands -- as well as *lspci -vvv* and *lshw* -- to text files to take home. Then you can do some research and find out how much work it would be. :D

---

### Post by iLoVe.cF- on 2007-05-07
The laptop is really nice for linux.. but.. Check for what kind of Wlan card it got.. only thing that can **** ya up.. a wlan card cost 7 usd for a nice one.. i use intel 2200 BG wlan card and worked outta the box :)

---

### Post by ice60 on 2007-05-07
great, thanks for all the help:) i'll see if i can use the internet in the shop to lookup things :D

---

### Post by jespdj on 2007-05-07
I normally run Ubuntu only on my desktop computer, but I also have a laptop from work (an IBM ThinkPad T42). Just for fun I tried if it could run Ubuntu. Booting Ubuntu 7.04 from a Live CD was no problem at all and also wireless networking works right out of the box. In the top right of the desktop, there are some icons (next to the clock) for networking. I can see a list of about 13 (!!) wireless networks when I did this at home (looks like a lot of my neighbours have wireless networks!).

So when you boot Ubuntu 7.04 a laptop with WiFi you should be able to see there if wireless networking works.

AFAIK wireless networking is one of the things that has been improved a lot on Ubuntu in the latest version.

---

### Post by ice60 on 2007-05-07
> **jespdj said:**
> I normally run Ubuntu only on my desktop computer, but I also have a laptop from work (an IBM ThinkPad T42). Just for fun I tried if it could run Ubuntu. Booting Ubuntu 7.04 from a Live CD was no problem at all and also wireless networking works right out of the box. In the top right of the desktop, there are some icons (next to the clock) for networking. I can see a list of about 13 (!!) wireless networks when I did this at home (looks like a lot of my neighbours have wireless networks!).

So when you boot Ubuntu 7.04 a laptop with WiFi you should be able to see there if wireless networking works.

AFAIK wireless networking is one of the things that has been improved a lot on Ubuntu in the latest version.

great, thanks. i'm going to the shops now :D

i've got about 5 livecds with me lol. i'll probably get thrown out of the place :lolflag:

---

