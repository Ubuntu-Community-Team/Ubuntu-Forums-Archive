---
title: "[SOLVED] Slow &amp;quot;Shut Down&amp;quot; Button Response"
date: 2008-08-21
forum: General Help
---

### Post by pofigster on 2008-08-21
I stay on top of the updates for Ubuntu, so I installed 8.04 as soon as it was available.  It's awesome.  However, in the past couple months as I've started applying new GTK2 themes including customizing the logo next to the Applications menu in Gnome I've noticed an incredible annoying problem.  Sometimes (about half the time) when I click the "shut down" button in the upper right hand of the screen to shut down my computer it literally takes 1.5-3 minutes for the window to pop up offering me the various options.  AND it's missing "Hibernate" as an option.

After I click the "shut down" button I can't do anything else - I can move the mouse around, but clicking doesn't do anything.  It's like Gnome is locked up or something.

Any idea what in the world is causing this and what I can do to fix it?  All the themes I've applied have come from gnome-looks.org or using the gnome-art package from the repositories.

---

### Post by Titan8990 on 2008-08-21
Do you have similar problems when doing:

sudo reboot

or

sudo shutdown

?

---

### Post by DJ_Peng on 2008-08-21
It sounds like you may be suffering from [Bug #150846 Quit button freezes screen but does not present Log out etc. options dialog]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/150846/comments/10"). this is the solution that I posted on [my blog]("http://nancib.wordpress.com/2008/04/29/is-ubuntu-freezing-when-you-try-to-quit-i-have-a-probable-solution-for-you/") back in April and seems to fix things for people.
> 

[LIST]
[*]Use **System > Preferences > Sessions** to make sure the Power Manager is set to run automatically every time you start Ubuntu.
[*] Use the System Manager to ensure that gnome-power-manager is running, and if it isn’t use Alt-F2 to get a Run dialog and run gnome-power-manager from there. (You can also run it from a Terminal.) This step is only needed during the session that you perform the first step.
[*] Attempt to Quit using either the Quit tool on your panel or by using **System > Quit**. You should get the Logout/Restart/Shutdown dialog.
[/LIST]


---

### Post by pofigster on 2008-08-21
Titan8990 - I'll check as soon as I'm back at the computer.
DJ_Peng - I'll give that a try to.  Thanks.

---

### Post by pofigster on 2008-08-22
It seems to have worked!  Thanks for your help!

---

### Post by DJ_Peng on 2008-08-22
Glad I could help.

---

