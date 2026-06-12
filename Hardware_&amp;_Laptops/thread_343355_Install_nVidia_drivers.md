---
title: "Install nVidia drivers"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by Tuffy on 2007-01-21
I want to enable 3D acceleration on my ubuntu box. My video card is a GeForce FX 5900XT. After searching with google I learned that I simply needed to type this in to the terminal:

```
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig
```

So I do, and after downloading and installing the driver, I type in the second command. All goes well, and I restart Gnome. then something comes up telling me X cannot start, so I try to restart the computer and I am back in ubuntu, but with no 3D acceleration. In xorg.conf the driver says its using nvidia, and I've tried restarting numerous times with the same results.

I am using a fresh install of Ubuntu Edgy Eft, so its perfectly ok for me to reinstall should something go horribly wrong :)

Tuffy AKA Sir Gravitico IV :cool:

EDIT: apparently I forgot to say that the problem is, the nvidia logo does not appear when I start the computer, so I dont think I have acceleration. Any way I can test? :)

---

### Post by roderikk on 2007-01-21
If you are willing to experiment you might try out the following tutorial which will install beryl too:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia#Installing_the_nVIDIA_Beta_Driver](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia#Installing_the_nVIDIA_Beta_Driver)

I have used it to good effect. However, be aware that you are installing the beta driver, so if you don't feel entirely comfortable with that don't do it. (You can expect occasional breakage).

Good luck!

---

### Post by Tuffy on 2007-01-21
Its probably obvious, but I have a Pentium 4 2.8 GHz processor, and I doubt it can run Armatron @ 2-300 FPS on its own. correct? then I guess I have installed the driver successfully!:guitar:

The only problem is, I cant change the screen resolution to over 1024x768 . Is there a way to change that? and yes, my monitor supports it  :)

---

### Post by roderikk on 2007-01-21
Hey, I have that very same problem quite regularly on a fresh install. I don't know if you are familiar with command line editing but if so you could do the following (otherwise I don't know exactly what you could do):

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

sudo gedit /etc/X11/xorg.conf
```

Look for the section containing the following code:

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
```

And in the Modes line add:
```

        Modes      "1280x1024" "1024x768" "800x600" "640x480"
```

Your xorg.conf might look a bit different, with multiple bit depth but don't worry about that, you only have to add the 1280 term at the bit depth you want that screen resolution at.

---

### Post by Tuffy on 2007-01-21
So I would only add "1280x1024" in the modes line, correct?

---

### Post by roderikk on 2007-01-24
Sorry for the late reply but yes :-).

Did it work out for you in the end?

---

