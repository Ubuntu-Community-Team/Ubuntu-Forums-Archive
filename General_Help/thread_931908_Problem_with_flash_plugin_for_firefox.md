---
title: "Problem with flash plugin for firefox"
date: 2008-09-27
forum: General Help
---

### Post by Axek on 2008-09-27
When I visit flash based websites I am asked to download flash player. I have ran "sudo apt-get install flashplugin-nonfree" and it says I have the most current version. Can anyone offer me help?

---

### Post by Sorivenul on 2008-09-27
Open FireFox and go to about:plugins.
See if you have swfdec or gnash (or both) there.
What you want to see is something like Shockwave Flash.  
If you have the others installed they will conflict, so uninstall them.

---

### Post by Axek on 2008-09-27
> **Sorivenul said:**
> Open FireFox and go to about:plugins.
See if you have swfdec or gnash (or both) there.
What you want to see is something like Shockwave Flash.  
If you have the others installed they will conflict, so uninstall them.
I have the shockwave flash plugin and something called FutureSplash Player. Do I need to uninstall FutureSplash, and if so how do I go about doing that?

---

### Post by Sorivenul on 2008-09-27
FutureSplash probably needs to be removed, though I am not wholly familiar with it.  Did you install it through Synaptic, Add/Remove/ or commandline?  I'm not on my Ubuntu right now, so I don't know if it's from the repository or not.

---

### Post by Axek on 2008-09-27
> **Sorivenul said:**
> FutureSplash probably needs to be removed, though I am not wholly familiar with it.  Did you install it through Synaptic, Add/Remove/ or commandline?  I'm not on my Ubuntu right now, so I don't know if it's from the repository or not.
I don't even remember installing a plugin called FutureSplash :P. Most likely through command line.

---

### Post by Sorivenul on 2008-09-27
Try:
```
sudo apt-get remove futuresplash
```
Though if it is not from the Ubuntu repository this probably will come up as an error.  

I did a little digging and found it may be part of the konqueror-nsplugins package.  Are you using KDE?

---

### Post by Axek on 2008-09-27
I'm using GNOME not KDE and I think that futuresplash is installed during the installation of the shockwave flash plugin, at least that is my assumption after some searching.

---

### Post by dondad on 2008-09-27
> **Axek said:**
> When I visit flash based websites I am asked to download flash player. I have ran "sudo apt-get install flashplugin-nonfree" and it says I have the most current version. Can anyone offer me help?

Do you by any chance have the noscript plugin for Firefox installed? If so, you will get this error if scripts are not enabled forthe site you are visiting.

---

### Post by Axek on 2008-09-27
No, I don't have a noscript plugin installed.

---

### Post by Axek on 2008-09-27
I can still play flash based games such as those on addictinggames.com.

---

