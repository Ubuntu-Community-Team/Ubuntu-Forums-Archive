---
title: "Transparent menus question"
date: 2008-07-21
forum: General Help
---

### Post by Drizzel on 2008-07-21
Is there a way to make the menus transparent without using compiz or without installing anything? I will install something if I have to, but Compiz doesnt like my graphics card, so thats out. 

I'm running Ubuntu Hardy. I have the Panel transparent and also the terminal. I would like the drop down menus under Applications, Places, and System to be transparent to match the rest of what I have going on my desktop. Actually it would be nice to be able to make everything transparent.. Menus, window borders etc, but I mostly just want the drop down menus transparent. Possible? I've been sifting through posts for awhile and haven't seen anything that covers the menus I'm speaking of.

---

### Post by jordanmthomas on 2008-07-21
It would be possible to make these menus transparent without compiz.
I'm not exactly sure of what would be needed, but it seems like you could do it with devilspie + xcompmgr + transset.

I haven't used devilspie much, so for me to give you the required rules would just have me googling / reading manpages like you now have to.  :)

---

### Post by Drizzel on 2008-07-21
:) lol ok sounds good. I'll investigate. Any other ideas are welcome. I think a menu transparency option would be a cool thing to add to the next ubuntu rls.

---

### Post by Drizzel on 2008-07-22
Anyother ideas? Devilspie + xcompmgr + transset is just too much for me to deal with. I'm still sorta new to Ubuntu and I'm not comfortable enough to attempt to configure those 3 things to work together in harmony. Does KDE have an option built in for transparent menus? If so I'll just switch to KDE and be done with it. 

I didnt know transparent menus in gnome would turn out to be such a task. I'm actually surprised there aren't more people wanting to do this. I cant be the only one that wants my drop-down menus to be transparent to match the rest of my desktop.

---

### Post by jordanmthomas on 2008-07-22
Yes, KDE has the option for transparent menus.
Go to the style page in kcontrol, then to the effects tab.

Transparent menus are possible in gnome if you're willing to go with compiz (I know you're not)

---

### Post by Drizzel on 2008-07-22
I wish I could go with compiz.. My graphics card isnt supported and I dont have the funds to buy one of the expensive ones that are supported. Is it possible to try out KDE on ubuntu, but still have Gnome in case I dont like KDE? I'm concerned it will use a lot of ram. Maybe I should just switch to Kubuntu. I'm not sure which route to take.

---

### Post by jordanmthomas on 2008-07-22
Nah, it's easy.  Installing KDE alongside GNOME won't cause any greater RAM usage, just extra disk space.
```
sudo aptitude install kubuntu-desktop
```
It'll ask you if you want to use kdm or gdm for your login screen as / after it installs.  Choose kdm for KDE's login screen.

In my experience, KDE is lighter than GNOME.  Of course, I use kdemod instead which is designed to be a little lighter since you just install the parts you want.  KDE definitely doesn't use much more RAM than GNOME, and in many cases uses less.

If you want to go back to gdm, you can run
```
sudo dpkg-reconfigure gdm
```
and tell it to use gdm instead of kdm.  Either way, you'll be able to select either kde or gnome from the session menu (F10 in gdm..I think Ubuntu has the clickable menu disabled, so F10 will let you get to it)

To completely get rid of kde should you hate it, 
```
sudo aptitude remove kubuntu-desktop
```
will remove it.

---

### Post by Drizzel on 2008-07-22
Well that totally didnt work. All it did was give me the kubuntu login screen, but then gnome started up after I logged in and I got several errors. I selected kdm when it asked, but gnome still starts up so I uninstalled kdm. Oh well. I'll just back up all my files and switch to kubuntu.. I'm downloading an iso right now.


Edit: Bahh scratch that. No Kubuntu LTS? Forget it. Seems Kubuntu is still to experimental for me. I see all this kde remix stuff and community support only. No updates like in Ubuntu? Not for me. I'll just stick with Gnome.. wow what a disappointment.

---

### Post by jordanmthomas on 2008-07-22
I think you need to select kde in the kdm logon screen, or else you'll get gnome.

I do think kubunutu is updated regularly, and of course all the non-kde stuff is updated at the exact same time as ubuntu.

---

### Post by kidux on 2008-07-23
XFCE is a great non resource intensive DE that allows for transparent menus. You can get it in Synaptic or Apt.

---

### Post by jordanmthomas on 2008-07-23
Nice point, it has a built-in compositor too that works very well.

---

### Post by Drizzel on 2008-07-23
Ok that sucked.. I successfully installed the Kubuntu desktop. Probably the worst desktop environment I've ever experienced. I dont see how it is so popular. Couldnt drag and drop much of anything, themes wouldnt install, way too much stuff crammed into one area etc, blah. I like gnome much better. What took me 20 mins to do in kde I can do in a matter of seconds in gnome. I'm no longer curious.

Thx for the suggestion Kidux, I'm about to try it out. :)

Edit: scratch that as well.. Another complete desktop takeover. I cant believe there is no way to make menus transparent without completely replacing gnome. I have to totally reinstall Ubuntu now as there are dupes of most of my apps, and stuff is all screwy.

---

### Post by jordanmthomas on 2008-07-23
> **Drizzel said:**
> Ok that sucked.. I successfully installed the Kubuntu desktop. Probably the worst desktop environment I've ever experienced.


To each his own I suppose.  I find GNOME's lack of options disturbing.  :popcorn:

---

### Post by f37u5g0d on 2008-07-23
I got an ATI radeon 9550 from tiger direct for $20.00 that compiz loves and I have seen it work on onboard video (not from nvidia or ati).  In order to start kde instead of gnome you have to change the session (it's in the lower left hand corner of the log-in screen) to kde instead of gnome.  The same procedure is true about xfce.  You can have all three installed at once and just select the one you want to use at start-up.

---

### Post by Drizzel on 2008-07-23
Maybe I just need to give it more of a chance.. Since I've managed to screw up my whole ubuntu installation and need to reinstall anyway, I think I'm going to just tryout Kubuntu. I'm all frustrated from spending so much time installing/uninstalling things. Probably why I didnt like it. Thanks for all your help and suggestions.

---

### Post by Drizzel on 2008-07-23
> **f37u5g0d said:**
> I got an ATI radeon 9550 from tiger direct for $20.00 that compiz loves and I have seen it work on onboard video (not from nvidia or ati).  In order to start kde instead of gnome you have to change the session (it's in the lower left hand corner of the log-in screen) to kde instead of gnome.  The same procedure is true about xfce.  You can have all three installed at once and just select the one you want to use at start-up.

Man thats a great deal, I love tigerdirect. I'll give it a look.

---

### Post by kidux on 2008-07-23
> **Drizzel said:**
> 
Thx for the suggestion Kidux, I'm about to try it out. :)

Edit: scratch that as well.. Another complete desktop takeover. I cant believe there is no way to make menus transparent without completely replacing gnome. I have to totally reinstall Ubuntu now as there are dupes of most of my apps, and stuff is all screwy.

Sorry, I should've explained better I suppose. KDE, Gnome, XFCE, etc are desktop environments, which means you get an entirely new desktop experience and look when you use them. I've never like the cluttered look and feel of KDE, so I prefer XFCE, which has a very minimalistic feel and look without sacrificing functionality. 

Gnome's default window manager doesn't support true transparency, which is why you need to use something like Compiz. You can also try Enlightenment, or E17 as it's also called. It's nice, and can be used over top of the Gnome desktop.

---

### Post by Drizzel on 2008-07-23
> **kidux said:**
> Sorry, I should've explained better I suppose. KDE, Gnome, XFCE, etc are desktop environments, which means you get an entirely new desktop experience and look when you use them. I've never like the cluttered look and feel of KDE, so I prefer XFCE, which has a very minimalistic feel and look without sacrificing functionality. 

Gnome's default window manager doesn't support true transparency, which is why you need to use something like Compiz. You can also try Enlightenment, or E17 as it's also called. It's nice, and can be used over top of the Gnome desktop.

I hear ya, I actually decided to install Kubuntu lastnight. I gave it a real chance, but like you said its way to cluttered and actually Gnome can do somethings that I really like that KDE cant. So 10hrs later here I am back with Ubuntu and Gnome. Feels so much better. I'll try out E17 since it works with Gnome. Thx for all your help. :KS

---

