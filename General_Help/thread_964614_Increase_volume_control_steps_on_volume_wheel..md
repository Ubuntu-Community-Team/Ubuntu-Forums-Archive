---
title: "Increase volume control steps on volume wheel."
date: 2008-10-31
forum: General Help
---

### Post by skinind95 on 2008-10-31
Hello,

I've done a lot of searching on this and have come up with nothing (I may be searching with the wrong terms).  I'm running Ubuntu 8.10, and it's been completely -perfect- so far.

What i'd like to do is increase the number of steps between mute and 100% while using my volume wheel. (It's okay if it affects all other volume keys)  Right now it seems like there are 8 steps, which is about a 12% change for just a small amount of rotation.  It'd be nice to have the volume up and down 'shortcut' to be more in the range of a 3-4% change.

I'd imagine this is hidden in a config file somewhere, but i'm not sure where to look.

Thank you very much in advance for your help!

,Travis

---

### Post by skinind95 on 2008-11-02
Hate to bump my own thread, but i'm still looking for a solution.  Anyone out there have any suggestions?

---

### Post by mdurham on 2008-11-02
Look in Configuration Editor->/apps/gnome_settings_daemon/volume_step and see if changing that does anything. I haven't tried, so I'm not sure.
Cheers, Mike

---

### Post by skinind95 on 2008-11-02
That worked perfect! Thank you, Mike. =)

Anyone else who'd like to change this, here's what I did. (There may be better ways to do this.)

On a new installation of Ibex you probably wont have "System Tools" under "Applications", so you'll need to go to *System->Preferences->Main Menu* and select "System Tools" on the left under "Applications".  On the right you'll have to check* Configuration Editor* and then hit close.  Now you can go to *Applications->System Tools->Configuration Editor*

[COLOR="Red"]Edit: Alt+F2 and enter *gconf-editor* to do this quicker.[/COLOR]  But it may be useful to have this in the menu so i'll leave the previous (though very basic) instructions as well.

From there you follow the path that mdurham provided to /apps/gnome_settings_daemon.  With gnome_settings_daemon selected on the left you should see the 'volume_step' key on the right with a value of 6. Right click this and select 'Edit Key...' to edit the value.  I changed mine to 1, which may be a too little for some people, but I like it.


Of course there is probably a config file somewhere that would be easy to edit, and you most likely don't have to add the Configuration Editor to the Applications menu to access it, but this is what I did to get it to work not knowing the Config Editor's actual command line name or the location of the config file.

Hope this helps someone.


Thanks again, Mike.

,Travis

---

### Post by habtool on 2009-01-04
> **mdurham said:**
> Look in Configuration Editor->/apps/gnome_settings_daemon/volume_step and see if changing that does anything. I haven't tried, so I'm not sure.
Cheers, Mike

Thanks, that has bugged more for so long!

---

### Post by BoomShaka on 2009-03-14
finally! a solution!
I found this too if you wanted to do it from the command line:
gconftool-2 --set --type int /apps/gnome_settings_daemon/volume_step 2

I did it your way though (using gconf-editor) seemed easier :)

---

