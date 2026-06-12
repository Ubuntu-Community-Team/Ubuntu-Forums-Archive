---
title: "I have Ubuntu 8.04 LTS, how do I get the 3D cube desktop?"
date: 2008-09-13
forum: General Help
---

### Post by GameGuru on 2008-09-13
Saw it in action in a video and would love to do that.

---

### Post by Zzl1xndd on 2008-09-13
You'll want to go to add remove programs then type in Compiz, and the Compiz manager should be the first option in the list. Install that and then go to System -> Preferences -> advanced desktop effects, and you can manipulate the settings from there.

---

### Post by Harisz750 on 2008-09-13
ok... first go system--> administration--> hardware drivers and enable the nvidia driver for your card
then  in terminal ```
sudo apt-get install compizconfig-settings-manager

```

then right click somewhere on your desktop-->change desktop backround and in visual effects tab click extra. 
finally go system ---> preferences---> advanced desktop effects settings

then change it as you like.. personally in general settings in desktop size tab, change horizontal virtual size to 4.  then enable cube and rotate cube

---

### Post by Oldsoldier2003 on 2008-09-13
Dont forget: in order for Cube to work you need to have your visual effects set to "extra".

 After installing ccsm you'll need to enable cube and cube rotation. Also make sure you go into the genersl settings and make sure you have 4 desktops, or you wont have a cube.

---

### Post by BenAshton24 on 2008-09-13
one simple command :D
> sudo apt-get install compizconfig-settings-manager emerald && compiz  --replace
then go to "system --> preferences --> Advanced desktop settings" and check the boxes next to "cube" and "rotate Cube" done :D have a fiddle with some of the other stuff as well compiz is absolutely amazing and has tones of awesome effects

Hope this helps :D
Ben.

---

### Post by GameGuru on 2008-09-13
Under Desktop Size tab I can't increase from one desktop, it has grayed out up and down arrows.  How do I fix this?

---

### Post by SunnyRabbiera on 2008-09-13
> **GameGuru said:**
> Under Desktop Size tab I can't increase from one desktop, it has grayed out up and down arrows.  How do I fix this?

if you use compositing, your desktop size options are changed.

The horizontal size is what you need

---

### Post by GameGuru on 2008-09-14
> **BenAshton24 said:**
> one simple command :D

then go to "system --> preferences --> Advanced desktop settings" and check the boxes next to "cube" and "rotate Cube" done :D have a fiddle with some of the other stuff as well compiz is absolutely amazing and has tones of awesome effects

Hope this helps :D
Ben.

Ok Ben, I have done that but I am not getting a cube, just the one desktop.  I decided to do that command again, this is what I am getting when it installs:

jason@jasonscomputer:~$ sudo apt-get install compizconfig-settings-manager emerald && compiz --replace 
[sudo] password for jason: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compizconfig-settings-manager is already the newest version.
emerald is already the newest version.
The following packages were automatically installed and are no longer required:
  libguichan2 tmw-data
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Checking for Xgl: not present. 
Detected PCI ID for VGA: 	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
01:00.0 0300: 10de:0392 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

Ok, what is going on at the end here?  Is this why I don't have a cube?  What can I do?

---

### Post by GameGuru on 2008-09-14
> **Harisz750 said:**
> ok... first go system--> administration--> hardware drivers and enable the nvidia driver for your card
then  in terminal ```
sudo apt-get install compizconfig-settings-manager

```

then right click somewhere on your desktop-->change desktop backround and in visual effects tab click extra. 
finally go system ---> preferences---> advanced desktop effects settings

then change it as you like.. personally in general settings in desktop size tab, change horizontal virtual size to 4.  then enable cube and rotate cube

I have followed this exactly, what do I have to do to make it a cube.  I open up multiple windows of stuff but it is just normal, no cube.

---

### Post by GameGuru on 2008-09-16
Can anyone help me please?

---

### Post by ellalan on 2008-09-16
Hi
1.Cube Reflection &Deformation-Deformation is- none
2.Desktop Cube-Opacity during rotation=0, Opacity when not rotates=0
3.Rotate Cube-Bindings--Enable(mouse)-see whether you see like this-
<control><Alt><left click>
To get the rotating cube you have to press ctrl+Alt+left mouse button.

HTH.

---

### Post by GameGuru on 2008-09-16
Ok are you saying I need to set this stuff to none etc or you see mine is set to it and I need to change it.

I am new to linux.

---

### Post by fballem on 2008-09-16
> **GameGuru said:**
> Can anyone help me please?

Could you please take a snapshot of your current screen and attach it?

Thanks,

---

### Post by ellalan on 2008-09-16
Hi
I have attached some screen shots of my settings to give you general idea but there are many and I haven't tried them yet. Have fun.

---

### Post by fballem on 2008-09-16
> **ellalan said:**
> Hi
I have attached some screen shots of my settings to give you general idea but there are many and I haven't tried them yet. Have fun.

Actually, I found what I was looking for.

On your top panel, you have the Trash can. Immediately to the right, you have the workspace.

If I'm reading this right, you have only two. If you right-click on one of the workspaces, you will get a menu. Select Preferences, and change the number of columns to 4, then select close.

I'm going to work my way through the rest of this, but that may solve part of your problem.

Hope this helps,

---

### Post by fballem on 2008-09-16
> **BenAshton24 said:**
> one simple command :D

then go to "system --> preferences --> Advanced desktop settings" and check the boxes next to "cube" and "rotate Cube" done :D have a fiddle with some of the other stuff as well compiz is absolutely amazing and has tones of awesome effects

Hope this helps :D
Ben.

Tried your setup and got an error. Please see the attached screenshot - I haven't got a clue on how to fix, so some help would be much appreciated.

Thanks,

---

### Post by crazypenguin2008 on 2008-09-16
open windows on different desktops then click on each of them on the desktop bar at the bottom right hand corner beside trash. you will see the cube flip to a different workspace

---

### Post by ellalan on 2008-09-16
> **fballem said:**
> Actually, I found what I was looking for.

On your top panel, you have the Trash can. Immediately to the right, you have the workspace.

If I'm reading this right, you have only two. If you right-click on one of the workspaces, you will get a menu. Select Preferences, and change the number of columns to 4, then select close.

I'm going to work my way through the rest of this, but that may solve part of your problem.

Hope this helps,

I have got the cube working and I was trying to help gameguru, I hope you don't mind me saying you misread my post.

---

### Post by fballem on 2008-09-16
> **ellalan said:**
> I have got the cube working and I was trying to help gameguru, I hope you don't mind me saying you misread my post.

Don't mind at all - even when English is my first language (which it is), I still make the occasional mistake.

---

### Post by GameGuru on 2008-09-17
I don't have a compizconfig setting manager but I have installed compiz.  What could be wrong?

---

### Post by Therion on 2008-09-17
[How to Set Up Compiz-Fusion](http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion) (including setting up the desktop cube and stuff).

---

### Post by GameGuru on 2008-09-17
Ok I have it setup exactly like it describes but I just have a single flat desktop, no cube.  What do I do to open up more desktops?

---

### Post by MarlonDean on 2008-09-17
Look at the bottom right of your screen, next to the trashcan you will see 2 grey blocks. Right click on them , select preferences, and make columns 4. Now you have 4 desktops, which make up the 4 sides of the cube

---

### Post by GameGuru on 2008-09-17
That must be the problem, there is nothing there now.  I was annoyed when things where flipping between two different screens so I got rid of it.  How do I put it back?

---

### Post by GameGuru on 2008-09-17
Ok I figured out how to add it back and have four things going.  It rotates windows but it isn't a cube in the middle of the screen with a background.  How do I do that.  right now I just have windows rotating quickly when I go from one to another.

---

### Post by Therion on 2008-09-17
> **GameGuru said:**
> ... It rotates windows but it isn't a cube in the middle of the screen with a background.  How do I do that.
Did you follow the steps in my previous post?  It walks you through setting up the Desktop Cube...  Step-by-step.

---

### Post by karlr42 on 2008-09-17
You won't see the cube itself unlesss you press ctrl-alt click & <mouse movement>, that rotates the cube around. ctrl-alt <arrows> just jumps one screen to another. If you want to see it during that movement, change the zoom settings for Rotate Cube in the compixConfig Settings Manager

---

### Post by GameGuru on 2008-09-17
Why is this not working?  I have followed all the steps, I can hold CTRL and ALT down and use the arrow keys to switch windows and it does rotate like a full screen cube.  I want the cube that you can completely see, it is smaller on the screen, you rotate aroudn and click on it to make it full screen.  Why is this not working?

---

### Post by karlr42 on 2008-09-17
> **GameGuru said:**
> Why is this not working?  I have followed all the steps, I can hold CTRL and ALT down and use the arrow keys to switch windows and it does rotate like a full screen cube.  I want the cube that you can completely see, it is smaller on the screen, you rotate aroudn and click on it to make it full screen.  Why is this not working?
My above post explained it- you're not using the right command, to see the cube it's **hold ctrl-alt click and move the mouse**. Then with the mouse  push left or right to rotate the cube, and release ctrl-alt to drop to the screen you're currently looking at.

---

### Post by GameGuru on 2008-09-17
Ok thanks, that is working but the cube is still huge.  The video I watched show the cube smaller and it was a solid cube, mine has a cube with the actually launched programs being offset of the cube.  Is there a way to fix this?

---

### Post by karlr42 on 2008-09-17
Yes, just go to System->Preferences->CompizConfig Setting Manager, then find Rotate Cube, and move the zoom bar(bottom of the screenshot below)- controls how much the "camera" zooms out when you rotate the cube. 
[IMG]http://i523.photobucket.com/albums/w351/karlr42/Screenshot-CompizConfigSettingsMana.png[/IMG]

---

### Post by quinnten83 on 2008-09-17
you can set that up in the Compiz configuration manager
if you've allready insalled it, you should have a blue box with a diagonal arrow pointing upleft next to your clock.
If you right click on that and select settings manager, you will be in the compiz settings manager, choose the rotate cube plugin (the rotate cube) on that screen all the way to the bottom there is an option for zoom, the higher the zoom the smaller the cube.
If you want a background search in the options for a skydome.

---

### Post by GameGuru on 2008-09-17
Thank you all, I know have it working.

---

### Post by yaboyLT on 2008-09-18
hey guys... sorry to bother... ive gone thru these steps several times making sure that everything is as stated... unfortunately i cannot bring the cube up... i hold ctrl alt and then the left mouse button but this does nothing except highlight some of the page... also i changed the preferences to 4 desktops and still no cube or rotation between workspaces!! someone please help!!!! thanks- tony

---

### Post by joshc_guitar on 2008-09-18
Thanks! I just started to use ubuntu. I like so far. I really liked the cube when a friend showed it to me so I'm exited to see this work!

---

