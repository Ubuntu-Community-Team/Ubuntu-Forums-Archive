---
title: "Acer aspire 5742g Bluetooth not working"
date: 2011-01-15
forum: Hardware
---

### Post by abrasax on 2011-01-15
I have this laptop with ubuntu x64 installed inside windows 7 x64. Everything is working nicely except bt. There is a fn switch for wifi and bt together, so it loops through all the possible settings. when i press it turn on button shows up in bluetooth preferences but it either dissappears when i press the button or just dissappears instantly. I have atheros bluetooth i think but cannot be sure of the model.

---

### Post by TuxOfGermany on 2011-02-15
Same to me. I just can say that I won't ever buy any Acer computer again. And because of the problem with the nvidia drivers I won't buy any computer with nvidia graphic card. That's all ********.

---

### Post by abrasax on 2011-02-15
I don't know of any problem with nvidia. Solution for bluetooth is fairly simple.
there are two files in /lib/firmware/ folder. One is ath3k-1.fw and the other is ath3k-2.fw. Rename the first into something else and the second ath3k-1.fw. That fixed the bluetooth issue for me.
so for example 
ath3k-1.fw -> ath3k-1b.fw
ath3k-2.fw -> ath3k-1.fw

If you don't have graphics support just go to System->Administration->additional drivers and install the driver provided there.

---

### Post by TuxOfGermany on 2011-02-23
Sorry for answering so late
**Thank you so much!!!! **It works very well. :)

The Nvidia problem is with optimus technology. [http://www.nvnews.net/vbulletin/showthread.php?t=144750](http://www.nvnews.net/vbulletin/showthread.php?t=144750)

---

### Post by abrasax on 2011-02-25
I don't have that problem, because I don't have optimus. It was never wired on my model. I only have nvidia graphics.

---

### Post by btermeli on 2011-04-02
The solution doesn't work for me, any other idea?

---

### Post by apoorvumang on 2011-07-23
Tyvm, worked for me!
However, I didn't find a file named ath3k-2.fw, just renaming the first file worked.

---

### Post by der011 on 2011-07-28
So cool, works also for Acer Aspire one D255

---

### Post by sumith_p on 2011-08-25
> **abrasax said:**
> I don't know of any problem with nvidia. Solution for bluetooth is fairly simple.
there are two files in /lib/firmware/ folder. One is ath3k-1.fw and the other is ath3k-2.fw. Rename the first into something else and the second ath3k-1.fw. That fixed the bluetooth issue for me.
so for example 
ath3k-1.fw -> ath3k-1b.fw
ath3k-2.fw -> ath3k-1.fw

If you don't have graphics support just go to System->Administration->additional drivers and install the driver provided there.
Hi...
i am using acer aspire 5750...
i renamed the first file....
ath3k-1.fw -> ath3k-1b.fw
but i couldnt find the 2nd one....
still bluetooth not working....

---

### Post by alighanbari on 2011-08-29
[LEFT]I have also problem with Bluetooth Suite.When i run it, nothing happens! I reinstalled driver in control panel, but still not working.I have[SIZE=4]**_[COLOR=Orange] ![/COLOR]_**[/SIZE] sign on its driver when you look it in device manager of control panel.I will try to change the name of m. a. files/ but i dont know its position. I wil try to find it.Anyone has a good solution for it?thanks a lot.
[/LEFT]

---

### Post by sumith_p on 2011-09-23
haah...finally bluetooth is working for me....installing older bluetooth version didnt do me any good..
i renamed the file mentioned in the thread then again changed to original name.....
thanks for the tip...

---

### Post by poobathy on 2012-03-12
i am using acer aspire 5742
i got first file and i renamed 
but there is no use...
still its not working
plz.. tell me a solution

---

### Post by sumith_p on 2012-03-12
> **poobathy said:**
> i am using acer aspire 5742
i got first file and i renamed 
but there is no use...
still its not working
plz.. tell me a solution

try turning off and on your wireless button.....my 5742 wont automatically turn on bluetooth.....i need to press  FN +F3....inorder to turn on my blue tooth.....

---

