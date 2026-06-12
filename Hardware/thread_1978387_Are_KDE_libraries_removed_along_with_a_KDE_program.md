---
title: "Are KDE libraries removed along with a KDE program removal (on Ubuntu)?"
date: 2012-05-11
forum: Hardware
---

### Post by brunces on 2012-05-11
Guys,

I have installed Kmess on my Ubuntu (12.04 LTS). Certainly, a lot of KDE libraries were installed as well. Now I want to uninstall Kmess. When I do this, will all those KDE libraries be removed as well? Or will they remain (garbage) even if they are not going to be used anymore?

Thanks, guys. :)

brunces

---

### Post by Enigmapond on 2012-05-11
Unless you remove them they will still be there. If you want to get back to pure Gnome...see this:
[http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

---

### Post by brunces on 2012-05-11
[quote=Enigmapond]Unless you remove them they will still be there.[/quote]

Enigmapond, thanks for your time. Please, is there any way to know exactly which KDE packages were installed along with Kmess, so that I can manually remove them? I mean, how/where can I get a list of all KDE libraries which were installed with Kmess?

brunces

---

### Post by Enigmapond on 2012-05-11
Well take a look here: [http://trac.kmess.org/wiki/Packaging%20notes](http://trac.kmess.org/wiki/Packaging%20notes)  

but along with libraries...it install all the KDE runtime things as well. The list is quite lengthy. That command will remove all those. I know there are things listed in the command that you probably don't have but it will ignore them.

---

