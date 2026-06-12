---
title: "Screen Resolution not optimum on 15 inch LED"
date: 2010-05-04
forum: Hardware
---

### Post by zeiger on 2010-05-04
Hi All,
I recently installed Ubuntu 10.04 on my Gateway ID 58 laptop.
I am very new to Linux, Ubuntu, so I'd appreciate some help on this.

My Gateway ID58 laptop has a dedicated NVidia GeForce 105M graphics card. The official website for the card ([http://www.nvidia.com/object/product_geforce_g105m_us.html](http://www.nvidia.com/object/product_geforce_g105m_us.html)) says that the maximum resolution supported is 2048x1536.
After going to System -> Administration -> Hardware Drivers, I installed the NVidia Accelerated Graphics Driver which is recommended by Ubuntu.
This installed successfully and I can see System -> Administration -> NVidia X Server Settings. I can also use the "Extra" option in the Visual Effects screen, which means that the recommended driver installed successfully.
But in the NVidia X Server Settings -> X Server Display Configuration, the maximum resolution I can select is only 1366 * 768, which is pretty low for my 15 inch monitor (I'm used to higher resolutions).

So how do I get a higher resolution? Have I missed something? Should I install the drivers supplied from the NVidia website instead?

Thanks,
Zeiger

---

### Post by techunit on 2010-05-04
What is the screen resolution on your 15 inch monitors? If it is lower than the maximum supported by the graphics card that becomes the highest possible screen resolution.

---

### Post by peter3 on 2010-05-04
And, in addition, if you are working on old hardware like mine, you may be limited by the video card.  I have old towers connected to a new display and can only get the maximum of the card, not the display.
There are limits everywhere.

---

### Post by techunit on 2010-05-04
Note that 1366 * 768 is pretty average for a 15inch notebook perhaps you are mistaken.

---

### Post by oldsoundguy on 2010-05-04
The NVida driver is trash right now!  NVida is a day late and a dollar short to the release party! Use the Ubuntu default driver instead of the restricted driver. Much better resolution .. yes, you will not have 3-D graphics for games and some of the graphics bells and whistles, but it will work in landscape and give you a LOT more in choices for your resolution.
You will have to wait on NVida to remove it's head from that dark place and get the new driver out and INSTALLABLE.  
(I lost the ability to rotate the screen along with the higher resolution when I migrated from 8.04 to 10.04 .. and no FIX at present.)

---

### Post by techunit on 2010-05-04
This shouldn't be too much of a problem seeing that ubuntu hasn't been develped for games to well, but those who do game on it will enjoy it.

---

### Post by zeiger on 2010-05-12
Thanks guys,
 1366 * 768 is infact, what I get with the pre-installed NVidia driver for Windows too. sorry for the post.
But I still have a feeling that things looks smaller in Windows 7 than in Ubuntu 10.04. :(
May be I should install some themes :)

---

### Post by techunit on 2010-05-16
Change Font Sizes to 8

---

### Post by oldsoundguy on 2010-05-16
A follow up .. MY problem mentioned above turned out to be a bloated xorg.conf  file as I had UPDATED and a lot of junk got dragged along ....ran remove/re-booted/and the DEFAULT driver did everything that I (personally) wanted .. have NOT tried the restricted driver after the fix as I do not game nor do I need eye candy, but suspect that as it is a cleaned up file, it should work just fine.

---

### Post by techunit on 2010-05-16
Well lets hope ATI and Nvidia get there drivers fixed because there are going to be alot of unhappy people

---

