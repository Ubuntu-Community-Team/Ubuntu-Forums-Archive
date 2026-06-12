---
title: "murrine rgba apps... how to do it?"
date: 2008-08-06
forum: General Help
---

### Post by Choad on 2008-08-06
they look schmexy, i want to play with it. i downloaded a murrine theme and it works, but apps that are supposedly supporting the rgba gtk extension do not appear transparent. (i was using gnome-system-monitor as my test app, which apparently supports it)

is there anything else i have to configure on a hardy machine?

---

### Post by klange on 2008-08-06
You'll have to find extensions or plugins for your binary applications. There are quite a few patches for other programs if you feel up to compiling from source. If you know what you're doing with any amount of programming, you can hack them in yourself. I wrote a [really short "guide"](http://forum.compiz-fusion.org/showthread.php?t=7326&highlight=argb) on how to do it at the C-F forums back when I was hacking in to various apps (like Pidgin and Nautilus, both of which were major pains).

For extensions, I only know of one that is stable, and it's for Gedit (which looks amazing with RGBA support). You can get them from [Cimitan's website](http://www.cimitan.com/murrine/).

---

### Post by Choad on 2008-08-06
> **WindowsSucks said:**
> You'll have to find extensions or plugins for your binary applications. There are quite a few patches for other programs if you feel up to compiling from source. If you know what you're doing with any amount of programming, you can hack them in yourself. I wrote a [really short "guide"](http://forum.compiz-fusion.org/showthread.php?t=7326&highlight=argb) on how to do it at the C-F forums back when I was hacking in to various apps (like Pidgin and Nautilus, both of which were major pains).

For extensions, I only know of one that is stable, and it's for Gedit (which looks amazing with RGBA support). You can get them from [Cimitan's website](http://www.cimitan.com/murrine/).
ok i see... because on [this](http://www.cimitan.com/murrine/rgba-support/list) list gnome sys mon was listed as "official", i assumed it would work with no extra hacks (my build of the program exceeds the version which it states officially adopted the rgba patches)

anyhoo, i added the plugin for gedit, no effect. added the plugin for rhythmbox... no effect.

methinks i am missing a step in the process here. i am using the MurrinaOranche gtk theme, compiz-fusion and emerald. other than that it's a standard hardy setup afaik.

thanks for the post btw! so many of my posts go unanswered :(

---

### Post by nwd on 2008-08-25
Same here... 
1. Installed svn version of murrine gtk engine
2. Added plugins for gedit, rhythmbox, patched sources of thunar and totem, compiled and installed them
3. downloaded few murrine themes
4. restarted applications but all of them looked the same... Tried with compiz, Xfwm, xcompmgr...
Still no effect, i don't understand why, no errors, no effects, no sence :)

What step I missed? it should be sth obvious, maybe I need special theme?

---

### Post by puccaso on 2008-09-14
you need to have either compiz running or just have whatever makes compiz work - work.. like the opengl drivers or something
i dont think it works without compiz?

---

### Post by nwd on 2008-09-14
Well compiz works just perfectly, but no rgba :\

---

### Post by appi2012 on 2008-09-15
the theme needs to enable support. Open the theme you are using - /home/username/.themes/themename/gtk-2.0/gtkrc - in text editor, and then add the line "rgba = TRUE" in the section 'engine "murrine"' under the section "theme-default" Then save and quit, and re apply the theme.

---

### Post by nwd on 2008-09-16
Thanks, works now ;)

---

### Post by Choad on 2008-09-29
> **appi2012 said:**
> the theme needs to enable support. Open the theme you are using - /home/username/.themes/themename/gtk-2.0/gtkrc - in text editor, and then add the line "rgba = TRUE" in the section 'engine "murrine"' under the section "theme-default" Then save and quit, and re apply the theme.
ok each time i do this it gives me an error  

unexpected identifier `rgba', expected character `}'

i am adding the line right after 

engine "murrine"  {

*confused* what theme are you using that supports this? i tried murrina gilouche and murrina oranche

---

### Post by Choad on 2008-09-29
never mind, i wasn't using the svn version. all good now thanks for the tip!

oh is there any way of setting the opacity level?

---

### Post by nwd on 2008-09-30
nope

---

### Post by Psyphre on 2009-02-14
Just bumping this because I too want to know how to patch applications. Ive got epiphany, image viewer, rhythmbox working because they just use plugins, but how would I patch totem for example?

---

