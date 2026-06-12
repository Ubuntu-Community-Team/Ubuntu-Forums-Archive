---
title: "How to remove the hibernation/suspend/restart icon on shutdown menu"
date: 2007-09-04
forum: Hardware &amp; Laptops
---

### Post by Jettechen on 2007-09-04
Dear all,
I'd like to remove the hibernate/suspend/restart button form the shutdown menu for some reasons.
But I don't now how to make this happen?
Can you please provide some suggestions?

Thank you very much.

---

### Post by banewman on 2007-09-04
One option is to make a launcher that uses the command -    shutdown -h , if you only want the option to shut down. :)

---

### Post by Jettechen on 2007-09-04
Now I can disable the suspend/hibernat from gconf-editor/apps/gnome-power-manager
but I can't find any restart relative information from that palce.
So there's still "restart" button on the log off menu

@banewman, sorry I can't understand you very much.
I need to remove the button on the menu, can you help me?
Thank you very much.

---

### Post by banewman on 2007-09-04
The option I gave was instead of editing the menu, have an icon on the panel to shutdown the computer. Right click the panel - the strip across the top of the screen - choose "add to panel" - then choose "custom application launcher". Call it "shutdown" and for the command type "shutdown -h". Then click "no icon" and it will let you pick an icon you like - says no icon because you haven't picked one yet. When you click this icon it will shut the computer down with no options - not sure if this is what you want? Hope this helps in some way. :)

---

### Post by Jettechen on 2007-09-04
@banewman,
OK I understand your meaning.
But, I still want my log off menu, because there is other buttons just like log off, switch user ...
That's the resean I want to edit the menu.

Do you have any other ideas?
Thank you very much.

---

### Post by Darkriser on 2007-09-07
> **Jettechen said:**
> @banewman,
OK I understand your meaning.
But, I still want my log off menu, because there is other buttons just like log off, switch user ...
That's the resean I want to edit the menu.

Do you have any other ideas?
Thank you very much.

I know what's he talking about. Have the same problem. I would like to deny other users to restart/shutdown my computer from menu (this is enough as they are not experienced users and console commands are out of their prehension). However, Lock or Logoff is OK, of course. Any solution for this?

Thanks,
Marcel

---

### Post by rubbsdecvik on 2007-10-19
I also would love to know how to do this.

---

### Post by oreodoh on 2008-01-18
Here's what I did to make this possible.  Yes, I'm sure there's a script that can do the same thing but do you want an answer or not?!  ;-)

[LIST=1]
[*]Install "pessulus", the lockdown editor for Gnome
[*]Open a terminal window and run "gconf-editor" (either sudo or as root)
[*]In Configuration Editor window, browse to "/desktop/gnome/lockdown/ folder"
[*]Change value of "disable_user_switching" from unchecked to checked (false to true)
[*]Right-click on "disable_user_switching" and click "Set as Mandatory".  I also clicked "Set as Default" but don't think this is necessary.
[*]Close Configuration editor.
[/LIST]

Theoretically, you should now be able to hit the Quit button and see the "Switch User" icon has disappeared!  If anyone has an easier method I'd be glad to hear about it.

Peace.

---

