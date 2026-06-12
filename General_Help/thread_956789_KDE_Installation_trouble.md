---
title: "KDE Installation trouble"
date: 2008-10-23
forum: General Help
---

### Post by ryclegman on 2008-10-23
Hello i just thought i would give kde a go. I found this : [http://news.softpedia.com/news/How-T...04-91034.shtml](http://news.softpedia.com/news/How-T...04-91034.shtml) .... when i try this i get this error in the terminal


WARNING: The following packages cannot be authenticated!
ark-kde4 juk-kde4 kdebase-bin-kde4 kdebase-workspace-bin libkcddb4-kde4
kdemultimedia-kio-plugins-kde4 kdepimlibs-data kdepimlibs5 kdm-kde4
klipper-kde4 kmix-kde4 knetworkconf-kde4 kopete-kde4 kppp-kde4 krdc-kde4
krfb-kde4 kscd-kde4 ksysguardd-kde4 ksysguard-kde4 ksnapshot-kde4
systemsettings-kde4 kubuntu-kde4-desktop kwalletmanager-kde4 gwenview-kde4
kamera-kde4
Install these packages without verification [y/N]?

I tried several different ways and did press Yes once and had other problems. When i booted into kde it looked ok, but when i wen to COMPUTER or MY computer it can up with an error and told me to run a DEBUGGER. I did and it found nothing. I tried it again and it said that something crashed. I was able to run applications. One thing that made me notice that there was a problem with my comp. when i downloaded a theme for kde i went to locate it to install it, and it wasn't on my desktop, so i went to Computer, and it came up with the error... It seems to be a problem with permissions with KDE stuff I just tried to update my Ubuntu and i get the same message about some new KDE things.. 

Hope Someone can help me with this odd problem!

Thanks Ryclegman

---

### Post by snova on 2008-10-23
It's because you aren't downloading from the official repositories, but from the ones Kubuntu developers upload to. These ones will be more recent (and crashier), but as they aren't official, apt-get is questioning their authenticity for your own good.

You could use the older ones in the official repos, but they're *really* old. KDE 4 has come a long way since then.

Alternatively, you could try installing KDE 3, which is more stable. I don't know if you realized this, but KDE 4 is still fairly new. You don't have to use any extra repos, just the "kde" package, which will pull in the entirety of the desktop environment.

I suggest the last option until KDE 4 stabilizes a bit more, especially if you just want to try KDE.

---

### Post by ryclegman on 2008-10-23
Yha i did have 3.5 installed for a while and truthfully didnt like it... I like the eye candy and stuff.... Is there anyway to authenticate the files so i can get KDE 4?

---

### Post by snova on 2008-10-23
Say yes? They're Kubuntu repositories, there shouldn't be any problem with them. apt-get is just being a little paranoid... I don't know how to get around it.

If you didn't like KDE 3, KDE 4 might be even worse. :) Although I can see myself making good use of the Folder View plasmoid after I upgrade to Intrepid. Also the desktop effects built in to Kwin, rather than using Compiz (which is a little glitchy and not quite as familiar as Kwin).

---

### Post by ryclegman on 2008-10-23
I can get the kde to work.. its when looking at my comp folder it crashes... like i cant see files or anything. the aps just work... if i save a doc i wont b able to find it... I do like kde4 tho..

---

### Post by snova on 2008-10-23
Sorry, but there's not much that can done about that. You're pulling packages from the Kubuntu developers PPA. That's about as bleeding edge as you're going to get without building from source. Like I said, KDE 4 is still quite in progress- though useable.

---

### Post by ryclegman on 2008-10-24
ic...  Its still weird though how you cant authenticate the files, like though terminal or sum thing like that.

---

### Post by ryclegman on 2008-10-24
I found this! 

First uninstall the previous version

sudo apt-get remove --purge kdebase-bin-kde3
sudo apt-get autoremove --purge

Install KDE4

sudo apt-get install kde4

---

