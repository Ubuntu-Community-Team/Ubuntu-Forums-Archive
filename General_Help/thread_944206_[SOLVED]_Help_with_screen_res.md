---
title: "[SOLVED] Help with screen res"
date: 2008-10-11
forum: General Help
---

### Post by Tech_Power888 on 2008-10-11
Hello,

I have recently reinstalled ubuntu on my computer (8.04) and I am using a rather old system with integrated graphics. Just wanting to know how I can go about enabling a higher resolution than 800 x 600? It seems that is the highest it will let me go by default. Any help would be greatly appreciated. Thanks in advance.

---

### Post by overdrank on 2008-10-11
> **Tech_Power888 said:**
> Hello,

I have recently reinstalled ubuntu on my computer (8.04) and I am using a rather old system with integrated graphics. Just wanting to know how I can go about enabling a higher resolution than 800 x 600? It seems that is the highest it will let me go by default. Any help would be greatly appreciated. Thanks in advance.


Hi and have you tried the command with the alt, F2 keys ```
gksu displayconfig-gtk
``` and adjust there.

---

### Post by Tech_Power888 on 2008-10-11
Gave this a try, and even tried identifying my onboard video (Via Unichrome TM2 graphics). Ran the test and it just comes up with a display of black and white squares. The resolution maximum is still 800 x 600 also. Where to from here?

EDIT: Ok I have a Compaq S920 monitor which was not on the list of available displays, so I chose the next closest thing which was the S910. I was then able to select from a list of resolutions. I chose 1024 x 768 to try, and was asked to log out. I logged out and got a MASSIVE login screen and could only see one corner of the picture. Once logged in though, the res went back to an appropriate 1024 x 768. I will reboot and have a bit of a play around and see how things go.

---

### Post by Tech_Power888 on 2008-10-11
Now that I have my resolution set up correctly, is there any correct way to properly install the drivers for my onboard video? Despite my resolution being fixed, everything is still laggy, as though the drivers are not fully installed. Anyone know how I might be able to fix this? Thanks in advance.

---

### Post by buixuanduong1983 on 2008-10-11
Can you check in System/Administration/Hardware Drivers to see if you have graphic display proprietary drivers not yet enable. If so, enable it to install the correct driver for your card.

---

### Post by Tech_Power888 on 2008-10-11
It says that no proprietary drivers are in use on my system. I am using onboard video, not a graphics card.

---

### Post by Ryadt on 2008-10-11
Try ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Tech_Power888 on 2008-10-12
Ryadt,

I gave your command a go, but the only difference it made was to the login screen, whereby I now get a very distorted image, rather than the previous "massive" image that didn't fit onto my screen. Seems to have made no difference whatsoever to the gui, which is still very laggy.

---

### Post by roger_1960 on 2008-10-12
Hi

Have a look at this:

[https://answers.launchpad.net/ubuntu/+question/32058](https://answers.launchpad.net/ubuntu/+question/32058)

but be careful to backup your xorg.conf file before trying to edit it!

---

### Post by overdrank on 2008-10-12
> **Tech_Power888 said:**
> Now that I have my resolution set up correctly, is there any correct way to properly install the drivers for my onboard video? Despite my resolution being fixed, everything is still laggy, as though the drivers are not fully installed. Anyone know how I might be able to fix this? Thanks in advance.

Hi and what is the model of the graphics? How much memory is being shared with the graphics?

---

### Post by Tech_Power888 on 2008-10-13
According to the official Gigabyte website, under the specifications of my motherboard, the graphics being used are "Via Unichrome TM2" graphics with 64mb shared memory.

Roger - I followed the advice in the link you gave me, and low and behold, my login splash screen is now back to normal! However, I am still experiencing the driver problems, because scrolling up and down in my browser, opening a new window and such, still appears very laggy, as though the drivers have not properly been installed. Almost there, just need to fix this driver problem.

EDIT: Thanks for the help guys, I basically ended up just buying an agp video card today anyway, so everything is running fine.

---

