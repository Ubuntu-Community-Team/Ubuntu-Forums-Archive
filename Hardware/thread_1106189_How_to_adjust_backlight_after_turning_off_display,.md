---
title: "How to adjust backlight after turning off display, sleep, hibernate or switching user"
date: 2009-03-25
forum: Hardware
---

### Post by Paddy Landau on 2009-03-25
On my laptop, I set up a dual screen environment with a script that runs at startup (the script checks whether I have the extra screen attached and sets appropriately with xrandr).

It also sets my laptop's brightness to dim, because it's very bright anyway:
```
xrandr --output LVDS --set BACKLIGHT 0
```However, whenever I switch user, wake up the computer after it turns off the display or after it sleeps, or after  hibernating, it always sets the brightness back to brightest.

How can I ask the computer to set the default brightness to dim?

Alternatively, is there somewhere that can I instruct the computer to run that command whenever it wakes up or after switching user?

TIA

---

### Post by rajan on 2009-05-11
it seems like you know what you're doing to a certain extent so i will suggest a bit more involved solution (which i've never tried, by the way)

a while back i was reading up on run levels and i seem to remember that there are 7 run levels, and one or two of them are levels that can be assigned to whatever you want them to be assigned to. it may be possible to assign a level to when you are switching from user to user, or waking up from sleep. 

after this, it is easy to insert a runlevel script into your /etc folder.

if this doesn't suit you, there's always the low tech approach to run a certain command with a quick keystroke. for example, i start my screensaver with <shift> F10 (it's actually the command gnome-screensaver-command --activate). i added the keybinding in the gconf-editor under the apps --> metacity. there's a really simple guide right here:

[http://ubuntuforums.org/showthread.php?t=42404](http://ubuntuforums.org/showthread.php?t=42404)

hope this helps (a bit late)

---

### Post by Paddy Landau on 2009-05-12
Thank you, rajan, for your suggestions.

I know of:

[LIST]
[*]ACPI: /etc/acpi/*.d
[*]PM-UTILS: /usr/lib/pm-utils/sleep.d
[*]Run levels: /etc/rc*.d and update-rc.d
[/LIST]
Unfortunately, none of them seems to trigger when waking up from a screensaver or suspend.

---

### Post by rajan on 2009-05-14
yeah, sorry i wasn't more specific. i meant the /etc/rc*.d/

what i was saying is that you could define a particular runlevel, and put a script in that runlevel's directory. here are a few interesting sites that explain this a bit better:

according to this one, runlevel 4 is user-defined:
[http://www.cyberciti.biz/faq/linux-define-the-runlevel-and-determine-which-runlevel-my-system-is-currently-in/](http://www.cyberciti.biz/faq/linux-define-the-runlevel-and-determine-which-runlevel-my-system-is-currently-in/)

this one is from an HPUX site, but still interesting:
[http://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1242277428647+28353475&threadId=1093613](http://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1242277428647+28353475&threadId=1093613)

and this is seems to be the best, most comprehensive resource, but it's really long:
[http://www.debian-administration.org/articles/212](http://www.debian-administration.org/articles/212)

good luck, sorry i can't be more help. hopefully someone will see this bump and be of more use. 

rajan

---

### Post by Paddy Landau on 2009-05-14
> **rajan said:**
> here are a few interesting sites that explain this a bit better:
Thanks for the links, Rajan. I'll have a good look in a couple of days and let you know if I manage to do anything.

---

