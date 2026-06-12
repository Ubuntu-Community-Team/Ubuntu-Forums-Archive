---
title: "A proper way to install compiz on my computer."
date: 2008-08-02
forum: General Help
---

### Post by Animeniac on 2008-08-02
Because I couldn't get any support for my problems about the top bar not appearing on the windows in Ubuntu, I reinstalled Ubuntu. Then I installed Kubuntu again and the top bar was still not appearing. I learned that the cause was compiz. Everytime I install KDE and Kubuntu, compiz is installed. I reinstalled Ubuntu again and tried to find a proper way to install compiz so that I won't get ANY problems nor errors. I followed one website and then Ubuntu won't even boot. Now I have reinstalled Ubuntu for the third time, and I'm not going to install Kubuntu until I an get both Kubuntu and Ubuntu to work properly and have compiz at the same time.

Now I've learned that installing compiz from Synaptic is a rather **improper way**. :cry: Having compiz has something to do with the hardware, like the Aero theme for Windows Vista Home Premium is. :cry: I have an NVIDIA GeForce 4 MX 4000 graphics card, and I have installed its driver by using EnvyNG. I would like to know the proper way to install compiz for my computer, so that I don't end up with problems nor errors.

Thank you very much.

---

### Post by pytheas22 on 2008-08-02
Installing compiz from Synaptic should be fine--that's the intended way to install software on Ubuntu--however as you say, you shouldn't really need to install compiz at all because it's included by default since *buntu 7.04 I think.  If you have an nvidia video card, though, then compiz won't work until you install the proprietary driver (which you did through envy, although there are other ways to do it and some people would tell you not to use envy); maybe that's why you're thinking that there's a "proper" and "improper" way to make compiz work.

I think that your issue has to do with a bug and is probably related to the video driver more than compiz.  If you describe the problem in more detail I'll try to help, although as a disclaimer, I don't know too much about nvidia on Ubuntu.

You can also compile compiz from source, but that's not the recommended way to do it.  Compiling from source is difficult, time-consuming and may not install the same version of compiz that Ubuntu needs to work correctly.  System updates will also not work for compiz if you compile from source.

---

### Post by UbuntuNerd on 2008-08-02
I don't know if this is the proper way but is a good guide I used it 

[http://thegabfather.wordpress.com/2008/05/17/how-to-install-compiz-fusion-in-ubuntu-hardy-heron/]("http://thegabfather.wordpress.com/2008/05/17/how-to-install-compiz-fusion-in-ubuntu-hardy-heron/")

---

### Post by sayakb on 2008-08-03
To install compiz: [http://ubuntuforums.org/showpost.php?p=5335372&postcount=24](http://ubuntuforums.org/showpost.php?p=5335372&postcount=24)
Also at a terminal:
```
sudo apt-get install emerald compizconfig-settings-manager
```Download emerald themes from [http://gnome-look.org/](http://gnome-look.org/)
At a terminal, do:
```
emerald --replace &
```

---

