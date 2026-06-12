---
title: "[SOLVED] Couldn't find Cairo-dock."
date: 2008-11-08
forum: General Help
---

### Post by ellalan on 2008-11-08
I have just installed cairo-dock using this method:
[http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en#8-32%20bits%20AND%2064%20bits](http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en#8-32%20bits%20AND%2064%20bits)

But I couldn't start it because its not showing under system tools or under preferences-> Main menu. 
Any ideas please.

---

### Post by cl0ckwork on 2008-11-08
doesnt run at all or just cant find the menu option?

try running it from the terminal
```
cairo-dock
```
and posting any errors it returns

---

### Post by ellalan on 2008-11-08
Hi
I am able to start in terminal and I get some warnings(see the attachment) but I couldn't find the menu option. Thanx for the help.

---

### Post by cl0ckwork on 2008-11-08
the warnings that show are just some options from cario that you would have to configure in the program.

other than that does it run ok when you start it through the terminal?
it seems that cairo doesnt create a menu option.
to run it, create an entry in system->pref->sessions so it starts up at boot
or run it from the terminal with an & sign like this
```
cairo-dock &
```
so it isnt depenant on that terminal window

---

### Post by ellalan on 2008-11-08
I think I'll give it a miss for a while because I have Cairo-dock installed in Hardy and its perfect but in Intrepid its crap.
When I close the Terminal the the dock vanishes, most of the preferences are default.
I got the menu option under System Tools when I installed the dock in hardy.
However, thank you for your help.

---

### Post by eternalnewbee on 2008-11-08
No idea if it makes a difference, but I pressed ALT-F2 and entered ```
cairo-dock
``` and it works just fine. Maybe you should add something from Synaptic...

---

### Post by ellalan on 2008-11-08
Thanx eternalnewbee, it works but every time I start the pc I have to press Alt+F2 because I can not see the dock icon to start under system tools. If I could see it I could add launcher to the panel. Another thing is personalisation options are very limited. I am aware that I could create an entry in sessions as cl0ckwork mentioned but I would prefer not to start automatically. 
In hardy I get an icon(orange coloured with CD inside). Thanks again.

---

### Post by eternalnewbee on 2008-11-08
> Thanx eternalnewbee, it works but every time I start the pc I have to press Alt+F2 because I can not see the dock icon to start under system tools. If I could see it I could add launcher to the panel. Another thing is personalisation options are very limited. I am aware that I could create an entry in sessions as cl0ckwork mentioned but I would prefer not to start automatically.
In hardy I get an icon(orange coloured with CD inside). Thanks again.
To do that go to **Main Menu > System > Preferences > Sessions**, and click **Add**. At name enter cairo-dock and at Command enter cairo-dock. The next time you start up your system cairo-dock will launch automatically.

---

### Post by ellalan on 2008-11-09
I have found the solution by going to System->Preferences->MainMenu, then clicked on the System Tools added the new item "cairo-dock".
Still I am not happy with the Personalise option as this is limited. Thanx again for all the help.

---

### Post by cl0ckwork on 2008-11-09
have you tried the advanced mode button?

---

### Post by ellalan on 2008-11-09
Thanx c10ockwork for this, I missed the Advanced mode completely. Thanks again.

---

### Post by n2dabloo on 2008-11-09
> **eternalnewbee said:**
> To do that go to **Main Menu > System > Preferences > Sessions**, and click **Add**. At name enter cairo-dock and at Command enter cairo-dock. The next time you start up your system cairo-dock will launch automatically.

Thank you very much for explaining that.  I was pulling my hair out trying to figure that one out :)  Now, cairo-dock starts with every start-up...

---

