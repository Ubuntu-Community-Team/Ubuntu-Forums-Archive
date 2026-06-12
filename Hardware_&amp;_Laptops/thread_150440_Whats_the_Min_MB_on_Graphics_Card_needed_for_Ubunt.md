---
title: "Whats the Min MB on Graphics Card needed for Ubuntu?"
date: 2006-03-26
forum: Hardware &amp; Laptops
---

### Post by LateNighter on 2006-03-26
I was wondering about something.

 What is the Min required MB of Onboard Memory for a Graphics Card in Ubuntu, and it still run Games like TuxKart?

 I heard 32MB was the min?

 But I was thinkin of a Nvidia MX440 64MB DDR, 8x AGP Card.:confused: 

 I'm looking at replacing a Graphics Card on another of my PC's, and wasn't going to Spend big $$$$$ on it if I did'nt have to.

 I Give up on trying to run Windows on a Dual Boot, it fouled up on Me again.
 And we all know if you reinstall Windows, you have to redo Ubuntu as well.

 The only reason I kept Windows around to begin with is because of a couple of games I like to Play.
 And these Games just ain't WORTH the Hassle anymore.

 And at the Sametime while High End Graphics and other Hardware are nice and Required to run Windows.
 Their not required to run Ubuntu and Linux as a whole, Therefore allowing Someone who Only runs Ubuntu some to SAVE some fairly decent $$$$$$$$$$$$....

 But in the last 2 months since I reinstalled it, I've not had it running Windows for more then 15hrs total time, just Playing Games, I don't even let Windows hook to the Web.
 And it still Frigs Up:twisted: 

 So in the VERY near future I'm redoing my Whole HD and this time Windows ain't seeing one Block on my HD....:KS 

 The Best part in the 2 months i've had it runnin, Ubuntu has NEVER once fouled me up, ONE IOTA...    Long Live Ubuntu   Arise Linux....:twisted: :mrgreen:

---

### Post by amohanty on 2006-03-26
>  And we all know if you reinstall Windows, you have to redo Ubuntu as well.

Umm. Actually no. All you need to do is to restore GRUB. The easiest way is here:
[http://ubuntuforums.org/showthread.php?t=24113&highlight=restore+GRUB](http://ubuntuforums.org/showthread.php?t=24113&highlight=restore+GRUB)


As to your original ques. tuxkart will run fine on the NVIDIA 64MB. I would however suggest a 128MB card if your wallet can handle it.

HTH
AM

---

### Post by LateNighter on 2006-03-26
[QUOTE=amohanty]Umm. Actually no. All you need to do is to restore GRUB. The easiest way is here:
[http://ubuntuforums.org/showthread.php?t=24113&highlight=restore+GRUB](http://ubuntuforums.org/showthread.php?t=24113&highlight=restore+GRUB)


As to your original ques. tuxkart will run fine on the NVIDIA 64MB. I would however suggest a 128MB card if your wallet can handle it.

HTH
AM[/QUOTE]

 Thanks for the quick reply.

 And I'll go and check out the Post about the Grub Menu.

 I thought the games would run decent on a 64 MB Card.

 But you hit it on the head with the Wallet thing, a 128 MB Card would be stretching the $$$$$$$$$$$$ a little to thin at the moment.
 BUT I'm Grateful for the imput.:D

---

### Post by az on 2006-03-27
Tuxkart works fine on a card with 8 megs of ram.

I can not get it to work on anything with less.

You may need to set your maximum resolution to something lesser (like 1024x768 if it is defaulting to 1600x1200)  That will chew up your card's ram and not leave you enough ram for hardware acceleration (dri).  You can also lower the color depth to decreas it's memory useage)

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start

---

### Post by mips on 2006-03-27
What's your budget for a gfx card ??? People can then recommend cards in that price range.

---

