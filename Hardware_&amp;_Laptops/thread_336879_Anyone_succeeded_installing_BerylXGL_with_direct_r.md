---
title: "Anyone succeeded installing Beryl/XGL with direct rendering and ATI card?"
date: 2007-01-12
forum: Hardware &amp; Laptops
---

### Post by franestepona on 2007-01-12
Hello everybody,

Since I installed edgy Beryl was running fine, no problems at all and direct acceleration working. The problem comes to xgl apps such as googleearth or secondworld, since I dont run a AGL session they dont work properly. But if I change to a XGL session as described in [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html) (one of a thousand I tried to follow without success) I loose direct rendering (and therefore those xgl programs dont work either)
I tried to install ATI propietary drivers but i lost direct rendering even without XGL.
My machine is an Intel Centrino 2 ghz 1 Gbyte DDRAM and ATI mobility Radeon (9600 I think) with 256 MByte.

Any help apreciated

---

### Post by franestepona on 2007-01-13
No one???

---

### Post by franestepona on 2007-01-13
](*,)

---

### Post by medley on 2007-01-13
> **franestepona said:**
> ](*,)
The silence is deafening, isn't it? To answer your question based on my experience....for every person that has succeeded in getting Beryly running there is (at least) one who hasn't. I fall into category B. You are also correct when you say there are 50 different howto's, and if your system is one that isn't going to work, it won't work following any of the 50 different approaches.

Mostly what you'll hear is "wow, it worked for me!". I'm using an NVidia card, but my sense is that whether ATI or NV, we're facing the same problems.

I also think that 99% of Linux users (which represents a rapidly growing number of people in absolute terms) don't have a clue how to fix these things, and that's to be expected. My contention is that Linux won't really take off in the average household until you just do 'A' and 'B' happens. It's not like that today.

I was immensely relieved to find a guy who goes by the alias 'tseliot' who (bless his heart) tries to get enough information from the user community to understand what are the typical problems they experience, and then builds a script that 'just works'. That's what a consumer community needs.

But that's a different subject. I just wanted to let you know, that I feel your pain. And the fact that there are so many people that have read your post, but nobody has answered means that a) you're not alone and/or b) they've got it working but don't know why.

:-k

---

### Post by Waappu on 2007-01-13
Hi

You can try open source drivers. I use these guides to install beryl
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

You can add this repo also
[http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/](http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/)

and you might look this as well
[https://wiki.ubuntu.com/EdgyKnownIssues](https://wiki.ubuntu.com/EdgyKnownIssues)
[http://wiki.beryl-project.org/index.php/Plugins/PluginOptions](http://wiki.beryl-project.org/index.php/Plugins/PluginOptions)
[http://wiki.beryl-project.org/wiki/Tips/Default_Commands](http://wiki.beryl-project.org/wiki/Tips/Default_Commands)
[http://forum.beryl-project.org/viewtopic.php?f=35&t=1500](http://forum.beryl-project.org/viewtopic.php?f=35&t=1500)
[http://koti.mbnet.fi/waappu/](http://koti.mbnet.fi/waappu/)

Hope this help somehow

---

### Post by Waappu on 2007-01-13
Hi

Here is script that remove ati fglrx driver, set up open source driver and install beryl.
[ati-aiglx-beryl.sh]("http://koti.mbnet.fi/waappu/download/ati-aiglx-beryl.sh")  USE AT OWN RISK!!

Save it to home folder and type
```
sudo chmod a+x ~/ati-aiglx-beryl.sh
sudo sh ~/ati-aiglx-beryl.sh
```

after script finish you still need to modify your /etc/X11/xorg.conf file Section "Device".
Here is mine for exsample
```
Section "Device"
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option 		"DRI" "true"
	Option 		"ColorTiling" "on"
	Option 		"EnablePageFlip" "true"
	Option 		"RenderAccel" "true"
        Option		"AccelMethod" "XAA"
        Option		"XAANoOffscreenPixmaps" "on"
	Option 		"AGPFastWrite" "on"
        Option		"AGPMode" "4"
	Option      	"AGPSize" "32"
EndSection
```
After re-boot login to Gnome session and press Alt+F2. Type beryl-manager. If Beryl start and runs Ok you can add Beryl to startup programs. system->preferences->sessions goto to startup programs tab, press add and type beryl-manager

---

### Post by thx_1138 on 2007-01-13
I got it working with the official method on Beryl's site and the same blog posting mentioned here, but once Beryl upgraded itself a few weeks later it lost stability on my laptop (Toshiba M50-MX2 1.5 Celeron, 512 RAM, 200m Xpress ATI). I ended up doing a fresh install last weekend since I hadnt used beryl in a quople of weeks. I think I might wait a little longer... probaley around when feisty betas appear and I will probably give it another go.

---

### Post by Waappu on 2007-01-13
Hi

Latest Beryl version from Treviño’s Ubuntu Repository working for me OK. I had also problem after one update. It messed up my Beryl settings and enabled e.g. blur and water plugins. Those plugins not working some reason for me. After I disapled those again everything works as before update.

---

### Post by franestepona on 2007-01-15
> **medley said:**
> The silence is deafening, isn't it? To answer your question based on my experience....for every person that has succeeded in getting Beryly running there is (at least) one who hasn't. I fall into category B. You are also correct when you say there are 50 different howto's, and if your system is one that isn't going to work, it won't work following any of the 50 different approaches.

Mostly what you'll hear is "wow, it worked for me!". I'm using an NVidia card, but my sense is that whether ATI or NV, we're facing the same problems.

I also think that 99% of Linux users (which represents a rapidly growing number of people in absolute terms) don't have a clue how to fix these things, and that's to be expected. My contention is that Linux won't really take off in the average household until you just do 'A' and 'B' happens. It's not like that today.

I was immensely relieved to find a guy who goes by the alias 'tseliot' who (bless his heart) tries to get enough information from the user community to understand what are the typical problems they experience, and then builds a script that 'just works'. That's what a consumer community needs.

But that's a different subject. I just wanted to let you know, that I feel your pain. And the fact that there are so many people that have read your post, but nobody has answered means that a) you're not alone and/or b) they've got it working but don't know why.

:-k

Thanks for understanding me, sometimes I even think about switch to windows (good that I always find a better reason to stick to Ubuntu). I love that you can modify everything to fits your needs, and that may be the reason why my system just dont work. I'm gona give a try to the guides posted above, and if that dont work I can either kill myself or wait until feysty comes to save my soul.

Thanks everybody I'll tell u if I finally succed!

---

### Post by patrickfromspain on 2007-01-15
I don't know if anyone said it but: you won't get direct rendering when running XGL. NEVER. It's impossible. To run beryl with direct rendering, you must run intel graphics, nvidia, or ati open-source drivers though AIGLX (included in xorg 7.1).

Cheers!

---

### Post by CowzRule on 2007-01-15
There are 3 different drivers that you can use with ATI cards. 2 that are "Open Source" and 1 "Closed Source". The first "Open Source" drivers are the drivers that are installed from a fresh installation of Ubuntu called "ATI" or "Radeon". With these drivers and Ubuntu 6.10 you can use "AiGLX" to run Beryl. See [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver") for info about the driver and then see [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX") for info about Beryl.
The second "Open Source" drivers that you get via "apt-get" or "Synaptic" are called "FGLRX". With these drivers you'll need to use "XGL" to run Beryl. See [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-02330ccb580b6a9411d32bf617cc5a82116ba6b9]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-02330ccb580b6a9411d32bf617cc5a82116ba6b9") on how to install those drivers and see [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL") on how to install XGL and Beryl.
The "Closed Source" drivers are also called "FGLRX" (I know confusing) and you get those from the ATI website. With these drivers you also need to use "XGL" to run Beryl. For info on how to install these drivers see the section titled "Method 2: Install the Driver Manually" at [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") and see the "XGL" link above for Beryl.
I have successfully ran Beryl with both the ATI/Radeon driver with AiGLX and with the closed source FGLRX driver and XGL. The links that I posted are the guides that I used.
What I learned is the most important thing is to make sure you get "direct rendering: Yes" when you do```
glxinfo | grep render
```before trying to install Beryl or running XGL. You need to get what ever driver you are using set up correctly. Reading through "/var/log/Xorg0.log" is very helpful in setting up the driver. One note about using the ATI/Radeon driver and AiGLX; When you run "glxinfo | grep render" you may also see something like "libGL warning: 3D driver claims to not support visual ...". Don't worry about that, as long as you got "direct rendering: Yes" you should be good to go.
AiGLX is very easy to set up and runs Beryl pretty good though it seems a bit slow and it can be a little "choppy" with some of Beryls effect (at least for me). XGL is faster and much smoother, however it is "buggy". Sometimes it works perfectly and sometimes it doesn't. Also, I have not been able to get XGL working at all with the latest version (8.32.5) of the "Closed Source FGLRX" driver. I've only been able to get it to work with the 8.31.5 version. 
One last thing. If you already have one of the "FGLRX" drivers installed, going back to the "ATI" driver can be a pain. I tried it and was unsuccessful. I could never get "direct rendering: Yes" and ended up formating and reinstalling Ubuntu.

Edit: I noticed that ATI has released a new version of there FGLRX driver, ver. 8.33.6. Gonna have to try'em.

---

### Post by franestepona on 2007-01-16
Hey guys, first of all thanks for the guides, they were great help. Finally I decide to reinstall ubuntu and now i have the opensource drivers working under xgl. One last thing, even aparently everything is working, I still have no direct rendering:
```
fran@fransmachine:~$ glxinfo | grep render
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: MOBILITY RADEON 9700 Generic
fran@fransmachine:~$ 

```

but ATI drivers seems correct:
```
fran@fransmachine:~$  fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.6286 (8.33.6)

```

And glxgeras seems faster than never (i know is not a good benchmark, but globs doesnt work now)
```
fran@fransmachine:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
25398 frames in 5.0 seconds = 5062.417 FPS
25843 frames in 5.0 seconds = 5149.143 FPS
25781 frames in 5.0 seconds = 5140.647 FPS

```

Beryl is running properly, Google earth did run, but only when I do the trick:

```
fran@fransmachine:~$ DISPLAY=:0 googleearth
```

So everything looks ok, but still no direct rendering, is that ok or should I fix that??

Thanks again for the help

---

### Post by Patrick-Ruff on 2007-01-16
it's impossible without the use of AIGLX.

---

### Post by franestepona on 2007-01-16
Ok, this is a little bit confussing. So let's say, I want the best graphics performance to run breyl and xgl programs such as googleearth. What should I try? beryl+aiglx or beryl+xgl?

---

### Post by franestepona on 2007-01-16
> **franestepona said:**
> Ok, this is a little bit confussing. So let's say, I want the best graphics performance to run breyl and xgl programs such as googleearth. What should I try? beryl+aiglx or beryl+xgl?

Anyone have experimented here and can give me some tips?

---

### Post by Toxic-Waste on 2007-03-12
Hello franestepona,
I am going through exactly what you were going through when you begun this post! Did you manage to install Beryl on your ATI after all? And if yes, what method did you follow?
Thanks mate

---

### Post by franestepona on 2007-03-12
Hi! Yes I did it. See I dont know for sure what I did, because the first method failed, so i moved to the second, and then i did this and i did the other thing, the i uninstall and reinstall and a ton of other things untill i finally got it. I got beryl running under XGL. Install XGL is easy, u can follow this guide:


[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29)

U can find how to install beryl in the same website i think. The hard part is the direct rendering. I tried the propietary drivers and it didnt work. I tried this guide here:


[http://ubuntuforums.org/showthread.php?p=1704886#post1704886](http://ubuntuforums.org/showthread.php?p=1704886#post1704886)

And i think it did work, but i dont remember what i did before that. I'm sorry mate everytime i have a driver problem i just try everything i see until it works.

Hope this actually help u.

---

### Post by Toxic-Waste on 2007-03-13
Thanks for your help mate. I will give the guides a shot and keep my fingers crossed!
Cheers!:)

---

### Post by phoenixfirebird on 2007-04-06
I have direct rendering while in the normal GNOME session, but not while under XGL.  And I also seem to have only some of beryl's functionality, wobbly windows, new alt+tab, scaling (though no hot corners), and transparency.  However, I don't have the cube (just changes desktop like it would under GNOME), water effects crash my computer, and I can't even use the emerald themes, the window decorators just disappear.  Is there anyway to get direct rendering running under XGL?

Acer 3100
ATI  X1100
Feisty
FGLRX drivers from Ubuntu

---

### Post by lebabyg on 2007-04-07
In simple terms:

ATI are pretty rubbish when it comes to linux, and aren't releasing their source code to let open source developers get involved in the fray.  So you have 2 choices for ATI drivers in linux:

1.  Open source 
2.  Closed source (proprietary ones from ATI's website)

With open source you can run AIGLX to run Beryl with.  AIGLX is built into the X-server so you can run hardware accelerated programmes as well as hardware accelerated desktop.  However, the acceleration achieved is without opengl (I think but don't quote me on this), but whatever, games, desktop etc etc run at pretty poor accelerated performance.

With closed source you can't run AIGLX because ATI haven't enabled that yet.  You do get **** hot acceleration however on a par with windows.  With this acceleration you can either run Opengl proggys (googlearth) OR (THAT IS OR) a 3D accelerated desktop in XGL. This is because XGL runs over the normal xserver.  Essentially, XGL-server is on open-GL programme running on X, which is why it eats resources.  

SO to conclude.  YOU CAN EITHER HAVE 3D DESKTOP OR 3D ACCELERATION FOR GAMES WITH ATI AND XGL.  You can't have your cake and eat it yet. ;).  Hope this clears up the issue for you and stops you chasing the impossible dream of Xgl AND direct rendering.

---

### Post by Toxic-Waste on 2007-04-18
Oh...
Bummer! This really sucks... :(

---

### Post by zhr3lpd00d on 2007-04-19
I got xgl to work and beryl seems to only crash the computer sometimes because somehow
i got beryl to work without direct rendering on

---

