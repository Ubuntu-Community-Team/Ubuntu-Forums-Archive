---
title: "ATI Radeon Xpress 200M Support"
date: 2009-11-12
forum: Hardware
---

### Post by dcmatt on 2009-11-12
Hello folks,

I'm new to Linux/Ubuntu [9.10], but am usually pretty good at figuring things out for myself.  That said, I'm having a heck of a time getting my video card fully supported.

I have a Compaq V2710US configuration of the Presario V2000; it has integrated ATI Radeon Xpress 200M video.  Ubuntu is running fine and the laptop LCD works at its native resolution in gdm; looks great in 2D, but the system will simply not support OpenGL.

I've installed the packaged for EnvyNG but it indicates my ATI Radeon Xpress 200M isn't supported (the available ATI driver is not recommended & not compatible.)  I've installed the proprietary driver via other means and, after installation, don't even see it in the list under "Hardware Drivers" as something I can enable.

I've attempted to utilize the ATI open source drivers as well but have had no luck  in getting openGL supported.

I've spent about 10 hours searching and trial-and-erroring every walkthrough I can find for ATI video support, all to no avail.

I feel like there's something critical and simple that I'm missing here.  Please help!

---

### Post by ublintu on 2009-11-12
Hi,

I had the same question in here: (post #6 and #7)  [http://ubuntuforums.org/showthread.php?t=1307044&highlight=200m](http://ubuntuforums.org/showthread.php?t=1307044&highlight=200m)
I don`t know much about it.

---

### Post by dcmatt on 2009-11-12
Hello Ublintu and thank you for your reply.  I saw that thread when I was surfing to find answers; I've also stumbled on the link you posted in your last comment on that thread ([https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver))

I tried to follow all the steps in that link but got hung up at 
glxinfo |grep vendor
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri

I had to force my system to generate an Xorg.conf file, which I moved into the /etc/X11 location.  Following the steps in that linked walkthrough thereafter have not really fixed it.

I'm at a loss!

---

### Post by ublintu on 2009-11-12
Actually when I did not find xorg.conf file, I stopped to follow the how to. I did not do anything with Xorg.conf (I just don`t wanted to reinstall ubuntu again... I did it sooo many times in 9.04) After this I enabled effects, installed compiz and it`s working 4 me. It isn`t in the Hardware Drivers list, but maybe it`s working, because compiz is working fine. 4 me this was the same situation in 9.04.

---

### Post by dcmatt on 2009-11-12
Hm. It might be a problem that is unique to the specific build of my laptop.  When I get home tonight I will try again to follow the steps in that link.

When you say "after this I enabled effects", can you tell me what you did?

---

### Post by ublintu on 2009-11-12
system-preferences-appearance-visual effects and after this I installed compiz. It`s workin, but  like in 9.04 no 3D games or really slow and ati isn`t in the  Hardware Drivers list. I did just this much. I`m still searching in the forum 4 better solution... At least I have effects :)

---

### Post by Yellow Pasque on 2009-11-12
> It isn`t in the Hardware Drivers list, but maybe it`s working
Only the proprietary driver shows up there. Since your card is unsupported by the proprietary driver, nothing shows there.

---

### Post by ublintu on 2009-11-12
Hi Temüjin,
Thank you 4 the answer. I see, understand.
+ I found this at the end of the guide:

"To see if you are using the driver you can test your 3D settings. To test your OpenGL acceleration you can run: 
$ glxinfo | grep vendor
This has to be SGI. Otherwise you did not install the driver properly."

I got this:
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: DRI R300 Project

---

### Post by dcmatt on 2009-11-12
Glad to hear you're still looking for the answer.

When I try to glxinfo | grep vendor I get:

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16

This is awfully frustrating.

Edited to add:  I just tried to enable desktop effects.  "Desktop effects could not be enabled."

Edited to also add: lspci -nn | grep VGA reports "01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) [1002:5955]" but according to the open source ATI driver guide it should be reporting it with an end string such as "AS [RS482 IGP]".

---

### Post by Yellow Pasque on 2009-11-12
dcmatt: do you have these issues with a LiveCD>?

---

### Post by dcmatt on 2009-11-12
Running the LiveCD now

**glxinfo | grep vendor**
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: DRI R300 Project

**lspci -nn | grep VGA**
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) [1002:5955]

Does this mean I screwed something up in the install?

edited to add: enabling desktop effects also worked no problem

---

### Post by Yellow Pasque on 2009-11-12
If you've ever tried to install the proprietary drivers, make sure you you purge them: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-nvidia%20and%20reinstall%20-nv%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-nvidia%20and%20reinstall%20-nv%20from%20scratch)

If that doesn't fix things, then maybe post (or pastebin) your /var/log/Xorg.0.log

---

### Post by ublintu on 2009-11-12
I get this:
lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]

"When I try to glxinfo | grep vendor I get:" Sorry but I don`t know why you get error. I`m just guessing, I don`t know, but you did something with the Xorg.conf file, what I did not... If you don`t generate one there...?

I need to go now. I will come back later.

---

### Post by dcmatt on 2009-11-12
Temüjin - that fixed it!!  I thought I had purged everything but clearly not.  Now I've enabled desktop effects and they work, which I've been told means OpenGL is functioning.  That said, trying to use glChess 2.28.0 in 3D mode returns an error saying no OpenGL support was found.  I think that's what started me down the proprietary driver path in the first place.

Is this a known issue?

---

### Post by Yellow Pasque on 2009-11-12
Install the python-opengl package (I forget the exact name) for 3D in glChess.

---

### Post by dcmatt on 2009-11-12
HALLELUJIAH!!!

Temüjin, the next time you are in Washington, DC, I owe you one tall frosty beer.

**THANK YOU!!!**

---

### Post by ublintu on 2009-11-13
Good for you, it`s working now.
Just to understand what happened: The problem was you did not purge remove fglrx? And what about if I did not configure Xorg.conf. Am I need to?
Now I have an other problem: About 2 days earlier, I did an update. It installed lots of packages and I can remember just for a kernel update. After this, I rebooted and after the white ubuntu logo I get a black screen with this:
Ubuntu 9.10 ublintu-laptop tty1
ublintu-laptop login:
After when I restart my laptop, it`s boot normally, like as usual. This happening about every second time.
I will post this somewhere else.

---

### Post by dcmatt on 2009-11-13
Ublintu,

Yes, that appears to be the problem. I could've sworn I had purged it.  A thought occurred to me as I was going through that purge process - fully stopping the graphics and going to a true terminal mode would probably ensure the full removal of all the graphics drivers.  Hard to get rid of something while it's actually in use.  Perhaps not the right answer but a step that may have impeded my earlier efforts.

What you're seeing looks to me like the normal non-graphical login screen.  Why it would intermittently be used rather than the graphical log-in is vastly beyond my knowledge.

---

### Post by Tomy on 2009-11-13
> **Temüjin said:**
> If you've ever tried to install the proprietary drivers, make sure you you purge them: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-nvidia%20and%20reinstall%20-nv%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-nvidia%20and%20reinstall%20-nv%20from%20scratch)

If that doesn't fix things, then maybe post (or pastebin) your /var/log/Xorg.0.log

I knew this. 

But I forgot.

Thanks for the reminder. Ubuntu and the great community here just rocks. 

My ati Xpress 200 now works with compiz. Things are a little jerky though -- maybe if I look around I'll find some Xorg.conf settings that help.

---

### Post by stevew45 on 2009-12-12
> **dcmatt said:**
> Hello folks,

I'm new to Linux/Ubuntu [9.10], but am usually pretty good at figuring things out for myself.  That said, I'm having a heck of a time getting my video card fully supported.

I have a Compaq V2710US configuration of the Presario V2000; it has integrated ATI Radeon Xpress 200M video.  Ubuntu is running fine and the laptop LCD works at its native resolution in gdm; looks great in 2D, but the system will simply not support OpenGL.

I've installed the packaged for EnvyNG but it indicates my ATI Radeon Xpress 200M isn't supported (the available ATI driver is not recommended & not compatible.) ** _I've installed the proprietary driver via other means _**and, after installation, don't even see it in the list under "Hardware Drivers" as something I can enable.

I've attempted to utilize the ATI open source drivers as well but have had no luck  in getting openGL supported.

I've spent about 10 hours searching and trial-and-erroring every walkthrough I can find for ATI video support, all to no avail.

I feel like there's something critical and simple that I'm missing here.  Please help!

By what other means did you install it? is it just the default policy script preventing it or what?

---

### Post by emeraldgirl08 on 2010-01-03
Don't mean to drag up an old thread but I have an IBM Thinkpad R51e that has the X200M graphics. 

The graphics by default seem to work very well with my machine. I just happened to be searching for info for someone and stumbled into this thread.

I have my Chess in 3D now also!!! It is a little buggy and picky. Try moving the window and it reverts to 2D. You have to go into view and tick off and on 3D again for it work.

Here is how I did my tweaking:

a)started off the default graphics. What I mean by this is I never edited any kind of scripts or tweaked anything. My graphics are from the install default graphic settings.

b)Went into the synaptic package manager>> typed Python-OpenGL>> installed python-opengl and marked it for install>> applied it and it installed.

c)ran the chess game...still no 3D. I got a "Python GTKGLExt" needed. Went back to Synaptics.

d)typed in python-gtkglext>> there will be a couple of them. I installed the one designated as python-gtkglext1. Checking this actually checked two boxes>> and then installed.

Now the 3D in chess works.

Here is my glxgears FPS in minimum sized window:

```
4195 frames in 5.0 seconds
4246 frames in 5.0 seconds
4229 frames in 5.0 seconds
4268 frames in 5.0 seconds
4226 frames in 5.0 seconds
4271 frames in 5.0 seconds
4242 frames in 5.0 seconds
4242 frames in 5.0 seconds
4273 frames in 5.0 seconds
4212 frames in 5.0 seconds
4292 frames in 5.0 seconds

```

In full screen:

```
768 frames in 5.0 seconds
770 frames in 5.0 seconds
772 frames in 5.0 seconds
770 frames in 5.0 seconds
771 frames in 5.0 seconds
773 frames in 5.0 seconds
770 frames in 5.0 seconds
769 frames in 5.0 seconds

```

My glxinfo | grep vendor:

```
nurset@nurset-laptop:~$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: DRI R300 Project

```

First of all. I'm amazed that an economy model older Thinkpad can pull this off :)

I should mention that I have wolfenstein enemy territory installed on this laptop also. It plays okay. I don't know how to measure framerate but it's definitely playable.

So hopefully this helps out anyone who has an affinity for the older model laptops that has this type of graphics card.

---

