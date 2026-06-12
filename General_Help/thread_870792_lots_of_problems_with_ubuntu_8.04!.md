---
title: "lots of problems with ubuntu 8.04!"
date: 2008-07-26
forum: General Help
---

### Post by mahela007 on 2008-07-26
I dont know if I'm the only one this is happening to but I installed ubuntu 8.04 with the alternate installation cd and there seem to be many problems.
first one: the themes dont change properly. No matter which theme i chose i sill get the same icon set and colors. I tried to customize the themes to change there colours but that doesn't work.

Second: Synaptic package manager wont work. Every time I tun it says an error occured. it also tells me to manually run something called "dpkg-- reconfiguire yada yada".
can someone tell me some solutions to there problems? I really liked ubuntu 7.10. whats up with this verision?

I also forgot to mention , Flash drives don't work in 8.04. It says  something about an error regarding security and mounting the drives

---

### Post by rune0077 on 2008-07-26
> **mahela007 said:**
> I dont know if I'm the only one this is happening to but I installed ubuntu 8.04 with the alternate installation cd and there seem to be many problems.
first one: the themes dont change properly. No matter which theme i chose i sill get the same icon set and colors. I tried to customize the themes to change there colours but that doesn't work.


A little more info, please. How exactly do you try to change the theme, what theme are you trying to change (is it the GTK, the icon-theme, the pointer, etc)?

> **mahela007 said:**
> 
Second: Synaptic package manager wont work. Every time I tun it says an error occured. it also tells me to manually run something called "dpkg-- reconfiguire yada yada".
can someone tell me some solutions to there problems? I really liked ubuntu 7.10. whats up with this verision?


Try and do what it says. Open a termnial and run the command Synaptic tells you to run.

---

### Post by mahela007 on 2008-07-26
i right clicked on the desktop and clicked change background.
then on the window that appeared i went to the tab called themes.
then i tried to change the themes. Only the shape of the window border changes.

I dont know the exact command it says.
Normally the command starts with sud apt something .... ( i dunno cos i'm still a newbie to linux,)

---

### Post by mahela007 on 2008-07-26
this is the error message i get when i open synaptic.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by rogier.de.groot on 2008-07-26
So, open up a terminal window and type in "sudo dpkg --configure -a", press enter, wait for the command to finish, and synaptic will work again.
Also, flash drives work just fine. Unless your user account has security restrictions.
EDIT: sudo will ask for your password - you can not run this command without administrative access.

---

### Post by rune0077 on 2008-07-26
> **mahela007 said:**
> i right clicked on the desktop and clicked change background.
then on the window that appeared i went to the tab called themes.
then i tried to change the themes. Only the shape of the window border changes.


From the theme tab, try clicking the button that says "Customize". This gives you a new window, where you can change lots of things, like the icon-theme, the controls (GTK) theme, and such. Make your changes here.

> **mahela007 said:**
> this is the error message i get when i open synaptic.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Then open a terminal (Applications > Accessories > Terminal), and type in the command:

```
dpkg --configure -a
```

---

### Post by northern lights on 2008-07-26
> **mahela007 said:**
> the themes dont change properly. No matter which theme i chose i sill get the same icon set and colors. I tried to customize the themes to change there colours but that doesn't work.After seleceting your preferred metacity theme under "System > Preferences > Appearance", click the "Customize..." button below the theme selection window. Here you'll find pointer and icon tabs. 



> **mahela007 said:**
> Synaptic package manager wont work. Every time I tun it says an error occured. it also tells me to manually run something called "dpkg-- reconfiguire yada yada".
Run ```
dpkg --configure -a
```from a terminal window.

[EDIT]
late...
[/EDIT]

---

