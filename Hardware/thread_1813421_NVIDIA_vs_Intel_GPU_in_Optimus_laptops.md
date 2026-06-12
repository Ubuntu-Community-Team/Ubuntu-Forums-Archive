---
title: "NVIDIA vs Intel GPU in Optimus laptops"
date: 2011-07-27
forum: Hardware
---

### Post by Blitzskee on 2011-07-27
Hi I was wondering how you would go about deselecting the NVIDIA driver and ensuring that the intel gpu is in use in a laptop with optimus.

In additional drivers I HAD Nvidia selected but it stated "This device is activated but not in use" and I had no 3D acceleration etc.  I have deactivated it but I still don't have any.

How do I activate the intel gpu?? I have searched the forums and google but could not find anything.

Thanks in advance.

---

### Post by ehode on 2011-07-27
You'll want to check into the bumblebee project.

I wrote up a guide in my blog that should work for any laptop using the nvidia optimus.

[http://e0d.com/blog/dell-xps-15-l502xrunning-linux-lubuntu-11-04-with-nvidia-optimus-support](http://e0d.com/blog/dell-xps-15-l502xrunning-linux-lubuntu-11-04-with-nvidia-optimus-support)

Bumblebee should keep the nvidia card turned off until you call it on for a program.

---

### Post by Blitzskee on 2011-07-27
I don't think my NVIDIA card even turns on anyways, is there a way to JUST run intel gpu.  I'll try your suggestion anyways and post back how it went.

P.s I read your blog, very simple instructions.  Thank you very much.

---

### Post by Blitzskee on 2011-07-27
Umm but sorry whats the Optirun command you state on your blog.  Do I have to run a program through there to use bumblebee?

Anyways I installed bumblebee...still no success as the program I wanted to open did not run, still unable to use unity.  I'm assuming for some reason I still don't have any 3D acceleration....

---

### Post by azzamite on 2011-07-27
Many of us are mad because we can't use our nvidia cards and you wand to use intel's as default??? :confused:

What I did was to install the nvidia driver as usual, and then used update-alternatives to fall back to mesa.

I also deleted /etc/X11/xorg.conf

Now my system is using intel's card for 3D acceleration, you can't expect much for this integrated card

```
update-alternatives --config glx
Existen 2 opcioens para la alternativa glx (que provee /usr/lib/glx).

  Selección   Ruta                    Prioridad  Estado
------------------------------------------------------------
  0            /usr/lib/nvidia          100       modo automático
* 1            /usr/lib/mesa-diverted   5         modo manual
```

```
lsmod | grep nvi
nvidia              11757407  0 
i2c_core               23766  7 nvidia,i915,drm_kms_helper,videodev,drm,i2c_algo_bit,i2c_i801
```

```
glxinfo | grep -C3 dire
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
```

---

### Post by Blitzskee on 2011-07-27
Interesting azzamite

What laptop are you using? I'll give it a go and post back my results.

I only want to use intel because I've been through so much **** in the past week trying to make NVIDIA work that I don't even care anymore I just want to run Unity and the game I play.

Also you said "used update-alternatives to fall back to mesa"

What exactly is update-alternatives and what is mesa? Sorry I'm quite new I just don't want to do anything wrong.

---

### Post by Blitzskee on 2011-07-27
Wait! Can I even try what you said now that I have bumblebee installed?

---

### Post by azzamite on 2011-07-27
> **Blitzskee said:**
> Wait! Can I even try what you said now that I have bumblebee installed?

I didn't install bumblebee at all, so I don't know, give it a try any way.

The intel card gives enough HW acceleration to draw transparent windows in KDE4 and run pcsx, I don't expect more than that.

AFAIK, without bumblebee the nvidia card should be turned off at all times, the difference is the driver used, is I'm using nvidia and i915.

I no driver is working correctly, your system may fall back to VESA and you get something like this:
```
glxinfo | grep dire
direct rendering: No
```

---

### Post by Blitzskee on 2011-07-27
Thanks, ill try it

So just to clarify the code you ran in terminal was?:

```
update-alternatives --config glx
```

??

---

### Post by Blitzskee on 2011-07-27
I ran the code and it came out with:

> update-alternatives: error: no alternatives for glx.


---

### Post by azzamite on 2011-07-27
> **Blitzskee said:**
> I ran the code and it came out with:

Maybe you don't have the nvidia driver installed?
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Why don't you first try checking the output of
lsmod | grep i915
if the module is loaded, then your intel card is working

And this will tell you whether or not you have 3D acceleration
glxinfo | grep dire

---

### Post by Blitzskee on 2011-07-28
Thanks again for your reply.  I installed it multiple times via jockey and I also have bumblebee installed which I have been told uses an nvidia driver anyway?.  I initially did a manual install of the latest drivers from the NVIDIA website but then I had no gui and could not "startx" so I had to remove it.  I tried your following commands.

lsmod | grep i915, gave me:

> i915                  450969  2 
drm_kms_helper         40745  1 i915
drm                   184133  3 i915,drm_kms_helper
i2c_algo_bit           13184  1 i915
video                  18951  1 i915


glxinfo | grep dire, gave me:
> Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".


---

### Post by ehode on 2011-07-28
Bumblebee should turn off the nvidia gpu from running and sucking down the battery you can invoke it with the optirun command.

I'm confused at what you are trying to accomplish.  The nvidia option will give you the higher end graphics support the intel gpu is for basic operations.

What laptop model are you using?

---

### Post by Blitzskee on 2011-07-28
I wanted to just run intel initially, I wasnt sure how to check if it was even being used.  Then from lots of advice I have been getting I eventually installed bumblebee.  Im just trying to get unity to work and trying to open a game I have.  I think its not working because I have no 3D acceleration. 

I assumed this was because neither intel or nvidia was working properly on my laptop....I could be completely wrong

Im using a Dell Inspiron 15R

To be honest I think this thread if solved if the code you told me to run says the intel gpu is working??????  Because my initial question was how do I activate it?

So thanks! =)

---

### Post by Lekensteyn on 2011-07-28
If you're trying Bumblebee, be sure to follow the instructions at [https://github.com/MrMEEE/bumblebee/issues/493#issuecomment-1662510](https://github.com/MrMEEE/bumblebee/issues/493#issuecomment-1662510) for now.  If you're not using bumblebee, but the nvidia driver screwed up compositing and graphical effects on the intel card, run:  ```
sudo update-alternatives --force --set gl_conf /usr/lib/mesa/ld.so.conf
```  Your /var/log/Xorg.0.log file should not contain any references to the nvidia driver (nvidia-current) after a restart of X (reboot)

---

