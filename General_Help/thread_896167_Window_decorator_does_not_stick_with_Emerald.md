---
title: "Window decorator does not stick with Emerald?"
date: 2008-08-20
forum: General Help
---

### Post by matxdr on 2008-08-20
Hi, 

I am a Ubuntu user for 4 months now and like it very much. I am trying to use the compiz options to improve the look, and I cannot get it to stay. I ran compiz-check and all is OK (I have a Geforce FX 5200 card). I use the enhanced driver from the installation. I was following this guide [http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/](http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/) but run into problems. 

I cannot get the cube to work, and when  troubleshooting it, I realize that something basic does not seem to work correctly. I may have screwed up something. 

When I activate System, preferences, appearance”  and it the “visual effects” tab, select “extra”, I see the new effects, and Emerald seems to be enabled (I choose it from the compiz-fusion icon). This is fine. However, if I open a window, say terminal, and then switch application using ALT-TAB, then the decoration goes back to the GTK look. If I go back to the visual effects, the "None" option is selected instead of extra. I noticed this behavior when I select the cube in advanced desktop settings as well.

Is there any log or command to check why I get this behavior? :confused:

Thanks alot!

---

### Post by tuxxy on 2008-08-20
Did you download the compiz effects manager? this is where you can enable the desktop cube,

```
sudo apt-get install ccsm
```

To enable emerald type in terminal, or add the command to your sessions.

```
emerald --replace
```

---

### Post by matxdr on 2008-08-21
Hi, 

Thanks for the reply!

The ccsm cannot be found, do you meant simple-ccsm?

I do have compizconfig-settings-manager installed.


[edit]
I am not actually sure if Emerald get replaces by GTK. What make be believe this is that when I start my session, Emerald seems to be enabled because the Windows border arre transparent, I get the effect and the Window Title is red. Everything works fine, except that if I ALT-TAB, of go in the advanced settings to turn on / off something, then (I think) the Window Manager reloads and I loose the window transparency, and the Window title bar becomes blue as my previous GTK setting made in the Preference GUI under theme. From there, going back to appearance shows me that the visual settings are set to none instead of extra. The compiz-fusion icon still shows that Emerald is in use, but I guess it only changes its selection on user intervention and does not auto-detect / update which decorator is used.

Cheers

---

### Post by generalguy on 2008-08-21
When you lose transpatency, do you also lose other compiz effects (wobbly windows etc.)?

---

### Post by generalguy on 2008-08-21
Double post, my bad.

---

### Post by matxdr on 2008-08-21
Yes, I lose all the effects as well. I also tried to do alt-f2 and run emerald --replace. This did not seem to have any effect.

---

### Post by matxdr on 2008-08-22
After trying again, I confirm that it is Metacity coming back instead of compiz. Then if I use the compiz-fusion icon to put compiz again, it works. Now if I set the cube, it falls back again to Metacity. If I change if back again to compiz, then I loose the window title bar and I cannot type in the window. I do not get any error message, I will try to query the logs to see if I find anything and post back my findings if anyone else have the same problem as I do.

---

### Post by Niscrome on 2008-08-22
Try downloading Compiz config setting manager through synaptic
*System>Administration>synaptic* and search: *compiz*.

That should solve the CCSM problem but I do know about the other.

---

### Post by Washer on 2008-08-23
Upgrade

[http://ubuntuforums.org/showpost.php?p=5293362&postcount=5](http://ubuntuforums.org/showpost.php?p=5293362&postcount=5)

---

### Post by techstop on 2008-08-23
Try entering "emerald --replace" in the Command text box in the Window Decoration plugin in ccsm.

---

### Post by matxdr on 2008-08-24
> **Washer said:**
> Upgrade

[http://ubuntuforums.org/showpost.php?p=5293362&postcount=5](http://ubuntuforums.org/showpost.php?p=5293362&postcount=5)

Thanks for the reply. I tried this and get the same result. As soon as I alt-tab, Metacity kicks in. Do you have any other suggestion?

---

### Post by matxdr on 2008-08-24
[QUOTE=tuxxy;5633087]
```
sudo apt-get install ccsm
```

This is what I get when I do this command (note this Ubuntu is in French)
sudo apt-get install ccsm
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
E: Impossible de trouver le paquet ccsm

This is a snapshot of the Synaptic when I search for compiz:

[ATTACH]82672[/ATTACH]

---

### Post by david sousa on 2008-08-24
Simple as that:

put "emerald --replace" in place of "compiz-decorator" at command box in windows decorator tab at compiz manager. So it should say "/usr/bin/emerald --replace"

Keep cool ;)

---

### Post by matxdr on 2008-08-24
> **david sousa said:**
> Simple as that:

put "emerald --replace" in place of "compiz-decorator" at command box in windows decorator tab at compiz manager. So it should say "/usr/bin/emerald --replace"

Keep cool ;)

It is what I have, still no luck :(

---

### Post by matxdr on 2008-09-02
I am still stuck with this issue. Others seems to have the same problem, does anyone  has any other suggestion? 

Thanks!

---

### Post by Garratt on 2008-09-02
emerald sux... I know the glass effects are cool, but it just seems to play with so many other things and stuff starts breaking, like icon themes.

my suggestion.

sudo apt-get remove emerald

you can always just go into compiz and click on "reflection" and adjust to your liking.. this seems to give a nice effect. additionally you can add your own images.


And also you may want to check through compiz and/or emerald (if you still have it installed) settings and check for any alt + tab keybindings. depending on what you have it bound to may cause some problems.

---

