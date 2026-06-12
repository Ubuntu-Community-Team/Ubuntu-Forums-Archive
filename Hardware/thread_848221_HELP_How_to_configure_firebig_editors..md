---
title: "HELP: How to configure firebig editors."
date: 2008-07-03
forum: Hardware
---

### Post by Raval on 2008-07-03
I know I should be asking this in a Firefox or firebug forum but I'm to lazy to go sign up for another account on another forum. I'm sure I'm not the only one who uses Firebug in FF3.

In FF3 in the rick-click menu there is a feature for Firebug that allows you to open items on a webpage in preset editors/apps.

My question is, what is the file path to bluefish & gimp?

---

### Post by Dave82 on 2008-07-15
The path for GIMP is /usr/bin/gimp (and I suppose it's the same for Bluefish).
Actually I was trying to configure Firebug to use Gedit (/usr/bin/gedit), but it doesn't work.
I discovered that there's an [open bug]("http://code.google.com/p/fbug/issues/detail?id=881") about "Open with editor" not working in Linux.
I also left a comment to let them know we have the same problem on Ubuntu.

---

### Post by deskartez on 2010-01-31
This will get Firebug to work with Gedit:

in firefoxes address bar type :
```

about:config

```then search for :
```

view_source.editor.external

``` - and _set this boolean_ to **TRUE**

then search for :
```

view_source.editor.path

```- and set this to ' /usr/bin/gedit '

then open FireBug's configure editor and add Gedit as an editor;
name it gedit and then browse for the executable within 'usr/bin' and select or type in gedit. 
If you did everythign correctly you should see 'usr/bin/gedit' underneath 'executable' column in the configured editors window.

This worked for me, although I am using fedora it should work for unbunto too. 
i found out about this 'fix' from Andrews :D post on :
[http://www.webupd8.org/2009/04/change-firefoxs-view-source-default.html](http://www.webupd8.org/2009/04/change-firefoxs-view-source-default.html)


This works for FireBug only for Gedit.  I could not get Gedit to work as the external source editor for the 'WebTools' plugin for FireFox and i could not get GIMP to work with FireBug either

regards,
deskartez

---

