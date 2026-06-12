---
title: "Problem with extra monitor"
date: 2011-07-07
forum: Hardware
---

### Post by TimmyK. on 2011-07-07
I posted this in another thread, but it's one of those threads cursed with invisibility. So here is what happened: a while ago, if I set up a dual monitor configuration, with my laptop screen and a Sony monitor, everything was dandy except I got this message that said, "you must enable compositing before using Docky. Please enable it and restart Docky." So I did, and now, if the two are set up in a side-by-side configuration with the laptop on 1280x800 and the Sony on 1024x768, everything gets really dark. Funny thing is, when I have them set up with one on top of the other or if I set the laptop to the same resolution as the Sony the problem goes away. Can someone please help me?

---

### Post by TimmyK. on 2011-07-08
Looks like this one is cursed with invisibility as well...

---

### Post by Blasphemist on 2011-07-08
OK, I'll admit to seeing this. It's not invisible, just unusual. First, what did you do to enable compositing? Next, help me out about the placement issue. Are you saying that when you change the position of the monitors in monitor preferences it has an affect on the issue?

I use natty and unity now so I don't use docky but I used to and have seen the compositing message. I actually don't remember what I did about that as the brain is getting old. :D I will help try and figure this out though.

---

### Post by TimmyK. on 2011-07-08
Yay! The curse has lifted! But yes, it only goes dark when you arrange it (on the computer, of course, not physically) so that one is beside the other, not with one below or above the other. And [here]("http://ubuntuforums.org/showthread.php?t=1719409&highlight=docky+timmyk.") is the thread explaining the old problem and what I did.

---

### Post by Blasphemist on 2011-07-09
Let's get back to default. If I understand right and based on my experience, once you're past the compositing message everything seems to work fine except you get that message sometimes. Even if it doesn't let's turn off metacity and try to use compiz for compositing. Run the code from your other thread to turn off metacity.
```
gconftool-2 -s --type bool /apps/metacity/general/compositing_manager false
```
Then check this to see if compiz shows turned on.
```
Go to System -> Preferences -> Desktop Effects and click 'Enable Desktop Effects'
```
Was this already checked or did you have to check it? Does this change anything?

I am assuming you're on maverick (10.10). Is that right? Do you have a nvidia gpu? I found this on the compiz wiki about a black screen issue with nvidia.
> NVIDIA

After a while, windows begin to go black

This is the infamous Black-Window Bug with the NVIDIA driver. It is caused by the graphics card running out of texture memory, and therefore all remaining windows (which are textures) will be black. If you have less than 128MB of video memory, disabling blur, and launching Compiz with --indirect-rendering will reduce the appearance of the bug.
Here is what wiki says about intel if that is what you have.
> ntel

White borders around certain window types when using AiGLX (Applies to the GTK-Window-Decorator, KDE-Window-Decorator)

This is because the i810 driver does not support 32 pixel shadows properly. To avoid this, you will need to change your CCSM backend to GConf temporarily, under Decoration change Shadow Radius to something other than 7.5 to 8.5. A similar problem can happen with some ATI cards (9200SE using the open source radeon drivers).
Graphics chipset supports GL_ARB_fragment_program, however some effects don't work in AiGLX

This is currently a driver issue, where the Intel Driver will not support fragment environment programs in indirect rendering. The following plugins will enable, but fail to work properly
Blur
Reflection
Depending on your graphics card, you may be able to work around this limitation by enabling the AIGLX Fragment Parameter Fix option in the Workarounds plugin.
This setup page on the wiki may also help.
[http://wiki.compiz.org/Setup](http://wiki.compiz.org/Setup)
I don't remember if 10.10 installs ccsm by default, natty doesn't. If you don't have it installed, do so in the software center. Just search ccsm.

You may also want to try installing the experimental plugins. [http://edigitales.org/experimental-compiz-plugins-install-on-ubuntu-10-10-maverick-meerkat/](http://edigitales.org/experimental-compiz-plugins-install-on-ubuntu-10-10-maverick-meerkat/)
This link also tells you how to uninstall those plugins.

This may be of interest if you have the Intel 855GM video chipset. [http://aaronwalrath.wordpress.com/2011/06/23/compiz-fusion-and-dell-inspiron-700m-with-intel-855gm-video-chipset/](http://aaronwalrath.wordpress.com/2011/06/23/compiz-fusion-and-dell-inspiron-700m-with-intel-855gm-video-chipset/)

Let's start with this and see if any of this helps. Let me know  how it's going.

---

### Post by TimmyK. on 2011-07-12
OK, I disabled compositing, and I have the same problem as before (the dark area around docky). And I have the Intel 945GM chipset. Meerkat doesn't come with ccsm, but I installed it. What now?

---

### Post by Blasphemist on 2011-07-12
> **TimmyK. said:**
> OK, I disabled compositing, and I have the same problem as before (the dark area around docky). And I have the Intel 945GM chipset. Meerkat doesn't come with ccsm, but I installed it. What now?

Try going back to my previous post and start at the checking if compiz shows turned on. Then keep following what I posted. If you come to a specific question, please post it.

---

### Post by john00 on 2011-07-13
The maximum texture size on a lot of cards at one stage was 2048x2048.  Having the two side by side may push it over this limit and give troubles with compositing window managers, wheras on top of each other is ok.

---

### Post by realzippy on 2011-07-13
from [http://askubuntu.com/questions/8474/what-is-compositing](http://askubuntu.com/questions/8474/what-is-compositing) :

[I]If you see a black border around docky, then compositing is not properly enabled. The warning you are getting is most likely a result of Docky starting before compositing kicks in.

See [https://bugs.launchpad.net/docky/+bug/552273](https://bugs.launchpad.net/docky/+bug/552273)[/I]

---

