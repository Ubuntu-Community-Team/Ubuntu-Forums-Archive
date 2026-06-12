---
title: "3d modelling programs similar to 3d Studio Max 4 or Gmax"
date: 2008-07-10
forum: General Help
---

### Post by vandorjw on 2008-07-10
Are there any 3d modelling programs that are somewhat cloned off 3ds max 4?

I want a program where you can just place an object on the working area, right click it, and do stuff like "convert to editable mesh" or "convert to editable poly" and stuff like that so you can easily make models.

The features are most important, I want to be able to make models that you can look at, not really coded/rigged models for gaming. I have blender3d, and it is painful. I also have wings3d.

What things are easier to use than those two? I just want to make models.

IF there are none, then please link me to topic that shows how to install virtual box, and then winXP in virtual box.

From there, I could just install gmax 1.2 in the virtual winXP. (I know it works because others have done it.... it was some guy at turbosquid)

---

### Post by DagMan on 2008-07-12
I've never used it, but there is a 3d program called, I think, blender.  I havent used any programs on any platforms to really compare them.

as for virtualbox it won't give you graphics acceleration if your software requires it. If it suffices, you can download it in the repos, virtualbox-ose and virtualbox-ose-modules
virtualbox-ose-modules will give you a selection of what to install matching your kernel. 

You can also download virtualbox from their site, google it, download it, checking all the 'I agree' boxes, and be sure to select the 8.04 ubuntu version, or hardy ubuntu, or whichever version you are running, then open a terminal and navigate to where you downloaded the file
```
sudo dpkg -i *irtual*deb
```
if yuo do the second method here, you'll have to add yourself tothe virtualbox group
```
sudo gpasswd -a YOURUSERNAME vboxuser
```
this wont take effect until after loggin out and back in

and if the kernel module didn't get built
```
sudo /etc/init.d/vboxdrv setup
```

the following is a crude explanation but searching the how to forum section should suffice if you run into a problem
pop in an xp disk hit New, select os type, new disk image, dynamically expanding, set the boot order, ram to set aside, video ram, etc... follow the prompts basically, put the cd option to use your systems cdrom and set the boot order, select the vm and hit start, it will install as normal in a small window.  You can add guest extentions later to get better functionality.  I really recommend just searching the how to section or using google to find something that will walk you through with screenshots.  Here's where you want to look in this forum, and there's a search function on the page [http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)
There is also a forum elswhere specifically for virtualbox.

---

### Post by vandorjw on 2008-07-14
thanks for the help... i see what I can do.

---

### Post by WinterWeaver on 2008-08-02
If you ask me, Blender3d is amazing. The biggest issue people have with it, is because it's VERY different from what everyone is used to.

The whole interface and the way you do things is different, and if you approach it the way you use other apps, like 3dMax and Maya, then yes, it will be painful.

I suggest that you empty your cup, take blender3d and go through the online tutorials (which is very good). There are even a couple of video tutorials.

Blender3D is actually a very powerful product, and once you get to know it a bit better, you will see why.

in the end it's up to you :)

have fun!

^_^

---

### Post by rainwalker on 2008-08-02
+1 for Blender; I haven't really gotten the hang of it, but there's already been one movie short made with it, called Elephant's Dream.

---

### Post by WinterWeaver on 2008-08-02
Actually... it's 3 I think

The last one was of a Bunny or something ^_^

---

### Post by rainwalker on 2008-08-02
> **WinterWeaver said:**
> Actually... it's 3 I think

The last one was of a Bunny or something ^_^

Ah, you're right! Apparently the latest one was Big Buck Bunny, released in April...didn't know that :)

---

### Post by ibuclaw on 2008-08-02
+1 Blender :)

And yes, [Big Buck Bunny]("http://www.bigbuckbunny.org/index.php/download/") it is called.

Made entirely with Ubuntu, Blender, Python, Gimp and Inkscape :D

Regards
Iain

---

