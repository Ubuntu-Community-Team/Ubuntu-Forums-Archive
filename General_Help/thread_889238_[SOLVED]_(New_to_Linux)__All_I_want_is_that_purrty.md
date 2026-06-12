---
title: "[SOLVED] (New to Linux)  All I want is that purrty AWN dock!"
date: 2008-08-13
forum: General Help
---

### Post by kevzik on 2008-08-13
Before I explain my deal, let me start be saying I am pretty new to Linux.  Minimal experience, but with your help, I am sure I can accomplish getting that dock to work.  

I should note I am having problems running the gnome session.  Instead I have to run failsafe.  That seems to work run, however, in the gnome session, I get stuck in a login loop (yes, I ran updates).  From the little research I have done, it seems like it might be a video card issue.  I believe mine is a integrated ati card.  Could this problem prevent me from getting the dock to appear?

On to the dock...

I followed these steps perfectly (twice, even did a reinstall of the OS) from this website:

[http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml](http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml)

After finishing those steps, I go to Accessories and open AWN, however, only a 1"x1" grey box appears in the upper left corner and disappears.  I am stumped.

Here is the log of my steps:

```
kevzik@kevzik-linux:~$ sudo apt-get install awn-manager-trunk awn-extras-applets-trunk
[sudo] password for kevzik: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  avant-window-navigator-data-trunk avant-window-navigator-trunk libawn0-trunk
  libwebkit-1.0-1 python-awn-trunk
Recommended packages:
  cairo-clock libvte python-alsaaudio python-libgmail vala-awn-trunk
The following NEW packages will be installed:
  avant-window-navigator-data-trunk avant-window-navigator-trunk
  awn-extras-applets-trunk awn-manager-trunk libawn0-trunk libwebkit-1.0-1
  python-awn-trunk
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 7032kB of archives.
After this operation, 25.2MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  libawn0-trunk python-awn-trunk avant-window-navigator-trunk
  avant-window-navigator-data-trunk libwebkit-1.0-1 awn-extras-applets-trunk
  awn-manager-trunk
Install these packages without verification [y/N]? Y
Get:1 http://ppa.launchpad.net hardy/main libawn0-trunk 0.3.1~bzr459-hardy1-1 [73.7kB]
Get:2 http://ppa.launchpad.net hardy/main python-awn-trunk 0.3.1~bzr459-hardy1-1 [29.8kB]
Get:3 http://ppa.launchpad.net hardy/main avant-window-navigator-trunk 0.3.1~bzr459-hardy1-1 [61.9kB]
Get:4 http://ppa.launchpad.net hardy/main avant-window-navigator-data-trunk 0.3.1~bzr459-hardy1-1 [261kB]
Get:5 http://ppa.launchpad.net hardy/main libwebkit-1.0-1 0~svn32442-1~ppa1.1 [2742kB]
Get:6 http://ppa.launchpad.net hardy/main awn-extras-applets-trunk 0.3.1~bzr812-hardy1-1 [3812kB]
Get:7 http://ppa.launchpad.net hardy/main awn-manager-trunk 0.3.1~bzr459-hardy1-1 [52.6kB]
Fetched 7032kB in 17s (400kB/s)                                                
Selecting previously deselected package libawn0-trunk.
(Reading database ... 95910 files and directories currently installed.)
Unpacking libawn0-trunk (from .../libawn0-trunk_0.3.1~bzr459-hardy1-1_i386.deb) ...
Selecting previously deselected package python-awn-trunk.
Unpacking python-awn-trunk (from .../python-awn-trunk_0.3.1~bzr459-hardy1-1_i386.deb) ...
Selecting previously deselected package avant-window-navigator-trunk.
Unpacking avant-window-navigator-trunk (from .../avant-window-navigator-trunk_0.3.1~bzr459-hardy1-1_i386.deb) ...
Selecting previously deselected package avant-window-navigator-data-trunk.
Unpacking avant-window-navigator-data-trunk (from .../avant-window-navigator-data-trunk_0.3.1~bzr459-hardy1-1_all.deb) ...
Selecting previously deselected package libwebkit-1.0-1.
Unpacking libwebkit-1.0-1 (from .../libwebkit-1.0-1_0~svn32442-1~ppa1.1_i386.deb) ...
Selecting previously deselected package awn-extras-applets-trunk.
Unpacking awn-extras-applets-trunk (from .../awn-extras-applets-trunk_0.3.1~bzr812-hardy1-1_i386.deb) ...
Selecting previously deselected package awn-manager-trunk.
Unpacking awn-manager-trunk (from .../awn-manager-trunk_0.3.1~bzr459-hardy1-1_all.deb) ...
Setting up libawn0-trunk (0.3.1~bzr459-hardy1-1) ...

Setting up python-awn-trunk (0.3.1~bzr459-hardy1-1) ...

Setting up libwebkit-1.0-1 (0~svn32442-1~ppa1.1) ...

Setting up awn-extras-applets-trunk (0.3.1~bzr812-hardy1-1) ...

Setting up avant-window-navigator-trunk (0.3.1~bzr459-hardy1-1) ...

Setting up awn-manager-trunk (0.3.1~bzr459-hardy1-1) ...

Setting up avant-window-navigator-data-trunk (0.3.1~bzr459-hardy1-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
kevzik@kevzik-linux:~$ 

```

Did anything go wrong?  Why is a grey box appearing and disappearing?  Is the failsafe session causing this?"

THANK YOU GUYS...HOPEFULLY I WASN'T TOO NOOBISH.  I am now realizing the importance of linux and really want to learn it like I know...windows.

---

### Post by Vadi on 2008-08-13
In the terminal, type "avant-window-navigator" and press enter. What does it say?

---

### Post by Lexrst on 2008-08-13
Gnome running in failsafe mode probably inhibits your ability to run a compositing Window Manager (like CompizFusion).  If you're not running a compositing Window Manager, you can't run AWN.

I think you need to fix the video card issue first, then make sure you can either enable 'Extra' in System -> Preferences -> Appearance -> Visual Effects (the easy quick way) or install and run Compiz Fusion from the Synaptic Package Manager.

AWN won't run unless those issues are cleared up first.

Cheers,
Lexrst

---

### Post by kevzik on 2008-08-13
Thanks you both :)

```
kevzik@kevzik-linux:~$ avant-window-navigator

(awn-applets-migration.py:6600): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `AwnConfigClient'
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.


```

---

### Post by kevzik on 2008-08-13
Just wanted to say thanks again.  I am able to run the dock fine now.  it was a VC issue.  Updated the driver and now I am in business.

:guitar:

---

### Post by Vadi on 2008-08-14
Excellent. Please click on 'Thread Tools - Mark Thread as Solved', so that others will have an easier time when they're looking for a solution.

---

### Post by dreamfly911 on 2008-08-27
> **kevzik said:**
> Just wanted to say thanks again.  I am able to run the dock fine now.  it was a VC issue.  Updated the driver and now I am in business.

:guitar:

hi,kevzik :

i installed the ubuntu 8.04 in the vmware virtual machine.
i encountered exactly the same problem with you when i open the AWN.
can you tell me how to fix this problem?
great thanks to you!

[email]dreamfly912@gmail.com[/email]

---

### Post by Vadi on 2008-08-27
I'm afraid that you cannot enable 3d compositing in vmware, which is what AWN requires.

You need to "really" install Ubuntu to get 3d compositing and thus awn.

---

