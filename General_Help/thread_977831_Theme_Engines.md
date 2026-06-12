---
title: "Theme Engines"
date: 2008-11-10
forum: General Help
---

### Post by herbie643 on 2008-11-10
How the heck do you install 'Theme' engines?   Not to be condescending, but, man it is soooooo confusing...  I open with  Archive Manager and extract and it extracts to the directory of where I downloaded it.  I mean, come on, extract the files to where they are supposed to go.   How is a noob, well not totally, but new enough, know where some of this stuff is supposed to go.  No readmes with install instructions.  If there is one area where Ubuntu, and probably other distro's fail, is in this area.
Sorry, didnt mean to rant, but man it sure is frustrating.

---

### Post by Idefix82 on 2008-11-10
> **herbie643 said:**
> 
Sorry, didnt mean to rant, but man it sure is frustrating.

Well, you did rant even if you didn't mean to.
What do you mean by "theme engines"? Do you mean gtk themes? Or do you really mean engines like clearlooks, pixbuf,... If it's the latter then you should install them via System->Administration->Synaptic Package Manager and not by downloading something and extracting it somewhere.
If you are talking about a gtk theme then simply open the System->Preferences->Appearance dialog and drag the tar ball that you obtain after extracting into the dialog.

---

### Post by herbie643 on 2008-11-10
Well I followed your advice and didnt find the gtk-smooth engine.  theres a gtk-smooth-theme but not a gtk-smooth-engine.  I also wanted the 'aurora engine'. no luck there either.
The  problem arises when you install a theme and then the Appearance tab complains about then 'engine' not being installed.   so you see my quandry.
But thanks anyway, and i do have a lot of engines installed but not the ones i want.

---

### Post by CarpKing on 2008-11-10
Try searching on gnome-look.org, getdeb.net, or even google (given of course that you make sure the engine cannot be installed through Synaptic).  Files ending in .tar.gz or .tar.bz2 are theme archives (source code is also distributed in such archives but that's beyond the scope of this thread).  Files ending in .deb are installation files.  You'll want something like "gtk-engines-smooth-v<version>.deb;" after you download this file, double click it to install.

---

### Post by blackened on 2008-11-10
Noob or no, there are certain basic things you need to understand. If there is a package you need that is not offered via Synaptic, then you can often find a pre-packaged version somewhere on the web, but make sure that it's packaged for your particular distro and version. These can be installed with dpkg a la:
```

sudo dpkg -i **packagename**

```

As for the smooth engine, I think the package was succeeded by the gtk2-engines package. So, try ```

sudo apt-get install gtk2-engines
```
for that one.

For Aurora, you could manually install the version for 8.04 from [here]("http://software.opensuse.org/search?q=gtk2-engines-aurora&baseproject=ALL&p=1"). First download the appropriate package for your architecture, either amd64 or i386, then install it with the dpkg command mentioned earlier.

---

### Post by herbie643 on 2008-11-10
Thank you so much guys.   getdeb.net was the place.  got the aurora engine and while there got candido.  dont know if i need it, but hey, what the heck.   as for the smooth enging, i already have the gtk-engines installed and the  Appearance tab still complains.  oh well.
Many thanks again  guys.

---

### Post by mac71 on 2008-11-10
Hi, go here:

[http://ubuntuforums.org/showthread.php?t=830587](http://ubuntuforums.org/showthread.php?t=830587)

Scroll to the last post on that page and you'll find a link to the aurora-engine.deb file.

For me, it only seems to want to install if i save it to my desktop first and then double click the icon to install.

Hope that helps.

Oops. didn't notice your last post

---

