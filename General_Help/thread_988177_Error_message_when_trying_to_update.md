---
title: "Error message when trying to update"
date: 2008-11-20
forum: General Help
---

### Post by Peterfc on 2008-11-20
Hi All

I am sorry to have to ask but after trying the search did not help. I do not have a disk in my cd drive. 

Thanks for reading this thread.


Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by philinux on 2008-11-20
Post the results of this

cat /etc/apt/sources.list

Dont forget to wrap it with code marks.

---

### Post by Peterfc on 2008-11-20
Hi Phil

May i ask what is a Code mark

---

### Post by renzokuken on 2008-11-20
the update is trying to read from the ubuntu installation cd since you still have it activated as a repo in your sources

simply open up the sources file

```
gksudo gedit /etc/apt/sources.list
```

and comment out (stick a # in front) of the lines relevant to cd-rom then try the update again

---

### Post by philinux on 2008-11-20
> **Peterfc said:**
> Hi Phil

May i ask what is a Code mark

When you post a reply, highlight any text then click the # key 
  [COLOR=#000000][IMG]http://ubuntuforums.org/images/editor/quote.gif[/IMG][/COLOR]   [COLOR=#000000][IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG][/COLOR]  [COLOR=#000000][IMG]http://ubuntuforums.org/images/editor/html.gif[/IMG][/COLOR]  [COLOR=#000000][IMG]http://ubuntuforums.org/images/editor/php.gif[/IMG]
[/COLOR]

---

