---
title: "Compiz with ADD helper and Scale plugin"
date: 2008-11-02
forum: General Help
---

### Post by Nirva on 2008-11-02
Hay,

because the Scale plugin doesnt work with minimized windows, I tried to found an alternative.

I enabled ADD helper and made al the unfocused windows "disappear" by setting the opacity to 0.
But when I then trigger the scale plugin, those windows still arent visible.
Is it possible in any way to make them visible again when triggering the scale plugin ?

Thanks

---

### Post by Greg T. on 2008-11-04
One option would to write a script that would use Compiz's dbus plugin. See [http://wiki.compiz-fusion.org/Plugins/Dbus](http://wiki.compiz-fusion.org/Plugins/Dbus). The script could be triggered via a launcher or through a screen edge using brightside. When invoked, the script would call dbus to change the opacity of the windows and then invoke scale. When scale is finished, the script would send another dbus call to return the unfocused windows to their earlier level of opacity.

The trickiest part would be knowing when Scale is finished. There's no way to determine this through Compiz, using dbus or otherwise. It's possible to set up a "handler" that would listen for window events after scale is initiated; once a window event occurs (such as a window being selected in scale), the script can respond accordingly.

I'm actually working on a python script that works along the lines above, except it unminimizes/minimizes windows instead of changing opacity. I'm going to post it in a few days; I'm holding off because many folks (me included) are dealing with the Intrepid upgrade at the moment.

---

### Post by Nirva on 2008-11-05
Awesome ! A Script like that is even more what I want.  
I know there is a script somewhere that does the same thing as you mention here, but it was too slow, to run smoothly.
Let me know when you're script is ready...

---

### Post by Greg T. on 2008-11-09
You can give it a whirl now:

[http://ubuntuforums.org/showthread.php?p=6135101](http://ubuntuforums.org/showthread.php?p=6135101)

It's a bit faster than the other script (mentioned in the above, BTW) in that it only activates the minimized windows, rather than cycling through all windows, but unminimizing is fundamentally slow. There's no getting around that fact given the way X is currently designed. However, the script will give you something to play with should you want to customize it for you own purposes.

---

