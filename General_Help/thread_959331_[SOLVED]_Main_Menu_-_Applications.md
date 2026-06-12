---
title: "[SOLVED] Main Menu - Applications"
date: 2008-10-26
forum: General Help
---

### Post by naknak987 on 2008-10-26
The Applications menu doesn't show up and when I try to run the main menu editor (alacarte) in the terminal I get this. 

naknak987@naknak987-desktop:~$ alacarte
/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 46, in __loadMenus
    self.applications.dom = xml.dom.minidom.parse(self.applications.path)
  File "/usr/lib/python2.5/xml/dom/minidom.py", line 1915, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 924, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 207, in parseFile
    parser.Parse(buffer, 0)
xml.parsers.expat.ExpatError: not well-formed (invalid token): line 35, column 49

I don't have no idea what caused this, but my places and system menus still work? I don't know if the info I provided is enough for you to help so if there is some other info I could provide I would be happy to.

---

### Post by bwhite82 on 2008-10-26
Hmmm...a very weird problem. Have you tried removing the 'Main menu' applet from the panel and then re-adding it? Or am I not understanding your problem correctly. If I'm not, perhaps a screenshot would help.

---

### Post by naknak987 on 2008-10-26
Ignore brasero 

In the upper left corner, Applications don't do anything when I click, but Places and System work like there supposed to.
[IMG]http://www.freewebs.com/naknak987/Screenshot.png[/IMG]

---

### Post by naknak987 on 2008-10-26
Nevermind. rm -f ~/.config/menus/applications.menu fixed it. I should have looked around somemore, yea, sorry.

---

