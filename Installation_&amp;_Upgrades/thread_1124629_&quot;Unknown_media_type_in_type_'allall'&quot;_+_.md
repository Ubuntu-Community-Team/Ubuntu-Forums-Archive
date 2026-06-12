---
title: "&quot;Unknown media type in type 'all/all'&quot; + other complaints during package installation"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by mrowth on 2009-04-13
I've finally upgraded my long-suffering Kubuntu Heron installation to Ibex. 

One minor problem I'm having is the following messages I'm getting every time I'm installing any packages. The messages are always the same:

```
Setting up kdeplasma-addons-data (4:4.2.0-0ubuntu1~intrepid1) ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'


Setting up kdeplasma-addons (4:4.2.0-0ubuntu1~intrepid1) ...

```

I've found seemingly corresponding XML files in /usr/share/mime, e.g. /usr/share/mime/all/all.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<mime-type xmlns="http://www.freedesktop.org/standards/shared-mime-info" type="all/all">
  <!--Created automatically by update-mime-database. DO NOT EDIT!-->
  <comment>all files and folders</comment>
</mime-type>
```

But I don't really know what's going on.

---

### Post by mrowth on 2009-04-13
What I meant to say was, of course: could somebody point me in the direction of a solution/explanation? 

:-({|=

---

### Post by FredJones on 2009-05-04
I have the same problem with my Ubuntu 9.04. Don't know why either. :(

---

