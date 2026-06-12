---
title: "updating azureus vuze"
date: 2008-11-25
forum: General Help
---

### Post by onemanclapping on 2008-11-25
hi.

I installed the new ubuntu 8.10 and he upgraded my azureus to the new Vuze. but now there's a newer version of azureus and every time I run it, it pops up a message asking me if I want to update. I select "yes", he downloads the update and then asks me if I want to restart azureus... I click "yes" and the same old azureus comes up and says the same message.... It seems not to be updating.

What's happening, does anyone know?

cheers!

azureus:
> Downloading: [[],]
Downloading: [[],]
    Downloading: [[http://torrents.aelitis.com:88/torrents/Azureus4.0.0.4.jar.torrent:](http://torrents.aelitis.com:88/torrents/Azureus4.0.0.4.jar.torrent:) torrent]
      Downloading: [http://torrents.aelitis.com:88/torrents/Azureus4.0.0.4.jar.torrent:](http://torrents.aelitis.com:88/torrents/Azureus4.0.0.4.jar.torrent:) torrent
        Downloading: [http://torrents.aelitis.com:88/torrents/Azureus4.0.0.4.jar.torrent](http://torrents.aelitis.com:88/torrents/Azureus4.0.0.4.jar.torrent)
      Downloading: Azureus4.0.0.4.jar
Torrent download complete
Data verified successfully


---

### Post by djbushido on 2008-11-25
I don't use azureus, i use deluge, but try removing all files related to azureus, restart your computer, and try installing from a download location.
I'll try and check back later, so if this doesn't work, let me know.

---

### Post by onemanclapping on 2008-11-26
> **djbushido said:**
> I don't use azureus, i use deluge, but try removing all files related to azureus, restart your computer, and try installing from a download location.
I'll try and check back later, so if this doesn't work, let me know.

hi! thanks, but which files should I delete? where are they located? If I uninstall vuze through Synaptic, nothing happens. It is still installed after I do it. which directories should I delete?

sorry, I'm a linux noob :/

---

### Post by rpainter on 2008-11-26
I have the same issue. I have just been hitting cancel, but I sure would like a real solution.

---

### Post by Forlong on 2008-12-03
I struggled with this for several days as well and ended up installing Vuze manually.
It's pretty easy to do, see here: [http://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu](http://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu)

---

### Post by OzzyFrank on 2008-12-18
Yup... I'm on a continuous loop of Vuze 3.1.1.0 trying to unsuccessfully update to 4.0.0.4 - if I disable the autoupdater it complains about it, but if I leave it enabled it just keeps downloading Azureus4.0.0.4.jar and does nothing with it (I of course let it restart when prompted, but it is still the same version). Apparently this is happening to MANY people out there, and seems to be a real Ubuntu-only bug. Of course, it has people asking what the hell Ubuntu is doing with such an ancient version of Vuze in the repos in the first place (when I contact developers directly about their apps not working in Ubuntu, they invariably ask why the "latest" Ubuntu version of their app is so outdated).

---

### Post by scouser73 on 2008-12-18
I updated to the "New Vuze" and I wish I didn't as it caused quite a few problems, and yes, by clicking on the Update to 4.0 it doesn't do a bloody thing really.

So here's the link for Vuze on GetDeb: [http://www.getdeb.net/search.php?keywords=vuze]("http://www.getdeb.net/search.php?keywords=vuze")

Hope you don't encounter the problems I had with the "upgrade".

---

### Post by OzzyFrank on 2008-12-18
I found the answer, and am happily using 4.0.0.4 without having to first uninstall 3.1.1.0. The original answer is here: [http://ubuntuforums.org/archive/index.php/t-972577.html](http://ubuntuforums.org/archive/index.php/t-972577.html) - but here it is with some extra info for those who have no idea where the updated file is and what to do with it:

[B]If you extract the "Azureus2.jar" from the tar.gz file, or simply copy the Azureus4.0.0.x.jar OVER /usr/share/java/Azureus2.jar, you will be halfway [COLOR="DarkRed"](edit: you should already have a new Azureus2.jar file in /home/yourusername/.azureus, so just open /usr/share/java/ as root or superuser and drag Azureus2.jar there and say yes to replacing the old one)[/COLOR]. At this point, you will get an error that the main class isn't found. Then edit /usr/bin/azureus so the classpath is "org.gudy.azureus2.ui.swt.Main" instead of whatever it was before (org.gudy.ui.azureus2.[something]).

That has me up and running.

So, to reiterate with sweet numbers:
1. Copy new Azureus2.jar file over /usr/share/java/Azureus2.jar
2. Edit /usr/bin/azureus and replace the classpath (on the last line) with "org.gudy.azureus2.ui.swt.Main"[/B]

---

### Post by Forlong on 2008-12-18
**OzzyFrank**

You could have simply followed the link I posted above where you can find out how to install Vuze properly (as in: available for every user, updateable and with a menu entry).


**scouser73**

Installing another deb will not solve the update issue!
Next time there's an update you will be left with the same problem.
Again, just follow the link, I explained everything there.

---

### Post by OzzyFrank on 2008-12-18
Forlong: Thanks, but this way was shorter, quicker, and didn't involve removing Vuze, so I took the easiest option. Took less than a minute and all went well (even downloaded and applied some small update to it successfully). Cheers

---

### Post by jpkotta on 2008-12-20
You don't have to update if you don't want to.  There is an option that disables the update nag.  Options -> Interface -> Start -> Check for latest version ...  It is easy to find with Vuze's helpful option search tool.

---

### Post by selector21 on 2008-12-29
> **Forlong said:**
> I struggled with this for several days as well and ended up installing Vuze manually.
It's pretty easy to do, see here: [http://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu](http://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu)

Does this method keep your settings intact if you have been using Azureus already? Just worried about the uninstall...

---

### Post by OzzyFrank on 2008-12-29
> **selector21 said:**
> Does this method keep your settings intact if you have been using Azureus already? Just worried about the uninstall...

Did you check out the method I outlined? It takes a minute and no uninstall is neccessary. By far the easiest solution.

---

### Post by selector21 on 2008-12-29
> **OzzyFrank said:**
> Did you check out the method I outlined? It takes a minute and no uninstall is neccessary. By far the easiest solution.


Hi OzzyFrank,

I did see you post but then was concerned by Furlong's comments...

[QUOTE=Forlong]You could have simply followed the link I posted above where you can find out how to install Vuze properly (as in: available for every user, updateable and with a menu entry).[/QUOTE]

Is this true? Will I have to use the same manual method for every update as auto update will continue not to work?

---

### Post by OzzyFrank on 2008-12-29
Dude, the method I outlined is really quick and absolutely painless! I restarted the new Vuze and my previous downloads automatically started, no problems. No more update errors, or any error messages of any kind. It has silently downloaded and installed an update or two, once again with no problems.

The other method outlined not only involves uninstalling then reinstalling Vuze 4, you even have to manually create your own menu launcher for it, hehehe... so, um, "you could have SIMPLY followed..." doesn't really apply with that method, methinks, hehe!

---

### Post by Forlong on 2008-12-30
> **selector21 said:**
> Does this method keep your settings intact if you have been using Azureus already? Just worried about the uninstall...
Yes, of course.
In Linux, all custom settings go to your home directory (/home/yourusername/ that is) and no program is allowed to delete those when uninstalling it.


edit: @OzzyFrank:
You do not *need* to uninstall Azureus nor create the launcher but it's simply the way it should be done, because it's **clean**.
**_Never_** advice people to mess with files under /usr/bin!

---

### Post by selector21 on 2008-12-31
> **Forlong said:**
> Yes, of course.
In Linux, all custom settings go to your home directory (/home/yourusername/ that is) and no program is allowed to delete those when uninstalling it.


Worked a treat - thank you!!

---

### Post by onemanclapping on 2009-01-03
> **Forlong said:**
> I struggled with this for several days as well and ended up installing Vuze manually.
It's pretty easy to do, see here: [http://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu](http://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu)

thank you very much! problem solved! :)

---

### Post by carlos-alberto-teixeira on 2009-01-12
> **Forlong said:**
> 
It's pretty easy to do, see here: [http://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu](http://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu)

Absolutely perfect instructions, Mr. Forlong.

Thousand thanks.

On service,

- c.a.t.

---

### Post by OzzyFrank on 2009-02-02
**_Never_** advice people to mess with files under /usr/bin![/QUOTE]

Why not? One would assume if someone was editing a file there (or any important file anywhere) they would create a backup of it first (just common sense). I just used my method to get out of the update loop from 4.0.0.4 to 4.1.0.0. Worked a treat. Oh, but I didn't need to edit the "azureus" file in /usr/bin again, just copy the new .jar file over the old in /usr/share/java/. I know I can turn off updates to Vuze, but at least I know I can just use this method to get out of a loop where it keeps downloading the update and not doing anything with it. I have actually mentioned this to the Vuze team, but it isn't such a big deal if you know you can overwrite the old .jar file with the new. Cheers.

---

### Post by Col-1023 on 2009-02-10
Thanks Forlong, a very helpful post, it got Azureus fixed and helped me change the interface back to the classic style.

---

### Post by fjpos on 2009-04-07
:guitar:Thanks Furlong, worked perfectly

---

### Post by Kralizec on 2009-05-06
Thanks, OzzyFrank; your method seemed simpler and did indeed take a max of 30 seconds, after downloading the tarball from Vuze. Vuze is now updating perfectly on its own, and I still have all of my menu entries, settings, etc. And if one knows what one is doing/trusts one's guide enough, modifying /usr/bin/ files isn't an issue.

---

### Post by OzzyFrank on 2009-05-10
Seems like every second update I have to do that again, but at least it takes less than a minute and there are no adverse effects. Azureus/Vuze should really look into that, as from what I see in forums all over the place, it is a real issue for many. Many people just end up choosing to disable the updates.

---

### Post by elnisi on 2009-05-17
I edit /usr/bin/azureus
in terminal
gksudo gedit /usr/bin/azureus

-classpath [COLOR="Red"]/usr/share/java[/COLOR]/Azureus2.jar

to

-classpath [COLOR="Red"]$HOME/.azureu[/COLOR]s/Azureus2.jar


org.gudy.azureus2.ui.[COLOR="Red"]common[/COLOR].Main

to

org.gudy.azureus2.ui.[COLOR="Red"]swt[/COLOR].Main

Work perfect it even update well now

---

### Post by linuxgr on 2009-05-20
Elnisi's solution worked perfect for me. But I lost the dashboard, dont know if that is part of the new version or collateral  of Elnisi's "fix".

Thanks anyway!!

---

### Post by MonkeyZiggurat on 2009-05-28
OzzyFrank's guide fixed it for me, cheers mate. Really didn't want to have to re-install so that was perfect.

---

