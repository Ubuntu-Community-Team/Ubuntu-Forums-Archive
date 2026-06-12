---
title: "Problems with Nvidia Geforce 310M (Optimus)"
date: 2011-05-15
forum: Hardware
---

### Post by skryter on 2011-05-15
Dear all,
 
I've got a new laptop, an Asus K42j with an Nvidia Geforce
310M in combination with an Intel graphics card (the so-called Optimus
technology). I installed Ubuntu 10.04 64-bit, and everything worked
perfectly. After installation, Ubuntu offered me to install the
proprietary Nvidia driver to improve graphics performance. I did, and
after installation I was stuck with a black screen.
 
So I did some Google research and found out that the Optimus setup
with an Intel graphics card combined with the Nvidia card is not
supported at all. I was not able to get rid of the Nvidia driver (for
some strange reasons it is not possible to get any virtual tty via
ctrl-alt-F1), so I did a complete re-install __- of course without
installing the Nvidia driver again.
 
Now I would like to learn about the options I have with this laptop. I
don't need the automatic switching between the two cards, I do not
mind rebooting while switching graphics card.
 
* Is it possible at all to use the Nvidia card?
 
* Is it possible to switch off the Nvidia card using only the Intel
  part (for saving some power)?
 
* Will things improve with Ubuntu 10.10?
 
The information I found on Internet was confusing me and it did not
work for me either (e.g. blacklisting the Intel driver). Do you have
any hints for me? (I'm not really a Linux expert so I would appreciate
some verbosity ...).
 
Many thanks in advance,

---

### Post by N2G(bn#7+ on 2011-10-16
I'm in exactly the same position. I wouldn't mind rebooting if it meant I could use the Nvidia card occasionally for graphics intensive applications or games. 

I'm using an Asus UL30JT and currently installing Ubuntu 11.10.

---

### Post by concomitantelegy on 2011-10-16
> **skryter said:**
> 
Asus K42j with an Nvidia Geforce 310M in combination with an Intel graphics card (the so-called Optimus technology)
 
Now I would like to learn about the options I have with this laptop. 

* Is it possible at all to use the Nvidia card?
* Is it possible to switch off the Nvidia card using only the Intel
  part (for saving some power)?
* Will things improve with Ubuntu 10.10?
 

A [search of the forums]("http://ubuntuforums.org/search.php?searchid=83504999") shows a [post by 3602]("http://ubuntuforums.org/showpost.php?p=10304516&postcount=1"), who describes Optimus in two ways. Either both cards work together, with the 310M - the more powerful card - doing the grunt work, or the integrated working alone. So you can't use only the discrete card, and you can't disable the integrated graphics. Five months later, 3602 updated his post.

There is a "[Bumblebee PPA]("https://launchpad.net/%7Ebumblebee/+archive/stable")" that might be useful. Please try it and report back.

EDIT: I replied to a thread started five months ago. Sorry.

---

### Post by realruntime on 2011-10-18
Yeeehaa! Bumblebee works great on my Travelmate TM8372GT! Thousand thanks for this info!

---

### Post by ikotlyarsky on 2011-10-18
I am experiencing same behavior on Lenovo T410 with Nvedia NVS 3100 M card. Any information appreciated.

---

