---
title: "easy ubuntu"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by atliia on 2009-02-17
Hello, 
I am trying to run easyubutnu however, I have encountered some problems. When I run from terminal this is the error message. When I run from Apps menu it does not open at all.
```
You appear to be running Gnome, using gksudo
/usr/lib/easyubuntu
When you get a 'Password: ' prompt, type in your user password.
System sanity check: PASSED!
Traceback (most recent call last):
  File "./easyubuntu.in", line 81, in <module>
    main()
  File "./easyubuntu.in", line 75, in main
    gtkfrontend.launcher(datadir, confdir, userPackageListPath)
  File "/usr/lib/easyubuntu/EasyUbuntu/gtkfrontend.py", line 208, in launcher
    pkglist = minidom.parse(os.path.join(datadir,userPkg))
  File "/usr/lib/python2.5/xml/dom/minidom.py", line 1915, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 922, in parse
    fp = open(file, 'rb')
IOError: [Errno 2] No such file or directory: '/usr/lib/easyubuntu/packagelist-intrepid.xml'

```

I would be grateful for any help.

---

### Post by Saija on 2009-02-17
there's a file missing in your easyubuntu installation:
> /usr/lib/easyubuntu/packagelist-intrepid.xml

maybe reinstalling create it again and so you could run it without problems


Wait, why are you using easyubuntu if the project page claims its develpment its already stoped? what are you trying to install with this script ?

---

