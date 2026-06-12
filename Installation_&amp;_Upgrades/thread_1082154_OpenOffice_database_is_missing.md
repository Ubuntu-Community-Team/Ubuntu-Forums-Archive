---
title: "OpenOffice database is missing"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by zacktu on 2009-02-27
I installed OpenOffice 3 (ppa.launchpad.openoffice-pkgs/ubuntu intrepid main) and have been using word processor, presentation, and spreadsheet for several months with no problems.  I wanted just now to open a new database and have discovered that database isn't there.  Is database still part of OpenOffice?  If so, can I get it through synaptic or must I abandon synaptic and download directly from the OpenOffice.org website?

---

### Post by Elfy on 2009-02-27
You can install it through synaptic if it's there - openoffice.org-base is what you are looking for.

---

### Post by zacktu on 2009-02-27
openoffice.org-base is version 2.4.1, whereas my OOo installation is 3.0.1.  Can I install the older version of the database?

---

### Post by Elfy on 2009-02-27
Well I would look at the ppa then see if base is available.

I would expect that trying to install the 2.41 base would call the rest of the 2.4 openoffice - you can check in synaptic though, mark it for installation.

I thought that I had base at version 3 in intrepid - I will have a look in there later.

Edit - yea, I do have base at version 3 - I must have got it at the same time - I can't remember exactly where I got it from, but do have a vague memory of using a ppa for it.

---

### Post by calc on 2009-03-04
Its available in the openoffice-pkgs ppa along with the rest of the openoffice.org packages. If you installed part of the 3.0 packages and then removed the ppa from your sources.list then you will have to add it back to get updates and any other packages you didn't have installed like openoffice.org-base.

---

