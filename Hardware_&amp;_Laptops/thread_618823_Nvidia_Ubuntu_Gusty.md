---
title: "Nvidia Ubuntu Gusty"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by l2thet on 2007-11-20
Alrighty, trying to find a little bit of help here.  Currently I am using a Geforce 7700 GT.  I started, went from a XP pc, and formated and installed with a Gusty CD.  The install went smooth, however I had a long battle after the first boot up with how Nvidia restricted drivers and dual screens with Xinerama.  Eventually I disabled them, and removed the second monitor, so I can get into X. 

   Currently though I am having a lot of problems with my FPS when doing anything with OpenGL.  3GHz 2gigs DDR2, and the 7700GT video card, and glxgears will give me a max of 2000fps, and thats if im not doing anything else on the system.When I play WoW with the -opengl, and a resolution of 800x600, I am sitting at 20FPS when I am looking at a wall................  I have attached my xorg.conf file, also my Xorg.0.log which is zipped.  I have enabled all the extra tweaks to my xorg.conf file that I can find from nvidia and other websites, and glx works.  It is just driving me up the wall that it is running this slow.  The one other thing I have tried to switch from AGPGART to the Nvidia AGP driver, however I cant seem to disable AGPGART, I have it in my blacklist, and in the /etc/modules  I have added the nvidia-agp, however after a boot, when I do a 
cat /proc/driver/nvidia/agp/status    I get

Status: Disabled

Glx still works however, I have read that I need to recompile my kernel, because AGPGARP is not loaded as a module, but after I get the source for this kernel then do a 
sudo make menuconfig
I cant even find the AGPGARP option,  doing a /    and searching reveals nothing.  I tried the linux-Headers as well, with no luck.  This is just frustrating as its been about a week of researching and nothing has come up with a solution.  I have a whole new set of components coming in, in the next couple of days, and if I cant get this to run any faster I will have to go back to XP just so I can play games :(

So frustrating it makes me want to kick a baby kitten :(

---

### Post by nick_h on 2007-11-20
Try changing:

Option "NvAGP" "3"

to

Option "NvAGP" "1"

---

### Post by l2thet on 2007-11-20
K gave it a shot, its still showing disabled.  All there other thing my xorg.conf should have in it besides "glx"?

---

### Post by l2thet on 2007-11-21
Where could I look to figure out why my FPS is so low with glxgears?

---

### Post by nick_h on 2007-11-21
You may have to disable another agp module in addition to agpgart.  Type:
```
lsmod | grep agp
```
and see if there is another agp module loaded.

I didn't add nvidia-agp to my /etc/modules either.

The NvAGP options are (from the Nvidia readme):
    Option "NvAGP" "0"  ... disables AGP support
    Option "NvAGP" "1"  ... use NvAGP, if possible
    Option "NvAGP" "2"  ... use AGPGART, if possible
    Option "NvAGP" "3"  ... try AGPGART; if that fails, try NvAGP

There is another thread giving instructions [here](http://ubuntuforums.org/showthread.php?t=589794).

---

### Post by l2thet on 2007-11-21
At work, but when I get home I will give that a try.  I remember one of the steps that I did, was blacklisting AGPGARP and AGPGARP_64?(sp), as the note from the forum I was looking at stated that both needed to be blacklisted,as one requires the other... not for sure though.  Last night I did do a lsmod, and found that nvidia-agp was there, even though AGPGARP was currently the driver running.  Its a bit confusing but I will look it over again tonight, and post if it worked or not, if it does great, hopefully that will get more over 2k FPS with glxgears..... if not, my new hardware arrives today, and I will install that, hopefully a fresh install of Gusty with a new nvidia card, maybe this time it will install correctly.... and I can play WoW without 20FPS, which is just sad for the hardware I have, if it doesnt then I guess its back to XP /sigh.

---

### Post by l2thet on 2007-11-21
K when I do a lsmod | grep agp, here is what I get
lsmod | grep agp
nvidia_agp              9756  1 
agpgart                35016  2 nvidia,nvidia_agp



So it looks like it loaded the nvidia_agp, however its not the driver that it is using, even when its set to 1 it just bugs out.  FPS is still crappy, I found a regedit that I could do to wine that improved my fps by about 15 in WoW, but it looks like this is as far as I can go.  Seems like no one has seen this problem before, my new hardware is here.... So I am going to build the system and put Ubuntu on it, set it up and see how it will do, if I get the same affect guess its back to XP which is pretty lame, and I dont mean mp3 lame :(

---

### Post by nick_h on 2007-11-21
Have you tried blacklisting nvidia-agp?

With lsmod | grep agp , I get:
agpgart                35016  1 nvidia

and I have agp enabled using the nvidia driver.

glxgears is not a benchmark program.  Unless you are actually experiencing problems I would ignore the FPS results from glxgears.

---

