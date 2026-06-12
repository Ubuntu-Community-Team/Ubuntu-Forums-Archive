---
title: "ATI HD 3470 and Ubuntu 9.04"
date: 2009-06-01
forum: Hardware
---

### Post by j_arquimbau on 2009-06-01
Hi!

I've installed ubuntu 9.04 and I've an ATI RADEON HD 3470 card. If I use no driver I can watch videos perfectly in fullscreen mode, but in the moment I install fglrx it turns tremendously slow at the moment of watching a film. The reason of the fglrx driver instalation was to be able to run the compiz, although the video problems happen either with the compiz enabled or disabled.
I tried to change gstreamer-properties but nothing happend. I've also installed the radeonhd driver, but then I cannot turn the compiz on. I also tried to change the VLC video output to X11, and all the other options, but still no good.

My question is: is there any way to be able to have the compiz on and watching videos normally at the same time?

I must say that it isn't a copmiz problem, but a driver problem, so I think that the compiz-fusion icon won't work. Thank you.

---

### Post by mindry on 2009-06-01
Same problem here with a Radeon HD 2400 using fglrx, any fullscreen video seems to crash the computer and need a cold restart

---

### Post by j_arquimbau on 2009-06-02
Got to solve it... It's a xorg problem and you have to patch it. Here's a link to what I did and it now works fine!! It's in spanish though. I will probably translate it this afternoon.

[http://www.fmhq.com.ar/2009/05/ubuntu-jaunty-ati-fglrx-arreglar-lag.html](http://www.fmhq.com.ar/2009/05/ubuntu-jaunty-ati-fglrx-arreglar-lag.html)

Be aware: 

In the point where it says:
[I]
agregando a este archivo el nombre completo del archivo .patch descargado

Cambiaremos el número de versión para que apt lo instale en vez del .deb del repo:

# vim /var/cache/apt-build/build/xorg-server-1.6.0/debian/patches/series

# dch -v 2:1.6.0-1loquequieran

2:1.6.0-1loquequieran (esto es el número de versión, pueden modificarlo :P)
[/I]

as it didn't work, I did

# cd /var/cache/apt-build/xorg-server-1.6.0/debian/
#dch -v 2:1.6.0-1patched

then chose nano
pressed F3, ENTER and F2
and then I continued as explained

---

### Post by j_arquimbau on 2009-06-02
First we must install apt-build

# apt-get install apt-build

Then the hard work:

# apt-build source xserver-xorg-core

This will make the sourcecode be in /var/cache/apt-build/build/xorg.server-1.6.0

Now we download the patch from: [http://svn.pardus.org.tr/viewcvs/tags/2008/desktop/freedesktop/xorg/xorg-server/files/ubuntu/107_fedora_dont_backfill_bg_none.patch?root=pardus&view=log](http://svn.pardus.org.tr/viewcvs/tags/2008/desktop/freedesktop/xorg/xorg-server/files/ubuntu/107_fedora_dont_backfill_bg_none.patch?root=pardus&view=log)

Now we&#8217;ll copy it:

# cp 107_fedora_dont_backfill_bg_none.patch /var/cache/apt-build/build/xorg-server-1.6.0/debian/patches/

We edit the list of active patches and uncomment the patched we have just moved. In my case it was number 107. If you don&#8217;t have it in the list, you write it with the exact name:

# gedit /var/cache/apt-build/build/xorg-server-1.6.0/debian/patches/series

Now we change the number of the version so that apt installs this instead of the .deb of the repositories:

# cd /var/cache/apt-build/build/xorg-server-1.6.0/

# dch -v 2:1.6.0-1patched

I chose nano editor, the I pressed F3, ENTER, then F2.

And now you compile It and install it:

# apt-build install xserver-xorg-core -y --force-yes

This take quite a long time. Afterwards, you restart and it&#8217;s done.

PS: When I did this I had compiz off and the fglrx driver not installed. When I had the patched Xorg, I restarted, activated the fglrx, restarted again and then applied the compiz. It just works! ;)

Translated from [http://www.fmhq.com.ar/2009/05/ubuntu-jaunty-ati-fglrx-arreglar-lag.html](http://www.fmhq.com.ar/2009/05/ubuntu-jaunty-ati-fglrx-arreglar-lag.html)

---

### Post by j_arquimbau on 2009-06-03
I doesn't seem to work as fine as I believed at the beggining... There is a problem resizing the wondows.

Any help?? :(

---

### Post by Troublegum on 2009-06-05
The link to the patch you've posted is down. Is this the same as this?

"XServer with no backfill functionality"
[https://launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill)

---

### Post by brotherlen on 2009-06-12
anybody have any luck with this? I'm running this now, somewhere between the instructions posted and the last link for the deb package install. If it works, I'll post. I've been having a strange time getting the 3470 to work on the T400 with Jaunty 64

---

### Post by brotherlen on 2009-06-12
Still no love, ran everything, installed ATI catalyst, received a splash screen, it ran then it freezes where the login screen would be. Pretty much a bunch of colors and random bricks. No error messages, etc. I have to reboot and apt-get remove fglrx* . via safe mode.

---

### Post by sadaka on 2009-06-14
Same problem, dude. =[ Posted a thread recently to no avail: [http://ubuntuforums.org/showthread.php?t=1184902](http://ubuntuforums.org/showthread.php?t=1184902). Also I am considering to start complaining at ATI forums. The thing that stops me is that it seems that ATI catalyst drivers were recently updated to 9.5: [http://en.wikipedia.org/wiki/Fglrx](http://en.wikipedia.org/wiki/Fglrx). And I am not sure what version is currently shipped with Jaunty. Any ideas?

---

### Post by avilella on 2009-06-20
Can you run this command on a terminal?

lspci | grep VGA

If you see two lines then you have a hybrid graphics card.

---

### Post by brotherlen on 2009-06-20
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series

This is what terminal posted back. I turned off switchable graphics, and have it set as PCI Express/Dedicated GPU in the Bios.

---

### Post by sadaka on 2009-06-29
It seems that with the latest ATI proprietary drivers the situation is now a bit better.
[Catalyst 9.6]("http://www2.ati.com/drivers/linux/catalyst_96_linux.pdf")

---

### Post by mr.x@w.cn on 2009-09-16
I have seam card can give me solutions 

type command
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series 

this some info  manufacturer : ATI   							
						 							type : ATI Mobility Radeon™ HD 3470 supporting HyperMemory™ technology   							
memory amount : 256 MB dedicated VRAM (up to 2,046 MB total available graphics memory using HyperMemory™ technology with 4 GB system memory) 
						 							memory type : GDDR2 (500 MHz) Video RAM (resp. Video RAM and system memory combined)   							
						 							connected bus : 16x PCI Express
 [Intel® Core™2 Duo processor]("http://syndication.intel.com/DistributeModule.aspx?ppc_cid=IIP_02105066901&cc=CI") T6400, Intel® GM45  

can help me :(

---

### Post by brotherlen on 2009-09-16
I haven't really worked on this in awhile, I'll try again later on today after class. If you run into any solutions, please post.

---

### Post by Infin1ty on 2009-09-19
People having problems with their ATI Card please post your xorg.conf file.
I have an ATI 3400HD (Lenovo T400) and it runs now perfect, just ran into this thread because of the backfill, i haven't applied that patch yet (because i use 1.6.3 from a repo and it's seems more complicated to apply that :\) but anyhow, it runs smooth if we put the maximized lag aside.

It's seems everything goes to xorg.conf which causes problems and should be adjusted.

---

### Post by deanhanson on 2009-09-19
'm Using Ubuntu 9.04 x64 with the restricted drivers on an HP dv2 with a mobility 3410. Short answer, ATI Linux drivers suck. As it stands now you have three options with Ubuntu (or Mint):
1. Use version 9.04 with the open source ATI driver (don't use the restricted driver manager): no 3d acceleration but stable
2. Use 9.04 with the restricted driver from ATI: disable compiz visual effects, xv video will crash, but open GL will work. Plenty of issues with hibernation. Forget about programs like AWN and Cairo dock.
3. Use Ubuntu 8.10 with 9.3 catalyst drivers. That seems to be the only combo that worked.
At any rate, I'm using the 9.6 catalyst drivers:.... Thanks for sharing the post....

---

### Post by Infin1ty on 2009-09-19
> **deanhanson said:**
> 'm Using Ubuntu 9.04 x64 with the restricted drivers on an HP dv2 with a mobility 3410. Short answer, ATI Linux drivers suck. As it stands now you have three options with Ubuntu (or Mint):
1. Use version 9.04 with the open source ATI driver (don't use the restricted driver manager): no 3d acceleration but stable
2. Use 9.04 with the restricted driver from ATI: disable compiz visual effects, xv video will crash, but open GL will work. Plenty of issues with hibernation. Forget about programs like AWN and Cairo dock.
3. Use Ubuntu 8.10 with 9.3 catalyst drivers. That seems to be the only combo that worked.
At any rate, I'm using the 9.6 catalyst drivers:.... Thanks for sharing the post....

that's not so true, it's true ati's driver sucks compare to the windows one or nvidia's one, but i'm running jaunty with my own compiled kernel 2.6.30 , ati cataylist 9.8 (there's 9.9 as it was released few days ago as  well) and i haven't had a single problem till now.
I use compiz with almost all the options, i play quake3 occasionally, also UT2003!! and for my surprise running world of warcraft with wine is alot faster than windows xp :)

it's just about knowing how to configure the device (xorg.conf) which is abit of a hassle but when you get it right it works awesome. 

btw, i use cairo-dock!!! (used awn before) all the time, works flawlessly, also got hibernation and suspend to work perfect :), it's all about configuration.

not knowing how to do things does not mean they sucks and not working for you.
btw, i was using ubuntu's jaunty default kernel 2.6.28-15 and it worked good as well, i compiled 2.6.30 because some stuff i needed (not regarding ati)

---

### Post by sadaka on 2009-09-19
> **Infin1ty said:**
> not knowing how to do things does not mean they sucks and not working for you.
Most of the desktop OS users does not want to spend several weeks to get info on some internal system configurations and apply it. Including me. PCs supposed to help you with your work, not vice versa. If you are delivering something, either desktop OS or device drivers, make sure it just works like it supposed to.

---

### Post by Infin1ty on 2009-09-19
> **sadaka said:**
> Most of the desktop OS users does not want to spend several weeks to get info on some internal system configurations and apply it. Including me. PCs supposed to help you with your work, not vice versa. If you are delivering something, either desktop OS or device drivers, make sure it just works like it supposed to.
Several weeks? well you just want a computer that configure itself automaticly, so why are you using linux? go back to windows and enjoy all the bugs.

So yeah, configuring ATI and NVIDIA!! is not like configuring them on windows, because windows tries to adjust everything automaticly (and have some bugs, not some, alot!) so if you require reading some on how to configure your ati card perhaps linux is not for you?

Ubuntu is nice and does a wonderfull job, but there are times when you need to adjust stuff manually , like editing the xorg.conf file. 

and PCs!!!! are helping with your work perhaps linux is not as user friendly as windows, but that's has nothing to do with a PC!!!! 

run a google search and see what is a PC. (it's not an operating system)

---

### Post by Pitxyoki on 2009-09-19
> **Infin1ty said:**
> that's not so true, it's true ati's driver sucks compare to the windows one or nvidia's one, but i'm running jaunty with my own compiled kernel 2.6.30 , ati cataylist 9.8 (there's 9.9 as it was released few days ago as  well) and i haven't had a single problem till now.
I use compiz with almost all the options, i play quake3 occasionally, also UT2003!! and for my surprise running world of warcraft with wine is alot faster than windows xp :)

it's just about knowing how to configure the device (xorg.conf) which is abit of a hassle but when you get it right it works awesome. 

btw, i use cairo-dock!!! (used awn before) all the time, works flawlessly, also got hibernation and suspend to work perfect :), it's all about configuration.

Hi Infinity,
I'm considering buying a laptop with an ATI 3470 graphics card. What kind of configuration did you have to do on your xorg.conf? Did you have to add anything else besides the "Device" and "Driver" strings?

Thanks,
Pitxyoki

---

### Post by Infin1ty on 2009-09-20
> **Pitxyoki said:**
> Hi Infinity,
I'm considering buying a laptop with an ATI 3470 graphics card. What kind of configuration did you have to do on your xorg.conf? Did you have to add anything else besides the "Device" and "Driver" strings?

Thanks,
Pitxyoki

i'm attaching my xorg.conf, it's a little messed up but you should be fine adjusting it for your needs.

btw, please note that changing the xorg.conf does not mean your x server with ati will use that configuration, you must also do "sudo aticonfig --input=/etc/X11/xorg.conf --tls=1(change --tls=1 to something else if neccessery but according to my xorg.conf that's it)" to make sure the ati db will get updated as well (by normally it does not read the xorg.conf automaticly which means changes you do in xorg.conf won't automaticly get updated to the ati database).

---

### Post by sadaka on 2009-09-20
> **Infin1ty said:**
> Several weeks? well you just want a computer that configure itself automaticly, so why are you using linux? go back to windows and enjoy all the bugs.

So yeah, configuring ATI and NVIDIA!! is not like configuring them on windows, because windows tries to adjust everything automaticly (and have some bugs, not some, alot!) so if you require reading some on how to configure your ati card perhaps linux is not for you?

Ubuntu is nice and does a wonderfull job, but there are times when you need to adjust stuff manually , like editing the xorg.conf file. 

and PCs!!!! are helping with your work perhaps linux is not as user friendly as windows, but that's has nothing to do with a PC!!!! 

run a google search and see what is a PC. (it's not an operating system)
my friend, for me there is no need to use any search engines for that. i used to work with all kinds of hw and sw, starting back from zxspectrum times, and i got pile of degree papers for that also. the point is that when i use desktop distro, i have to:
- spend several eves after work to utilize my GPU at least in half of how it is utilized in win
- spend several eves to get my camera working, and few more to get it work with specific sw
- same with audio system
- and same with each new damn stuff  i need to use.
luckily, these issues improved dramatically, comparing with the situation that was several years ago, and luckily, it keeps improving (thx to guys in canonical and similar orgs)

Contrary, with shipped vista i got all things i need running smoothly, without any need of spending time on additional configurations. Everything works order of magnitude faster, and YES, without bugs! I can concentrate on my work and on the things i need to get done.

i understand that this is more problems of damn hw and sw manufacturers, then the problem of linux itself. however, these are the facts for today. the reason why i use linux is MS license agreements and policies. i find them impossible for me to accept. and most important, religiously, i stick with free and open software.

---

### Post by klemzy on 2009-09-20
Hi

I have a question, and since this thread is similar to my problem I'll just post it here. I've been using fglrx ati drivers from repositories. Today I downloaded newest drivers (9.9) and installed them. My question is, can I now disable fglrx drivers in System/Administration/Hardware Drivers or it will mess up my computer? I'm not sure if i'm using the latest drivers and I don't want to mess my comp.

---

### Post by Infin1ty on 2009-09-25
> **klemzy said:**
> Hi

I have a question, and since this thread is similar to my problem I'll just post it here. I've been using fglrx ati drivers from repositories. Today I downloaded newest drivers (9.9) and installed them. My question is, can I now disable fglrx drivers in System/Administration/Hardware Drivers or it will mess up my computer? I'm not sure if i'm using the latest drivers and I don't want to mess my comp.

Before you install a new drivers you must uninstall the old one completely, it can look that everything went well while installing the new driver, also if you will check you will see that you do use the latest one but you might experience lots of problems.
from my experience and others as well, installing a new catalyst driver over an old one without completely removing the old can cause unknown problems. 

you can check which version do you use by issuing: dpkg -l | grep fglrx in a terminal. you should see something similiar to this: 2:8.650-0ubuntu1 as the version (this is how it looks if you have 9.9 installed).

also, please take a look here on how to uninstall, install or upgrade to a new version: [http://wiki.cchtml.com/index.php/Category:Installation_Documentation](http://wiki.cchtml.com/index.php/Category:Installation_Documentation) it's very informative.

---

### Post by Pitxyoki on 2009-10-01
Hi again,
Thank you for the help, Infin1ty. I bought the laptop I was talking about, and fortunately I had no problems configuring the ATI graphics adapter.
I installed Debian 'squeeze' (testing), and everything went fine. The fglrx version is 9.9, xorg 7.4 and the kernel is 2.6.30 (64 bit).

I documented the steps I made to configure the radeonhd and the fglrx drivers. You can see them at the debian wiki: [http://wiki.debian.org/InstallingDebianOn/Acer/Extensa 5630G#Display](http://wiki.debian.org/InstallingDebianOn/Acer/Extensa 5630G#Display). I recommend anyone willing to follow those instructions to do them in a tty (Ctrl+Alt+F1), with xorg stopped:
```
$ sudo invoke-rc.d gdm stop
```
Replace gdm with kdm if you use KDE instead of Gnome.


Afterall, everything was quite simple and I didn't have to edit any configuration files. :)

Thanks again for the helpfulness.

---

### Post by peih on 2010-02-04
> **Infin1ty said:**
> that's not so true, it's true ati's driver sucks compare to the windows one or nvidia's one, but i'm running jaunty with my own compiled kernel 2.6.30 , ati cataylist 9.8 (there's 9.9 as it was released few days ago as  well) and i haven't had a single problem till now.
I use compiz with almost all the options, i play quake3 occasionally, also UT2003!! and for my surprise running world of warcraft with wine is alot faster than windows xp :)

it's just about knowing how to configure the device (xorg.conf) which is abit of a hassle but when you get it right it works awesome. 

btw, i use cairo-dock!!! (used awn before) all the time, works flawlessly, also got hibernation and suspend to work perfect :), it's all about configuration.

not knowing how to do things does not mean they sucks and not working for you.
btw, i was using ubuntu's jaunty default kernel 2.6.28-15 and it worked good as well, i compiled 2.6.30 because some stuff i needed (not regarding ati)

Hi,
I am using a lenovo T400 with ATI HD 3470 graphic card like yours. I use the fglrx driver, version 2:8.660 (i suppose it is 9.11 version). I have got problem in running(using) application which need OpenGL support, for example I can run cairo-dock without OpenGL, but when I run cairo with OpenGL, I get a big black background behind the dock. I tried also a script named compiz-check which checks whether a machine i capable to run compiz, and then I got many indications that my machine could not. One of those indications is RENDERING : NOT FOUND or something like that. 
Since you posted that your laptop works well with cairo-dock, I have changed my xorg.conf in favour of your config file, and then ran aticonfig ..... --tls=1 such that the laptop updates those changes. Nothing happens. I got the same black background behind the dock like it was ...
Have you got any new tips to help me?
Thanks in advance
peih

---

### Post by madscientist032 on 2010-02-17
Wow. Nice to know I'm not the only T400 user here with issues with ATI and Compiz. I didn't see my specific problem in the thread, so here we go.

Lenovo Thinkpad T400
Intel Core 2 Duo P8700
ATI Mobility Radeon HD 3400 Series (3450 I believe) with 256 MB dedicated VRAM
3 GB RAM
160 GB 7200 RPM Hard drive

Problem only happenes when I go to open, maximize, minimize, or un-minimize anything WHILE (and only WHILE) Compiz is enabled via "fancy / Extra" graphics. There is a noticable delay, roughly 1 second, that occurs when I attempt any of the previous actions. 

However, I've used Compiz before on my iMac (ATI Radeon X1600 128 MB) with no problems, even with the fancy graphics stuff (including wobbly windows) was enabled. It worked like a dream.

Is there a patch or something to get the proprietary ATI drivers running smoothly or do I have to edit the xorg.conf file? I already have the latest drivers from ATI (dated 1/27/2010, installed last night) and that didn't fix the problem. 

Any suggestions?

---

