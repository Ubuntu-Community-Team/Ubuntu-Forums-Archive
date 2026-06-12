---
title: "Some compiz animations not working!"
date: 2008-09-11
forum: General Help
---

### Post by chrisruls00 on 2008-09-11
For some reason some of my compiz animations are not working at all. The focus and shade type animations are not working at all, but all the other ones are. Does anyone know why this happens? I use NVidia drivers (I think it is the legacy type, or something like that.) if it makes a difference.

---

### Post by overdrank on 2008-09-11
> **chrisruls00 said:**
> For some reason some of my compiz animations are not working at all. The focus and shade type animations are not working at all, but all the other ones are. Does anyone know why this happens? I use NVidia drivers (I think it is the legacy type, or something like that.) if it makes a difference.

Hi and what is the model of the nvidia card? I have had some effects not work with older nvidia and ati cards but it was like the rain effect.

---

### Post by Uchiha_madara on 2008-09-12
There are many reason's :

1 - The problem is with vga card .....
2 - Try to Make The Update to be sure that the Effects are the installed Correctly

3 - install The Compiz setting manager

---

### Post by chrisruls00 on 2008-09-12
I might add that I have had these effect working on this laptop before but while trying to update compiz one time (to a newer git version) They stopped working and they now don't work with anything, even the version supplied by kubuntu by default. The driver I use is the Latest Legacy GPU version (1.0-96xx series)

---

### Post by chrisruls00 on 2008-09-14
I tried re-installing and I found an error with the animation plug-in.

```
Makefile:152: [WARNING] This plugin might be needed by other plugins. Install it with "BUILD_GLOBAL=true sudo make install"
install   : /home/chrisruls00/.compiz/plugins/libanimation.so
install   : /home/chrisruls00/.compiz/metadata/animation.xml
install   : build/compiz-animation.schemaWARNING: failed to associate schema `/schemas/apps/compiz/plugins/animation/screen0/options/' with key `/apps/compiz/plugins/animation/screen0/options/': Bad key or directory name: "/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to install schema `/schemas/apps/compiz/plugins/animation/screen0/options/', locale `C': Bad key or directory name: "/schemas/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to associate schema `/schemas/apps/compiz/plugins/animation/screen0/options/' with key `/apps/compiz/plugins/animation/screen0/options/': Bad key or directory name: "/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to install schema `/schemas/apps/compiz/plugins/animation/screen0/options/', locale `C': Bad key or directory name: "/schemas/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to associate schema `/schemas/apps/compiz/plugins/animation/screen0/options/' with key `/apps/compiz/plugins/animation/screen0/options/': Bad key or directory name: "/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to install schema `/schemas/apps/compiz/plugins/animation/screen0/options/', locale `C': Bad key or directory name: "/schemas/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to associate schema `/schemas/apps/compiz/plugins/animation/screen0/options/' with key `/apps/compiz/plugins/animation/screen0/options/': Bad key or directory name: "/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to install schema `/schemas/apps/compiz/plugins/animation/screen0/options/', locale `C': Bad key or directory name: "/schemas/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to associate schema `/schemas/apps/compiz/plugins/animation/screen0/options/' with key `/apps/compiz/plugins/animation/screen0/options/': Bad key or directory name: "/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to install schema `/schemas/apps/compiz/plugins/animation/screen0/options/', locale `C': Bad key or directory name: "/schemas/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to associate schema `/schemas/apps/compiz/plugins/animation/screen0/options/' with key `/apps/compiz/plugins/animation/screen0/options/': Bad key or directory name: "/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to install schema `/schemas/apps/compiz/plugins/animation/screen0/options/', locale `C': Bad key or directory name: "/schemas/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to associate schema `/schemas/apps/compiz/plugins/animation/screen0/options/' with key `/apps/compiz/plugins/animation/screen0/options/': Bad key or directory name: "/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to install schema `/schemas/apps/compiz/plugins/animation/screen0/options/', locale `C': Bad key or directory name: "/schemas/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to associate schema `/schemas/apps/compiz/plugins/animation/screen0/options/' with key `/apps/compiz/plugins/animation/screen0/options/': Bad key or directory name: "/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to install schema `/schemas/apps/compiz/plugins/animation/screen0/options/', locale `C': Bad key or directory name: "/schemas/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to associate schema `/schemas/apps/compiz/plugins/animation/screen0/options/' with key `/apps/compiz/plugins/animation/screen0/options/': Bad key or directory name: "/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to install schema `/schemas/apps/compiz/plugins/animation/screen0/options/', locale `C': Bad key or directory name: "/schemas/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to associate schema `/schemas/apps/compiz/plugins/animation/screen0/options/' with key `/apps/compiz/plugins/animation/screen0/options/': Bad key or directory name: "/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to install schema `/schemas/apps/compiz/plugins/animation/screen0/options/', locale `C': Bad key or directory name: "/schemas/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to associate schema `/schemas/apps/compiz/plugins/animation/screen0/options/' with key `/apps/compiz/plugins/animation/screen0/options/': Bad key or directory name: "/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to install schema `/schemas/apps/compiz/plugins/animation/screen0/options/', locale `C': Bad key or directory name: "/schemas/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to associate schema `/schemas/apps/compiz/plugins/animation/screen0/options/' with key `/apps/compiz/plugins/animation/screen0/options/': Bad key or directory name: "/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to install schema `/schemas/apps/compiz/plugins/animation/screen0/options/', locale `C': Bad key or directory name: "/schemas/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to associate schema `/schemas/apps/compiz/plugins/animation/screen0/options/' with key `/apps/compiz/plugins/animation/screen0/options/': Bad key or directory name: "/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to install schema `/schemas/apps/compiz/plugins/animation/screen0/options/', locale `C': Bad key or directory name: "/schemas/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to associate schema `/schemas/apps/compiz/plugins/animation/screen0/options/' with key `/apps/compiz/plugins/animation/screen0/options/': Bad key or directory name: "/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to install schema `/schemas/apps/compiz/plugins/animation/screen0/options/', locale `C': Bad key or directory name: "/schemas/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to associate schema `/schemas/apps/compiz/plugins/animation/screen0/options/' with key `/apps/compiz/plugins/animation/screen0/options/': Bad key or directory name: "/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to install schema `/schemas/apps/compiz/plugins/animation/screen0/options/', locale `C': Bad key or directory name: "/schemas/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to associate schema `/schemas/apps/compiz/plugins/animation/screen0/options/' with key `/apps/compiz/plugins/animation/screen0/options/': Bad key or directory name: "/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to install schema `/schemas/apps/compiz/plugins/animation/screen0/options/', locale `C': Bad key or directory name: "/schemas/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to associate schema `/schemas/apps/compiz/plugins/animation/screen0/options/' with key `/apps/compiz/plugins/animation/screen0/options/': Bad key or directory name: "/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to install schema `/schemas/apps/compiz/plugins/animation/screen0/options/', locale `C': Bad key or directory name: "/schemas/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to associate schema `/schemas/apps/compiz/plugins/animation/screen0/options/' with key `/apps/compiz/plugins/animation/screen0/options/': Bad key or directory name: "/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to install schema `/schemas/apps/compiz/plugins/animation/screen0/options/', locale `C': Bad key or directory name: "/schemas/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to associate schema `/schemas/apps/compiz/plugins/animation/screen0/options/' with key `/apps/compiz/plugins/animation/screen0/options/': Bad key or directory name: "/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to install schema `/schemas/apps/compiz/plugins/animation/screen0/options/', locale `C': Bad key or directory name: "/schemas/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to associate schema `/schemas/apps/compiz/plugins/animation/screen0/options/' with key `/apps/compiz/plugins/animation/screen0/options/': Bad key or directory name: "/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to install schema `/schemas/apps/compiz/plugins/animation/screen0/options/', locale `C': Bad key or directory name: "/schemas/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to associate schema `/schemas/apps/compiz/plugins/animation/screen0/options/' with key `/apps/compiz/plugins/animation/screen0/options/': Bad key or directory name: "/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to install schema `/schemas/apps/compiz/plugins/animation/screen0/options/', locale `C': Bad key or directory name: "/schemas/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to associate schema `/schemas/apps/compiz/plugins/animation/screen0/options/' with key `/apps/compiz/plugins/animation/screen0/options/': Bad key or directory name: "/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to install schema `/schemas/apps/compiz/plugins/animation/screen0/options/', locale `C': Bad key or directory name: "/schemas/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to associate schema `/schemas/apps/compiz/plugins/animation/screen0/options/' with key `/apps/compiz/plugins/animation/screen0/options/': Bad key or directory name: "/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to install schema `/schemas/apps/compiz/plugins/animation/screen0/options/', locale `C': Bad key or directory name: "/schemas/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to associate schema `/schemas/apps/compiz/plugins/animation/screen0/options/' with key `/apps/compiz/plugins/animation/screen0/options/': Bad key or directory name: "/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to install schema `/schemas/apps/compiz/plugins/animation/screen0/options/', locale `C': Bad key or directory name: "/schemas/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to associate schema `/schemas/apps/compiz/plugins/animation/screen0/options/' with key `/apps/compiz/plugins/animation/screen0/options/': Bad key or directory name: "/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
WARNING: failed to install schema `/schemas/apps/compiz/plugins/animation/screen0/options/', locale `C': Bad key or directory name: "/schemas/apps/compiz/plugins/animation/screen0/options/": Key/directory may not end with a slash '/'
install   : build/compiz-animation.schema

```

---

### Post by chrisruls00 on 2008-09-16
no one knows what this means?

---

### Post by Uniq PhoeniX on 2008-09-17
For me shade animation and some other (I think minimize) didn't work, but I got them to work after setting them back to default, not sure if that was what fixed it, but you can try.

---

### Post by chrisruls00 on 2008-09-17
THANK YOU!!! I did not even notice there was a default button for animation plug-in untill you mentoined it, otherwise I would have tried sooner. Thanks again! It works perfectly!

---

### Post by Braedley on 2008-11-01
From the compiz forums:
> Just reset the open and close animation matches to defaults with the brush button under the match list and reconfigure them.

Yes, you loose your settings, but yes, this is the easiest way.  It's much faster and easier than the solution I found 6 months ago (something about loading a new default profile and then reloading your previous settings from a saved profile).

---

### Post by forest.r on 2008-11-06
I installed 8.04 from a cd, then upgraded via update manager.

your defaults solution works for the default setting, but if i try to use the extra animations plugin (explode, burn, etc.) none of the effects work.

any ideas?

---

### Post by shadow1983 on 2008-11-13
Thanks Braedley, didnt know the brush icon reset to default again, did that and now all my animations work :)

---

