---
title: "Screen Resolution Issues"
date: 2009-04-17
forum: Hardware
---

### Post by Wamellx on 2009-04-17
Hello,
I have a HP Pavilion dv2815nr laptop. (Specs here [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01391851&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN)](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01391851&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN)). It dual boots between Intrepid and Vista Ultimate 32 bit. The only two screen resolutions offered are 800 x 600 and 640 x 480. I would like 1200 x 800 though. I am a total n00b when it comes to command prompt things and anything that doesn't require a GUI. If the solution does require stuff like that, then please explain very very slowly. Lol.
Thank you so so much.

---

### Post by Jenkins1 on 2009-04-17
Open up the command prompt (Applications > accesories > terminal)
Type    xrandr
The output should list all possible diplay options you highest should be listed

type    xrandr -s ****X*** (replace the * with your highest screen resolution listed)

---

### Post by Wamellx on 2009-04-17
I did the first part of command prompt but the highest possible listed is 800x600, same as in the screen resolution menu. Is there any way that I can get it to 1200x800 like I have it set in Vista?

---

### Post by cariboo on 2009-04-17
It would help if you told what kind of graphics adapter your computer has. Open a terminal and type:

```
lspci | grep VGA
```

and paste the output in your next post. VGA has to be in capitalized.

I have a feeling you don't have the restricted drivers installed.

Jim

---

### Post by Wamellx on 2009-04-17
Well, before I saw your post. I installed all 200something updates and the recommended nvidia driver. When I restarted my computer, everything looked how it should, but when I logged in the screen went black and stayed there. I can still boot into Vista though.
Thanks

---

### Post by cariboo on 2009-04-17
I think your monitor isn't being detected properly. I've never had the problem, nvidia has always worked for me.

Jim

---

### Post by Wamellx on 2009-04-18
I don't think that my screen is being detected properly. I did what you said, but when I opened the nVidia X server settings it gave the message 
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server." I did alt-f2 and typed nvidia-xcongig closed the box and did ctrl-alt-backspace to restart the x server. It is still at 800x600 and i still get the message when i open the nvidia x server settings.
 
BTW, when i did lspci | grep VGA , it gave me this:

00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)

---

### Post by Wamellx on 2009-04-18
Actually, I downloaded a different nvidia driver, version 177 instead of the recommended version 180, and it is working perfectly now. Thank you all so so much for fixing what would have probably been the deciding factor on whether or not I use ubuntu on a regular basis. 

Thanks,
Max

---

### Post by goms on 2010-08-25
guys, im facing an issue with my hp laptop whose specs are as [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01391851&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN%29](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01391851&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN%29)

I also run Vista, the graphic card is nvidia 7150M but ubuntu 10.04 does not seem to detect my card... What do i do in this case?

---

