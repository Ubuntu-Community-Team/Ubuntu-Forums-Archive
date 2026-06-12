---
title: "[SOLVED] Keyboard shortcuts"
date: 2008-08-24
forum: General Help
---

### Post by swappo1 on 2008-08-24
Hello,

How do I create a keyboard shortcut to open gedit?  I didn't find an action for gedit in the keyboard shortcut list.  Is it possible to create an action for gedit?  There is one for terminal so I would expect to be able to add one for gedit.  Thanks.

---

### Post by pikabuntu on 2008-08-24
I think this thread might help :)

[http://ubuntuforums.org/showthread.php?t=42404](http://ubuntuforums.org/showthread.php?t=42404)

Also here are some more shortcuts:

[http://ubuntuforums.org/showthread.php?t=50794](http://ubuntuforums.org/showthread.php?t=50794)
[ ]("http://ubuntuforums.org/showthread.php?t=42404")

---

### Post by drs305 on 2008-08-24
Keyboard shortcuts can be made via the gconf-editor. Here is the short version. You should substitute whatever key combination you want for "<ALT>G". Try the key combination you select before changing this to make sure you are not overr-writing some key combination that may already exist.

```

gconftool-2 --set --type string  /apps/metacity/keybinding_commands/command_10  &#8220;gedit&#8221;
gconftool-2 --set --type string /apps/metacity/global_keybindings/run_command_10 &#8220;<Alt>G&#8221;

```

If you want a full explanation of how to do this I will be happy to explain it or provide a link.

Added: The links provided by pikabuntu should suffice if you don't want to use the commands above.

---

### Post by swappo1 on 2008-08-24
Thanks guys,

I set gedit up through the command line.  I tried the link posted by pikabuntu but couldn't find gconf-editor on the GUI.:)

---

### Post by drs305 on 2008-08-24
> **swappo1 said:**
> Thanks guys,

I set gedit up through the command line.  I tried the link posted by pikabuntu but couldn't find gconf-editor on the GUI.:)

If you want to run the gui, you start it with:
```
gconf-editor
```
Add "sudo" before the command if it is to apply to everyone.

If you want to make a gui shortcut, right click on the panel, Add to Panel, Custom Application Launcher, type a name and in the command window type "gconf-editor". When you enter that, the icon symbol will automatically become the symbol for the gconf Configuration Editor. 

If you open it, you can drill down following the path given in the commands in post # 3 to see which items were changed.

I use gconf-editor for all sorts of things, such as displaying trash bins, the desktop, volumes (partitions), nautilus list view defaults, etc. One hint, use the 'Edit, Find' function to find the what you are looking for - there are hundreds of entries - and tick the 'key names' for the search.

If you don't have any other questions, please mark this thread solved with the "Thread Tools" link at the top right of the first post.

---

