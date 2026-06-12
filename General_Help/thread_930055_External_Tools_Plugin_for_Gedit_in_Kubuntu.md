---
title: "External Tools Plugin for Gedit in Kubuntu"
date: 2008-09-25
forum: General Help
---

### Post by Vegabondsx on 2008-09-25
Hi,

I have a script that I wrote for Gedit's External Tools plug-in in Ubuntu and I wish to use it on a machine running Kubuntu. So, I used apt-get to install gedit. Now gedit is installed and running fine, but when I try to enable the external tools plug-in it grays out.

When I launch gedit from the terminal to see the output when I try enabling the plug-in I get this:

```
File "/usr/lib/gedit-2/plugins/externaltools/__init__.py", line 24, in <module>
    import gnomevfs
ImportError: No module named gnomevfs

** (gedit:7246): WARNING **: Cannot load Python plugin 'External Tools' since file 'externaltools' cannot be read.

** (gedit:7246): WARNING **: Error activating plugin 'External Tools'
```

Any help would be greatly appreciated. This is part of a project to help move a lab in my University from Windows to Linux (Kubuntu).

Thanks.

---

### Post by Idefix82 on 2008-09-25
Have you got the package libgnomevfs2-0 installed?

---

### Post by Vegabondsx on 2008-09-25
I tried apt-get install libgnomevfs2-0 and it told me it was already installed and at the newest version. No updates were neccessary.

---

### Post by Idefix82 on 2008-09-25
Personally, I don't have any experience with Kubuntu. But do you mind me asking, why Kubuntu if you want to use Gnome applications?

---

### Post by Vegabondsx on 2008-09-25
Because the script I wrote was written for gedit, which is the only gnome application thats really needed. I'm trying to get my script to work with Kate, but I'm not very familiar with Kate or Kubuntu/KDE in general so I haven't gotten it working yet. Being able to use Gedit and the External Tools would make it easier as I could just copy it right over. It wasn't my choise to use Kubuntu opposed to Ubuntu. I am trying to get my script and setup working on the school computer's or get Kate to do the same thing.

---

