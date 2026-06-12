---
title: "OpenOffice 3.0 installation woes."
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by Envergure on 2009-01-24
Downloaded the package, unzipped, opened terminal and cd'd to the right place and entered ```
sudo ./update
```  Got this output:  ```
Skipping deselected package ooobasis3.0-en-us-writer.
Skipping deselected package ooobasis3.0-testtool.
Skipping deselected package ooobasis3.0-impress.
Skipping deselected package ooobasis3.0-binfilter.
Skipping deselected package ooobasis3.0-core05.
Skipping deselected package ooobasis3.0-core02.
Skipping deselected package ooobasis3.0-en-us-math.
Skipping deselected package ooobasis3.0-base.
Skipping deselected package ooobasis3.0-core04.
Skipping deselected package ooobasis3.0-core06.
Skipping deselected package ooobasis3.0-ooolinguistic.
Skipping deselected package ooobasis3.0-calc.
Skipping deselected package ooobasis3.0-javafilter.
Skipping deselected package ooobasis3.0-onlineupdate.
Skipping deselected package ooobasis3.0-images.
Skipping deselected package ooobasis3.0-en-us-impress.
Skipping deselected package openoffice.org3-dict-fr.
Skipping deselected package openoffice.org3-calc.
Skipping deselected package ooobasis3.0-en-us-base.
Skipping deselected package openoffice.org3.
Skipping deselected package ooobasis3.0-en-us-binfilter.
Skipping deselected package openoffice.org3-base.
Skipping deselected package ooobasis3.0-kde-integration.
Skipping deselected package ooobasis3.0-draw.
Skipping deselected package ooobasis3.0-core03.
Skipping deselected package ooobasis3.0-ooofonts.
Skipping deselected package openoffice.org3-writer.
Skipping deselected package openoffice.org3-dict-en.
Skipping deselected package openoffice.org3-dict-es.
Skipping deselected package ooobasis3.0-graphicfilter.
Skipping deselected package openoffice.org-ure.
Skipping deselected package ooobasis3.0-core01.
Skipping deselected package ooobasis3.0-xsltfilter.
Skipping deselected package ooobasis3.0-core07.
Skipping deselected package openoffice.org3-math.
Skipping deselected package openoffice.org3-impress.
Skipping deselected package ooobasis3.0-gnome-integration.
Skipping deselected package ooobasis3.0-en-us-draw.
Skipping deselected package ooobasis3.0-en-us-res.
Skipping deselected package ooobasis3.0-math.
Skipping deselected package openoffice.org-debian-menus.
Skipping deselected package ooobasis3.0-writer.
Skipping deselected package openoffice.org3-en-us.
Skipping deselected package ooobasis3.0-en-us-help.
Skipping deselected package openoffice.org3-draw.
Skipping deselected package ooobasis3.0-en-us-calc.
Skipping deselected package ooobasis3.0-en-us.
Skipping deselected package ooobasis3.0-pyuno.

```

Already tried this:
[http://ubuntuforums.org/showthread.php?t=1049232](http://ubuntuforums.org/showthread.php?t=1049232)

Any ideas?

Thanks, 
Chris

---

### Post by lemming465 on 2009-01-25
Did you try *sudo apt-get update; sudo apt-get upgrade*?  If you have successfully added the 3rd party repository, you could also just try selecting the ooo3 packages in synaptic (GUI package manager).

---

### Post by Envergure on 2009-01-25
I didn't know there *was* a separate repository for 3.0;  I'll try to find it...

_LATER_
Here it is:  ```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

It's downloading...

Got a "not authenticated" warning.  Phooey.

---

### Post by pvalley1967 on 2009-01-26
try this it worked for me

[http://www.tectonic.co.za/?p=3363:guitar:](http://www.tectonic.co.za/?p=3363:guitar:)

---

