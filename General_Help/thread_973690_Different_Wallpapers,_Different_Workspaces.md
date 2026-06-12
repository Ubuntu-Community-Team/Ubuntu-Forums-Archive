---
title: "Different Wallpapers, Different Workspaces"
date: 2008-11-06
forum: General Help
---

### Post by thecrimsonalchemist42 on 2008-11-06
Hello everyone,

Can somebody please help show me how to put a different wallpaper on each workspace of the desktop? I know there are ways of doing this, but I don't know how to.

Also, if it is important, I am using Intrepid Ibex.

Thanks :)

---

### Post by HyperHacker on 2008-11-07
I think the latest Compiz has a Wallpaper plugin that can do this. I haven't got it working with Xfce, but it looks like you can load multiple images and position them wherever you want; I assume you could put them on different workspaces.

---

### Post by slinkey1981 on 2008-11-07
You need to be using Compiz 7.6  there is a Wallpaper plugin that does allow you to use different wallpapers on different desktops, but you have to set Nautilus to *NOT draw the desktop.

This causes you to lose your desktop icons, because Nautilus will NOT place icons on a transparent desktop.

But yes...  You can do it.

---

### Post by HyperHacker on 2008-11-07
Can this be done in Xfce? Same problem, turning off desktop management = no icons/menu/etc, and no option not to draw a background.

---

### Post by slinkey1981 on 2008-11-07
> **HyperHacker said:**
> Can this be done in Xfce? Same problem, turning off desktop management = no icons/menu/etc, and no option not to draw a background.

As much as I would LIKE to help, I have only ever used gnome. Hopefully some XFce users will come along.

Sorry.

---

### Post by R2D2! on 2008-11-28
You need to d&#305;sable Naut&#305;lus from show&#305;ng the desktop
In gconf-ed&#305;t, set /apps/nautilus/preferences/show_desktop to false.
Then use Comp&#305;z Wallpaper to select each wallpaper for each desktop

&#8212;Ilhu&#305;temoc &#948;

---

### Post by coldReactive on 2009-10-01
> **slinkey1981 said:**
> As much as I would LIKE to help, I have only ever used gnome. Hopefully some XFce users will come along.

Sorry.

Bumping this thread, because would be nice to have it in xfce. I don't use nautilus.

---

### Post by marmotapl on 2009-10-01
Try using Wallpapoz...

[http://wallpapoz.akbarhome.com/](http://wallpapoz.akbarhome.com/)

Cheers.

---

### Post by coldReactive on 2009-10-01
> **marmotapl said:**
> Try using Wallpapoz...

[http://wallpapoz.akbarhome.com/](http://wallpapoz.akbarhome.com/)

Cheers.

See this portion:

> 20 July 2008, I think this is sad news for you. I decided to postpone the development of new version of Wallpapoz for a very long time. Well, this sentence is a soft version of this sentence: **_*I quit developing Wallpapoz.*_**

---

### Post by marmotapl on 2009-10-02
@coldReactive.

My bad,

It's there any problem on using an old version of the program?. I'm new in this... sorry

---

### Post by AbdRahim on 2009-10-03
I get the following error when trying to run Wallpapoz. Any ideas on how to fix it? Running jaunty. 

Traceback (most recent call last):
  File "/usr/local/bin/wallpapoz", line 1239, in <module>
    wallpapozgui = Wallpapoz()
  File "/usr/local/bin/wallpapoz", line 125, in __init__
    self.load_treeview()
  File "/usr/local/bin/wallpapoz", line 680, in load_treeview
    worklist = self.wallpapozxml.fill_list()
  File "../share/wallpapoz/lib/xml_processing.py", line 247, in fill_list
    worklist[index].append(node.firstChild.data)
AttributeError: 'NoneType' object has no attribute 'data'


To me it does not make sense to have multiple workspaces, all with the same background.

---

### Post by &lt;h1&gt;Mckennie&lt;/h1&gt; on 2009-11-16
i dont really like it but wallpapoz can do that its not really seamless ut it gets the job done

---

### Post by dushy4 on 2010-04-08
Sorry to bump into such a old thread but i just found the solution at some other site.
I had the following error while running wallpapoz:
/usr/local/bin/wallpapoz
Traceback (most recent call last):
File "/usr/local/bin/wallpapoz", line 1239, in <module>
wallpapozgui = Wallpapoz()
File "/usr/local/bin/wallpapoz", line 125, in __init__
self.load_treeview()
File "/usr/local/bin/wallpapoz", line 680, in load_treeview
worklist = self.wallpapozxml.fill_list()
File "../share/wallpapoz/lib/xml_processing.py", line 247, in fill_list
worklist[index].append(node.firstChild.data)
AttributeError: 'NoneType' object has no attribute 'data'

and the solution is at: [http://wallpapoz.akbarhome.com/faq.html](http://wallpapoz.akbarhome.com/faq.html)

which is 
Open the Wallpapoz configuration file, /home/your_user_name/.wallpapoz/wallpapoz.xml.
You will have something like this:
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE Wallpapoz>
<wallpapoz interval="5" random="0" style="2" type="workspace">
<workspace name="rename this" no="1">
<file></file>
</workspace>
<workspace name="rename this" no="2">
<file></file>
</workspace>
</wallpapoz>
Make it something like this:
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE Wallpapoz>
<wallpapoz interval="5" random="0" style="2" type="workspace">
<workspace name="rename this" no="1">
<file>blabla</file>
</workspace>
<workspace name="rename this" no="2">
<file>blabla</file>
</workspace>
</wallpapoz>
Restart Wallpapoz.

works perfectly!!!!
(changed the <file></file>  to <file>blabla</file> for each wallpaper:guitar:)

---

