---
title: "gksudo and smeg"
date: 2005-11-20
forum: General Help
---

### Post by cbudden on 2005-11-20
Arrgh.

Ok, I have two problems.  If I try to run smeg from the terminal, i get the following errors and it fails to run :

```

sudo smeg
Traceback (most recent call last):
  File "/usr/bin/smeg", line 562, in ?
    main()
  File "/usr/bin/smeg", line 558, in main
    smeg = Smeg()
  File "/usr/bin/smeg", line 61, in __init__
    self.handler = MenuHandler(self, self.options)
  File "/usr/lib/smeg/MenuHandler.py", line 56, in __init__
    xdg.MenuEditor.MenuEditor.__init__(self, menu_path, root=options.root_mode)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 28, in __init__
    self.parse(menu, filename, root)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 42, in parse
    self.menu = parse()
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 516, in parse
    __parse(doc, filename, tmp["Root"])
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 537, in __parse
    __parseMenu(child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 691, in __parseMenu
    __parse(child, filename, m)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 575, in __parse
    __parseMergeFile("applications.menu", child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 742, in __parseMergeFile
    __mergeFile(os.path.join(p,rel_file),child,parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 785, in __mergeFile
    __parse(child,filename,parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 586, in __parse
    __parseDefaultMergeDirs(child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 762, in __parseDefaultMergeDirs
    __parseMergeDir(os.path.join(dir, "menus", basename + "-merged"), child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 755, in __parseMergeDir
    __mergeFile(os.path.join(valueg, item), child, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 778, in __mergeFile
    raise ParsingError('File not found', filename)
xdg.Exceptions.ParsingError: ParsingError in file '/etc/xdg/menus/applications-merged/nxclient.menu', File not found
cbudden@ubuntu:~$


```

The second problem is this.  If I try to run anything with gksudo, wifi-radar for instance, I get this error:
```

Failed to run wifi-radar as user root:
 Unable to copy the user's Xauthorization file.

```

Thanks :)

---

### Post by aysiu on 2005-11-20
[QUOTE=cbudden]
The second problem is this.  If I try to run anything with gksudo, wifi-radar for instance, I get this error:
```

Failed to run wifi-radar as user root:
 Unable to copy the user's Xauthorization file.

```

Thanks :)[/QUOTE] I don't have any experience with this, but [this search](http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+%22Unable+to+copy+the+user%27s+Xauthorization+file%22&btnG=Google+Search) might help.

---

### Post by cbudden on 2005-11-20
Ok, silly me.  Looked at the .Xauthority file and its owner was root and could not be accessed by anyone else.  chown'd it and gksudo is working again.  Thanks

---

### Post by installer on 2005-11-20
In Breezy all you have to do is right click on the Gnome menu button, and there is the menu edit (Smeg) option.

---

### Post by cbudden on 2005-11-20
Unfortunatly this does not work either, i just get the Starting Applications Menu editor box come up on my panel.

---

### Post by aysiu on 2005-11-20
[It's not looking good for your SMEG problem](http://www.google.com/search?num=100&hl=en&lr=&safe=off&q=%22Parsing+Error+in+file%22+%22file+not+found%22&btnG=Search). Have you tried doing a complete removal it through Synaptic Package Manager and then reinstalling it?

---

### Post by cbudden on 2005-11-21
Did the complete remove even though I have tried it before, but before re installing smeg I right clicked the ubuntu logo and click edit menus and it worked.  Here is a screenshot.
[IMG]http://static.flickr.com/24/65642016_a8fcc8a5c9_o.png[/IMG]

---

