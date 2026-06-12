---
title: "Metabar 0.8"
date: 2005-11-29
forum: General Help
---

### Post by Jeff Eklund on 2005-11-29
Hi! 
The metabarpackage in the reps are a bit out-of-date, since Metabar was totally rewritten since version 0.8 and the version in the reps is 0.7. Is there any chance that someone could upgrade the package in the reps or does anyone know of a .deb found somewhere else that works untill the package is officially updated in the reps?
Thanks.

---

### Post by daller on 2005-11-29
I found this using google...

[http://codigolivre.org.br/frs/?group_id=1202&release_id=1740](http://codigolivre.org.br/frs/?group_id=1202&release_id=1740)

...I had some troubles downloading the file, here is a deeplink:

[http://mirror.codigolivre.org.br/pub/pacotesdeb/Todos/1.0/metabar_0.8-1_i386.deb](http://mirror.codigolivre.org.br/pub/pacotesdeb/Todos/1.0/metabar_0.8-1_i386.deb)

---

### Post by ltmon on 2005-11-29
You could also try requesting on backports, because it 0.8 will be in the next version.  Check the dapper drake repository, and when it appears there request a backport.

L.

---

### Post by Chris_(medico_2001) on 2005-11-30
I built a .deb package for Kubuntu (5.10).
can be downloaded [here](http://www.klikit.org/programs/metabar_0.8-1_i386.deb) (right click and save)  (metabar-0.8-1 - 95 Kb)
Have Fun!

---

### Post by ltmon on 2005-11-30
**<plug mode="shameless">**
Use my metabar theme available here: [http://kde-look.org/content/show.php?content=31268](http://kde-look.org/content/show.php?content=31268)
**</plug>**

---

### Post by cLawhammer on 2005-11-30
Hi,

I have problem installing the .deb. Is reported as a know problem of 3.5RC but isn't there the solution.

[https://wiki.ubuntu.com/KubuntuKDE35BetaKnownProblems]("https://wiki.ubuntu.com/KubuntuKDE35BetaKnownProblems")

I have installed KDE 3.5 final

(home made translation, sorry)
```

gred@ubuntu:~/Desktop$ sudo dpkg -i metabar_0.8-1_i386.deb
(Reading data base...
124651 files and directories installed )
Unpacking metabar (de metabar_0.8-1_i386.deb) ...
dpkg: error procesing metabar_0.8-1_i386.deb (--install):
trying to overwrite `/usr/lib/kde3/konqsidebar_metabar.la', is also in the packet konq-plugins
dpkg-deb: subproceso paste fue terminado por la señal (Tubería rota)
Errors found processing:
 metabar_0.8-1_i386.deb

```

Any tip?
Thanks

---

### Post by Chris_(medico_2001) on 2005-12-01
Try sudo dpkg -i --force-overwrite metabar_0.8-1_i386.deb, and it should work

---

### Post by Chris_(medico_2001) on 2005-12-01
[QUOTE=ltmon]**<plug mode="shameless">**
Use my metabar theme available here: [http://kde-look.org/content/show.php?content=31268](http://kde-look.org/content/show.php?content=31268)
**</plug>**[/QUOTE]

I've been using your theme in my Kubuntu system...
It is very nice, and blends just perfect with my current desktop

---

### Post by cLawhammer on 2005-12-01
Problems of dependencies but seems to work, konqueror takes 10-15 seconds to open.
Thanks for help 

```

Unpacking metabar (de metabar_0.8-1_i386.deb) ...
dpkg: problemas de dependencias impiden la configuraci&#243;n de metabar:
 metabar depende de kdelibs4 (>= 4:3.3.2-6.1); sin embargo:
  el paquete kdelibs4 no est&#225; instalado.
 metabar depende de libidn11 (>= 0.5.18); sin embargo:
  Versi&#243;n de libidn11  en el sistema es 0.5.13-1.0.
 metabar depende de libqt3c102-mt (>= 3:3.3.4); sin embargo:
  el paquete libqt3c102-mt no est&#225; instalado.
 metabar depende de libxrender1 (>> 1:0.9.0-1); sin embargo:
  Versi&#243;n de libxrender1  en el sistema es 1:0.9.0-1.
dpkg: error al procesar metabar (--install):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 metabar

```

OT : Any easy way to set up all aplications in English and delete other languages installed?

---

### Post by manubreizh on 2005-12-01
hi,
in kde3.5 final, metabar is by default in konqueror ; i've had troubles because i used to install it through the repositories, but after uninstalling it (with synaptic), i found it in konqueror, and everything works like a charm !!
maybee uninstalling emtabar 0.7 and upgrading to 3.5final could make it for you too ?
hope that helps

---

### Post by cLawhammer on 2005-12-01
Removing all metabar packages and upgrading via aptitude -> I can't add to konqueror. My system needs the version 0.7 of repositories or the .deb with 0.8 :confused:

---

### Post by manubreizh on 2005-12-01
don't you have it in the universal sidebar ? in my case, it appears without any configuration...
strange indeed...
have you tried to right-click on universal sidebar and do you have "add metabar" in context menu ?

---

### Post by cLawhammer on 2005-12-01
Yes, I try it. Only appears if a install metabar 0.7 or 0.8.

---

### Post by nrwilk on 2006-01-25
I've installed the .deb of metabar 0.8 from this thread, and I want to use this kubuntu theme:

[http://www.kde-look.org/content/show.php?content=34127](http://www.kde-look.org/content/show.php?content=34127)

But, when I right click on metabar and select "configure", there is no option to select a new theme to use with metabar.  All I get is a configuration window with three  tabs, "General", "Actions", and "Links."

I also tried putting it in ~/.kde/share/apps/metabar/themes, even though I'm running KDE 3.5, but this hasn't worked either.

How do I use this theme?

---

### Post by Vetto on 2006-05-02
[QUOTE=nrwilk]
But, when I right click on metabar and select "configure", there is no option to select a new theme to use with metabar.  All I get is a configuration window with three  tabs, "General", "Actions", and "Links."
[/QUOTE]
I only have the same options...I think that is because we only have metabar 0.7...what came with 5.10 I suppose.

There has to be a way to upgrade this to 0.8...

Anyone get this to work?  stock 5.10 install with KDE3.5 does not have metabar with the "install theme" option in the configure dialog....or at least mine doesn't

---

### Post by flapane on 2006-05-11
same problem here (amd64). I need 0.8

---

