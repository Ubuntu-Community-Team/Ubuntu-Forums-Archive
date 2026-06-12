---
title: "ATI x1600 pro installation and beryl"
date: 2007-01-22
forum: Hardware &amp; Laptops
---

### Post by tintii on 2007-01-22
hi all,

i'm new to ubuntu so please bare with me.

basically firstly after installing ubuntu i wend to this site: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

and followe the guide and installed the drivers ubuntu way.. that went fine then i looked for beryl installation and i came across aixgl and xgl

aixgl:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

xgl
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL)

So.. i installed as the XGL instructions told me to and it seemed to go fine.. i managed to get the beryl manager running but nothing lse happened.. every time i tried to use beryl the windows flash and eveerything remains normal.

any help will be much appreciated... thanks in advance.

tintii

---

### Post by tintii on 2007-01-22
forgo to include with the above:


the error message is:

XGL Absent, checking for NVIDIA

Nvidia Absent, assuming AIGLX

beryl: No composite extension

XGL Absent, checking for NVIDIA

Nvidia Absent, assuming AIGLX

beryl: No composite extension

Window manager warning: Lost connection to the display ':0.0';

most likely the X server was shut down or you killed/destroyed

the window manager.

XGL Absent, checking for NVIDIA

Nvidia Absent, assuming AIGLX

beryl: No composite extension

XGL Absent, checking for NVIDIA

Nvidia Absent, assuming AIGLX



thanks

---

### Post by CowzRule on 2007-01-22
If you made XGL a separate session, you need to log out, hit F-10, select Session, XGL, then log back in.

---

### Post by Lord Illidan on 2007-01-22
> **CowzRule said:**
> If you made XGL a separate session, you need to log out, hit F-10, select Session, XGL, then log back in.

His problem ( I am a friend of his in RL) is that his ATI drivers are not working correctly as in direct rendering is not working.

I tried to help him but I dunno much about ATI as mine is NVIDIA.

If anyone can help him, please do.

---

### Post by Ravanous on 2007-01-22
I  have the same card & I did manage to get it working with direct rendering enabled.

Have you tried [this]("http://albertomilone.com/nvidia_scripts1.html")?

Between the links you posted and that script, I did have it working.

Then I broke it over the weekend :(

I am going to start again from scratch and make a note of everything that I do this time!

---

### Post by CowzRule on 2007-01-22
Log out. When the new log in screen appears, hit "Ctrl-Alt-Backspace" at the same time. That restarts the X server. Now when the log in screen appears, hit F-10, Select Session, and be sure to select Gnome. We DO NOT want XGL running.
Once Gnome loads up, open a terminal and type this```
glxinfo | grep render
``` and then type```
fglrxinfo
```and post the outputs here.

---

### Post by tintii on 2007-01-23
Hi all,

thanks for the help... although i managed to install beryl and all the rest.. i followed the following:

[http://www.ubuntuforums.org/showthread.php?t=342812&highlight=beryl+with+ati](http://www.ubuntuforums.org/showthread.php?t=342812&highlight=beryl+with+ati)

its pretty simple..

thanks again.

---

