---
title: "new to kde, some questions :)"
date: 2005-11-05
forum: General Help
---

### Post by jamesford on 2005-11-05
hi, ive used linux now for about 6 months, gnome only. i feel ive finally mastered basic linux pretty well, and gnome really well.

so i was thinking about giving kde a go, but ive got some questions:

1: is firestarter the recommended firewall for kde too, or is there something else i should look into

2: is superkaramba sort of the kde version of gdesklets ?

3: will i have to do soemthing to make certain programs liek thunderbird, amule, azureus, xchat and firefox look like other kde apps ?

4: can i use gaim in kde and can i make it look like other kde apps ?

5: how about programs that i suppose are gnome specific apps like gnomebaker (i really love gnomebaker)?

6: how do i make things run at startup, like a firewall

7: is there a kubuntuguide liek ubuntuguide.org somewhere ?

8: how do i get rid of all the annoying effects in kde, like the jumping cursor animation when you open a program, the ridicolously big tooltip/balloon things when u hold the mouse over something. im sort of a minimalist (maybe xubuntu is the thing for me)

9: im using ontv with xmltv in gnome, i really need something similar in kde that can display tv program schedules

im sure most of these questions are answered elsewhere, but i find all the documentation quite overwhelming, especially as it took me 6 months to learn gnome properly ;) so i was hoping some kind souls would help me get started with these, for me relatively important questions

thanks :)

---

### Post by `GooZ´ on 2005-11-05
Well for all these things you COULD stick to gnome ;-)
Otherwise, most (if not all) gnome apps should work fine in KDE. Just as my gnome install runs many KDE apps.
I think Karamba is gdesklets for KDE.
The standard IM for KDE that looks a bit like gnome is Kopete.
Ubuntuguide should be suitable for kubuntu too, i guess....

---

### Post by LorenzoD on 2005-11-06
If you want your KDE and Gnome applications to have the same look, you'll want  to use similar looking themes on the two. There is also a theme engine for Gtk that call Qt to do the actual drawing. It's called gtk2-engines-gtk-qt. You could try that. Then you could run Gaim in KDE with a similar look to native KDE applications.

I personally prefer to run native applications as far as possible. So when I'm running Gnome I stick to Gnome applications and when I use KDE I use KDE applications.

---

### Post by mlomker on 2005-11-06
> 1: is firestarter the recommended firewall for kde too, or is there something else i should look into


Yup.  The firewall that I recommend would be hardware, but if you need a software firewall then firestarter is it.

> 4: can i use gaim in kde and can i make it look like other kde apps ?

The taskbar icon looks a little odd but that's what I use.

> 6: how do i make things run at startup, like a firewall

By default anything open at shutdown will be reopened, otherwise use the 'save session' option on the main menu.

> 7: is there a kubuntuguide liek ubuntuguide.org somewhere ?
[URL="http://kudos.berlios.de/kf/kf1.html"]
Yeah, but it's a little out of date now.[/URL]  

> 8: how do i get rid of all the annoying effects in kde, like the jumping cursor animation 

**kdesu kcontrol** and look under Appearance & Themes.

---

