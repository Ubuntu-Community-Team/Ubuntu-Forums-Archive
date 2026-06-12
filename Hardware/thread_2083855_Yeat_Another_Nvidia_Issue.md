---
title: "Yeat Another Nvidia Issue"
date: 2012-11-13
forum: Hardware
---

### Post by cromefx on 2012-11-13
So I bought an Asus N55S laptop, with 8 gigs ram, i7  and a Nvidia Geforce GT 635, 2 gigs. 

Great system to start developing in OGRE under Linux, right?! Very, very wrong...

After breaking my system so many times in the last 4 months trying to get my Nvidia card to work I have only learnt 2 or 3 things:

[LIST=1]
[*]Nvidia and Ubunto (or linux) mix as well as oil and vinegar.
[*]apt-get --reinstall install libgl1-mesa-glx avoids me to reinstall the whole system
[*]I'm a noob...
[/LIST]
So why didn't I just google and solved my issue? Well... I did google and did try to solve my issue, but EVERYTIME I tried to install or fiddle with Nvidia drivers I broke my system (I'm on xubuntu 12.04 BTW). Except last time where I learnt the *apt-get --reinstall install libgl1-mesa-glx* trick.


So I don't know if I'm going to be bugged off for being a noob but I have a couple of questions:

[LIST=1]
[*]Is there any *buntu version AND Nvidia driver that can coexist without my computer explode in my face in a 600x400 pixel mode?
[*]Is there anybody out there that is willing to at least show me the link (magical one I guess) where I can solve my issue as I seem to not be able to do that by myself...
[*]I need some enlightenment.
[/LIST]
Thank you gents,
cromefx

---

### Post by jerome1232 on 2012-11-13
Actually Nvidia and Linux mix well, unless your using a laptop which utilizes Optimus as Nvidia doesn't support that in their Linux drivers.

Your laptop uses Optimus.




I have no experience personally dealing with optimus, but I understand bumblebee can get it to work, I would try adding their ppa and installing it.

To add their ppa
```

sudo add-apt-repository ppa:bumblebee/stable
```To install bumblebee and nvidia drivers

```
sudo apt-get install bumblebee bumblebee-nvidia

```Let us know how it goes or if you've already tried that.

Linky to Bumblee project:  [http://bumblebee-project.org/index.html](http://bumblebee-project.org/index.html)

---

### Post by cromefx on 2012-11-13
will be back in a few minutes, I hope *apt-get --reinstall install libgl1-mesa-glx* trick works again... :)

---

### Post by cromefx on 2012-11-13
Is this good news?

> tsunami@N55SL-xubuntu-12-4:~$ glxspheres
Polygons in scene: 62464
Visual ID of window: 0xa7
Context is Direct
OpenGL Renderer: Mesa DRI Intel(R) Sandybridge Mobile 
59.925563 frames/sec - 66.876928 Mpixels/sec
59.763443 frames/sec - 66.696002 Mpixels/sec
59.484619 frames/sec - 66.384835 Mpixels/sec
59.959308 frames/sec - 66.914588 Mpixels/sec
60.146596 frames/sec - 67.123601 Mpixels/sec
59.908401 frames/sec - 66.857776 Mpixels/sec
59.828857 frames/sec - 66.769004 Mpixels/sec
tsunami@N55SL-xubuntu-12-4:~$ optirun glxspheres
Polygons in scene: 62464
Visual ID of window: 0x21
Context is Direct
OpenGL Renderer: GeForce GT 635M/PCIe/SSE2
103.176459 frames/sec - 115.144928 Mpixels/sec
117.107757 frames/sec - 130.692256 Mpixels/sec
109.170391 frames/sec - 121.834157 Mpixels/sec
119.371814 frames/sec - 133.218945 Mpixels/sec
121.364292 frames/sec - 135.442550 Mpixels/sec
112.987460 frames/sec - 126.094006 Mpixels/sec
115.263513 frames/sec - 128.634080 Mpixels/sec
110.055245 frames/sec - 122.821654 Mpixels/sec
109.943983 frames/sec - 122.697486 Mpixels/sec

And I have never had Nvidia drivers listed in the Additional Drivers, will restart now :))) and update

---

### Post by cromefx on 2012-11-13
OK, so after

> sudo apt-get install bumblebee bumblebee-nvidiaI do have Nvidia list on the additional drivers, but after restarting in order to finish the installation, there are no more additional drivers there.

then I

> sudo apt-get install bumblebee bumblebee-nvidiaagain and the drivers are there. After activating and restart they disappear again...

but at least I have:

> tsunami@N55SL-xubuntu-12-4:~$ optirun glxspheres
Polygons in scene: 62464
Visual ID of window: 0x21
Context is Direct
OpenGL Renderer: GeForce GT 635M/PCIe/SSE2
120.180973 frames/sec - 134.121966 Mpixels/sec
123.570745 frames/sec - 137.904951 Mpixels/secwhich makes me believe the Nvidia is being used.



On the other side:

> Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources
  504  Gateway Time-out
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages
  504  Gateway Time-out
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages
  504  Gateway Time-out
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Fetched 5,150 B in 2min 2s (42 B/s)
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  504  Gateway Time-out

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages)  504  Gateway Time-out

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  504  Gateway Time-out

E: Some index files failed to download. They have been ignored, or old ones used instead.I will now try with OGRE.

---

### Post by cromefx on 2012-11-13
OGRE is not working anymore. :(

> 00:29:37: GLRenderSystem::_createRenderWindow "TutorialApplication Render Window", 1024x768 fullscreen  miscParams: FSAA=0 displayFrequency=60 Hz gamma=No vsync=No 

00:29:37: OGRE EXCEPTION(3:RenderingAPIException): Unexpected failure to determine a GLXFBConfig in GLXWindow::create at /home/tsunami/Programming/Ogre/OgreSource/ogre_src_v1-8-1/RenderSystems/GL/src/GLX/OgreGLXWindow.cpp (line 304)
00:29:37: *-*-* OGRE ShutdownIt was working before in fullscreen.

---

### Post by cromefx on 2012-11-13
After
> apt-get purge nvidia-currentand
> apt-get --reinstall install libgl1-mesa-glxI can run OGRE again.

Of course optirun glxspheres is a no go, so I'm back to this setup until further information.

Thank you very much jerome1232

---

### Post by jerome1232 on 2012-11-13
Well the link I provided at the end of my first post does have some troubleshooting steps if you run into problems with bumblebee, I would check that out.

Unforunatly due to lack of personal experience dealing with this that's the most help I can be.

---

### Post by cromefx on 2012-11-13
T[FONT=Arial]hank you again, I am on bumblebee page now and I guess that should be the the path to success.

from their page I did:

[/FONT][FONT=Arial]> sudo add-apt-repository ppa:bumblebee/stable
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates sudo apt-get updateand it worked well until I restarted (OGRE and optirun glxspheres) .

I purged again to be able to work normally, though now my computer is lagging while writing and scrolling the browser, copy/paste, etc...
[/FONT]
:confused::(

---

### Post by jerome1232 on 2012-11-13
[https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting](https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting) try this

---

### Post by cromefx on 2012-11-13
I am there :)

---

### Post by cromefx on 2012-11-13
> **jerome1232 said:**
> [https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting](https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting) try this

So from this link I purged everything again, installed it again and... GREAT even after restart I have optirun running AND OGRE running with or without optirun :)

Still a few issues regarding the additional drivers (not there) and dual monitor but nothing compared to this issue. My fps went from 50's to 120...

Thank you very, very much jerome1232, you made my month :)

I will now try to install Nvidia config, which gave me problems before...

---

### Post by jerome1232 on 2012-11-14
Don't install anything nvidia, you're using an opensource driver bumblbee which allows you to switch between your two cards. If you want to run something with your nvidia card launch it from a terminal with optirun, if you launch something a lot i'd suggest making a launcher for it (install alacarte to make new launchers easily)

ie if I wanted to run minecraft and I had an optimus setup

```
optirun java -jar minecraft.jar
```

---

