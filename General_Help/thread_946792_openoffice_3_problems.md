---
title: "openoffice 3 problems"
date: 2008-10-13
forum: General Help
---

### Post by Tag_yer_dead on 2008-10-13
Hey guys, I just downloaded Openoffice 3 (DEB download) but now im having trouble installing it... heres my code i type


```
tar -xzvf /home/corey/Desktop/oo.tar.gz
```

then I run ./configure but it wont allow me to.
Sorry I am not the greatest with installing these so thanks a lot for the help.

Corey

---

### Post by GuitarRocker2562 on 2008-10-13
yuo don't need to configure, just to install the debs. I am not sure of the command but it should be something like dpkg --install *.deb in the extracted folder.

---

### Post by shawnrgr on 2008-10-13
Some more detailed information would be nice. when you run ./configure what does it return?

ps
GuitarRocker2562 is correct. $ sudo dpkg -i *.deb in the folder would work. However when you extract that archive do you have any debs?

---

### Post by Tag_yer_dead on 2008-10-13
GuitarRocker was right, thanks a lot for the help guys

---

### Post by mcomeau on 2008-10-13
Hi! I've used this to install it, with full explanations...
[http://linuxpromagazine.com/online/blogs/productivity_sauce_dmitri_s_open_source_blend_of_productive_computing/installing_openoffice_org_3_0?blogbox](http://linuxpromagazine.com/online/blogs/productivity_sauce_dmitri_s_open_source_blend_of_productive_computing/installing_openoffice_org_3_0?blogbox)

But I don't know how to execute open office 3 after install!!!

Martin

---

### Post by ddarsow on 2008-10-13
I get the following error on trying to install desktop-integration:

 ```
openoffice.org-core conflicts with openoffice.org-unbundled
  openoffice.org-debian-menus provides openoffice.org-unbundled and is to be installed.
dpkg: error processing openoffice.org3.0-debian-menus_3.0-9354_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 openoffice.org3.0-debian-menus_3.0-9354_all.deb

```

anyone else get a similar problem?

---

### Post by fballem on 2008-10-13
> **mcomeau said:**
> Hi! I've used this to install it, with full explanations...
[http://linuxpromagazine.com/online/blogs/productivity_sauce_dmitri_s_open_source_blend_of_productive_computing/installing_openoffice_org_3_0?blogbox](http://linuxpromagazine.com/online/blogs/productivity_sauce_dmitri_s_open_source_blend_of_productive_computing/installing_openoffice_org_3_0?blogbox)

But I don't know how to execute open office 3 after install!!!

Martin

Right click on the application menu at the top of the page, then select edit menu. You may need to 'Add a new item' and you will also need to locate the OpenOffice directory (I think it's off of /opt).

---

### Post by BobJoe on 2008-10-13
i think you have to uninstall the previous one, not sure though.

---

### Post by scouser73 on 2008-10-13
> **Tag_yer_dead said:**
> Hey guys, I just downloaded Openoffice 3 (DEB download) but now im having trouble installing it... heres my code i type


```
tar -xzvf /home/corey/Desktop/oo.tar.gz
```

then I run ./configure but it wont allow me to.
Sorry I am not the greatest with installing these so thanks a lot for the help.

Corey

Here you go, it worked for me; [http://www.quicktweaks.com/2008/10/11/install-openoffice-30-final-in-ubuntu/]("http://www.quicktweaks.com/2008/10/11/install-openoffice-30-final-in-ubuntu/")

---

### Post by fballem on 2008-10-13
> **BobJoe said:**
> i think you have to uninstall the previous one, not sure though.

Yes - you do have to completely uninstall Open Office 2. If you do, then execute the instructions in Post 7 of this thread, then the new versions will show up on Applications | Office.

---

### Post by boogers on 2008-10-14
> **ddarsow said:**
> I get the following error on trying to install desktop-integration:

 ```
openoffice.org-core conflicts with openoffice.org-unbundled
  openoffice.org-debian-menus provides openoffice.org-unbundled and is to be installed.
dpkg: error processing openoffice.org3.0-debian-menus_3.0-9354_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 openoffice.org3.0-debian-menus_3.0-9354_all.deb

```

anyone else get a similar problem?

I am having the same issue.  I have removed prev install of Oo2.4 and am trying to run the Desktop integration with no luck. I would prefer the pretty little icons over the custom app launcher generic springboard icon :D

---

### Post by ddarsow on 2008-10-14
> **boogers said:**
> I am having the same issue.  I have removed prev install of Oo2.4 and am trying to run the Desktop integration with no luck. I would prefer the pretty little icons over the custom app launcher generic springboard icon :D
I have the right icons...it is just that nothing happens when I try to open Calc or Base!

---

