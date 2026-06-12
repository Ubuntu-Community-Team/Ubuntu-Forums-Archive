---
title: "New to Linux - Hardware Issues: Audigy LS and nVidia 5700"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by Kung on 2005-06-27
Hi Everybody!1  :grin: 

I am fairly new to Linux and installed Ubuntu a few days ago. As as I installed Ubuntu I was struck by the fact that the desktop looked of very low colour depth, resolution and refresh rate AND that I had no sound what so ever.

My Computer hardware consists of: 
-P4 2.8Ghz
-120GB WD HDD
-512mb 500Mhz RAM in Dual Channel
-XFX nVidia 5700 256mb
-Creative Labs Audigy LS

Now,

Graphics card:

I was able to follow the steps on this site here to help install my NVIDIA Graphics drivers: [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

It went thru sucessfully and I was able to get that nice fancy little control panel aswell. But my resolution was still capped to 1024x768 @ 60Hz and 24bit colour depth when my monitor and graphics card is capable of atleast 1280x1024 @ 80Hz and 32bit colour depth (This is what I used day in day out on my pc when Windows was installed).

Also, I installed the game Neverwinter Nights and I was able to open it with all the graphics looking fine but the only resolutions it had available in the video options were 800x600 and 1024x768 with no mention of the refresh rate it's running at, so I set it at 1024x768 and logged into my favourite server.

Straight away I could tell I was getting extremely poor performance and I checked and saw I was getting less than 10fps stationary in an area with no fancy rain or lighting effects. I was able get atleast 30fps in this area while on Windows. This obviously will not do!

That is my first issue, I need you guys to help me getting my graphics running at full performance as it were on Windows.

Secondly.

Sound Card:

As soon as I log into KDE I get the error message that the soundcard was not detected. I have a Creative Labs Audigy LS and according to all the other threads around here, it really should work. But mine DEFINATLY isn't. Opening KMix shows that there is no selectable mixer at all! My Audigy LS came with a CD full of software and drivers. Even if I am unable to get the software working I would atleast want to be able to get my sound working at good quality. 

If it's possible the extra's that my soundcard can provide and the main reason I bought the soundcard such as Bass Redirection, Dolby Decoding, EAX etc could be enabled that would be great.

All help is greatly appreciated.

----

Thanks in Advance

-Kung

---

### Post by Kung on 2005-06-27
I have tried the instructions on this thread here: [http://ubuntuforums.org/showthread.php?t=19307&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=19307&page=1&pp=10) to try fix my soundcard and it worked for a while and the sound was EXTREMELY choppy. It was working until I restarted and opened synaptic which said alsa-modules was broken and it forced me to remove it and now it's not working. If I remove all traces of what I did and then try again I get strange errors.

---

### Post by Kung on 2005-06-28
I also have followed the instructions on this thread here: [http://www.ubuntuforums.org/showthread.php?t=39743&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=39743&highlight=nvidia) to try get my video card working.

The installation of the driver itself went fine, but I seemed to have many of the problems that other people have been having with them such as, blank screens. I have reinstalled Ubuntu and now I'm able to run at resolutions of 1280x1024 but still stuck at 60Hz. 

Also I'm still stuck with NO SOUND and very crappy 3D acceleration, please help!

EDIT: After much difficulty I was able to get my sound working, I still am unable to get my video card working with full 3D Acelleration.

---

### Post by Kung on 2005-06-28
Anyone?

---

### Post by Teroedni on 2005-06-28
Hello i can try to help you with the resolotion
In order for me to help you i need to see your x org config file

Heres what you do

Start terminal
(If you dont know where to find terminal
click program in left uppercorner in Ubuntu
then you move the pointer to the 6th line where it states system or something alike
then your follow into the next menu and in line 12 it states terminal. click it

or

right click choose terminal:)
Iprefer the last one \\:D/ 


Copy this and paste it in the terminal:
cd /
cd etc/X11
sudo gedit  xorg.conf

Now you will get  the xorg.config file
Copy all the text in the file and paste it here
Then i or someone much clever than me :roll: 
should be able to sort out your problem.

Hope this helps

As for the other im to much a newbie to answer , but i sure the others ones will come up with something.

---

