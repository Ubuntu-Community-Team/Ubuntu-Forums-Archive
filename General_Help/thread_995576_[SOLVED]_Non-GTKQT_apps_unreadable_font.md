---
title: "[SOLVED] Non-GTK/QT apps unreadable font"
date: 2008-11-27
forum: General Help
---

### Post by Biznarie on 2008-11-27
The fonts in apps like VLC, VirtualBox, and OpenOffice have an unreadable font. I'm running Ubuntu 8.10, how can I fix this? I've added a screenshot with a GTK and QT app (amarok and totem) which are fine, but the rest are unreadable.

---

### Post by kerry_s on 2008-11-28
that's the encryption, it's for your own good. :lolflag:

check your font settings in the font manager. move them to a different font then back and apply.

also are you using any other languages?

---

### Post by Biznarie on 2008-11-28
Thanks for the reply. I tried changing to a few different fonts, went back and still having the same problem. I'm only using English.

---

### Post by kerry_s on 2008-11-28
weird, i never seen dingbat fonts do that.
try using synaptic to reinstall the ttf dejavu fonts.

if all else fails, you could try renaming/removing the settings file/folders for those applications. press ctrl+h in your file browser to see hidden.

---

### Post by Biznarie on 2008-11-28
Still nothing, I have some more information though, I have a feeling it may have something to do with KDE, I dont have it installed fully but I use amarok and when I installed 8.10 there was no Kcontrol to change colors so I followed this from the Kubuntu forums ([http://kubuntuforums.net/forums/index.php?topic=3097927.msg148351#msg148351]("http://kubuntuforums.net/forums/index.php?topic=3097927.msg148351#msg148351")). It worked fine for for what I wanted (I'm not sure if that could mess up anything) I was also messing around with the systemsettings app from KDE4 but I couldn't get it to do anything I wanted. As soon as I tried installing more modules (only Icons and Emoticons modules come with systemsettings) I would just get a blank grey window when I opened systemsettings. After looking for the name of the package I need to install to get the font settings in KDE4 systemsettings I found a screen of it and I noticed something, the dingbats font on the screenshot looks just like my screwed up font, heres the link. [http://www.flickr.com/photos/abhayks/2191352245/]("http://www.flickr.com/photos/abhayks/2191352245/") I changed my font and rebooted after I saw this to make sure it wouldn't work.

While I was looking for the settings files for vlc I noticed that in my VLC folder under ~/.config/vlc theres 2 files vlcrc and vlc-qt-interface.conf (deleting it does nothing), seems to me its possible all my non GTK apps are running as if I'm using KDE but I'm not, If this is the case how can I make these apps use GTK settings? or get the fonts module working in the KDE systemsettings so I can change the font?

---

### Post by kerry_s on 2008-11-28
> **Biznarie said:**
> Still nothing, I have some more information though, I have a feeling it may have something to do with KDE, I dont have it installed fully but I use amarok and when I installed 8.10 there was no Kcontrol to change colors so I followed this from the Kubuntu forums ([http://kubuntuforums.net/forums/index.php?topic=3097927.msg148351#msg148351]("http://kubuntuforums.net/forums/index.php?topic=3097927.msg148351#msg148351")). It worked fine for for what I wanted (I'm not sure if that could mess up anything) I was also messing around with the systemsettings app from KDE4 but I couldn't get it to do anything I wanted. As soon as I tried installing more modules (only Icons and Emoticons modules come with systemsettings) I would just get a blank grey window when I opened systemsettings. After looking for the name of the package I need to install to get the font settings in KDE4 systemsettings I found a screen of it and I noticed something, the dingbats font on the screenshot looks just like my screwed up font, heres the link. [http://www.flickr.com/photos/abhayks/2191352245/]("http://www.flickr.com/photos/abhayks/2191352245/") I changed my font and rebooted after I saw this to make sure it wouldn't work.

While I was looking for the settings files for vlc I noticed that in my VLC folder under ~/.config/vlc theres 2 files vlcrc and vlc-qt-interface.conf (deleting it does nothing), seems to me its possible all my non GTK apps are running as if I'm using KDE but I'm not, If this is the case how can I make these apps use GTK settings? or get the fonts module working in the KDE systemsettings so I can change the font?


okay i got you, i been so busy i didn't think about kde settings.
the program you want is qtconfig, there's a qt3 and qt4 version, i'm going to assume your using the latest qt4.
sudo apt-get install qt4-config

then you just select the tab for the the different qt parts you want to change.

---

### Post by Biznarie on 2008-11-29
Thanks a ton, that solved it! :)

---

