---
title: "Installation bash"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by kristensson.jonas on 2009-04-13
Hello!
Ive started to sell some computers to beginners and I use ubuntu as the main OS. When I install ubuntu i remove packages i think is unecessary for the user and add other programs before I hand the computer over. However as the number of customers grow larger it starts to get quite time consuming to do this manually. I was thinking of writing a bash file that removes the package x and adds the package y and so on. I therefore have 2 questions.

First what is the bash command for adding a package from the apt library or from a web adress. And whats the command for removing one?

Second, is there anyway to include this bashfile in the installation script so when i install ubuntu this bashfile runs at the end of the installation and updates the system automatically? and is it possible to burn this on a cd as a sort of customized installation disc?

Best regards
Jonas):P

---

### Post by glotz on 2009-04-13
May I suggest you do an image file and then restore it onto the disks of the boxen you sell.

First, perpare an install the way you like it, remove and install things, then make an image of it and then use this image.

[http://www.partimage.org/](http://www.partimage.org/)

Best of luck with your enterprise!

---

### Post by kristensson.jonas on 2009-04-13
Thank you! 
Never heard of this utility but it sounds great! How much of my changes will it copy? Will it for example copy icons positioned on the desktop and favorites stored in firefox?

/Jonas

---

### Post by Aubergines on 2009-04-13
It should copy everything

---

### Post by glotz on 2009-04-13
Yeah, the all of it, bit for bit.

---

