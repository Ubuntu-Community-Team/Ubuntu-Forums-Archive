---
title: "Carefully switching to Ubuntu :)"
date: 2008-10-28
forum: General Help
---

### Post by thomasmahler on 2008-10-28
Hey guys,

I've been dabbling with Ubuntu in the past a bit and I'm mighty impressed with 8.10 rc1 (ibex) - Also, I had quite some problems with Vista 64bit (yesterday it ran a chkdsk on my RAID Setup - in Vista, you apparently can't skip chkdsk anymore, took the machine 6 hours only to find nothing, bleh!), so Ubuntu seems more and more attractive for getting some serious work done.

Now, I sitll need to rely on a lot of Windows or OSX-only apps at the moment - especially the Adobe suite. I'm a [freelance character artist]("http://wwww.thomasmahler.com") and most of the tools I'm using are using OpenGL on Win.

Still, I have access to the 64bit versions of Maya and could get quite some work done here - so it's tempting.

Now, I wonder how well Windows App run through virtualization - I'd need at least Photoshop and ZBrush to run well on Linux. Is that possible with todays software? Photoshop and ZBrush only really make use of the (edit: oops!) CPU, so I'm guessing a good virtualization setup should probably make them work pretty well on Ubuntu. How well do these packages work for 3d stuff?

Also, I'm having a couple of problems with my intuos 3. In 8.10, it works nicely out of the box - it recognizes tablet mode and everythings fine. Now, I installed the wacom-tools package from synaptic, but I can't seem to find where I can access these tools. I'd need to make some changes to the tablet, change the button layout, the input area (constrain it to one monitor and set one of the express keys to switch to the other monitor) and so on. Are these things supposed to be under System - Preferences after installation? Cause there's nothing in there.

Would be great if you guys could help me out a bit. Windows becomes more and more of a pain in the **** to work with and these modern Linux distros are really sweet. Would love to use them for doing actual work!

---

### Post by geirha on 2008-10-28
> **thomasmahler said:**
> 
Now, I wonder how well Windows App run through virtualization - I'd need at least Photoshop and ZBrush to run well on Linux. Is that possible with todays software? Photoshop and ZBrush only really make use of the GPU, so I'm guessing a good virtualization setup should probably make them work pretty well on Ubuntu. How well do these packages work for 3d stuff?


Running the applications in a virtual machine will not let them utilize the GPU. Wine might work for that cause though. 

Zbrush has platinum and gold rating, which is promising.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12004](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12004)

Some versions of photoshop seems to be platinum as well.
[http://appdb.winehq.org/appview.php?appId=17](http://appdb.winehq.org/appview.php?appId=17)

> **thomasmahler said:**
> 
Also, I'm having a couple of problems with my intuos 3. In 8.10, it works nicely out of the box - it recognizes tablet mode and everythings fine. Now, I installed the wacom-tools package from synaptic, but I can't seem to find where I can access these tools. I'd need to make some changes to the tablet, change the button layout, the input area (constrain it to one monitor and set one of the express keys to switch to the other monitor) and so on. Are these things supposed to be under System - Preferences after installation? Cause there's nothing in there.


Sounds like a command line application, and judging by the list of files the package installs ([http://packages.ubuntu.com/intrepid/i386/wacom-tools/filelist](http://packages.ubuntu.com/intrepid/i386/wacom-tools/filelist)), there seems to be instructions on how to use it in /usr/share/doc/wacom-tools/

> **thomasmahler said:**
> 
Would be great if you guys could help me out a bit. Windows becomes more and more of a pain in the **** to work with and these modern Linux distros are really sweet. Would love to use them for doing actual work!

It's unfortunate that a lot of the commercial software developers seem to ignore linux entirely, but wine does a good job in making windows software available in linux, with varying degree of success. You might find some open source applications that can replace some of the applications you require. Gimp for image manipulation and blender for 3d rendering for example, though this is not my field, so I really have no idea if those applications are applicable for your work (which is very impressive btw!)

---

### Post by ju2wheels on 2008-10-28
I run photoshop through VirtualBox and it works quite fine. I cant even tell its in a virtual machine. In fact, Creative Suite apps load up much faster in the VM than they do on Windows, but that is the case overall since running Windows in a VM on Linux is orders of magnitudes faster than a true Windows install (on a decent machine).

---

### Post by thomasmahler on 2008-10-28
That sounds really promising! Now, I have to get some work done right now, so I can't use Linux at the moment. Thanks a lot for all the input though, great post, geirha, really appreciate it!

About the tablet: What I'm looking for is a GUI-kinda setup thing that'd let me configure the tablet much like I can in Windows / OSX - is there anything like that out there? My setup is kinda specific:

I use the thumb buttons on the Intuos as MMB and RMB (upper is MMB, lower is RMB), I use an express key to switch between my 2 displays (one click and I'm on the left display, click again and I'm on the right one), and I've set one of the express keys to 'enter', so that I can quickly work through my media library through Picasa. The command line stuff seems a bit limited in that regard, so it'd be cool if someone who has his intuos running like that could share his experience.

About the applications: A lot of apps I'm using already have Linux compiles, so that'd be neat. What I'd miss the most would be the Adobe Suite (if that runs as well as ju2wheels says, it'd be awesome) and stuff like ZBrush. This stuff really has to work stable and fast, so I can get work done.

So, under a virtual machine, none of the GPU stuff would work? The virtual machines don't work with OpenGL or DX?

---

### Post by annatar on 2008-10-28
> 
So, under a virtual machine, none of the GPU stuff would work? The virtual machines don't work with OpenGL or DX?

Indeed none of it will work. If you need OpenGL/DX support for your windows app, you have to use WINE. Mind that WINE is still...quite quacky on its DX support

---

### Post by thomasmahler on 2008-10-28
Only DX support or generally GPU Support? Does it tackle any OpenGL Apps?

---

### Post by annatar on 2008-10-28
WINE can run quite a few OpenGL apps, such as World of Warcraft (in opengl mode) and some other games

---

