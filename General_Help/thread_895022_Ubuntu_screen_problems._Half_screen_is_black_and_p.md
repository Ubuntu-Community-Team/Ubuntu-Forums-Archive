---
title: "Ubuntu screen problems. Half screen is black and pink!"
date: 2008-08-19
forum: General Help
---

### Post by linuxisevolution on 2008-08-19
No matter what display manager i use, it messes up. Xfce,gnome,kde. . . I got the pics below. If i hit crtl+alt+backspace i get a purple/black screen with random letters. please help. It used to work fine.The imagaes where taken when using the live cd. ( before reinstall )

[http://i289.photobucket.com/albums/ll207/winrid/sany2274.jpg](http://i289.photobucket.com/albums/ll207/winrid/sany2274.jpg)

[http://i289.photobucket.com/albums/ll207/winrid/sany2275.jpg](http://i289.photobucket.com/albums/ll207/winrid/sany2275.jpg)


[http://i289.photobucket.com/albums/ll207/winrid/sany2276.jpg](http://i289.photobucket.com/albums/ll207/winrid/sany2276.jpg)


Thanks you guys for helping me! Even if you don't know the answer, POST!!! It will help. . .

---

### Post by PaulFr on 2008-08-20
I can only point you in the direction of checking the screen resolution. My 1440 x 900 monitor used to display such borders when Ubuntu could not recognize it (and defaulted to 1024 x 768 ). Please check the forums for your specific hardware (laptop make and model OR graphics card).

---

### Post by mb_webguy on 2008-08-20
I can't really tell much from those photos.  Next time, you might want to turn off the flash on your camera.  Your monitor already produces light, after all.

From your description, it sounds like a video driver problem.  What kind of video card are you using, and did you enable the proprietary drivers using the restricted drivers manager?  Once you're sure you have the appropriate drivers installed for your video card, you could try typing "sudo dpkg-reconfigure xserver-xorg" in the terminal...

---

