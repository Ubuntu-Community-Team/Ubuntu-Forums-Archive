---
title: "[SOLVED] Firefox packages kept back"
date: 2008-07-25
forum: General Help
---

### Post by agaudio on 2008-07-25
I noticed something odd this morning when I was updating to the latest packages with Update Manager. First, there were several Firefox packages, including 

```

firefox-3.0
firefox-3.0-gnome-support

```

However, these two were not checked by default, and I simply proceeded with the update. The other packages, at least some of which had to do with Firefox, I think, updated no problem. However, when I run Update Manager again, the two packages above remain in the list but are greyed out. If I run
 
```
sudo apt-get update
```
 
and then

```
sudo apt-get upgrade
```

I get

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  firefox-3.0 firefox-3.0-gnome-support
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

If I go in via Synaptic Package Manager and mark firefox-3.0-gnome-support for upgrade, it says it depends on firefox-3.0. If I mark firefox-3.0 for upgrade, it says

```

firefox-3.0:
  Depends: xulrunner-1.9 (>=1.9.0.1) but 1.9+nobinonly-0ubuntu0.8.04.1 is to be installed

```

So I checked xulrunner-1.9 in Synaptic, and it is not available for an upgrade. However, I did notice here [http://ubuntuforums.org/showthread.php?t=865728&highlight=firefox-3.0+xulrunner+back]("http://ubuntuforums.org/showthread.php?t=865728&highlight=firefox-3.0+xulrunner+back") that there should be an update for xulrunner this week.

Does anyone understand what is going on? I guess it is worth mentioning I run a mixed system, where one user runs Firefox in English and one user runs it in Swedish.

---

### Post by Archmage on 2008-07-25
Strange, I got update for xrunners and firefox.

---

### Post by Stainesy on 2008-07-25
> **Archmage said:**
> Strange, I got update for xrunners and firefox.
Me too.

---

### Post by agaudio on 2008-07-25
Could it be an issue of the multiple languages and the packages being kept back until such time as there is an upgrade for both Swedish and English firefox? I have noticed previously that upgrades for Firefox often come for English first and then other languages later on.

Then again, if I go into the Firefox page, I see that 3.0.1 is available for download for both Swedish and English.....

Hmm.... would really like to have the latest version of Firefox, and even more understand what the heck is going on.....

---

### Post by agaudio on 2008-07-25
Odd! If I change the download server under Software Sources from "Server for Sweden" to "Main Server", then the option to download the disabled packages as well as the xulrunner packages and some Evolution packages suddenly become available. So I guess that the conclusion is that the upgrades for firefox-3.0 and firefox-3.0-gnome-support had propograted out to the Swedish server but not the upgrade for xulrunner.

Does anyone know if it makes a difference which server I use? I have been using the server for Sweden until now without even thinking about it.

Even more odd, if I change back to the server for Sweden, the packages remain available.

---

