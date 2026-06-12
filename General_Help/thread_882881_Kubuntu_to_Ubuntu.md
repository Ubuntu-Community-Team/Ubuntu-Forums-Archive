---
title: "Kubuntu to Ubuntu"
date: 2008-08-07
forum: General Help
---

### Post by ger_macaco on 2008-08-07
Hi
I am running Kubuntu 8.04 on an amd64 enviroment with KDE 4.1 (and Compiz).

I would like to try Ubuntu itself and not Kubuntu. If the only difference is Gnome instead of KDE (if not, please tell me so), how do I remove KDE and install Gnome?

Many Thanks

---

### Post by tangibleorange on 2008-08-07
Hi there,

In response to your first question, the only difference (as far as I know) between Kubuntu and Ubuntu is the KDE over GNOME (and the respective applications) so in Kubuntu you get Amarok instead of Rhythmbox, or Kopete instead of Pidgin. These are only defaults - you can install the "other one" - both get their software from exactly the same place.

In order to install an ubuntu desktop, you can use this command:

```
sudo aptitude install ubuntu-desktop
```

Doing this will allow you to use either GNOME or KDE at the startup screen (under "Sessions"). However, many people find this is ugly as KDE applications will fill up the GNOME menu and vice versa. You may then wish to remove your Kubuntu installation with this command:

```
sudo aptitude remove kubuntu-desktop
```

Hope that helps!

---

### Post by snowpine on 2008-08-07
And if that doesn't work (likely because you used apt-get to install kubuntu-desktop), here are more detailed instructions: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by LitusMayol on 2008-08-07
Oh my god!
Once I moved (in the exact way: Kubuntu-> Ubuntu). I still on Ubuntu (I don't like KDE 4... ) but also still running **Amarok** (for me the best reproducer ever created -the scripts! youtube, guitar tabs, lyrics, the wiki...-)


As B]tangibleorange[/B] has told you, I runned this codes:
```
sudo aptitude install ubuntu-desktop
sudo aptitude remove kubuntu-desktop
```

For me it has worked fine. Any problems. Wish you like Gnome! ;)

---

