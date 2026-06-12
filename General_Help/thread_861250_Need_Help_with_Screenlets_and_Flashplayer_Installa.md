---
title: "Need Help with Screenlets and Flashplayer Installation"
date: 2008-07-16
forum: General Help
---

### Post by chiefbobkat on 2008-07-16
I am using Ubuntu 8.04 and Firefox 3.0. I have the Adobe Flashplayer 10 Beta installed. 

Slacker, Pandora, Youtube.com and other sites requiring flash work fine within the browser.

However screenlets such as Ryan McGuire's SlackerScreenlet V0.3, Travis Bailey's Pandora screenlet and the Youtube screenlet by Helder Fraga fail to function reporting that they require flash.

I have modified the path in the screenlet files to point to the new firefox folder (/usr/lib/firefox-3.0) but the I still cannot get the screenlet to work. 

Any ideals on how to make these screenlets work would be greatly appreciated.

---

### Post by chiefbobkat on 2008-07-16
Update.
Per the request from Ryan McQuire the Slacker Screenlet creator, I have uninstalled the Beta 10 verision of the flashplayer and installed Verison 9.X.

Symptoms remain the same. Flash sites work in the browser but don't work with Screenlets.

---

### Post by chiefbobkat on 2008-07-17
Problem Fixed!
The solutions was installing the FLASHPLUGIN-NONFREE package (apt-get install flashplugin-nonfree).

I was downloading and installing the libflashplayer.so directly from Adobe and coping the file into Firefox Plugin directory. The Flashplugin-nonfree installer creates a Flashplugin-nonfree directory in /use/lib and the screenlet application must be looking for that directory.

---

### Post by soccerush10 on 2008-08-04
How do you get Travis Bailey's [COLOR="Red"]Pandora screenlet[/COLOR] to work on Hardy without iTunes?  Whenever I start it using the screenlet manager, the thing tells me it's searching for iTunes, and after a few minutes it stops trying and tells me to click on my iTunes thing in the task bar, or something to that effect.  Basically, it asks for iTunes, and since I'm so againts Apple and everything it produces, I am stumped.  Please advise.

Edit-
I found a webframe screenlet that does the same as Travis Bailey's, but in a more simplistic way because it is basically a smaller version of the online Pandora application:
[http://www.gnome-look.org/content/show.php/Pandora+Webframe?content=85876](http://www.gnome-look.org/content/show.php/Pandora+Webframe?content=85876)

BUT, please let me know what the deal is with Travis Bailey's version.  Does it need iTunes to work, or am I just hallucinating? lol, thanks :)

---

### Post by chiefbobkat on 2008-08-04
I get the samthing. So I don't know about the Pandora plugin.
Perhaps someone elses does. Have you emailed Travis?

---

### Post by soccerush10 on 2008-08-12
No, I haven't, though this would be as good a reason as any to Email him.  Good suggestion.

Edit-
The developer, Travis Bailey, states in the following page that he doesn't want to debug it since he got it to work on his computer:

[COLOR="Blue"][http://linux.softpedia.com/get/Desktop-Environment/Screenlets/Pandora-37345.shtml]("http://linux.softpedia.com/get/Desktop-Environment/Screenlets/Pandora-37345.shtml")
[/COLOR]

I don't mind, because I like the full-browser version, which I am running.  I can even use it as a quick Google browser too, so it's much more flexible than Bailey's version. 

I suggest you try it, if you need help running it, feel free to ask me for pointers:
[COLOR="Blue"][http://www.gnome-look.org/content/show.php/Pandora+Webframe?content=85876]("http://www.gnome-look.org/content/show.php/Pandora+Webframe?content=85876")[/COLOR]

---

