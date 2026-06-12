---
title: "Disable Compiz from failsafe terminal"
date: 2008-11-13
forum: General Help
---

### Post by casperthefriendlyghost on 2008-11-13
Hi there,

I have encountered a problem after the installation of Compiz Fusion on Ubuntu 8.10. 

Clicking on, or hovering over buttons, menus, and files renders these items permanently black(like a silhouette). As well as turning my screen black I can't launch the Compiz fusion settings application  or any other application, in fact all mouse clicks result to nothing(or black).

This problem came about when I was trying out what each effect did. I think I clicked on 'bipolar', or  'bicubic' or something along those lines to cause this.

The only way I can think to solve this is to turn off Compiz fusion from the terminal. Now I tried metacity --replace but that doesn't work because it requires x display.

One last point to mention, is that the failsafe gnome doesn't help, I still encounter the same problems.

Anyone think of how to fix this?

---

### Post by loomsen on 2008-11-13
If you got a backup of your compiz settings you may either edit the textfile by hand,search for one of the suspects and change its value (most likely from 1 to 0), or remove the folder ~/.config/compiz or rename it, or back it up and then remove it, simply make sure theres no configuration file left for compiz in your home folder.

If you have it configured using gconf, you'll prlly have to run a locate command, for instance, if you think blur caused it:
```

 locate compiz | grep gconf | grep blur

```
this is what i get for the command, but i used water cause my blur is disabled:
```

docter[~] locate compiz | grep gconf | grep water
/home/docter/.gconf/apps/compiz/plugins/water
/home/docter/.gconf/apps/compiz/plugins/water/%gconf.xml
/home/docter/.gconf/apps/compiz/plugins/water/allscreens
/home/docter/.gconf/apps/compiz/plugins/water/allscreens/%gconf.xml
/home/docter/.gconf/apps/compiz/plugins/water/allscreens/options
/home/docter/.gconf/apps/compiz/plugins/water/allscreens/options/%gconf.xml
docter[~] 

```
The file you're looking for is the deepest %gconf.xml, so in this case the last one.
This is whats written into it:
```

docter[~] cat /home/docter/.gconf/apps/compiz/plugins/water/allscreens/options/%gconf.xml
<?xml version="1.0"?>
<gconf>
        <entry name="title_wave" mtime="1226425048" type="bool" value="true">
        </entry>
</gconf>
docter[~] 

```

The one for blur should look similar, just change the value from "true" to "false"

---

