---
title: "Which video card on a Dell Inspiron?"
date: 2007-02-13
forum: Hardware &amp; Laptops
---

### Post by darthsabbath on 2007-02-13
Hi, all.

I'm looking to get an Inspiron 6400/E1505, and have the option of getting either the Intel 950 GMA chip or the ATI Mobility Radeon X1400.  I'm wanting to run Beryl or Compiz if possible.  I know the Intel 950 is pretty well supported, but I'm not sure how well it can handle a compositing WM.  On the other hand, I've heard of some issues with the X1400.

Any help or advice would be much appreciated. :-)

Thanks!
Phil

---

### Post by tubasoldier on 2007-02-13
Personally I have had major issues with my ati card. its a crappy ATI express 200M. So personally I would never reccomend ATI to anyone. But I'm not sure how well the Intel card does with beryl or compiz.

---

### Post by nachotronics on 2007-02-17
Hi Phil, I recently bought an Inspiron 6400/E1505, with the following specs:

-Intel® Core 2 Duo processor T7200 (4MB Cache/2.00GHz/667MHz FSB)
-15.4 inch Wide Screen XGA Display with TrueLife
-1GB DDR2 SDRAM
-256MB ATI MOBILITY RADEON® X1400 HyperMemory
-Network Card and Modem 	Integrated 10/100 Network Card and Modem
-Optical Drive 	8X CD/DVD Burner (DVD+/-RW) with double-layer DVD+R write capability
-Integrated Audio(Sigmatel, the cheapest option :wink: )
-Dell Wireless 1390 802.11b/g Mini Card (54Mbps)(also the cheapest option :wink:)
-Dell Wireless 355 Bluetooth Internal (2.0 + Enhanced Data Rate)  

Everything is perfect, its all working, wifi, xgl/beryl(don't worry I'm not posting a fancy screenshot here:p )

What can I say, it pretty much worked out of the box, except for the X1400 which i installed really easily, and the wireless card which took me a while to find the right driver, because you need to use the windows driver with ndiswrapper for that one(once i got the right one its been really easy to install) the Intel wireless works out of the box, but i wouldn't pay for the difference since its easy to get it going

I'm very happy with the ATI X1400, It works great for me, enough for my gaming needs also(Battlefield 2142 runs at full res with medium detail)

Anyway, thats my experience, also if you need any help when installing feel free to contact me.

Regards

---

### Post by satchelpig on 2007-02-18
Nach -- 

Can you point me to the x1400 driver as well as installation instructions -- I am completely new to this . . . .ie this will be my first installation of anything in Ubuntu.

If you know where I can figure out how to configure my wireless card, I'd be appreciative of that too.  I have the Dell Wireless 1500 (Draft N).

---

### Post by nachotronics on 2007-02-19
You get your wireless card working following **[these steps]("http://www.ubuntuforums.org/showthread.php?t=297092&highlight=edgy+dell+1390")**
The post is about configuring the Dell 1390 wlan, but as it uses the same drivers as the 1500, the procedure is exactly the same(i checked that on the Dell site, the driver installer is the same one R140747.EXE) 
In my case the driver from dells page didn't work, instead i used the one i'm attaching to this post.

After getting your wlan working you might want to install network-manager-gnome following **[this howto]("https://help.ubuntu.com/community/WifiDocs/NetworkManager?highlight=%28network%29%7C%28manager%29")**. This utility helps you set up WEP or WPA secured networks

You can install the ATI drivers as described in **[this howto]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")**
I followed the first method, installing from ubuntu repositories, its easier than the other method and just works.

If you feel like installing xgl and beryl **[here it is]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL")**

---

### Post by satchelpig on 2007-02-19
Both of these worked brilliantly, thank you!  I'm now posting this on a wireless connection at full screen resolution.  Happy day!

I'm sorry to be thick, but what are xgl and beryl and why should I install them?  Thank you!

---

### Post by nachotronics on 2007-02-20
I'm glad it all worked for you!, i'm still curious, which driver did you use, the one in the howto direct from dell.com, or the one i posted??

**[XGL]("http://en.wikipedia.org/wiki/Xgl")** is an x-server architecture and **[Beryl]("http://en.wikipedia.org/wiki/Beryl_%28window_manager%29")** is a composite manager, you can find a lot of informatino about these two if you want to go further on the learning, but they provide basically eyecandy for linux, gnome or kde, it's the famous 3d cube you've seen in SO MANY screenshots since the Novell Linux Desktop video came out, where you can switch from virtual desktops as if they where the different faces of a cube, you also get wobbly windows, and many transition efects at maximizing, minimizing, etc. 
It is 90% stable, at my opinion, and it's great to show off to your friends :wink:
It usually takes a little work to get it going, so if you don't care about eyecandy or such things, then my advice is to just leave things as they are. 

Hope this helps

---

### Post by satchelpig on 2007-02-24
I used what you posted, nach.

Now . . . on to Beryl and XGL.

I am ALL ABOUT eye candy and would really like to get these going, but my first effort just plain failed to work.

I'm hoping you can help.

Basically, everything appears to be installed, but when i actually try to use the Beryl manager in the system tray, nothing happens.  I try to select beryl as the window manager and it immediately and without intervention switches back to Metacity.

I've obviously missed something somewhere along the way.  Any ideas?

Thanks for helping me get started.
SATCH

---

### Post by satchelpig on 2007-02-24
By the way, the following should help --- this is what the terminal is telling me:

* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

---

### Post by UltraMathMan on 2007-02-24
If you are using the ati fglrx drivers (not the radeon driver), which I assume you are (it's what I use for my ATI X1400) then from what I've read AIGLX is a no go and you'll need to use XGL instead. FYI: AIGLX is built into the xserver and XGL is a rebuild of the xserver. I already had the drivers and XGL installed but I followed::[This Guide]("http://www.ubuntuforums.org/showthread.php?t=291464&highlight=xgl+beryl")::from then point where you do ```
$ sudo aticonfig --overlay-type=Xv
```

Hope this helps :)

---

### Post by satchelpig on 2007-02-24
OK --- the weird thing is that I thought I had installed XGL but for some reason it's still saying AIGLX, so obviously something isn't set right.

I followed the steps in the tutorial you linked to, and I get stuck at the following step:

> Now create the XGL script. Edit "/usr/bin/startxgl" and paste in this:
Code:

#!/bin/sh Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer & DISPLAY=:1 exec dbus-launch --exit-with-session gnome-session

Make it executable:
Code:

$ sudo chmod +x /usr/bin/startxgl

Now make a separate session for XGL. Edit "/usr/share/xsessions/xgl.desktop":
Code:

[Desktop Entry] Encoding=UTF-8 Name=Xgl Comment=Start an Xgl Session Exec=/usr/bin/startxgl Icon= Type=Application



Basically when I try to do that first part, Ubuntu says I don't have the permissions necessary to do what I'm asking.  Any ideas?

---

### Post by UltraMathMan on 2007-02-24
Are you accessing the file with root privleges? ie. ```
 sudo gedit /usr/bin/startxgl
``` with your account password

---

### Post by satchelpig on 2007-02-24
OK . . . progress . . . xgl is up and running . . . but now when I start beryl-manager I get the dreaded "white screen of death."  Any guidance . . . ?

---

### Post by UltraMathMan on 2007-02-24
Try starting it with ```
beryl-manager >> ~/berylstart-log.txt
``` This will write everything that is output to a text file in your home directory called berylstart-log.txt -- Then you should be able to see what sort of errors are occuring.

---

### Post by satchelpig on 2007-02-24
OK, I have solved that problem (I don't know why, but when you ask it to render via "copy" under the advanced settings, the white screen problem goes away.

So now I kind of have it going with a couple of glitches.

(1) No buttons for minimize, maximize, or close window.  You have to kind of guess where they are approximately.

(2) There are no themes in the theme manager window.  There are theme ENGINES to work with, but no pre-set themes.

Any help would be welcomed.

---

### Post by nachotronics on 2007-02-25
Setting rendering path to copy is not the best workaround for that problem, because xgl-beryl will get really slow, the best solution i found was installing the previous working svn version which is not the last one in Treviños svn repositories (deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) beryl-svn). This can be done following these steps i posted somewhere else

> **nachotronics said:**
> Here's the solution from _[**Forlong's** post in the beryl forums]("http://forum.beryl-project.org/viewtopic.php?f=43&t=70&st=0&sk=t&sd=a&start=330")_[SIZE="2"]** it consists in downgrading to the last working version from Treviños svn repository. **[/SIZE]

1. Uninstall Beryl completely
```
sudo apt-get remove 'beryl*'
```

2. Remove the SVN-repository (or any other Beryl-repo) so it won't update, till the next tested working version comes out
```
sudo gedit /etc/apt/sources.list
```
Then comment every beryl related line by adding # at the beggining, in my case they looked like this:
```
# deb http://ubuntu.beryl-project.org edgy main
# deb-src http://ubuntu.beryl-project.org edgy main
# deb http://www.beerorkid.com/compiz edgy main-edgy
# deb http://media.blutkind.org/xgl edgy main (latest: beryl 0.1.1)
# deb http://beryl.xglusers.de/ edgy main (latest: beryl 0.1.4; no aquamarine)
# deb http://download.tuxfamily.org/3v1deb edgy beryl-svn ( bleeding edge beryl development, use with care )
```

3. Look for these packages in /var/cache/apt/archives/

beryl_0.2.0+svn20070216-r4103+3v1ubuntu0_i386.deb
beryl-core_0.2.0+svn20070216-r4103+3v1ubuntu0_i386.deb
beryl-manager_0.2.0+svn20070213-r4019+3v1ubuntu0_i386.deb
beryl-plugins_0.2.0+svn20070218-r4130+3v1ubuntu0_i386.deb
beryl-plugins-data_0.2.0+svn20070218-r4130+3v1ubuntu0_all.deb
beryl-settings_0.2.0+svn20070218-r4140+3v1ubuntu0_i386.deb
beryl-settings-bindings_0.2.0+svn20070201-r3550+3v1ubuntu0_i386.deb
emerald_0.2.0+svn20070208-r3810+3v1ubuntu0_i386.deb
libberyldecoration0_0.2.0+svn20070216-r4103+3v1ubuntu0_i386.deb
libberylsettings0_0.2.0+svn20070216-r4103+3v1ubuntu0_i386.deb
libemeraldengine0_0.2.0+svn20070208-r3810+3v1ubuntu0_i386.deb

also optional: emerald-themes_0.2.0+svn20070126-r3229+3v1ubuntu0_all.deb

Or download them from _[**Treviños** svn repository]("http://download.tuxfamily.org/3v1deb/pool/edgy/beryl-svn/")_ or [_**get the entire set at once from rapidshare -> beryl-svn.etar.gz**_]("http://rapidshare.com/files/17958701/beryl-svn.tar.gz.html") or **run the attached script** by typing in any terminal console:
```
. downgrade.sh
```
which will download packages, uninstall installed beryl packages and install the mentioned ones.

4. Copy them to another folder e.g. beryl-svn on your desktop

5. Open a terminal and go to that directory
```
cd ~/Desktop/beryl-svn
```

6. Install all packages of that folder:
```
sudo dpkg -i *.deb
```

7. Restart X by pressing ctrl + alt + backspace, then login to the xgl session you already created.

8. Start beryl-manager if it is not started yet

9. Enjoy\\:D/

That will probably solve all your problems, since you are also installing the emerald-themes package, anyway, once you get it running i suggest gnome-look.org for downloading extra themes, my favorite is "blubuntu"

---

### Post by satchelpig on 2007-02-25
Thanks for being such a big help.  I don't see any way to give you "reputation points"  or the like the way you see on some forums, but if I could give you some I would!

I'm 72 hours into Ubuntu, and though I don't have it looking EXACTLY the way I want it, it is well on the way.  Now I just need to dive into other types eye candy -- backgrounds, icons, etc. . . . if there are any easy starting points there, please let me know! :popcorn:

---

### Post by UltraMathMan on 2007-02-25
First check out [http://www.gnome-look.org/]("http://www.gnome-look.org/"), for widescreen backgrounds check out  [http://interfacelift.com]("http://interfacelift.com/wallpaper/index.php?sort=date") and for individual icons (for icon themes see gnome-look) check out [http://www.customxp.net/images/PngFactory/]("http://www.customxp.net/images/PngFactory/")

Glad you were able to get everything working!

---

### Post by satchelpig on 2007-02-25
Well, if either of you (or anyone else) has time to indulge another question of mine, please click [here ]("http://www.ubuntuforums.org/showthread.php?p=2211354#post2211354")and let me know --- it has to do with getting icon themes to work in Beryl.  Bottom line: when I boot into XGL/Beryl I can't seem to get any of the new icon themes to appear.  But if I boot into AIGXL/Non-Beryl, they will.  Trying to figure out how to have my cake and eat it too!

---

### Post by satchelpig on 2007-02-26
> **UltraMathMan said:**
> First check out [http://www.gnome-look.org/]("http://www.gnome-look.org/"), for widescreen backgrounds check out  [http://interfacelift.com]("http://interfacelift.com/wallpaper/index.php?sort=date") and for individual icons (for icon themes see gnome-look) check out [http://www.customxp.net/images/PngFactory/]("http://www.customxp.net/images/PngFactory/")

Glad you were able to get everything working!

By the way, that interfacelift.com site has some unbelievable stuff.  Thanks for the heads-up!

---

