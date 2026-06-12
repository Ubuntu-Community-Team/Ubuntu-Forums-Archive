---
title: "How do I enable that rotating cube thing for Ubuntu's different windows?"
date: 2008-10-02
forum: General Help
---

### Post by riahc3 on 2008-10-02
How do I enable that rotating cube thing for Ubuntu's different windows? Ive tried the settings and setting the horizontal setting to 4 but nothing. How do I get it to work?

---

### Post by Ryadt on 2008-10-02
> **riahc3 said:**
> How do I enable that rotating cube thing for Ubuntu's different windows? Ive tried the settings and setting the horizontal setting to 4 but nothing. How do I get it to work?
Go in System > Preferences > Advanced Desktop... In Category, click on Desktop and then check 'Desktop cube' and 'Rotate cube'.

---

### Post by mocoloco on 2008-10-02
You may first need to install the settings tool before you can do what Ryadt says, open Add/Remove Applications and search for "advanced" and install the "Advanced Desktop Effects Settings".

---

### Post by Aero-Z on 2008-10-02
+ it's the wrong subforum. Check the right forum's very first sticky post: [Desktop Effects & Customization]("http://ubuntuforums.org/forumdisplay.php?f=330")

---

### Post by riahc3 on 2008-10-02
> **Ryadt said:**
> Go in System > Preferences > Advanced Desktop... In Category, click on Desktop and then check 'Desktop cube' and 'Rotate cube'.

Already done.

> **mocoloco said:**
> You may first need to install the settings tool before you can do what Ryadt says, open Add/Remove Applications and search for "advanced" and install the "Advanced Desktop Effects Settings".

Already done too....


What else?

---

### Post by Brain-free on 2008-10-02
Uhm... CTRL + ALT + <<click>> ?

Really, if you've done all this and Desktop Cube ad Rotating Cube are ticked, I.. I really don't know...

---

### Post by riahc3 on 2008-10-02
> **Brain-free said:**
> Uhm... CTRL + ALT + <<click>> ?

Really, if you've done all this and Desktop Cube ad Rotating Cube are ticked, I.. I really don't know...

Then if you "really don't know" why are you posting?

---

### Post by Brain-free on 2008-10-03
<<Not another YouTube comment...>> 

I don't know what else can be done besides ticking the corresponding boxes and pressing CTRL + ALT + BUTTON1. 

Unless... what kind of graphics card do you use? It must have 3d acceleration for the compiz to work.

---

### Post by Aero-Z on 2008-10-03
First you got to enable Desktop Cube and Rotate Cube effect. Then check the bindings under Rotate Cube effect. I think you also need to make 4 virtual desktops instead of the default two desktops.

---

### Post by riahc3 on 2008-10-03
> **Brain-free said:**
> <<Not another YouTube comment...>> 

I don't know what else can be done besides ticking the corresponding boxes and pressing CTRL + ALT + BUTTON1. 

Unless... what kind of graphics card do you use? It must have 3d acceleration for the compiz to work.

I have a GeForce 8400GS M which is perfectly compatible.


> **Aero-Z said:**
> First you got to enable Desktop Cube and Rotate Cube effect. Then check the bindings under Rotate Cube effect. I think you also need to make 4 virtual desktops instead of the default two desktops.

How Do I set that? I think I have 4 desktops, and in the bottom-right I have 4 horizontal desktops selected.

---

### Post by Aero-Z on 2008-10-03
> **riahc3 said:**
> I have a GeForce 8400GS M which is perfectly compatible.




How Do I set that? I think I have 4 desktops, and in the bottom-right I have 4 horizontal desktops selected.
Do you have the effects enabled at all and are working? Are your windows wobbling and all?
Yup, that's what I ment - 4 desktops at bottom right corner.
Didn't you find the Cube settings?

---

### Post by riahc3 on 2008-10-04
I have 4 and 4 set but Ctrl+Alt+Lclick dont do anything.

---

### Post by riahc3 on 2008-10-06
Maybe some of you don't understand what IM saying.


IM saying there is a key combo that zooms out my display and makes me see a full 3D cube where I can click on a side of a cube or press a key and change workspaces.

---

### Post by mondoUNC on 2008-10-06
It's called Cube Reflection, found in Compiz settings whatever.

---

### Post by bharadwaj on 2008-10-06
The default keys for activating it are [ctrl][alt]{left mouse button} 
Have you checked if the above key binding is used for any other application?
Below is a useful link. I  am sure you will have no problem following that :)

[http://mikecantelon.com/story/getting-rotating-desktop-cube-working-ubunutu-hardy-heron](http://mikecantelon.com/story/getting-rotating-desktop-cube-working-ubunutu-hardy-heron)

---

### Post by vrodkaraf on 2008-10-13
Ok, I'm wigging out.  I can't find the cube tool!  It's not offered as you describe above.  There is NO category called desktop.  Searching on 'advanced' in the add/remove apps window does not bring one up. 

I have installed the nvidia-glx package, it looks like the nvidia-glx-new may not support the old GeForce4 Ti...?  Could this be my problem?

Other ideas?  :confused:

My Compiz output is:
 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a3)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Could not check the amount of memory on your Nvidia chip. 
=================================================================

Thanks!

---

