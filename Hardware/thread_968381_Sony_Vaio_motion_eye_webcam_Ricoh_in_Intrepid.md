---
title: "Sony Vaio motion eye webcam Ricoh in Intrepid?"
date: 2008-11-02
forum: Hardware
---

### Post by Sealbhach on 2008-11-02
I never got this working in Hardy and I heard there was better support for webcams in Intrepid.

It needs the Ricoh driver r5u870 but according to this site

[http://www.palmix.org/r5u870-en.html](http://www.palmix.org/r5u870-en.html)

there is no working driver for the 2.6.27 kernel.

I was wondering how other Vaio owners have been affected by this?


.

---

### Post by Boss_scout on 2008-11-02
I am using a Sony vaio VGN-FZ38M, Intel Core 2 T8100, 4GB, 200GB HDD, NVIDIA GeForce 8400M GT GPU.
My integrated webcam is operating correctly using Cheese under 8.10 and did so under 8.04. Unfortunately i do not know the details of the webcam but it does work.

---

### Post by Sealbhach on 2008-11-03
Bump, anyone got any news on getting a driver for Intrepid?


.

---

### Post by p.i.m.p on 2008-11-03
BUMP ditto - need the driver for intrepid... hate having to boot windows just to use the webcam :(

@sealbach actually it was pretty simple to install the webcam in hardy.. they just haven't released a compatible driver for intrepid. this is a shame though.. i might have to downgrade to hardy just because of this bug

---

### Post by pihhan on 2008-11-04
There is firmware loader for this camera, which might or may be not enough. See [http://www.bitbucket.org/ahixon/r5u87x/](http://www.bitbucket.org/ahixon/r5u87x/), please try it and report success or problems for your model. It does not work for me, but you might be lucky one. Webcam claims to support USB Video standard, which would work with uvcvideo driver after firmware loading. YMMV

Original driver is at [http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870) I cannot get there right now, but you might be able to use webcam, if you get 2.6.25 kernel or upgrade the driver to support newer kernels.

---

### Post by p.i.m.p on 2008-11-04
> **pihhan said:**
> There is firmware loader for this camera, which might or may be not enough. See [http://www.bitbucket.org/ahixon/r5u87x/](http://www.bitbucket.org/ahixon/r5u87x/), please try it and report success or problems for your model. It does not work for me, but you might be lucky one. Webcam claims to support USB Video standard, which would work with uvcvideo driver after firmware loading. YMMV

Original driver is at [http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870) I cannot get there right now, but you might be able to use webcam, if you get 2.6.25 kernel or upgrade the driver to support newer kernels.
omg it worked like a charm first time around without any problems.. thank you so much.. really appreciate it

---

### Post by Sealbhach on 2008-11-04
YAY!!  Worked like a charm. Didn't even need the driver. Had to reboot for it to take effect. Works in Cheese and Skype, but not in Camorama. In Ekiga it detects light but the image is all bugged out.


.

---

### Post by cake_or_death on 2008-11-05
Hi.
This may be a silly question.  I'm running 8.10 on my Vaio vgn-cr290.  I'd like to try the firmware fix mentioned above at [http://www.bitbucket.org/ahixon/r5u87x/](http://www.bitbucket.org/ahixon/r5u87x/), but I'm not sure how to install or apply the settings once I've downloaded the files.  Can I get a quick step-by-step from somebody?

---

### Post by p.i.m.p on 2008-11-05
Download the source as a zip file from the link and extract the folder in it to you r home directory. Then start a terminal from the applications menu and navigate to the folder you just created. Installing the source is simple:

> 
make
sudo ./loader
sudo modprobe -r uvcvideo
sudo modprobe uvcvideo


The catch is that these steps have to repeated every time you power off your computer so you can save them as a script file which can be done from the terminal as:

gedit camera_load.bash

Paste the following:

#!/bin/bash
cd /home/[username]/r5u87x-f24553d56d3e
./loader
modprobe -r uvcvideo
modprobe    uvcvideo

Now make this file executable as:
chmod +x camera_load.bash

Now, every time you want to load the camera firmware just type:
"sudo camera_load.bash" from your home directory.

---

### Post by Sealbhach on 2008-11-05
> **p.i.m.p said:**
> 

The catch is that these steps have to repeated every time you power off your computer so you can save them as a script file which can be done from the terminal as:

gedit camera_load.bash

Paste the following:

#!/bin/bash
cd /home/[username]/r5u87x-f24553d56d3e
./loader
modprobe -r uvcvideo
modprobe    uvcvideo

Now make this file executable as:
chmod +x camera_load.bash

Now, every time you want to load the camera firmware just type:
"sudo camera_load.bash" from your home directory.

Good idea! I was just wondering if you could add that command to Startup Sessions? I have a Conky script that starts up that way, but it doesn't require sudo.


.

---

### Post by p.i.m.p on 2008-11-05
You can try adding "gksudo camera_load.bash" to the gnome startup. You will however, have to enter your password each time on startup. Alternatively, you could add the script to system startup

Cheers,

---

### Post by cake_or_death on 2008-11-06
So I downloaded the zip file, extracted it to my home folder, and executed the make command in the directory.  I'm pretty sure it was a failure.  This was my output:


meg@TheBeast:~$ cd r5u87x*
meg@TheBeast:~/r5u87x-f65c81a1980c$ make
cc -g -Wall  `pkg-config --cflags glib-2.0 libusb` -c loader.c loader.h
Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found
Package libusb was not found in the pkg-config search path.
Perhaps you should add the directory containing `libusb.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libusb' found
loader.c:28:18: error: glib.h: No such file or directory
loader.c:29:25: error: glib/gstdio.h: No such file or directory
loader.c:30:17: error: usb.h: No such file or directory
In file included from loader.c:32:
loader.h:42: error: expected declaration specifiers or ‘...’ before ‘gint’
loader.c:34: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c:35: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘force_clear’
loader.c:36: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘no_load’
loader.c:38: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c:39: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘dump_ucode’
loader.c:41: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘entries’
loader.c:60: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c:78: error: expected declaration specifiers or ‘...’ before ‘gint’
loader.c: In function ‘find_device’:
loader.c:80: error: ‘gint’ undeclared (first use in this function)
loader.c:80: error: (Each undeclared identifier is reported only once
loader.c:80: error: for each function it appears in.)
loader.c:80: error: expected ‘;’ before ‘i’
loader.c:84: warning: implicit declaration of function ‘usb_get_busses’
loader.c:84: warning: assignment makes pointer from integer without a cast
loader.c:85: error: dereferencing pointer to incomplete type
loader.c:88: error: dereferencing pointer to incomplete type
loader.c:88: error: dereferencing pointer to incomplete type
loader.c:90: error: ‘i’ undeclared (first use in this function)
loader.c:91: error: dereferencing pointer to incomplete type
loader.c:92: error: dereferencing pointer to incomplete type
loader.c:94: error: ‘version’ undeclared (first use in this function)
loader.c: At top level:
loader.c:109: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_upload’
loader.c:191: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_status’
loader.c:208: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_version’
loader.c:227: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_enable’
loader.c:244: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_clear’
loader.c:266: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘load_firmware’
loader.c:385: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘main’
loader.h:21:18: error: glib.h: No such file or directory
loader.h:42: error: expected declaration specifiers or ‘...’ before ‘gint’
make: *** [loader.o] Error 1
meg@TheBeast:~/r5u87x-f65c81a1980c$ 

any insight?

---

### Post by p.i.m.p on 2008-11-06
Try "sudo apt-get install libusb-dev libglib2.0-dev" and repeat the process

---

### Post by rajsaini on 2008-11-07
I have HP dv1600 and Webcam 1000. ./loader gives me the below error:

l:~/r5u87x$ ./loader
Searching for device...

Error: Failed to find any supported webcams

lsusb out is:

Bus 005 Device 002: ID 05ca:1870 Ricoh Co., Ltd Webcam 1000

My web cam is listed in the model-matrix.txt file but it says not supported by loader. Is there any other way to load the firmware?

Extract from supported model file.
---------------------------------
0x05CA  0x1870  R5U870  WDM     HP Pavilion Webcam / HP Webcam 1000         VID/PID combination used by two distinct devices. dv1xxx appears to be
                                                                            the less common of the two. The only way to check the difference is to
                                                                            read the model number out via DMI. Not currently supported by loader.

Thanks,

Raj

---

### Post by linuxgr on 2008-11-09
Hey guys, I have a Sony Vaio AR825e. Ricoh webcam works great out of the box with vlc and cheese(maybe more, dont know). But with skype, I get a very weird picture, like a blurry mirror-image. On hardy I used r5u870 and skype video worked fine. On ibex there is no support unfortunately, but I find it pretty weird, don't you? I mean, if it didn't work at all on skype it would be ok but working funny like that?

I tried the firmware you mentioned here, no change. Also for you vaio owners, did you also get weird sound issues when upgrading to ibex? When I plug in headphones only one the left one works now.... (I have made changes to /etc/modprobe.d/alsa-base and everything worked fine on hardy).

I think my laptop needs exorcism.... Do you know any good priest willing to perform one?

---

### Post by p.i.m.p on 2008-11-09
:) i know exactly where u are coming from.. i have a sony vaio cr220e... My skype video is blurry too.. used to work fine on hardy..

i faced a lot of problems with sound while upgrading to ibex but i managed to get it working.. do you mean to say that your speakers work fine but when you plug in headphones then you get sound only in the left? it seems that something is wrong with the headphones in that case?

---

### Post by linuxgr on 2008-11-09
I just figured it out. The problem with the headphones(only left working) happens only in skype..... I changed the audio devices from "default" to "pulse" in skype config and now both of them work now...


But the camera is still unsolved..... It is really really weird isn't it? I can barely describe the picture it shows.... Blurry and even if I put my head right in front of the camera I see one half of my face on one side and the other half on the other, nothing in the middle. Cannot describe it better if I have time I will provide a screenshot later.... 

Anyone else has the same issue? And hopefully solved it???

---

### Post by campbuds on 2008-11-17
I too have a sony vgn-cr220e and I cannot get the webcam to work at all not will my mic work. I would greatly appreciate some help.

I tried following the directions above but I must be doing something wrong. Nothing seems to happen.

I am running vs 8.10

---

### Post by cake_or_death on 2008-11-21
Ok, so thanks to p.i.m.p. I got my webcam working (though "sudo camera_load.bash" isn't doing the trick.  I just run ./loader and the modprobes), but my mic is still defunct.  Anyone with success stories on the internal mic issues?

---

### Post by SteveMcQwark on 2008-11-22
So, how would I add this to my system startup?

Edit: And skype gives me a weird zoomed in mirror effect. Any way to fix this?
Edit 2: And Ekiga gives me horizontal black and white lines that move when I move.
Edit 3: Both these effects are achieved in cheese by reducing the resolution to below 640x480.

---

### Post by campbuds on 2008-11-22
PIMP... is your webcam working?

also, what about your screen resolution? I am trying to go to 1280x800 but I lose 1/4 of my screen.

---

### Post by linuxgr on 2008-11-22
In case it helps someone figure out what the heck is wrong with skype, I will post some further info that I just experienced:

without using the firmware(loader), uvcvideo module works just fine with cheese,vlc and many more, but as I said something weird is wrong with skype. 

What I realized recently is that once you open skype and use the camera(either during call or using the "test" from options), then all other applications like vlc and cheese show the same lousy, weird picture skype does. I have to rmmod uvcvideo and modprobe it again in order to get picture on vlc and cheese work again. So each time I use camera with skype, the camera gets messed up.


So my question is: does skype somehow manage to "screw up" the uvcvideo module?


All this sounds very weird to me. 

@ p.i.m.p : does the same thing happen to you too?

---

### Post by p.i.m.p on 2008-11-26
Sorry, I wasn't around for a while. Yes, I get that weird ghosting effect in skype too. Cheese works fine :(

---

### Post by p.i.m.p on 2008-11-26
Guys there is a fix for this issue on this page: 
[http://www.bitbucket.org/ahixon/r5u87x/issue/17/distorted-video-uvcvideo-resolution-issue](http://www.bitbucket.org/ahixon/r5u87x/issue/17/distorted-video-uvcvideo-resolution-issue)

I am not on Ubuntu right now or I would try it myself. Apparently, it is something to do with the resolution. Scroll down to the bottom of the page

---

### Post by linuxgr on 2008-11-27
P.I.M.P. it works great!!!!!!!! Thanks for finding that!!!!


Quick solution: edit /home/user/.Skype/config.xml

and under <lib> add these lines:

<Video>
      <CaptureHeight>480</CaptureHeight>
      <CaptureWidth>640</CaptureWidth>
</Video>


I've tested it with more resolutions but skype seems to crash. Still, 640x480 is a fair picture until a better ricoh module arrives....

Now everything works out of the box(I do not need the loader). Although sometimes the uvcvideo module is not loaded correctly during boot(dmesg shows errors), everything works fine.

thanks again

---

### Post by p.i.m.p on 2008-11-27
Great! I just installed Ubuntu and it works for me as well. Only thing is, I have to edit config.xml in /home/[user]/.Skype/[user]

For those who have not been able to get their mic working, it takes some tweaking and playing around with the settings in skype->options as well as system->preferences->sound

Unfortunately, I don't remember what setting I changed that made my mic work.

A good place to start though is by right clicking on the volume icon on the gnome panel and opening volume control and then clicking on preferences. Then select the option to show all the capture interfaces. After doing this, you will notice that they start out as muted :confused:So unmute them here. After this, it is a matter of playing around with the sound settings.

Here are my sound settings, you can try these to see if they work for you:
System->Preferences->Sound:

All on autodetect except for capture which is on HDA Intel

Skype->Options->Sound

All on pulse except for sound in which is on hw:intel

My laptop is a Sony VGN-CR220E. Hope this helps somebody :)

---

### Post by linuxgr on 2008-11-27
My sound preferences are EXACTLY the same so I can confirm this....

---

### Post by hoogland on 2008-12-02
Also some vaio owners with non-working microphones may want to check that they have done this:

sudo gedit /etc/modprobe.d/alsa-base

and added the following line to the end of this file:

options snd-hda-intel model=vaio

now the microphone works for me.

---

### Post by steve101101 on 2008-12-03
> **linuxgr said:**
> P.I.M.P. it works great!!!!!!!! Thanks for finding that!!!!


Quick solution: edit /home/user/.Skype/config.xml

and under <lib> add these lines:

<Video>
      <CaptureHeight>480</CaptureHeight>
      <CaptureWidth>640</CaptureWidth>
</Video>


I've tested it with more resolutions but skype seems to crash. Still, 640x480 is a fair picture until a better ricoh module arrives....

Now everything works out of the box(I do not need the loader). Although sometimes the uvcvideo module is not loaded correctly during boot(dmesg shows errors), everything works fine.

thanks again

I did this but my video is still distorted as before. Please help me.

---

### Post by p.i.m.p on 2008-12-04
Try editing /home/[user]/.Skype/[user]/config.xml

---

### Post by steve101101 on 2008-12-04
> **p.i.m.p said:**
> Try editing /home/[user]/.Skype/[user]/config.xml

I did. Also the config file already had them. I can output my config file. Could someone upload one that works so i could just download it.

---

### Post by p.i.m.p on 2008-12-04
Here.. hope this works :)

---

### Post by steve101101 on 2008-12-04
> **p.i.m.p said:**
> Here.. hope this works :)

thanks ill give it a go in a sec

---

### Post by steve101101 on 2008-12-04
:D :D :D :D :D IDK whats different but it works. thanks.

---

### Post by Yako on 2008-12-13
What about R5U870 WDM-camera's? I have one in my HP Pavilion dv1668ea. It doesn't work with uvcvideo and the firmware loader.

---

### Post by linuxgr on 2008-12-13
Hey guys, sorry for the off-topic, since there are a lot of Vaio owners in this page, could you take a look at the thread I just opened in case you can offer some insight? 

[http://ubuntuforums.org/showthread.php?t=1010211](http://ubuntuforums.org/showthread.php?t=1010211)


Thanks and sorry for the off-topic again

---

### Post by WinzZ on 2008-12-15
my webcam cannot work in ubuntu 8.10 but in 8.04 its work with r5u870 driver. anyone can help me where i can download driver webcam for sony vaio.

$lsusb
Bus 003 Device 003: ID 05ca:1839 Ricoh Co., Ltd 

Thanks a lot

---

### Post by linuxgr on 2008-12-16
WinZz, the camera you have is the same most people in this forum have. Read the forum from the beginning and follow instructions, then your camera should work.

Cheers

---

### Post by steve101101 on 2008-12-16
> **linuxgr said:**
> winzz, the camera you have is the same most people in this forum have. Read the forum from the beginning and follow instructions, then your camera should work.

Cheers

+1

---

### Post by namd3r on 2008-12-21
It is probably worth noting that my webcam is now working thanks to following the instructions near the beginning of this thread.  The only thing currently not working is Ekiga, which isn't showing the proper input from the webcam, but I don't use Ekiga anyway.  It was just for testing my webcam.

It did work with Cheese.

---

### Post by epvipas on 2008-12-23
I tried compiling the latest r5u870 driver from svn against the latest 2.6.27-11-generic headers today and it appears to have worked and be fully functional in amsn and all apps that use cam. 

Not sure what's changed but not looking a gift horse in the mouth. 

No more ghosting and resolution problems at present.

---

### Post by SteveMcQwark on 2008-12-30
A link would be nice here...

---

### Post by happy_pig on 2008-12-30
Hi All
First time here.
I have tried the commands listed at post #9 but don't seem to get any luck to get the webcam working.
Here is my terminal:
> david@david-laptop:~$ cd /home/david/webcam
david@david-laptop:~/webcam$ sudo ./loader
[sudo] password for david: 
r5u87x firmware loader v0.1
Searching for device...
Found camera   : 05ca:1830
Firmware       : ucode/r5u87x-05ca-1830.fw

Camera reports positive microcode state.
Camera reports microcode version 0x0100.
Not doing anything - camera already setup.

Successfully uploaded firmware to device 05ca:1830!
david@david-laptop:~/webcam$ sudo modprobe -r uvcvideo
david@david-laptop:~/webcam$ sudo modprobe uvcvideo
david@david-laptop:~/webcam$ 


So it seems that it has gone ok, but still nothing in Cheese, Camorama, Skype. Doesn't seem to recognise the webcam 

here is my lsusb
> david@david-laptop:/$ lsusb
Bus 005 Device 006: ID 05ca:1830 Ricoh Co., Ltd Visual Communication Camera VGP-VCC2
Bus 005 Device 004: ID 054c:0281 Sony Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 044e:300c Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 062a:0001 Creative Labs Notebook Optical Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Is there anything here conflicting.
Thanks in advance but still new at linux


Additionally, looks like my camera is WDM (?), Like Yako at post #35, I am wondering what this means and what I can do to make the camera work?

---

### Post by epvipas on 2009-01-01
Doesn't seem to be working any more. Did work very well for a while but it's not compiling cleanly or modprobing any more. Shame as it worked very well.

---

### Post by avilella on 2009-01-02
Hi all, with the help of one of the Sony Vaio users that patched the drivers for the Intrepid kernel, I've updated the information on how to make it work (with skype at least) here:

[http://avilella.googlepages.com/vaiosz](http://avilella.googlepages.com/vaiosz)

If you have any updates, please let me know at avilella at gmail.

---

### Post by Yako on 2009-01-03
It works for my HP Webcam 1000, which is a :1870. Thanks! I've been waiting for this :)

---

### Post by campbuds on 2009-01-04
I still do not have my webcam on my vaio vgn-cr220e working

after typing ./loader I get this...

```
r5u87x firmware loader v0.1
Searching for device...
Found camera   : 0000:0000
Firmware       : ucode/r5u87x-0000-0000.fw


Error: Failed to open /usr/lib/r5u87x/ucode/r5u87x-0000-0000.fw. Does it exist?
```

I did look in the lib folder and it is not there. How do I put it there, and why is it not there?

---

### Post by campbuds on 2009-01-06
did everyone abandon this thread? I was point here to get help but no one is responding.

---

### Post by epvipas on 2009-01-07
I think the problem here is that there are two different ways of going about getting these cams to work. 

The old way was using the r5u870 driver which worked well with 8.04 but then stopped working with 8.10 due to a kernel upgrade and the move to the new uvcvideo drivers. 

A new way of doing it was therefore proposed at [http://www.bitbucket.org/ahixon/r5u87x/](http://www.bitbucket.org/ahixon/r5u87x/) which involved running a tool to upload the firmware to the camera then reloading the uvcvideo driver. Trouble here is that the camera resolution wasn't changing properly giving corruption for many. Some apps could be changed to work with the 640x480 resolution. 

I then recently had limited success for a couple of days in going back to the old driver although it then promptly stopped working again. Not sure whether this was also due to running a development version of the UVC driver and I need to find time to explore this. 

This resurgence of interest in the old R5U870 driver has been marked by a new patched version being made available here [http://avilella.googlepages.com/r5u870_patched.tar.bz2](http://avilella.googlepages.com/r5u870_patched.tar.bz2)

Yet to have success myself but I hope this post will clear up some of the confusion and talking cross purposes that appears to be going on here.

---

### Post by Mandalore on 2009-01-07
New patched Driver work very well, Thank You Very Much!! =)

Cheese, Ekiga, Skype work for me

Linphone not fully tested yet( green cam-LED on, but only green video screen)

VAIO AR-51J
05ca:1839 Ricoh Co., Ltd
Intrepid, 2.6.27-9-generic

---

### Post by campbuds on 2009-01-07
I am running Hardy and tried to follow PIMP directions on page 1.

Will this patched driver be any different on Hardy? I will not go to intrepid, it seems to have too many quirks for me out of the box, including Sun Java issues so I am staying Hardy until the next LTS.

So if the new patched one will work on Hardy, how do I install it?

Please see my post above to note my issues.

---

### Post by AlanR8 on 2009-01-07
campbuds said....

> I still do not have my webcam on my vaio vgn-cr220e working

after typing ./loader I get this...

Code:

r5u87x firmware loader v0.1
Searching for device...
Found camera   : 0000:0000
Firmware       : ucode/r5u87x-0000-0000.fw


Error: Failed to open /usr/lib/r5u87x/ucode/r5u87x-0000-0000.fw. Does it exist?

I did look in the lib folder and it is not there. How do I put it there, and why is it not there?

After the "make" command in the original post you have to also issue the command "make install" (without the quotes).

I had the same issue and the make install command creates the relevant folder for you.

---

### Post by AlanR8 on 2009-01-07
Have followed the instructions in this thread and got the web cam in my Sony VGN-FZ21S working in Skype....to a point!

Now if I go into settings and test the camera all is well. I'm trying it out on a call to my brother and am finding the image will drop out to that blurry image you get unless the Skype config file is altered to provide 640 X 480. Then after a few minutes the proper image will come back.

Any thoughts? By the way, I can't get it to work with Cheese

---

### Post by AlanR8 on 2009-01-10
Bump my last comment!!!! The picture is dropping out on a regular basis when using Skype. Any Thoughts?

In addition, I've now installed the patched driver as mentioned above and it automatically loads on booting the machine. I'm running Kubuntu and in my Applications/System/Hardware Drivers from my "start" menu the driver shows as installed and active.

Bit of a result but until the clarity issue goes away it's not a full success story! 

BTW, I get the same blurry image by default using AMSN. Is there a way to set the resolution by editing a config file in AMSN? Some reading suggests AMSN needs 32 bit colour depth and I'm only getting 24 bit on this Nvidia 8600M.

Thoughts?

---

### Post by epvipas on 2009-01-11
I'm back up and running on the patched version as detailed in my last post on this thread. Had to do the following 

```
cd /usr/src/linux-headers-2.6.27-11
sudo make clean
cd ~/r5u870_patched
make
sudo make install

```
then 

```
sudo modprobe -r uvcvideo
sudo modprobe r5u870
```

And after that it's available in amsn.

---

### Post by AlanR8 on 2009-01-12
Epvipas

Good news! But what's your image quality like in AMSN? Mine is distorted, like you're looking cross eyed! I'm sure this is a resolution issue.

---

### Post by epvipas on 2009-01-12
I can confirm that I've just done a hard boot from cold and it's working in aMSN straight away with no manual loading of drivers needed. Looking at logs it's trying to load the uvcvideo driver which fails and it's then loading the usbcam and r5u870 drivers. Theoretically if the firmware had already been loaded in a prior boot of windows on the same machine without actually powering the machine right down (as opposed to resetting) the uvcvideo driver could succeed in loading and would then give the ghosting. 

Have you tried powering right down? Might be worth blacklisting the uvcvideo module if you regularly use Windows.

---

### Post by AlanR8 on 2009-01-12
Thanks Epvipas I'll give that a go...when I've remembered how to blacklist a device.........

---

### Post by 82jack on 2009-01-13
> **epvipas said:**
> 
...
[http://avilella.googlepages.com/r5u870_patched.tar.bz2](http://avilella.googlepages.com/r5u870_patched.tar.bz2)
...




> **epvipas said:**
> I'm back up and running on the patched version as detailed in my last post on this thread. Had to do the following 

```
cd /usr/src/linux-headers-2.6.27-11
sudo make clean
cd ~/r5u870_patched
make
sudo make install

```
then 

```
sudo modprobe -r uvcvideo
sudo modprobe r5u870
```

And after that it's available in amsn.

Thanks mate... for weeks I've been unable to find a solution for that. It perfectly works on Linux Arch too.

---

### Post by 82jack on 2009-01-13
> **hoogland said:**
> Also some vaio owners with non-working microphones may want to check that they have done this:

sudo gedit /etc/modprobe.d/alsa-base

and added the following line to the end of this file:

options snd-hda-intel model=vaio

now the microphone works for me.

I'll give my contribute to this wonderful topic: I've got some problems with "./alsamixer" in this way, so i had to add

options snd-hda-intel model=vaio **probe_mask=1**

and it perfectly works. 
If i can spend a line _for linux arch users you have to create a file called "options" in /etc/modprobe.d/ and add that line_.

Thank you for the best linux topic for vaio users of the year :)

---

### Post by campbuds on 2009-01-16
after I enter... "sudo ./loader" I get this

```
r5u87x firmware loader v0.2

Searching for device...
Found camera: 0000:0000

Error: Failed to get filesize of firmware.
```

---

### Post by soko-ban on 2009-01-17
Hi

I managed to make my webcam work in luvcview following instructions in the begining of the forum. But in Skype, all I get is distorted image or, if I add the resolution configuration, a green image that is not looking nice.

Now I would like to try a patched version. How do I remove my previous installation (drivers).

Thank you.

---

### Post by alexb81 on 2009-01-17
Hi all. Happy to see that this forum is more active for this problem than the french one, where i couldn't find someone to help me to install my sony VGP-VCC2 on Intrepid.
Cause i'm a new user on Linux, i've read all the posts right there but cant find a way to try an installation.
On [http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)
EDIT : I downladed the zip file there, and i'll retr to install it. 
I missed something maybe cause my english is not perfect, i'll read another time all the treads to try to understand. But if someone could do a simple tutorial for a debutant to explain how to install it, it would be extremely appreciated. And i would translate also for all french users of Ubuntu.
Thanks a lot for your time helping others, in any case.

---

### Post by AlanR8 on 2009-01-17
Hi Alexb81

Try the following it worked for me but I still have some issues. This will install and load the driver for your web cam. However, I find that sometimes it does not load and I have to do a reboot and then it works.

> Source of driver is: [http://avilella.googlepages.com/r5u870_patched.tar.bz2](http://avilella.googlepages.com/r5u870_patched.tar.bz2)

Extract the driver to a convenient folder.

Open the folder r5u870_patched and then a terminal in the same folder. The Readme File has the instructions but this is what to do.

make
sudo make install

This should install the driver in a persistent state.

To load the driver for the current session (needed to action one time only as it will load automatically on reboot):

modprobe r5u870

Let us know your results!

---

### Post by alexb81 on 2009-01-17
Hi Alan, thanks a lot for this link but still not working..

First, i installed [http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)
seeing it's not working, i used an uninstall command.

Then i installed your link, using modprobe after, rebooting.
The cam is still not detected.

So i used even a checkinstall, rebooting...

here's a copy/paste of some commands : [http://paste.ubuntu-fr-secours.org/src-9298](http://paste.ubuntu-fr-secours.org/src-9298)

i'm still searching right now meanwhile

---

### Post by AlanR8 on 2009-01-17
My Sony is a VGN-FZ21S, what is yours? Maybe someone else can post a helpful reply! Mi cam works, most of the time. Maybe the next release will help us all!

---

### Post by alexb81 on 2009-01-17
I hope so ! Mine is a SZ serie, with a VGP-VCC2 cam
still trying :|

---

### Post by epvipas on 2009-01-18
Sorry to hear people are still having problems. 

I found I had to do the following to make mine work but some of this is from memory as I'm away from home on my netbook. 

(1) If you're going to reboot with a firmware in memory then Ubuntu will try to load the uvcvideo module which will then work in a similar way to as if the r5u87x firmware loading script had been used. If you're wanting to use the cam at the right resolution you need to add the line "blacklist uvcvideo" to your /etc/modprobe.d/blacklist file. 

(2) If you've compiled any other custom drivers such as the r5u87x driver I have then found it difficult to compile the patched drivers against this. As I suggested earlier you need to go to /usr/src/linux-headers-2.6.**-** where ths stars match the version of the kernel that you are running. If you're not sure then run uname -r from a terminal. 

Once in this directory run "sudo make clean" and then change to the directory you extracted the r5u870_patched drivers in and do the usual
```
make
sudo make install

```
You should then be able to remove uvcvideo if loaded then to modprobe the r5u870 driver. 

Mine is working fine with aMSN and flash clients which are what I want it to work with but not working with cheese or camorama at present. 

Hope that clears a few things up and that other people can have the success I have had or if not that other more clever people can suggest what other steps need to be taken.

---

### Post by soko-ban on 2009-01-18
Hi epvipas,

When I tried to do "make" in r5u870_patched directory I get "Error 2" in terminal. This is my output:

> make -C /lib/modules/2.6.27-9-generic/build M=/home/zoran/r5u870_patched V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/zoran/r5u870_patched/r5u870.o
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /home/zoran/r5u870_patched/r5u870.c:52:
include/linux/mmzone.h:18:26: error: linux/bounds.h: No such file or directory
include/linux/mmzone.h:197:5: warning: "MAX_NR_ZONES" is not defined
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /home/zoran/r5u870_patched/r5u870.c:52:
include/linux/mmzone.h:218: error: ‘MAX_NR_ZONES’ undeclared here (not in a function)
/home/zoran/r5u870_patched/r5u870.c:874:1: warning: "V4L2_CID_LASTP1" redefined
In file included from include/linux/videodev.h:16,
                 from /home/zoran/r5u870_patched/usbcam/usbcam.h:38,
                 from /home/zoran/r5u870_patched/r5u870.c:59:
include/linux/videodev2.h:873:1: warning: this is the location of the previous definition
make[2]: *** [/home/zoran/r5u870_patched/r5u870.o] Error 1
make[1]: *** [_module_/home/zoran/r5u870_patched] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [all] Error 2

Can you help me with this?
Thank you.

---

### Post by epvipas on 2009-01-18
Hi Soko-ban. Looks like you're on kernel version 2.6.27-9 and I'm on 2.6.27-11. Might be worth upgrading to the latest kernel then trying again.

---

### Post by Sealbhach on 2009-01-19
Woot!!! 


I just happened to look in the Hardware Drivers section and look what I found?

---

### Post by AlanR8 on 2009-01-19
Mine's a FZ21S and yes, I get the same info! Result.

But here's the thing. The driver only loads every other boot! Work that one out!!!!! :)

---

### Post by epvipas on 2009-01-19
> **Sealbhach said:**
> Woot!!! 


I just happened to look in the Hardware Drivers section and look what I found?

Yeah - I get the same too. Strange seeing as searches for ricoh or r5u870 don't find anything when searching in Synaptic package manager. More to the point I would already appear to have their driver installed even though I've not installed theirs but rather built my own from source. I don't understand. 

Adding to my last point the file bounds.h is missing from linux-2.6.26-9 but present in 2-6.26.11 which would explain the compile error. Couldn't check up on that over the weekend as I was away and only had my netbook which runs on Linpus.

---

### Post by Sealbhach on 2009-01-19
> **epvipas said:**
> Yeah - I get the same too. Strange seeing as searches for ricoh or r5u870 don't find anything when searching in Synaptic package manager. More to the point I would already appear to have their driver installed even though I've not installed theirs but rather built my own from source. I don't understand. 

I assume "Hardware Drivers" (Jockey) found the driver you had already installed and sees that it doesn't need to do anything.


.

---

### Post by campbuds on 2009-01-20
it is not showing up on my hardware list... is there something I need to do to get it there?

---

### Post by davehn on 2009-01-20
user-laptop:~/r5u87x$ make
cc -g -Wall -DHAVE_CONFIG_H -DUCODE_PATH=\"/usr/lib/r5u87x/ucode/"r5u87x-%vid%-%pid%.fw"\"  `pkg-config --cflags glib-2.0 libusb` -c loader.c loader.h
Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found
Package libusb was not found in the pkg-config search path.
Perhaps you should add the directory containing `libusb.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libusb' found
loader.c:25:20: error: string.h: No such file or directory
loader.c:26:19: error: fcntl.h: No such file or directory
loader.c:27:19: error: errno.h: No such file or directory
loader.c:28:18: error: glib.h: No such file or directory
loader.c:29:25: error: glib/gstdio.h: No such file or directory
loader.c:30:17: error: usb.h: No such file or directory
In file included from loader.c:32:
loader.h:42: error: expected declaration specifiers or ‘...’ before ‘gint’
loader.c:38: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c:39: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘force_clear’
loader.c:40: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘no_load’
loader.c:42: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c:43: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘dump_ucode’
loader.c:44: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘reload’
loader.c:46: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘entries’
loader.c:71: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c:89: error: expected declaration specifiers or ‘...’ before ‘gint’
loader.c: In function ‘find_device’:
loader.c:91: error: ‘gint’ undeclared (first use in this function)
loader.c:91: error: (Each undeclared identifier is reported only once
loader.c:91: error: for each function it appears in.)
loader.c:91: error: expected ‘;’ before ‘i’
loader.c:95: warning: implicit declaration of function ‘usb_get_busses’
loader.c:95: warning: assignment makes pointer from integer without a cast
loader.c:96: error: dereferencing pointer to incomplete type
loader.c:99: error: dereferencing pointer to incomplete type
loader.c:99: error: dereferencing pointer to incomplete type
loader.c:101: error: ‘i’ undeclared (first use in this function)
loader.c:102: error: dereferencing pointer to incomplete type
loader.c:103: error: dereferencing pointer to incomplete type
loader.c:105: error: ‘version’ undeclared (first use in this function)
loader.c:116: error: ‘NULL’ undeclared (first use in this function)
loader.c:117: warning: control reaches end of non-void function
loader.c: At top level:
loader.c:120: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_upload’
loader.c:202: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_status’
loader.c:219: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_version’
loader.c:238: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_enable’
loader.c:255: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_clear’
loader.c:276: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c:290: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘load_firmware’
loader.c:410: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘main’
loader.h:21:18: error: glib.h: No such file or directory
loader.h:42: error: expected declaration specifiers or ‘...’ before ‘gint’
make: *** [loader.o] Error 1

Does anybody knows what that means I Am trying to install my motion eye webcam please help:(

---

### Post by soko-ban on 2009-01-21
Hi.

I managed to make my web cam "Bus 003 Device 002: ID 05ca:1839 Ricoh Co., Ltd" work fine with pached driver for kernel 2.6.27, but that is after rebooting the computer every time I turn it on.

I have to reboot it if I wont to use my web cam. Do you have any idea way or how to correct that?

Thank you.

---

### Post by soko-ban on 2009-01-21
p.s.: I have it on my hardware list even if my web cam does not work in skype (of course after rebooting comp everything works just fine).

---

### Post by alexb81 on 2009-01-21
Hi again all. And thanks for what you're doing here.
I'm tired by this problem 3 days plenty on it. So i tooked a break :popcorn:, 

Well, I also have the driver actived in the Hardware Drivers ! Someone have also a VGP-VCC2 like me?


here's a copy paste of the install (cause i'm noob, i prefer to let you know how i did) :
> 
bast@bast-laptop:~/Bureau/r5u870_patched$ make
make -C /lib/modules/2.6.27-9-generic/build M=/home/bast/Bureau/r5u870_patched V=0 modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-2.6.27-9-generic »
  Building modules, stage 2.
  MODPOST 2 modules
make[1]: quittant le répertoire « /usr/src/linux-headers-2.6.27-9-generic »
bast@bast-laptop:~/Bureau/r5u870_patched$ sudo make install
make -C /lib/modules/2.6.27-9-generic/build M=/home/bast/Bureau/r5u870_patched V=0 modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-2.6.27-9-generic »
  Building modules, stage 2.
  MODPOST 2 modules
make[1]: quittant le répertoire « /usr/src/linux-headers-2.6.27-9-generic »
make INSTALL_MOD_PATH= INSTALL_MOD_DIR=extra \
		-C /lib/modules/2.6.27-9-generic/build M=/home/bast/Bureau/r5u870_patched modules_install
make[1]: entrant dans le répertoire « /usr/src/linux-headers-2.6.27-9-generic »
  INSTALL /home/bast/Bureau/r5u870_patched/r5u870.ko
  INSTALL /home/bast/Bureau/r5u870_patched/usbcam/usbcam.ko
  DEPMOD  2.6.27-9-generic
make[1]: quittant le répertoire « /usr/src/linux-headers-2.6.27-9-generic »
install -m 0644 -o root -g root r5u870_1830.fw r5u870_1832.fw r5u870_1833.fw r5u870_1834.fw r5u870_1835.fw r5u870_1836.fw r5u870_1870_1.fw r5u870_1870.fw r5u870_1810.fw r5u870_183a.fw r5u870_183b.fw r5u870_1839.fw r5u870_1841.fw /lib/firmware
/sbin/depmod -a
bast@bast-laptop:~/Bureau/r5u870_patched$ 


Still not working ! (VGP-VCC2)


Maybe my cam needs a module?

Thanks a lot for your help.

See you

---

### Post by campbuds on 2009-01-23
I would like to know how to get it to show up in the hardware list.

I have gotten it to run as stated on the front page with the updated drivers but I need to restart it everytime I want to use it and in Skype where I want it most it is all ghosty or something with the picture. It's weird.

---

### Post by AlanR8 on 2009-01-24
> I have gotten it to run as stated on the front page with the updated drivers but I need to restart it every time I want to use it and in Skype where I want it most it is all ghostly or something with the picture. It's weird.

Join the club! Exactly as described. The machine has to be rebooted for the camera to work!

As I stated in a post above, I get ghosting in Skype when I chat to my Brother on his Apple Mac but had a perfect image when chatting to a mate using XP. Very odd.

Is there a form of "handshake" between machines connected by Skype?

---

### Post by penguinfan on 2009-01-25
My experience

```
~$ uname -a
Linux sz28gp 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux
```

```
~$ cat /proc/version_signature
Ubuntu 2.6.27-9.19-generic
```

```
~$ sudo lspci -vvnn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
	Subsystem: Sony Corporation Device [104d:81e6]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: intel-agp
```

Attached is my
lspci -vvnn log
dmesg log

```
~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 04e8:04e8 Samsung Electronics Co., Ltd 
Bus 001 Device 004: ID 05ca:1830 Ricoh Co., Ltd Visual Communication Camera VGP-VCC2
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


Skype doesnt find camera when run as normal user, but when i start skype as root and > options > video devices > test webcam i get this :
```
~$ sudo skype
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
Skype V4L2: Failed to change capture framerate (15)
Starting the process...
Skype Xv: Xv ports available: 64
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 355
libv4l2: error dequeuing buf: Invalid argument
```

Same with ekiga. Camera only works when run as root:
```
~$ sudo ekiga

(ekiga:8362): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
```

I dont know where to go from here. Maybe a beer and a smoke will help :)

Here's my output when i run xawtv
as user
```
~$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.27-9-generic)
xinerama 0: 1280x800+0+0
WARNING: No DGA direct video mode for this display.
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: Permission denied
v4l2: open /dev/video0: Permission denied
v4l: open /dev/video0: Permission denied
no video grabber device available

```

and a root
```
~$ sudo xawtv
[sudo] password for wayne: 
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.27-9-generic)
xinerama 0: 1280x800+0+0
WARNING: No DGA direct video mode for this display.
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_S_STD(std=0x0 []): Invalid argument
game over

```

---

### Post by Arabso on 2009-01-25
thanks

---

### Post by alexb81 on 2009-01-25
Unbelievable Penguinfan ! My cam was working all that time just with opening skype as Root ! Thank you. I didnt even tryed it!

---

### Post by campbuds on 2009-01-25
> **p.i.m.p said:**
> Download the source as a zip file from the link and extract the folder in it to you r home directory. Then start a terminal from the applications menu and navigate to the folder you just created. Installing the source is simple:



The catch is that these steps have to repeated every time you power off your computer so you can save them as a script file which can be done from the terminal as:

gedit camera_load.bash

Paste the following:

#!/bin/bash
cd /home/[username]/r5u87x-f24553d56d3e
./loader
modprobe -r uvcvideo
modprobe    uvcvideo

Now make this file executable as:
chmod +x camera_load.bash

Now, every time you want to load the camera firmware just type:
"sudo camera_load.bash" from your home directory.

Can someone explain how I make this script file that you make executable?

---

### Post by AlanR8 on 2009-02-01
This thread's gone a tad quiet!

Just upgraded to the 2.6.27-11-generic kernel and all is well apart from the fact that on the initial boot the camera doesn't work!

A quick sudo reboot and when all is back the camera works! It even works in Cheese

---

### Post by campbuds on 2009-02-01
I am still waiting to hear about how to create an executable that I can have run at startup... it was expained early in this thread. I just don't understand it.

---

### Post by campbuds on 2009-02-01
Here is what I get...

```
rick@rick-laptop:~$ camera_load.bash
bash: camera_load.bash: command not found

```

---

### Post by brainsonfire on 2009-02-02
there is a new driver for the 2.6.27 kernel at [http://www.palmix.org/r5u870-en.html](http://www.palmix.org/r5u870-en.html)

works flawlessly for me.

---

### Post by albertongai on 2009-02-04
> **brainsonfire said:**
> there is a new driver for the 2.6.27 kernel at [http://www.palmix.org/r5u870-en.html](http://www.palmix.org/r5u870-en.html)

works flawlessly for me.

I Tried everything, and the last thing I tried was that version..

It built ok, first I read that I should stop/remove uvcvideo module, so i did like this..


```

rmmod uvcvideo
cd r5u870_k2_6.27/
make
make installer
modprobe r5u870

```

Then i get this error..

```

FATAL: Error inserting r5u870 (/lib/modules/2.6.27-11-generic/extra/r5u870.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```


Does anyone know what is missing? The only thing left besides the sd card reader is the webcam...

My Kernel version is 2.6.27-11-generic , with latest ubuntu release.. i guess its 8.10 or something...

---

### Post by campbuds on 2009-02-05
i guess no one is offering help with this anymore.

---

### Post by brainsonfire on 2009-02-05
> ```

rmmod uvcvideo
cd r5u870_k2_6.27/
make
make installer
modprobe r5u870

```

Then i get this error..

```

FATAL: Error inserting r5u870 (/lib/modules/2.6.27-11-generic/extra/r5u870.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```


what does dmesg say after the error? does lsmod | grep r5u870 return anything? make sure any previous drivers are uninstalled.

---

### Post by brainsonfire on 2009-02-05
> **campbuds said:**
> Can someone explain how I make this script file that you make executable?


open a terminal and type:  gedit camera_load.bash


Paste the following:
#!/bin/bash
cd /home/[username]/r5u87x-f24553d56d3e
./loader
modprobe -r uvcvideo
modprobe uvcvideo


save the file. back in terminal type:  chmod +x camera_load.bash


finally, everytime you want to load the camera firmware type:  sudo camera_load.bash

---

### Post by epvipas on 2009-02-07
Just done a system reinstall having had a brief flirtation with Jaunty and struggled to get up and running again. Didn't realised that the default user is not automatically put into the "Capture Video from TV or a Webcam" Group using the menu option "System/Administration/Users and Groups" 

Useful test is to see if you can "cat /dev/video0". If you get a permissions error then things won't work but if you get a screen full of garbage then it's working - press Ctrl-C to come out. Just bear in mind that you may need to log out or reboot for the permissions change to be applied.

---

### Post by kerml on 2009-02-07
I have a HP Pavilion dv9750ep. My built-in webcam is 

```

Bus 002 Device 003: ID 05ca:1812 Ricoh Co., Ltd

```

I used the drive of Ricoh R5U87x chipsets at [http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)
But i think the is still issues with the model "Bus 002 Device 003: ID 05ca:1812 Ricoh Co., Ltd".
Anyone have one of this working?

---

### Post by nasir8891 on 2009-02-14
i am facing the same problem as "campbuds".

is there any one who can help me use the web cam in my laptop.

---

### Post by campbuds on 2009-02-23
> **linuxgr said:**
> P.I.M.P. it works great!!!!!!!! Thanks for finding that!!!!


Quick solution: edit /home/user/.Skype/config.xml

and under <lib> add these lines:

<Video>
      <CaptureHeight>480</CaptureHeight>
      <CaptureWidth>640</CaptureWidth>
</Video>


I've tested it with more resolutions but skype seems to crash. Still, 640x480 is a fair picture until a better ricoh module arrives....

Now everything works out of the box(I do not need the loader). Although sometimes the uvcvideo module is not loaded correctly during boot(dmesg shows errors), everything works fine.

thanks again

I am running Skype but I don't seem to have this file location to adjust the resolution. A little help locating what I need to edit would be apprecaited since I don't have a skype folder in my user file

---

### Post by campbuds on 2009-02-23
figured out how to find it!!! WOO HOO!!!

skype video is clear... I have one last chain to windows to break.

my audio in skype is not good

---

### Post by rexb on 2009-02-24
> **campbuds said:**
> I still do not have my webcam on my vaio vgn-cr220e working

after typing ./loader I get this...

```
r5u87x firmware loader v0.1
Searching for device...
Found camera   : 0000:0000
Firmware       : ucode/r5u87x-0000-0000.fw


Error: Failed to open /usr/lib/r5u87x/ucode/r5u87x-0000-0000.fw. Does it exist?
```

I did look in the lib folder and it is not there. How do I put it there, and why is it not there?


**see**: [http://bitbucket.org/ahixon/r5u87x/issue/58/searching-for-device-found-camera-0000](http://bitbucket.org/ahixon/r5u87x/issue/58/searching-for-device-found-camera-0000)

---

### Post by PokeParadox on 2009-03-10
Does anyone know how to be able to access the cam without sudo?
I get a perfect picture in skype with the patched driver but I have to run ```
sudo skype
```

in AMSN it's the same but even then I get a horribly dark picture that it will not let me adjust with the AMSN sliders.

Any ideas guys?

---

### Post by epvipas on 2009-03-10
Try this pokeparadise - it's basically what I said a few posts up but from the command line which may be easier for some 
```
sudo gpasswd -a myusername video
```

---

### Post by PokeParadox on 2009-03-10
> **epvipas said:**
> Try this pokeparadise - it's basically what I said a few posts up but from the command line which may be easier for some 
```
sudo gpasswd -a myusername video
```

Thanks I actually missed your first post, but after searching around I found this solution elsewhere. I fixed it exactly as you described.

---

### Post by SteveMcQwark on 2009-03-16
The new driver isn't working for me, just not being picked up. lsmod | grep r5u870 returns

```

r5u870                 32452  0
usbcam                 50176  1 r5u870
usbcore               149360  7 uvcvideo,r5u870,usbcam,btusb,ehci_hcd,uhci_hcd

```

It seems I have multiple drivers installed? What should I do from here?

Edit: Ah I see. went back and fiddled with uvcvideo a bit, and it works. Still have the problems with res under 640x480 though

---

### Post by steve101101 on 2009-03-16
I am just glad that this thread is getting so much use and helping more than just me. It is just annoying that sony won't release a linux version of the driver.

---

### Post by PokeParadox on 2009-03-16
It seems I can't get it to use r5u870 exclusively. Somehow uvcvideo keep getting loaded, even though I blacklisted it!

---

### Post by steve101101 on 2009-03-16
did you try uninstalling it.

---

### Post by Francus on 2009-03-18
> **steve101101 said:**
> did you try uninstalling it.

Is it very complicated to uninstall a driver?

---

### Post by Sealbhach on 2009-04-06
OK, I have my webcam working in Jaunty after installing and running the firmware from ahixon:

[http://bitbucket.org/ahixon/r5u87x/issue/21/support-for-05ca-183d-ricoh-on-sony-vaio-vgn](http://bitbucket.org/ahixon/r5u87x/issue/21/support-for-05ca-183d-ricoh-on-sony-vaio-vgn)

 It's this one here:

```
Bus 001 Device 002: ID 05ca:183b Ricoh Co., Ltd
```

It works with Cheese and Skype, the only two I've tested. It's also working even though I did not rmmod uvcvideo.


.

---

### Post by Sealbhach on 2009-04-08
Not working now.:frown:

.

---

### Post by jeepmonster01 on 2009-05-02
when i do this (edit /home/user/.Skype/config.xml); it says that i dont have write permission; does anyone have an answer to this; i also use sudo and it says the same thing

---

### Post by lajfi on 2009-05-02
Hi

i am running Jaunty on my Vaio VGN-FZ29VN. I got my motioneye webcam to run ok in Cheese, after installing the driver found here:

[http://bitbucket.org/ahixon/r5u87x/issue/21/support-for-05ca-183d-ricoh-on-sony-vaio-vgn](http://bitbucket.org/ahixon/r5u87x/issue/21/support-for-05ca-183d-ricoh-on-sony-vaio-vgn)

but in amsn and skype i get a distorted image in amsn and skype.
It shows only a part of what the cam should be showing, it has lines and "double image"...

any idea anyone?

---

### Post by soko-ban on 2009-05-07
Hello lajfi,

Regarding Skyp, change resolution in yours config.xml (url of file: /home/zoran/.Skype/your_username)

Add this to your config file (it has to be inside  <Lib> </Lib>):

    <Video>
      <CaptureHeight>480</CaptureHeight>
      <CaptureWidth>640</CaptureWidth>
      <RecvPolicy>contacts</RecvPolicy>
    </Video>

---

### Post by AlanR8 on 2009-05-07
This thread has been great, it got my webcam up and running a while ago! Just one question though.

On first boot the camera does not work despite the fact the driver is reported to be active. Reboot the machine and it works!

Any ideas?

---

### Post by campbuds on 2009-05-08
> **soko-ban said:**
> Hello lajfi,

Regarding Skyp, change resolution in yours config.xml (url of file: /home/zoran/.Skype/your_username)

Add this to your config file (it has to be inside  <Lib> </Lib>):

    <Video>
      <CaptureHeight>480</CaptureHeight>
      <CaptureWidth>640</CaptureWidth>
      <RecvPolicy>contacts</RecvPolicy>
    </Video>

I used this when in Intrepid and it worked good. In Jaunty it is not fixing my ghost situation in skype. Anyone else with this? I wish Jaunty had resolved this issue.

---

### Post by rrbarbosa on 2009-05-14
> I used this when in Intrepid and it worked good. In Jaunty it is not fixing my ghost situation in skype. Anyone else with this? I wish Jaunty had resolved this issue.

I have the same 'ghost' situation with skype. It works for sometime until the image complete lose focus. The only way around is to reload the uvcvideo module. 

A second problem I have is that the image gets really dark, is there any way around it?

---

### Post by ivainsencher on 2009-05-14
the builtin webcam on my vaio vgn-tz170n
works now and then; why?
it took a while to have it functional on 8.10;
then it worked fine at first with 9.04 too, but after today's update it works sometimes, doesn't some other.

today, again, after powering on, no webcam.
but then, upon reboot, it is back!
any hint?

dmesg |grep -i "uvc"
[   14.968997] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:183a)
[   14.969651] input: UVC Camera (05ca:183a) as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input8
[   14.972186] usbcore: registered new interface driver uvcvideo


lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
09:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
09:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
09:04.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)

---

### Post by campbuds on 2009-05-14
it ghosts for me all the time now that i am in jaunty when using skype.

---

### Post by enigma32 on 2009-06-07
ivainsencher:

Do you have both the uvcvideo and r5u870 drivers installed and loaded? I've had conflicts with two modules in the past that would cause devices to work sometimes and not others, seemingly randomly.
I'd try removing one or the other module if they're both running.




I've managed to get the camera working on my TZ17TN using the r5u870_patched driver. Had to add myself to the "video" group.... still no luck with the microphone.
If the uvcvideo module is loaded I get very weird video. Mirror images and all sorts of crazy stuff.
(The microphone was my biggest issue in ubuntu 7.10 also... hoping I'll get it eventually)

Any ideas for getting a working mic? I've tried the vaio and probe_mask=1 settings in alsa conf... Can't remember what settings I had before I wiped the machine to install 9.04 :-(

---

### Post by soko-ban on 2009-06-08
I had similar problems with microphone.

I found solution here:
[http://ubuntuforums.org/showthread.php?p=7321036](http://ubuntuforums.org/showthread.php?p=7321036)

p.s.: my laptop is sony vaio and I have 32 bit ubuntu 9.4

---

### Post by enigma32 on 2009-06-09
I actually figured out my microphone problem now.

I used the config file changes mentioned here:
[http://www.pulseaudio.org/wiki/PerfectSetup#Skype](http://www.pulseaudio.org/wiki/PerfectSetup#Skype)

but ultimately ended up playing with the input options and making a setting change in the gnome audio control screen:
The microphone needing a setting changed in the Gnome Volume Control panel under the Options tab-- I changed my input source from "Mic" to "Front Mic"

That is, I'm not using Pulse anymore.

Skype seems very happy now.

I was having no issues with the webcam until I went to try it just now. The driver seems to still be working but I'm getting a resource error. *shrug
I have a feeling if I were to reboot it would be fine again.

Seems my video conferencing woes never end...

---

### Post by rcrc on 2009-06-20
This worked for me! 
Before, the image was fade and double.
webcam on ubuntu 9.04, sony vaio vgn cr21s, skype 2.0.0.72. 


Thanks!



> **soko-ban said:**
> Hello lajfi,

Regarding Skyp, change resolution in yours config.xml (url of file: /home/zoran/.Skype/your_username)

Add this to your config file (it has to be inside  <Lib> </Lib>):

    <Video>
      <CaptureHeight>480</CaptureHeight>
      <CaptureWidth>640</CaptureWidth>
      <RecvPolicy>contacts</RecvPolicy>
    </Video>

---

### Post by soko-ban on 2009-07-02
Hi rcrc,

which drivers did you use?

nice day

---

### Post by 2LSS on 2009-07-02
Will this driver work in Hardy?

[http://bitbucket.org/ahixon/r5u87x/i...-sony-vaio-vgn]("http://bitbucket.org/ahixon/r5u87x/i...-sony-vaio-vgn")

or do I need to upgrade to intrepid or jaunty?

---

### Post by torii on 2009-08-09
i really don't get what i'm doing wrong
i've downloaded the drivers but i just cant seem to get them to work with these instructions
anyone got any ideas?

---

### Post by AlanR8 on 2009-09-12
Further update!

Am now running UBUNTU Karmic Alpha 5 fully updated with the 2.6.31-10-generic Linux Kernel.

I picked up the latest driver from:

[http://www.palmix.org/r5u870-en.html](http://www.palmix.org/r5u870-en.html)

then:

> sudo make

sudo make install

sudo modprobe r5u870

and all is well!

---

### Post by AlanR8 on 2009-09-24
But Skype is borked.....double image beer goggles!!!!!! Have tried changing the config.xml file to change resolutions but no joy.

Any ideas?

---

### Post by steve101101 on 2009-09-24
> **AlanR8 said:**
> Further update!

Am now running UBUNTU Karmic Alpha 5 fully updated with the 2.6.31-10-generic Linux Kernel.

I picked up the latest driver from:

[http://www.palmix.org/r5u870-en.html](http://www.palmix.org/r5u870-en.html)

then:



and all is well!

worked for me thanks

---

### Post by AlanR8 on 2009-09-25
Result for you!

After today's updates all is well with Skype here as well.

---

### Post by AlanR8 on 2009-10-03
Hey all

Just did a clean install of Karmic Beta 1 today and the web cam just worked straight out the box!!!!!

---

### Post by steve101101 on 2009-10-04
sweet. im using the beta but have been using it for about a month now. glad ubuntu keeps getting better. :KS

---

### Post by AlanR8 on 2009-10-31
I've discovered something about the way Skype video seems to work on my machine.

If I start Skype in low light conditions I almost invariably get beer goggle double vision from the cam. If I start it in good light, perfect single vision.

How odd's that?

---

### Post by McGerger on 2009-11-01
> **AlanR8 said:**
> Further update!

Am now running UBUNTU Karmic Alpha 5 fully updated with the 2.6.31-10-generic Linux Kernel.

I picked up the latest driver from:

[http://www.palmix.org/r5u870-en.html](http://www.palmix.org/r5u870-en.html)

then:



and all is well!

Hello, I'm having problems after entering "make". I got this:

> 
user@ubuntu:~/r5u870$ make
make -C /lib/modules/2.6.31-14-generic/build M=/home/gerald/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/gerald/r5u870/r5u870_md.o
In file included from /home/gerald/r5u870/r5u870_md.c:55:
/home/gerald/r5u870/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
make[2]: *** [/home/gerald/r5u870/r5u870_md.o] Error 1
make[1]: *** [_module_/home/gerald/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [all] Error 2
What should I do?

---

### Post by AlanR8 on 2009-11-01
Hi McGerger.

You are using sudo make and sudo make install aren't you? If not give it a go.

---

### Post by oooh on 2009-11-03
More problems here:

- It works in ubuntu 8.10, sony vaio FZ21m, ricoh 183b camera, with driver [http://www.palmix.org/r5u870-en.html](http://www.palmix.org/r5u870-en.html) (r5u870_k2.6.27), for 2.6.27 kernel.

- But after I  hibernate, when the system recovers, the camera does not work anymore, and I get in the hibernation recovery a message like this:

Microcode file "r5u870_183b.fw" is missing
Please see [http://wiki.mediati.org/r5u870/Microcode](http://wiki.mediati.org/r5u870/Microcode)

And the FW file that system says that it does not find after hibernation IT IS in /lib/firmware/r5u870_183b.fw, so I do not know why it does not find it.

Any clue??

---

### Post by audaz17 on 2009-11-04
same problem with vaio vgn-cr160f in karmic 9.10

	
however, found the solution in

[http://bitbucket.org/ahixon/r5u87x/changesets/](http://bitbucket.org/ahixon/r5u87x/changesets/)

download using hg clone [http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)

and follow the instructions in the file readme,:p

plus this firware use uvn modele

---

### Post by alikebabay on 2009-11-08
> **audaz17 said:**
> same problem with vaio vgn-cr160f in karmic 9.10

    
however, found the solution in

[http://bitbucket.org/ahixon/r5u87x/changesets/](http://bitbucket.org/ahixon/r5u87x/changesets/)

download using hg clone [http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)

and follow the instructions in the file readme,:p

plus this firware use uvn modele

Hi! Where do I find the readme file? and the rest?

---

### Post by 2dvisio on 2009-11-09
> **AlanR8 said:**
> Hey all

Just did a clean install of Karmic Beta 1 today and the web cam just worked straight out the box!!!!!

Hey hey hey :) 
I'm writing now from the live version of Karmic and actually the webcam is not recognized.

which model of Vaio+Ricoh do you have?

Thanks for the info.

---

### Post by 2dvisio on 2009-11-09
> **2dvisio said:**
> Hey hey hey :) 
I'm writing now from the live version of Karmic and actually the webcam is not recognized.

which model of Vaio+Ricoh do you have?

Thanks for the info.


OK I realized I have a motion eye but you were talking about the model : 05ca:183b. And mine is : 05ca:1839 ...

I don't know if the two drivers are compatible if I'll do the experiment I'll poste the results ;).

CIAO

---

### Post by cfduarte on 2009-11-16
Hello!
I have the Karmic and i've downloaded it in --- [http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/) ---- select getsource and .zip ---and i done what he says  in the readme and it works perfectly now. In the paste he has the matrix models and it covers a great length of Vaios.
Thanks to all, in particularly to pihhan and P.I.M.P. that helped me very much with his posts.

---

### Post by duxi on 2009-12-01
Here's a nice tutorial!

[http://duxthefux.blogspot.com/2009/11/webcam-ricoh-r5u870-einrichten.html](http://duxthefux.blogspot.com/2009/11/webcam-ricoh-r5u870-einrichten.html)

Best regards

---

### Post by AlanR8 on 2010-02-24
Just to let followers of this thread know.

I'm now running Lucid Alpha 4 and all I have to do is install the driver, as explained elsewhere in this thread and all is well. 

Don't even have any Skype issues!

---

### Post by epvipas on 2010-02-25
Which driver are you using AlanR8? The r5u870 (non uvcvideo one) or the r5u87x which loads the firmware to then go on and use uvcvideo?

---

### Post by AlanR8 on 2010-02-25
> Ricoh R5U870 Linux Driver
Version 0.11.1, 2008/06/15

Above direct from the Help/Readme file

---

### Post by oooh on 2010-03-04
Hi there !

New updates ...

I changed to Ricoh R5U87X Linux Driver, as the R5U870 was giving no control on brightness and contrast, and the image was completelly green and dark.

R5U87X does the trick with brightness and contrast, but ...

The image in Skype is doubled and transparent. Problem is related to the allowed resolution I believe, as supported by Skype.

Cheese works perfect, gstreamer-properties perfect, xawtv as well.

Any ideas about this?

---

### Post by oooh on 2010-03-07
Problem solved!

I updated skype, to 2.1.0.81 did the trick, together with adding this in the skype config.xml:

    <Video>
      <AutoSend>1</AutoSend>
      <CaptureHeight>480</CaptureHeight>
      <CaptureWidth>640</CaptureWidth>
      <Fps>32</Fps>
      <RecvPolicy>callpolicy</RecvPolicy>
    </Video>

Now everything goes nice ! Great !

---

### Post by mblanton1234 on 2010-03-10
I have a Sony Vaio C1MZX (Japanese version) which I got from a friend last year. It looks like my Motion Eye camera is a PCI device instead of a USB device. I am a total newbie to Ubuntu (and Linux in general). I can really use some help getting the camera working.

lsusb shows this:

mblanton@mblanton-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 054c:0069 Sony Corp. Memorystick MSC-U03 Reader
Bus 001 Device 003: ID 044e:3002 Alps Electric Co., Ltd Bluetooth Device
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
mblanton@mblanton-laptop:~$ 

lspci shows this:

mblanton@mblanton-laptop:~$ lspci
00:00.0 Host bridge: Transmeta Corporation LongRun Northbridge (rev 03)
00:00.1 RAM memory: Transmeta Corporation SDRAM controller
00:00.2 RAM memory: Transmeta Corporation BIOS scratchpad
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
00:0a.0 Multimedia controller: Fujitsu Limited. Device 2011
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0c.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Non-VGA unclassified device: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 80)
00:14.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
01:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
mblanton@mblanton-laptop:~$ 

This is the only thing in lspci I can see that might be the camera:

00:0a.0 Multimedia controller: Fujitsu Limited. Device 2011

Any help is greatly appreciated.

---

### Post by oooh on 2010-03-10
I think yours has no Ricoh webcam

Have you checked [http://jcsu.jesus.cam.ac.uk/~mma29/c1/#motioneye](http://jcsu.jesus.cam.ac.uk/~mma29/c1/#motioneye) ?

---

### Post by mblanton1234 on 2010-03-10
Yes I believe the camera in my C1MZX is a PCI device.  I am running Ubuntu 9.10 dual-boot with Windows XP Pro.  The Motion Eye camera works in XP.  I looked in Windows Device Manager and the driver in XP is PCI. How would I install the driver from the site you referred to in the previous post?  I have learned how to install software with Package Manager and the Update tool, but have not figured out how to install software in Ubuntu manually yet. Modifying the Kernel in particular scares me. I have been dealing with Windows computers since 1986 but just started in Ubuntu last week. Help!

---

### Post by hugo_koopmans on 2010-05-05
Super work guys works like a charm!
I was looking for this for a long time.

Thank you

hugo

Sony Vaio SZ 61 XN 4GB RAM !!!!(they said it could not be done ...)

Ubuntu 9.04 Karmic 2.6.19-31-generic

great stuff!

---

### Post by AlanR8 on 2010-09-29
I just came across this in another thread. Since putting Maverick on the Sony Vaio VGN-FZ21S, the motion eye web cam was not working, again. 

I followed my own instructions, as above but the driver would not install.

I found this: 

> sudo add-apt-repository ppa:r5u87x-loader/ppa
sudo apt-get update
sudo apt-get install r5u87x
sudo /usr/share/r5u87x/r5u87x-download-firmware.sh

It just worked!

Run one command line at a time in terminal.

---

### Post by cannaratone on 2010-11-03
Ok, maybe not a Vaio computer but still a ricoh Webcam. Here is my situation: fresh Maverick install over a HP Pavilion (dv600?), computer has a 1870 WDM webcam. I downloaded the latest .deb packages from Arakhne.org and webcam works with a little flaw with Cheese, skype, vlc and mplayer. Only problem is that colors are some kind of messed up, so that in higher exposure areas (lights, light colors, white areas) they appear like 'burned' and turn red (some kind of 'Predator vision' !). I then tried v4l2ucp, but many settings appear to be shaded - also exposure - which seems to be responsible for the funny behaviour. If I play with 'auto exposure' or 'night mode' i can reduce the weird effect, but can't get rid of it. However, after launching and closing the program many times, sometimes the 'exposure' slider unshades (only happens when launching v4l2ucp with root privileges) and then voila! the weird colors disappear!

---

### Post by AlanR8 on 2011-04-03
Another update!

Things move on and I'm now on 11.04.

Point is that my previous solution, documented in the last couple of pages of this thread, used to just work but not on 11.04. 

So having trawled around the net for an hour I came up with this from:

[http://www.big-boogi.de/?tag=r5u870](http://www.big-boogi.de/?tag=r5u870)

> First install the needed packages:

sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial

Now we get the required software (firmware files and udev rules):

hg clone [http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)

Change directory to the currently loaded:

cd r5u87x

Make the script:

make

And the whole installation:

sudo make install

And now all is well again.

In fact, for the first time since I've had this Sony VGN-FZ21S the brightness keys work as well. Result everything working as Mr Sony intended, just NOT on his chosen OS!!!

---

### Post by nkbielst on 2011-04-05
Hi,

I have a Sony SZ650n, running maverick. Works great.

Trying to get the webcam working...Found instructions on this thread:

sudo add-apt-repository ppa:r5u87x-loader/ppa
sudo apt-get update
sudo apt-get install r5u87x
sudo /usr/share/r5u87x/r5u87x-download-firmware.sh

When running the sh script, I get this error:

cd: 78: can't cd to r5u87x

And it just quits. 

Any ideas what my problem is?

Thanks.

---

### Post by AlanR8 on 2011-04-05
> cd: 78: can't cd to r5u87x

EXACTLY the same message I was getting using my old method which is the same as you found else where! Try looking at the new method in my thread above, worked a treat for me.

Please report back.

---

### Post by nkbielst on 2011-04-05
> **AlanR8 said:**
> EXACTLY the same message I was getting using my old method which is the same as you found else where! Try looking at the new method in my thread above, worked a treat for me.

Please report back.

Thanks, Alan.

That worked beautifully.

Question: Will the PPA still provide updates, or should I remove that repository?

---

### Post by AlanR8 on 2011-04-05
> Question: Will the PPA still provide updates, or should I remove that repository?

Not a clue mate! Just happy it works for now...

---

