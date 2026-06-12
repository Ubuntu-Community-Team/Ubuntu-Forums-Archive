---
title: "Not getting hardware-acceleration from ATI-graphicscard"
date: 2012-07-13
forum: Hardware
---

### Post by Kols on 2012-07-13
So, I just installed Tuxracer (for those who doesn't know, it's a racing-game similar to Mariocart), only to discover extreme choppiness.

Now, this shouldn't be, given that I'm running **Intel i5 @ 3300MHz**, a sufficient ATI-graphicscard (good enough to run ME3 smoothly in Windows), and **12GiB RAM**.
OS is Ubuntu **12.04 LTS 3.2.0-26-generic-pae-i686** (yeah yeah, I know I should install 64-bit).
**Output of  $lsb_release -a says that "Graphics" is VESA:RV770**

In proprietary drivers, it says that the driver **"ATI/AMD proprietar FGLRX graphicsdriver"** is installed, and in use.

What could possibly be the issue here?

I will provide full name of graphicscard if nescessary (I didn't bother now, cause then I'd have to boot up Windows=P )

Thanks in advance for any help!=)


SOLVED

Solution was to upgrade to 64-bit, and just do the install from proporitary drivers. 
Then, I used command 

#sudo aticonfig --adapter=all --odgt

which prompted me to first do

#sudo aticonfig --initial

Things now seem to be stable and working.

Also, guide in below post is more meant for laptops running dual graphics, and should NOT be used for desktops. I may have done something wrong following the guide, but the result from using it was reinstall of system. Oh well.

---

### Post by N0oki3 on 2012-07-13
Hi. Follow this [guide](http://ubuntuforums.org/showthread.php?t=1930450)

---

