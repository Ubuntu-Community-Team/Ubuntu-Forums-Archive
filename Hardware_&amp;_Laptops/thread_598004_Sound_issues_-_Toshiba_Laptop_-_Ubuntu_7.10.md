---
title: "Sound issues - Toshiba Laptop - Ubuntu 7.10"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by karlb8 on 2007-10-30
I have a Toshiba A215-S7444 and I am having issues with configuring the sound.  I have tried several different techniques recommended in the ubuntuforums but I have had no luck as of yet.  I have attached the aadebug output.  I was hoping somebody might be able to point me in the right direction.

thx.

-karl

---

### Post by RandyNose on 2007-10-31
I did what this guy did to get my Toshiba A135 going.   Might  I suggest that you try option   # 3 First, as I think that helped my problem back with Fiesty. But I did the whole deal that he did in the post with the URL that I provided on the bottom of the message. And I did      this right after a fresh install of Gutsy Plain vanilla Ubuntu. Hope this helps ya.
R_ 

3.Edit /etc/modprobe.d/alsa-base

Code:

sudo nano /etc/modprobe.d/alsa-base

Scroll down to the bottom using the down arrow key and add

Code:

options snd-hda-intel model=



[http://ubuntuforums.org/showthread.php?t=568463&highlight=No+sound+on+toshiba+laptop](http://ubuntuforums.org/showthread.php?t=568463&highlight=No+sound+on+toshiba+laptop)

---

