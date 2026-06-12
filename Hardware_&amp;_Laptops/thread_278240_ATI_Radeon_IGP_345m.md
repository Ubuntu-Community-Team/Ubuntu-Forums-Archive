---
title: "ATI Radeon IGP 345m"
date: 2006-10-16
forum: Hardware &amp; Laptops
---

### Post by GMUDuckman on 2006-10-16
Hello all,

I am a newbie to the Ubuntu world but I do like it so far. With one exception.. I can not get my video card to do 3d acceleration! I have an ATI Radeon IGP 345m,  its not that great of a card but it will do the job IF I could get the drivers install correctly.  I have been searching the internet for 3 days straight now trying all sorts of things, installing uninstalling this and that. I am very close to just saying screw it and uninstalling ubuntu and going back to windows xp](*,) .  
I have already tried the suggestions at this place:
[http://www.ubuntuforums.org/archive/index.php/t-189137.html]("http://www.ubuntuforums.org/archive/index.php/t-189137.html")
and this place:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") 

I have ubuntu dapper 6.06 and i really need help with this... I really want 3d destop and such! but I just can't get anything to work! Please please please help me with your almighty ubuntu king knowledge!!

---

### Post by GMUDuckman on 2006-10-16
Will none of you Linux Gods out there help me? :-(

---

### Post by GMUDuckman on 2006-10-17
Well no thanks to anyone on this forum I managed to get my 3d acceleration working and 3d desktop working so w00t

---

### Post by dthvid1 on 2006-10-27
> **GMUDuckman said:**
> Well no thanks to anyone on this forum I managed to get my 3d acceleration working and 3d desktop working so w00t

Hi GMUDuckman,

I'm another Ubuntu newbie, I have the same card that you, can you tell me the solution that you found ?

TIA and greetings

---

### Post by yarri on 2006-10-28
Hi!

Thats a great news! How you have got it done? I am looking for a solution since I started using linux (over a year ago). It seemed to me that no one knows. There were some posts on the ubuntu forum, but nobody really gave a good answer. Sa I am all ears!

---

### Post by draeath on 2006-10-28
Hi all. Bad news. That card does not really have acceleration, at least in my experience. I hail from distros like Red Hat, SuSE, gentoo... and none of them seem to have anything for that card.

I'm stuck with it too! Basically, the only connection the card has to real Radeons is the name. Personally I can't wait till I get the cash together to build a new system and get a real video system.

---

### Post by GMUDuckman on 2006-11-07
> **draeath said:**
> Hi all. Bad news. That card does not really have acceleration, at least in my experience. I hail from distros like Red Hat, SuSE, gentoo... and none of them seem to have anything for that card.

I'm stuck with it too! Basically, the only connection the card has to real Radeons is the name. Personally I can't wait till I get the cash together to build a new system and get a real video system.

If you check the card in windows XP it actually does have 3d acceleration, I just don't think its supported in linux yet.  I am currently able to run beryl pretty well though. Yes I do get some errors in my terminal but it hasn't seemed to affect the actually running of beryl or my computer so w00t

---

### Post by edemark on 2006-11-09
hi 
I have just read your thread so i do not know if you still need help (i mean you might allready be back on xp sic!) ok so getting to the issue. I have an hp compaq nx 9010 that comes with an igp 345M graphic chip. I actually have 3d accel out of the box with xorg better than 6.8 (my dapper actually uses 7.0) notwithstanding this acceleration is somehow slow (gave me approx 400 fps). So if you would like to have something faster than you  should install the latest radeon dri shapshot. That pushed up my plxgears fps to 1100 (with changing the color depth to 16 bits i get 1600).
On the other side i am not that lucky with beryl as i am unable to set it up to work. So if you would be so kind to indicate your xorg.conf and the way how you get beryl to work to have a look on it i would be really thankful.

ok good luck

---

### Post by GMUDuckman on 2006-11-09
> **edemark said:**
> hi 
I have just read your thread so i do not know if you still need help (i mean you might allready be back on xp sic!) ok so getting to the issue. I have an hp compaq nx 9010 that comes with an igp 345M graphic chip. I actually have 3d accel out of the box with xorg better than 6.8 (my dapper actually uses 7.0) notwithstanding this acceleration is somehow slow (gave me approx 400 fps). So if you would like to have something faster than you  should install the latest radeon dri shapshot. That pushed up my plxgears fps to 1100 (with changing the color depth to 16 bits i get 1600).
On the other side i am not that lucky with beryl as i am unable to set it up to work. So if you would be so kind to indicate your xorg.conf and the way how you get beryl to work to have a look on it i would be really thankful.

ok good luck


I never was actually able to get beryl to work with dapper. I've upgraded to edgy and beryl just works off a clean install of that for me. I haven't touched anything with my video card.  I do get some errors in the terminal but its nothing that makes my computer crash or makes beryl not run so I suggest upgrading to edgy if you wanna do beryl.

---

### Post by edemark on 2006-11-09
I might try to upgrade to edgy but for now i just enjoy being able to play games.
Anyway what fps you get glxgears?

thanks

---

### Post by GMUDuckman on 2006-11-09
> **edemark said:**
> I might try to upgrade to edgy but for now i just enjoy being able to play games.
Anyway what fps you get glxgears?

thanks

how do you output fps with glxgears?

---

### Post by edemark on 2006-11-09
for me it comes out on the terminal from where i start glxgears. In case that it does not gives you any results try "glxgears -printfps" command

---

### Post by GMUDuckman on 2006-11-09
> **edemark said:**
> for me it comes out on the terminal from where i start glxgears. In case that it does not gives you any results try "glxgears -printfps" command

197.878 FPS

---

### Post by edemark on 2006-11-09
i might suggest that you try (at your own risk) to follovw this thread:
[http://www.ubuntuforums.org/showthread.php?t=221672&highlight=7000VE](http://www.ubuntuforums.org/showthread.php?t=221672&highlight=7000VE)

this pushed up my fps to 1100 at 24 bits color depth and 1600 at 16 bits color depth. Remember that i use dapper.
However if you try it out please let me now if it worked out or not

good luck

---

### Post by shellhrs on 2007-03-22
> **GMUDuckman said:**
> I never was actually able to get beryl to work with dapper. I've upgraded to edgy and beryl just works off a clean install of that for me. I haven't touched anything with my video card.  I do get some errors in the terminal but its nothing that makes my computer crash or makes beryl not run so I suggest upgrading to edgy if you wanna do beryl.

I have a Compaq Presario 2598AT. Windows XP showed that it uses ATI 345M.

I've been trying to install Beryl on Edgy in this machine, but while Beryl installed just fine, it simply wouldn't work. Everytime I clicked on Beryl icon, the system sent me back to login screen. Would you mind telling me how you managed to install it (and run it)?

Thanks

---

### Post by Chii on 2007-05-03
> **edemark said:**
> hi 
I have just read your thread so i do not know if you still need help (i mean you might allready be back on xp sic!) ok so getting to the issue. I have an hp compaq nx 9010 that comes with an igp 345M graphic chip. I actually have 3d accel out of the box with xorg better than 6.8 (my dapper actually uses 7.0) notwithstanding this acceleration is somehow slow (gave me approx 400 fps). So if you would like to have something faster than you  should install the latest radeon dri shapshot. That pushed up my plxgears fps to 1100 (with changing the color depth to 16 bits i get 1600).
On the other side i am not that lucky with beryl as i am unable to set it up to work. So if you would be so kind to indicate your xorg.conf and the way how you get beryl to work to have a look on it i would be really thankful.

ok good luck

I recently reinstalled Ubuntu as yet ANOTHER try to get into linux (AND STICK TO IT) after a bad bout of getting frustrated with windows Vista this time around.  And I am wondering, HOW did you get that many fps?  

I am new to all of this, and am still scratching my head on what Im supposed to do other than go to the repository loader/downloader and download these drivers.  Could you please tell me what to do?  

Thank you!
-Chii

*edit*

I also tried following the thread on how to increase the fps from 3xx-4xx to a higher amount, but I am stuck at the point where it asks you to get the linux kernel and linux kernel x86 files.  Because in searching the repository I *cant* find it anywhere in there -_-

---

