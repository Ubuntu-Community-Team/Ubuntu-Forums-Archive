---
title: "MSI Wind Top"
date: 2009-06-06
forum: Hardware
---

### Post by 98xjdmb on 2009-06-06
Hey all,  i'm really liking the MSI Wind Top AE1900-10SUS, but its quite new and i can't seem to find anyone running ubuntu on it. Should i just look for systems with the same hardware to see if everything will work well? I'm just concerned that nothing is running all the same components together and don't want an issue.

Also, does anyone know a way to purchase one of these without windows installed? Man do i wish this could happen!

thanks!

[IMG]http://www.msicomputer.com/product/netpc/9S6-6638-63S/02.jpg[/IMG]

---

### Post by Gadgetech on 2009-06-06
Many people, including myself, are running Ubuntu on MSI Wind netbooks, so I imagine it's doable. Don't know about the touch screen.  Your best bet is to check the Linux section of the MSI Wind forums. [http://forums.msiwind.net/default-msiwind/]("http://forums.msiwind.net/default-msiwind/")

There have been some success stories on the net about rejecting the Windows EULA and obtaining a refund. However, an OEM version of XP or Vista Home Basic is probably only costing MSI around $15 to include, so it may not be worth the effort.

Looking at the specs, I'm thinking it should be pretty straight forward for everything but the touchscreen and the wireless card. You might want to grab the Windows wireless drivers from the hard drive in case you need to use ndiswrapper to get the wifi going.

Here's my writeup on [installing Ubuntu on the MSI Wind netbook]("http://tuxtweaks.com/2009/01/ubuntu-on-the-msi-wind/").

---

### Post by 98xjdmb on 2009-06-07
Thanks for the info and links. I want to use this computer as an easy to access "public" computer in my house. i'm currently running an old dell for the same purpose, but for $600 this thing would be great, even if the touch screen doesn't work (yet).

---

### Post by comtux on 2009-06-15
I just bought this everything works out of the box except..

1. The video settings and the touchscreen are mis-configured.

sudo apt-get install xserver-xorg-input-evtouch

Download the fdi file below and issue the following command.
[http://launchpadlibrarian.net/26936548/50-ideaco.fdi](http://launchpadlibrarian.net/26936548/50-ideaco.fdi)
sudo cp -a 50-ideaco.fdi /etc/hal/fdi/policy/50-ideaco.fdi

Download this xorg.conf file and issue the following command.
[http://launchpadlibrarian.net/26936554/XorgConf.txt](http://launchpadlibrarian.net/26936554/XorgConf.txt)
sudo cp -a XorgConf.txt /etc/X11/xorg.conf
  


2. The mic does not work out of the box and i have not managed to get it to work yet.

Over all its a really great system i am very happy. And i will keep this post updated with new info as i figure it out.

---

### Post by GREZZO16 on 2009-06-20
hi to everyone
i'm GREZZO16 from italy and i have a MSI WINDTOP AE1900-04IT (it=italy) with atom single core, 1gbram.

I've tried to install Ubuntu Netbook Remix about 1 month ago and i've discovered some probems:
1: the correct resolution wasn't avaiable (1360x768max, instead of 1366x768)
2: the touchscreen doesn't work.
3: the webcam doesen't work.

i'm actually using Windows7 and i find it pretty good, but i want to use ubuntu.

How did you manage to fix resolution? did you use the same fix for the touchscreen (i mean, if i do what you said, i'll fix both problems?)

thank you for you attention!

---

### Post by comtux on 2009-06-21
> **GREZZO16 said:**
> hi to everyone
i'm GREZZO16 from italy and i have a MSI WINDTOP AE1900-04IT (it=italy) with atom single core, 1gbram.

I've tried to install Ubuntu Netbook Remix about 1 month ago and i've discovered some probems:
1: the correct resolution wasn't avaiable (1360x768max, instead of 1366x768)
2: the touchscreen doesn't work.
3: the webcam doesen't work.

i'm actually using Windows7 and i find it pretty good, but i want to use ubuntu.

How did you manage to fix resolution? did you use the same fix for the touchscreen (i mean, if i do what you said, i'll fix both problems?)

thank you for you attention!

Install the normal Ubuntu 9.04 32 bit addition instead of the Netbook Remix. The NetBook Remix doesn't work right. Everything works except the mic and i haven't really played with that yet. Im still working on a xorg.conf file for the correct resolution but you can set the resolution to the highest setting in Display for a temp fix.

---

### Post by comtux on 2009-06-21
Ok i got the mic working it was just muted.
So everything works perfectly except i need to figure out the resolution issue.

---

### Post by GREZZO16 on 2009-06-22
hi comtux
thank you for your infos and your work: i've used UNR because it seemed more "optimized" for netbooks hardware.
Anyway i have a question:
what about the 64bit version? we should use it only with more ram?
i'm asking this because the atom 230 supports the 64bit architecture.

byeee

---

### Post by comtux on 2009-06-22
> **GREZZO16 said:**
> hi comtux
thank you for your infos and your work: i've used UNR because it seemed more "optimized" for netbooks hardware.
Anyway i have a question:
what about the 64bit version? we should use it only with more ram?
i'm asking this because the atom 230 supports the 64bit architecture.

byeee

I noticed the 64bit version is a little bit slower than the 32bit version but thats not the main issue. The main issue with the 64bit version is that it is harder to get certain programs to work like boxee and a few others. The 32bit version just works better.

I also got skype working with the webcam and mic the only thing i don't like about the webcam was it seemed like the framerate is low. Note: This could have been because of my slow internet connection.

Moblin seems to set the video up properly i am going to have to see how that xorg.conf is set up.

And i also tested out compiz fusion and it works great! I have also tested out burning dvds that works fine today ill be testing dvd video playback.

Ohh and i have started testing out 3D games i tried glest it work fine the mouse move just a little slow. The only issue with glest was i had to take it out of fullscreen mode because it messes the video up "Bunch of horizontal colored lines". My guess is a properly setup xorg.conf file will fix all of they above issues.

This is the MSI Wind Top that i purchased.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16883152004](http://www.newegg.com/Product/Product.aspx?Item=N82E16883152004)

---

### Post by lepat on 2009-06-24
> **comtux said:**
> I just bought this everything works out of the box except..

1. The video settings and the touchscreen are mis-configured.

sudo apt-get install xserver-xorg-input-evtouch

Download the fdi file below and issue the following command.
[http://launchpadlibrarian.net/26936548/50-ideaco.fdi](http://launchpadlibrarian.net/26936548/50-ideaco.fdi)
sudo cp -a 50-ideaco.fdi /etc/hal/fdi/policy/50-ideaco.fdi

Download this xorg.conf file and issue the following command.
[http://launchpadlibrarian.net/26936554/XorgConf.txt](http://launchpadlibrarian.net/26936554/XorgConf.txt)
sudo cp -a XorgConf.txt /etc/X11/xorg.conf


Hi,
Thanks comtux for your help to configure the touchscreen                                                   
Now with the 50-ideaco.fdi I can launch "Calibrate Touchscreen". I have added this line in the xorg.conf : 
Option   "Calibrate" "1""
With this option the calibration is saved (in /etc/evtouch/config). But the cursor is not at the same place as my finger. When I move on the touchscreen horizontally the cursor go on the opposite. Vertically it goes on the same way but exept on the center the position of the cursor is different.   
Comtux do you use a swapx,swapy,rotate or any other options ? Can you post your /etc/evtouch/config ?
Thanks for your help

---

### Post by GREZZO16 on 2009-06-24
thank you very much
i'll try in the next days the linux MInt 7 x64 distro, because on my old pc it were running very well.

i hope we will fix the resolution problem.

byeeeeeeee

---

### Post by comtux on 2009-06-25
> **lepat said:**
> Hi,
Thanks comtux for your help to configure the touchscreen                                                   
Now with the 50-ideaco.fdi I can launch "Calibrate Touchscreen". I have added this line in the xorg.conf : 
Option   "Calibrate" "1""
With this option the calibration is saved (in /etc/evtouch/config). But the cursor is not at the same place as my finger. When I move on the touchscreen horizontally the cursor go on the opposite. Vertically it goes on the same way but exept on the center the position of the cursor is different.   
Comtux do you use a swapx,swapy,rotate or any other options ? Can you post your /etc/evtouch/config ?
Thanks for your help

I haven't totally figured out the video/touchscreen settings yet. So i have the same problem. But on the bright side we are getting closer!

---

### Post by lepat on 2009-06-29
> **comtux said:**
> I haven't totally figured out the video/touchscreen settings yet. So i have the same problem. But on the bright side we are getting closer!
Thanks for your reply.

---

### Post by waldmeister on 2009-07-01
May find some hints here:

[http://ubuntuforums.org/showthread.php?t=1196829](http://ubuntuforums.org/showthread.php?t=1196829)

Would be nice if s/o can help me in return :KS

---

### Post by comtux on 2009-07-01
> **waldmeister said:**
> May find some hints here:

[http://ubuntuforums.org/showthread.php?t=1196829](http://ubuntuforums.org/showthread.php?t=1196829)

Would be nice if s/o can help me in return :KS

Could you post your xorg.conf file i tried following your direction for the resolution but its not working for me.

---

### Post by comtux on 2009-07-01
I don't know if the rest of you are having the same problem with blender on this system.
But I found this on blenderartists.

> For those of you who have a Intel graphics card (many laptops), and are running Ubuntu and haven't upgraded yet. Don't upgrade until you've read up on the problems people have been having with hardware accelerated graphics, including Blender. Check out the thread here called Blender in Ubuntu 4.09 (spelling mistake in the subject [IMG]http://blenderartists.org/forum/images/smilies/sago/smile.gif[/IMG] ). Then go over to the Ubuntu forums and search for problems with intel graphics cards and Jaunty. There are some instructions there for possible solutions, but most of them are not that simple, and some require installing a newer kernel and stuff, which may break support for other hardware (wireless network cards, newer soundcards and so on).

I've tried some of the safer and simpler fixes on my laptop, and while I've gotten improved performance in glxgears and wobbly windows working. Blender is still broken. Half the viewport doesn't update correctly and is filled with garbage. For me it's not a huge problem, as I mostly use my workstation with an Nvidia card for Blender, but still somewhat annoying. Apparently a lot of the intel bugs are on Ubuntus to-do list for the next milestone, so maybe it will be fixed in the not so distant future.

Note that this only applie to people with Intel graphics cards, not if you have an Nvidia or Ati one. Those run fine as far as I know.Just gives me some conformation on the issue with blender i was having.

---

### Post by chemisus on 2009-07-03
these are the magic numbers it took for my screen to be properly calibrated.

```
Option "minx" "7336"
Option "miny" "6967"
Option "maxx" "839"
Option "maxy" "1162"

```

very accurate even under the stylus. easy to use with finger pointing as well. was even "average user" tested with other people to test ease of use.

my system is the same as mentioned before, the MSI Wind Top AE1900-10SUS purchased at same link previously provided referring to newegg.com.

system is currently running kubuntu 9.04 64bit. works great, even with the small title bar buttons that come with oxygen theme.

hope the numbers work for you, if not, i can give you the xls file i created to help calibrate. feel free to email me.

---

### Post by GREZZO16 on 2009-07-05
hi chemisus
thank you for your infos
i have UNR 9.04 32bit

i've installed the .fdi and .txt file posted in the first page, both corrected with your values:
1: the calibration doesn't work. my input device isn't recognized
2: the touchscreen works but the pointer isn't accurate: it works about 5cm upper right far from my finger

should i change the values?

---

### Post by chemisus on 2009-07-06
no, ive been meaning to post this, but just forgot too.

i found that the input file often changes when you restart. so if you set device to /dev/input/event6 and restart, then the device might actually be at /dev/input/event4.

the fix would be to only have the screen values in your 50-ideaco.fdi file, no where else. and to remove the position options and the "device" option from your xorg.conf.

these are the files i am currently using:
[http://www.chemisus.com/files/ae1900/xorg.conf](http://www.chemisus.com/files/ae1900/xorg.conf)
[http://www.chemisus.com/files/ae1900/50-ideaco.fdi](http://www.chemisus.com/files/ae1900/50-ideaco.fdi)

edit: to easily find the device file that the touchpad is currently using, run from console:
```
lshal | grep -A 10 input.touchpad | grep input.device;
```

---

### Post by GREZZO16 on 2009-07-07
hi chemisus
i've used your files and everything seems works "better" but it's not stable: i mean, the touchscreen works better (it's not exactly under my finger, but it's quite close; calibration works) but every 2 or 3 reboot, the touchscreen "lose" the settings and works totally bad.
have you got any idea?
should i calibrate touchscreen with the default application?

about the webcam: i'm following the italian thread copy of that ([http://ubuntuforums.org/showthread.php?t=838210](http://ubuntuforums.org/showthread.php?t=838210)) because on the latest pages there are solutions compatible with 9.04.
anyway i've not yet managet to let the webcam work.

about the video performances: i've followed this italian wiki ([http://wiki.ubuntu-it.org/Hardware/Video/Intel/Jaunty](http://wiki.ubuntu-it.org/Hardware/Video/Intel/Jaunty)) and i've added repository for updated xorg drivers: with those tweaks and new drivers my graphic perfomances are BOOSTED!

byeee

---

### Post by chemisus on 2009-07-07
did you make any changes to the xorg.conf or the 50-ideaco.fdi files?

if so, please post them.

i would not recommend using the screen calibration, as it really does not offer any good information. if you have the "calibrate" option in the xorg.conf, you should remove that as well.

there are three files (that i know of) that can have the calibration numbers:
/ect/hal/fdi/policy/50-ideaco.fdi
/etc/X11/xorg.conf
/etc/evtouch/config

the only one that should have the screen calibration coordinates in it is the 50-ideaco.fdi. on my touchscreen, i do not even have the /etc/evtouch/config file existing, thus my xorg.conf file does not have the "calibrate" option, which appears to tell xorg.conf to load the evtouch/config file.

from a fresh install (and please note, i am using kubuntu 9.04 64bit version) i do:

(this is handtyped, so errors might exist)

```
sudo aptitude update;
sudo aptitude upgrade -y;
sudo aptitude install xserver-xorg-input-evtouch -y;
mkdir ~/ae1900;
cd ~/ae1900;
wget http://www.chemisus.com/files/ae1900/xorg.conf
wget http://www.chemisus.com/files/ae1900/50-ideaco.fdi
sudo cp -b xorg.conf /etc/X11/xorg.conf
sudo cp 50-ideaco.fdi /etc/hal/fdi/policy/
sudo shutdown -r now;
```

when comp restarts, touchscreen works fine, and has for many restarts. even when the input file (/dev/input/event#) changes, it still continues to work because xorg.conf is not linked to the device file. instead, the config information seems to get loaded when it loads the 50-ideaco.fdi.

this is why i have been saying not to run the calibration tool, because it really doesnt do anything that ive noticed.

i have already ordered another touchscreen, and it should be here in about a week or so. i will test my config options on that and continue to play around with it, and compare what works and what doesnt with the two touchscreens.

---

### Post by GREZZO16 on 2009-07-09
hi chemisus
thank you for your efforts: i've downloaded and installed correctly the files you uploaded but nothing changed-> the touchscreen still doesn't work well (i drag right, and the cursor go left...)

anyway in these days i've worked hard on the system and i've fixed some problems:
1: webcam (installing external driver)
2: video perfomances (new repository for xorg with 2.7 drivers AND kernel 2.6.30 by ubuntu)

next days i'll write here an small how to

byeee

---

### Post by GREZZO16 on 2009-07-09
EHY LOOK HERE
[http://forum-en.msi.com/index.php?topic=128465.0](http://forum-en.msi.com/index.php?topic=128465.0)

msi start to support actively the forum!

in next days i'll post something in the guide section: an AE1900 LINUX GUIDE with everything i know (and suggestions allowed)

---

### Post by GREZZO16 on 2009-07-13
i have a problem with the microphone (front)

how did you managed to let it work? i've tried allt he options in Sistem->preferences->audio->capture device with the application "Sound Recorder" installed by default.

i've read your words in past posts: "the mic was just silenced/muted".
i've turned on all the switches but nothing works.

can you help me?

---

### Post by comtux on 2009-07-15
This gets my touch screen and my resolution working better.

> **chemisus said:**
> 
```
sudo aptitude update;
sudo aptitude upgrade -y;
sudo aptitude install xserver-xorg-input-evtouch -y;
mkdir ~/ae1900;
cd ~/ae1900;
wget http://www.chemisus.com/files/ae1900/xorg.conf
wget http://www.chemisus.com/files/ae1900/50-ideaco.fdi
sudo cp -b xorg.conf /etc/X11/xorg.conf
sudo cp 50-ideaco.fdi /etc/hal/fdi/policy/
sudo shutdown -r now;
```


This fixes my video drivers.
[http://webupd8.blogspot.com/2009/05/graphic-video-drivers-ubuntu-repository.html](http://webupd8.blogspot.com/2009/05/graphic-video-drivers-ubuntu-repository.html)

---

### Post by chrae on 2009-10-24
I'm running Karmic Koala, instructions for Jaunty should be similar. 

To get the microphone to working, edit 
```
/etc/modprobe.d/alsa-base.conf
```
and add the following line at the end of the file
```
options snd-hda-intel model=acer
```
Reboot.

Open the input tab in sound preferences and chang the connector to Microphone 2 and boost the input volume a little and it should work.
 
It doesn't seem like the correct way to do things since Acer != MSI , but it works.

---

### Post by GREZZO16 on 2009-11-01
hi to everyone
9.10 is out, and i've just installed on my MSI Ae1900: everything works fine except touchscreen and microphone.

With comtux and chrae help i've managed to fox my problems (touchscreen is not well calibrated, but it works).

Since i've read lot of threads talking about WindTop and Ubuntu, i've opened a thread on the Msi Official Forum, with the solutions for the 2 main problems (touchscreen and microphone) of this WindTop.  -->   [http://forum-en.msi.com/index.php?topic=128477.0](http://forum-en.msi.com/index.php?topic=128477.0) 

i suggest to rewrite the first post of this thread, updating the infos for 9.10 and adding the 2 solutions as i did on other forum.

---

### Post by Joern_MSI on 2009-12-31
Hello

I also have an AE1900 and installed Ubuntu 9.04. After typing 

```
sudo aptitude update;
sudo aptitude upgrade -y;
sudo aptitude install xserver-xorg-input-evtouch -y;
mkdir ~/ae1900;
cd ~/ae1900;
wget http://www.chemisus.com/files/ae1900/xorg.conf
wget http://www.chemisus.com/files/ae1900/50-ideaco.fdi
sudo cp -b xorg.conf /etc/X11/xorg.conf
sudo cp 50-ideaco.fdi /etc/hal/fdi/policy/
sudo shutdown -r now;
```

it worked but it was not nice calibrated. After running the "calibrate touchscreen" (from the menu) no everything is inververted on the x-axis and even after changing the minx &maxx by hand in 50-ideaco.fdi I cannot recognized any change after reboot...

How can I force hin to used the in50-ideaco.fdi?? Or is there actually any better way to do it?

---

### Post by Joern_MSI on 2009-12-31
i just read in another thread to this topic and it solved my problem. After editing this file and deleting all other settings than maxx,maxy & minx, miny.

```
 /etc/evtouch/config 
```

---

### Post by kolbyjack on 2010-01-09
I recently purchased an AE1900-01SUS and had some trouble getting the touchscreen to work with Ubuntu 9.10.  After following some of the instructions in this thread, and having them not work completely, I messed around a bit on my own and seem to have a fully working touchscreen.  To begin, I installed xserver-xorg-input-evtouch, then ran the calibration tool.  I wrote down the min and max x and y coords that appeared while running the calibration.  After completing the calibration, I deleted the generated /etc/evtouch/config file and edited /usr/share/hal/fdi/policy/20thirdparty/50-ideaco-idc6681.fdi as follows:

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="IDEACO">
      <match key="info.product" contains="IDC 6681">
        <match key="info.capabilities" contains="input.touchpad">
          <merge key="input.x11_driver" type="string">evtouch</merge>
          <merge key="input.x11_options.reportingmode" type="string">raw</merge>
          <merge key="input.x11_options.taptimer" type="string">50</merge>
          <merge key="input.x11_options.longtouchtimer" type="string">30</merge>
          <merge key="input.x11_options.movelimit" type="string">15</merge>
          <merge key="input.x11_options.emulate3buttons" type="string">true</merge>
          <merge key="input.x11_options.emulate3timeout" type="string">50</merge>
          <merge key="input.x11_options.maxx" type="string">7298</merge>
          <merge key="input.x11_options.maxy" type="string">7050</merge>
          <merge key="input.x11_options.minx" type="string">836</merge>
          <merge key="input.x11_options.miny" type="string">1258</merge>
          <merge key="input.x11_options.swapx" type="string">true</merge>
          <merge key="input.x11_options.swapy" type="string">true</merge>
          <merge key="input.x11_options.x0" type="string">0</merge>
          <merge key="input.x11_options.y0" type="string">0</merge>
          <merge key="input.x11_options.x1" type="string">0</merge>
          <merge key="input.x11_options.y1" type="string">0</merge>
          <merge key="input.x11_options.x2" type="string">0</merge>
          <merge key="input.x11_options.y2" type="string">0</merge>
          <merge key="input.x11_options.x3" type="string">0</merge>
          <merge key="input.x11_options.y3" type="string">0</merge>
          <merge key="input.x11_options.x4" type="string">0</merge>
          <merge key="input.x11_options.y4" type="string">0</merge>
          <merge key="input.x11_options.x5" type="string">0</merge>
          <merge key="input.x11_options.y5" type="string">0</merge>
          <merge key="input.x11_options.x6" type="string">0</merge>
          <merge key="input.x11_options.y6" type="string">0</merge>
          <merge key="input.x11_options.x7" type="string">0</merge>
          <merge key="input.x11_options.y7" type="string">0</merge>
          <merge key="input.x11_options.x8" type="string">0</merge>
          <merge key="input.x11_options.y8" type="string">0</merge>
        </match>
      </match>
    </match>
  </device>
</deviceinfo>
```As you can see, my mins are smaller than my maxes, unlike the other fdi files I've seen on here.  I've been able to reboot the system several times, and the touchscreen is still working perfectly for me every time.  I had to include the [xy][0-8] settings because somehow hal seemed to be caching some old settings that a previous calibration had set.  I think I know how to set them manually, but I haven't tried.  If anyone would like, I could post how I think they should be calculated to improve your touch accuracy, but my screen is just fine with them all 0.

---

### Post by tomazo on 2010-01-27
I bought an AE2220M yesterday and can't get wifi working. I'm using Ubuntu 9.10 x64 and installed this driver ([http://launchpadlibrarian.net/34090326/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz](http://launchpadlibrarian.net/34090326/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz)), but it just won't connect to my wifi network.
Are you seriously saying that it worked out of the box for you? o.O

---

### Post by SnowflakeRV7 on 2010-03-25
I will be picking up an AE2020-49SUS tomorrow for my wife, it's coming with Win7 Premium but I want to try booting it from an Ubuntu 9.10 CD to see what it's like.  Maybe i'll try Mint too, I have a CD of that handy.

I'm considering getting the AE2220 for myself if it looks like a good platform.  I love the idea of the touchscreen.  We'll see how practical it is in everyday use... :)

---

### Post by williamblue on 2010-06-09
Anyone have a list of drivers needed for a MSI Windtop AE2220 running Windows 7?

---

### Post by KiaZ on 2011-04-19
Hello, 
sorry for bringing up an old thread. 
I HAVE to install ubuntu 10.10 (or any other working recent linux version) on a MSI Wintop 1920: ghrapic chipset is Intel GMA 3150. 
Actually I'm having no luck, installation freezes when trying to go in graphical mode. Now I'm downloading the alternate install for having text mode, and hope there's a way to configure xorg manually in the correct way. 
I don't need the whole hardware working: just a correct graphic display and networking (wireless and wired) will be enough for the machine's purpose . 
I hope somenome can give me some hint ...
thanks in advance. 
KiaZ

---

### Post by KiaZ on 2011-04-19
no way out :(
tried in text mode too with alternate cd but it freezes after detecting hardware ... 
I don't know what to do, should I give up and evelutate another all-in-one ?

---

### Post by KiaZ on 2011-04-19
I'm having (and don't know why) more success with 9.10 netbook remix : everything is working "out of the box" except for wireless card, which is not working neither listing with lspci . 
Can someone tell me what kind of wireless driver I should look for ? 
My windtop is this one : 
[http://www.solidblogger.com/msi-wind-top-ae1920-001us-specs/](http://www.solidblogger.com/msi-wind-top-ae1920-001us-specs/)

---

### Post by KiaZ on 2011-04-20
Sorry, yesterday I was wrong. 
That's what lspci says about my wireless NIC : 


01:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8171 (rev 10)
    Subsystem: Micro-Star International Co., Ltd. Device 6897
    Flags: bus master, fast devsel, latency 0, IRQ 10
    I/O ports at d800 [size=256]
    Memory at feafc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>


A rapid search reported me I have to use NDISwrapper. Can someone confirm ?

---

