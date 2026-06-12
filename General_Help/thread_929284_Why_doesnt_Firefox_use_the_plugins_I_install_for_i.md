---
title: "Why doesnt Firefox use the plugins I install for it and keep asking me to install?"
date: 2008-09-24
forum: General Help
---

### Post by riahc3 on 2008-09-24
Why doesnt Firefox use the plugins I install for it and keep asking me to install? Ive tried Flash/Java and when the instalation is complete, it still asks me to install plugins that are needed for the site.

---

### Post by matt79 on 2008-09-24
Check and make sure you do not have to download them first then install. You might have them downloaded.......and waiting to be installed

---

### Post by aysiu on 2008-09-24
Well how did you install them?

And are you using the repositories version of Firefox or the Mozilla version of Firefox?

---

### Post by riahc3 on 2008-09-24
> **matt79 said:**
> Check and make sure you do not have to download them first then install. You might have them downloaded.......and waiting to be installed

I installed them by going to a page that required them. It downloaded and installed them.


Should I go manually to Java/Flash's site and download/install them?

---

### Post by matt79 on 2008-09-26
> **riahc3 said:**
> I installed them by going to a page that required them. It downloaded and installed them.


Should I go manually to Java/Flash's site and download/install them?

I would do that. You might want to check and make sure that the plugins are enabled after you install them.

---

### Post by riahc3 on 2008-09-26
It works in Opera but not in Firefox.

---

### Post by TransitMan on 2008-09-27
Open Firefox and in the browser address bar type about:plugins and see what plugins Firefox is seeing.

As asked before, how did you install Firefox? Was it a download from the Mozilla site or from the Ubuntu repositories? This particular piece of information would be helpful in helping you get a resolution to your problem.

---

### Post by riahc3 on 2008-09-27
Firefox comes with Ubuntu so from Ubuntu

---

### Post by TransitMan on 2008-09-27
Have you tried using the Ubuntu repositories to install the plugins needed for Firefox? They are there. Make sure you have all the repositories checked and install the plugins you need from there.

Going to a web site to install a plugin because Firefox complains about a missing plugin does not guarantee it will be installed correctly.

As far as Opera goes, it will search your drive for plugins, not so with Firefox. The plugins required for Firefox need to be in the proper place within the /usr/lib/mozilla, /usr/lib/firefox, /usr/lib/flashplugin-nonfree folders for them to be seen by Firefox.

---

### Post by riahc3 on 2008-09-29
> **TransitMan said:**
> Have you tried using the Ubuntu repositories to install the plugins needed for Firefox? They are there. Make sure you have all the repositories checked and install the plugins you need from there.

Going to a web site to install a plugin because Firefox complains about a missing plugin does not guarantee it will be installed correctly.

As far as Opera goes, it will search your drive for plugins, not so with Firefox. The plugins required for Firefox need to be in the proper place within the /usr/lib/mozilla, /usr/lib/firefox, /usr/lib/flashplugin-nonfree folders for them to be seen by Firefox.

I guess you mean repositories by "Sympatic" or whatever its called.

---

### Post by TransitMan on 2008-09-29
Yes, that is the one.

---

