---
title: "Ubuntu/Linux is not allowing me to install Adobe Flash 10?"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by dizzygamr on 2009-08-18
I have been trying to install the new flash player and it's been giving me this: 
[http://s236.photobucket.com/albums/ff12/dizzygamr/?action=view&current=Screenshot.png](http://s236.photobucket.com/albums/ff12/dizzygamr/?action=view&current=Screenshot.png)

I know that I do not have a later version because I cannot play videos on my computer (such as on facebook, but youtube works). When I went to the Abobe site to get the flash player, it gave me these download options:
-YUM for Linux
-tar.gz. for Linux
-.rpm for Linux
-.deb for Ubuntu 8.04+

I chose the last option, and it gave me what is in the previous link I posted. I am absolutely stumped, so if you could please give detailed instructions that would be great. Thanks

---

### Post by dizzygamr on 2009-08-18
Also, here is the Abobe site that I was using if that helps at all:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by Bachstelze on 2009-08-18
Please open a terminal and paste the output of

```
sudo dpkg -l | grep flash
```

---

### Post by dizzygamr on 2009-08-18
> **HymnToLife said:**
> Please open a terminal and paste the output of

```
sudo dpkg -l | grep flash
```
I put the command into a terminal and I got this:

[http://s236.photobucket.com/albums/ff12/dizzygamr/?action=view&current=Screenshot-1.png](http://s236.photobucket.com/albums/ff12/dizzygamr/?action=view&current=Screenshot-1.png)

---

### Post by ajgreeny on 2009-08-18
I think you can uninstall the flashplugin-nonfree using synaptic or apt-get, and install the adobe-flashplugin.  In my opinion you should be using just the adobe-flashplugin from the repos; there is no need to install from adobe direct.

Can you also check that you do not have gnash or swfdec installed and if you do have them, uninstall them as they certainly conflict with adobe flash.

---

### Post by Scott M. Sanders on 2009-08-22
I am having the exact same trouble. I installed Firefox 3.5.2 (how long to get this in repo?), and Ubuntu 9.04 claims that Adobe Flash Player 10 is installed, but in Firefox's Tools > Add-ons, I just see these two:
[LIST]
[*]Shockwave Flash 9.0 r124
[*]Shockwave Flash 9.0 r999
[/LIST]
If I disable r124, Flash stops working entirely; if I disable r999, nothing happens. Right-clicking on a Flash element in Firefox reports it as Adobe Flash Player 9. I also get no sound nor background behind any Flash when I can on say my Vista setup with Flash 10 working. 

I've uninstalled and reinstalled all the Flash packages, from repo and Adobe's .deb file, and even went back to the repo versions for both Firefox and Adobe Flash Player, but no luck. 

I could uninstall Gnash fine, but uninstalling Swfdec wants me to remove GNOME as well? No thanks! Not to mention I had Adobe Flash Player working alongside these two just fine before, and one can configure which to use by click the white Lego icon at the bottom right of the Firefox from repo on a webpage with Flash content and selecting Adobe Flash Player for Flash content, or possibly from Firefox > Edit > Prefs > Apps even.

Anyway, where to go from here?

---

### Post by RandyFulcher on 2009-08-28
> **ajgreeny said:**
> I think you can uninstall the flashplugin-nonfree using synaptic or apt-get, and install the adobe-flashplugin.  In my opinion you should be using just the adobe-flashplugin from the repos; there is no need to install from adobe direct.

Can you also check that you do not have gnash or swfdec installed and if you do have them, uninstall them as they certainly conflict with adobe flash.


Had the same exact problem! Thanks, removing the swfdec fixed my problem with adobe 10 flash.

---

### Post by Scott M. Sanders on 2009-08-28
OK, in Synaptic, I marked for removal the package "swfdec-mozilla," which then required marked for removal the package named simply "gnome," which was rather scary, however GNOME is still here even on system restart, and Flash 10 has magically reappeared in my custom-installed Firefox 3.5.2 add-ons list, and now I can see images behind Flash and hear Flash audio again, yay.

---

### Post by Scott M. Sanders on 2009-08-29
I got it! Removing Swfdec didn't really work; I mean, it did the first time for some reason but not after... 

I had installed Adobe Flash Player 9 from Adobe's .tar.gz, and it turns out it had installed to /home/scott/.mozilla/plugins/ rather than /usr/lib/adobe-flashplugin/ as Flash 10 does. 

When Flash 10 was installed, it never removed this custom install of Flash 9 and therefore was apparently causing conflicts. (I guess the 1 and 9 confused the otherwise brilliant Firefox.) 

I went into terminal, ran "sudo nautilus," did View > Show Hidden Files, deleted that old file, and now it seems to be working every time. 

I think I'll just stick with the Ubuntu repos for Adobe Flash Player hereafter. What a pain that was. (Let's update these more, eh?)

---

### Post by Impact9 on 2009-08-29
Removing  "swfdec-mozilla" from synaptic also worked for me. :P

---

### Post by dizzygamr on 2009-10-19
EVERYONE i found the way to fix the issue. What i did was i navigated to the "plugins" folder under the ".mozilla" folder (shown by pressing control-h its a hidden folder) i extracted the file "libflashplayer.so" from the package downloaded from the Adobe sight, then dropped the file in the "plugins" folder. done

---

