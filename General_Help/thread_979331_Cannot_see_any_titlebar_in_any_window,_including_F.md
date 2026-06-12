---
title: "Cannot see any titlebar in any window, including Firefox (Ubuntu 8.10)"
date: 2008-11-11
forum: General Help
---

### Post by catchagato on 2008-11-11
There were some updates which I installed today, and after I rebooted my laptop, all the titlebars just seemed to disappear. Whenever I open a window, such as Terminal, the window is stuck on the top left side of my desktop, and there is no titlebar. If anyone is experiencing this same problem, or knows a solution, please help. This only started to happen after the latest update I received through Update Manager (Nov. 11).

[IMG]http://i115.photobucket.com/albums/n314/catchagato/Screenshot-2.png[/IMG]

[IMG]http://i115.photobucket.com/albums/n314/catchagato/Screenshot-1.png[/IMG]

---

### Post by catchagato on 2008-11-11
Update: Pressing F11 a few times does nothing, but I figured out that in Visual Effects, the missing titlebars ONLY happen when my Visual Effects are on EXTRA mode. When I set it to either NONE or NORMAL, the titlebars are all there, and everything seems fine. It is just when my visual effects are set to extra, and then the problem occurs. But if anyone knows how to get the titlebars back in Extra mode, then please let me know.

---

### Post by dlm4849 on 2008-11-11
Looks like what happens when you have the command under compiz's window decorator wrong. Verify that the command under window decoration reads "/usr/bin/compiz-decorator" unless you were using Emerald.

---

### Post by cl0ckwork on 2008-11-11
yes, it seems something with compiz has been botched.
try installing the full compiz config settings manager and the fusion-icon

hopefully that can fix it

---

### Post by catchagato on 2008-11-11
Alright, thanks for the suggestions. I am still a little bit new with Ubuntu. Where do I go to check the command line, and would how do I know if I have installed the "full" compiz-settings manager? It is installed through the package manager right now.

---

### Post by dlm4849 on 2008-11-11
Go to the main menu deal and the preferences, then advanced desktop effects settings. That will bring you to the compiz settings manager. Then scroll down to effects, where you will find window decoration. Once you click on that, you will see the command box I was referring to.

---

### Post by catchagato on 2008-11-11
The command line is correct after checking it. So now I can rule that possibility out. Thanks though.

---

### Post by dlm4849 on 2008-11-11
What is in the Decoration Windows field in that same area say? That should read "any" by default. Short of that, Im not sure what else could be wrong.

Also, you do have the check box marked so that window decoration is enabled, right?

EDIT: Do all of this while youre on the extra settings, so that you cannot see your title bar. Switching to the normal may be putting different values in for these fields.

---

### Post by catchagato on 2008-11-11
That worked! Thank you very much. The Window Decorations box was not checked when I selected the Extra mode. I assume my most recent update unchecked it or did something else to it... But thank you again.

---

### Post by dlm4849 on 2008-11-11
Not a problem. Glad I could help.

---

### Post by David Valentine on 2008-11-12
Well, I've tried everything in this thread, and my titlebars are still not visible when desktop effects are set to "normal" or "extra".  They were fine under Hardy.  I have also tried resetting everything to default values in the compiz setting manager.  Any other ideas?  Do I need to delete a configuration file so it'll get rebuilt?

---

### Post by Tony Myers on 2008-11-12
Same, I've tried all methods here and still have "damaged" window borders.

---

### Post by cl0ckwork on 2008-11-12
check and make sure your video drivers are still configured properly.
the upgrade to 8.10 could have messed with then since it is not truly open source and not supported fully

---

### Post by David Valentine on 2008-11-12
I've rechecked the drivers and as far as I can tell they're configured correctly.  I get direct rendering, for example--what else should I look for?:confused:

---

### Post by catchagato on 2008-11-12
UPDATE: The problem is NOT fixed actually. I have Windows Decoration selected, and the titlebars return, BUT it automatically selected None for desktop effects. When I select Extra, and then tick the Windows Decoration box, it reverts back to None. I don't know what's causing this problem. If only I didn't download those updates...

---

### Post by AlexDonald on 2008-11-12
I had this problem with a completely fresh (formatted hard drive) install of Intrepid. I couldn't figure out what I had done for ages, then I remembered that I had backed up my home directory from when I had Hardy. I stupidly copied the hidden Firefox folder into my new home directory so I would still have all my bookmarks, passwords, history and add-ons. I didn't think that maybe Intrepid uses slightly different config files (It shouldn't do, as Firefox is the programme using them and it's the same).

Long story short, I deleted the contents of the folder (~/.mozilla/firefox) and restored my bookmarks the proper way and re-installed my add-ons.

Now unless you've done something as crude as me, maybe the update process does something weird when it keeps all your personal settings. If you can deal with losing your private data, try deleting these files.

It has worked for me fine and I now have no problems...

Could someone who knows more about these files and what they do and the implications of changing them make any suggestions?

---

### Post by David Valentine on 2008-11-12
Firefox is but one application--none of my application windows, including firefox, have borders or titlebars on that PC.  My other PC's upgraded essentially without incident, and compiz runs fine on them.  I'm wondering now if it's a limitation of my GeForce 6200 video card--should I downgrade the nVidia driver to 173 or even the previous version?  Can I do that by running the "Hardware Drivers" without borking my system?  I haven't had the best history of swapping drivers without precipitating xorg headaches.

---

### Post by slinkey1981 on 2008-11-12
> **David Valentine said:**
> Firefox is but one application--none of my application windows, including firefox, have borders or titlebars on that PC.  My other PC's upgraded essentially without incident, and compiz runs fine on them.  I'm wondering now if it's a limitation of my GeForce 6200 video card--should I downgrade the nVidia driver to 173 or even the previous version?  Can I do that by running the "Hardware Drivers" without borking my system?  I haven't had the best history of swapping drivers without precipitating xorg headaches.

I am running 8.10 with a GeForce 6200 and no problems. You can try using EnvyNG to switch your card drivers.

---

### Post by AlexDonald on 2008-11-12
> **David Valentine said:**
> Firefox is but one application--none of my application windows, including firefox, have borders or titlebars...

When you installed Intrepid (which I guess is when the problem started occurring), did you upgrade and port all of your personal settings across from Hardy?

If so, maybe the files that personalise each of these programs is playing up... Maybe try renaming the folders for these programs to see if there is any difference?

I would have thought if this was the case, then the problem would be the backwards compatibility of a component in compiz maybe when used with certain graphics card (I haven't a clue what I'm using, it's a 2nd hand laptop); but that would surely be something that was come across in testing?

---

### Post by catchagato on 2008-11-12
Are there any new updates for the nVidia drivers? I don't know what else could be the cause of this problem. It is not just Firefox, but all other windows which don't have titlebars, so I don't think it's just a Firefox problem...

---

### Post by Tony Myers on 2008-11-13
> **catchagato said:**
> Are there any new updates for the nVidia drivers? I don't know what else could be the cause of this problem. It is not just Firefox, but all other windows which don't have titlebars, so I don't think it's just a Firefox problem...

Same here for me, does it in terminal.

Specs:
Ubuntu 8.10 fresh install.
nvidia 6600gt, driver 177.
Linux citrus 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux

---

### Post by David Valentine on 2008-11-14
Downgrading the nVidia drivers to 173 or 96 did **not** solve the missing titlebar problem.  I also tried```
sudo dpkg-reconfigure xserver-xorg
``` and ```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
``` to no avail.  Other ideas?

---

### Post by David Valentine on 2008-11-16
Problem solved.  I had to do 2 things:  
1.  Reset all gnome configuration settings to default values.  Open a terminal and type ```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```2.  Ensure I'm using emerald instead of metacity.

---

