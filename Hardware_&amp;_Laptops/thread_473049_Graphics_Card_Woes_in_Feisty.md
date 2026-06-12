---
title: "Graphics Card Woes in Feisty"
date: 2007-06-13
forum: Hardware &amp; Laptops
---

### Post by RelativelyQuantum on 2007-06-13
Hi all.

The other day I opened up Aptitude in Terminal to try to take care of some trouble I was having with Beryl - graphics card compatibility - and reset my card's manufacturer to what it should have been, according to the technical specs of my computer. Now when I boot into my Ubuntu partition (1/3 of my HDD) there is only textual input/output, and I get a message which says that no screen is detected.

The real question is, how can I reset my graphics card from terminal? I suppose since the trouble arose there, I should be able to fix it from there, but my attempts have turned up nothing.

I'll try running aptitude again to set the computer to detect a different card. Please let me know if there is anything else I should be doing. Responses would be appreciated as this is extremely incapacitating :(

Cheers,

RelativelyQuantum

---

### Post by neptho on 2007-06-14
dpkg-reconfigure xserver-xorg - select VESA or VGA.

---

### Post by RelativelyQuantum on 2007-06-14
Thanks alot - I'll try that.

---

### Post by RelativelyQuantum on 2007-06-14
This might be a really basic question, but what's VESA? :(

---

### Post by RelativelyQuantum on 2007-06-15
Ok; I tried it. I got messages saying that neither VGA nor VESA were installed. What now?

---

### Post by Syke on 2007-06-15
sudo apt-get install xserver-xorg-video-vesa

---

### Post by RelativelyQuantum on 2007-06-15
Though, won't that just build drivers for my screen? Everything worked before, aside from Beryl's complete non-functionality; would that indicate that it wasn't recognizing my graphics card? (Intel GMA 900)

---

### Post by Syke on 2007-06-17
Oh, if you have an Intel GMA you'll want to install the intel driver.

```
sudo apt-get install xserver-xorg-video-vesa
```

and then reconfigure X

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and hopefully you can select "intel" from the list.

---

