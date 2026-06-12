---
title: "[SOLVED] Can't get a clean install of Java plugin into Firefox 3"
date: 2008-07-27
forum: General Help
---

### Post by ChrisC on 2008-07-27
I need the java plugin for Firefox.  I go to a website that requires it, and it says that I need a plugin.  I see it needs java, and upon checking about: plugins indeed I do not have java.  Hmmm, not part of the default Hardy install I guess.  Ooookay, so I let Firefox install the necessary plugin.  Of the 4-5 available options, I select the GCJ option, since it's at the top, and it seems to be what Ubuntu prefers based on some sleuthing around.

Restart Firefox, no java.  Check about: plugins, no java.

Check that the so file is there, and it is:
prompt$> ls -l /usr/lib/mozilla/plugins/lib*
lrwxrwxrwx 1 root root 34 2008-07-27 21:54 /usr/lib/mozilla/plugins/libgcjwebplugin.so -> ../../classpath/libgcjwebplugin.so

Check the config:
prompt$> sudo update-alternatives --config java
There is only 1 program which provides java
(/usr/bin/cacao). Nothing to configure.

Hmmmm.  What's cacao and what does it have to do with GCJ?

I searched this forum up and down (and googled generally) and I give up.  I did see some posts proposing some ugly steps involving Sun's Java package, which seems to me is just going to put me into dependency hell.  Is there a solution that doesn't involve massaging this by hand?

This has probably been my ugliest experience with Ubuntu 8.04 Hardy so far.  Hopefully the fact that Sun is open sourcing Java (we'll see) is ultimately going to make this whole process work better.  In the meantime, I've got my vanilla 8.04 installation and I need Java :)

---

### Post by braddcadd on 2008-07-29
Here are some instructions on how to install it from the terminal:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Browser_plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Browser_plug-ins)

---

### Post by ChrisC on 2008-07-30
Well, I was trying to avoid the Sun Java package since the Ubuntu maintainers had chosen to avoid it, but, you know, I don't really care any more as long as it works.  So I installed it via Synaptic, and it works!  Thanks.

Ubuntu, you need to improve your Firefox/Java integration.

Now, on to finding an mp3 player that's better than the execrable Totem player ...

---

