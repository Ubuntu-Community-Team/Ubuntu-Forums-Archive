---
title: "How do you edit the Applications menu?"
date: 2008-09-07
forum: General Help
---

### Post by xeddog on 2008-09-07
I am running hardy with the gnome desktop and just installed the OpenOffice 3.0 beta.  The install process does not add any icons to the applications menu, so I want to add them manually.  But when I right-click on the applications menu and select edit menus, the only thing I can do is either select or deselect items for display.  I cannot find any option to add or delete items.

I did find one article on manually editing the configuration files for the menus, but about 1/4 of the way through it I was getting a headache.  :-)  Anyway, not what I was looking for and I hope it doesn't come down to that.  Is there an application that I can get/use that will easily let me add items to the applications (and Places while I am at it) menu?

Thanks,

xeddog

---

### Post by sefs on 2008-09-07
Hmmm....

I just tried right clicking on my Edit Menus, and they have opitons to add new menus (circled in red) and items (circled in black).

Yours does not have that as well?

---

### Post by ubername on 2008-09-07
> **xeddog said:**
> I am running hardy with the gnome desktop and just installed the OpenOffice 3.0 beta.  The install process does not add any icons to the applications menu, so I want to add them manually.  But when I right-click on the applications menu and select edit menus, the only thing I can do is either select or deselect items for display.  I cannot find any option to add or delete items.

I did find one article on manually editing the configuration files for the menus, but about 1/4 of the way through it I was getting a headache.  :-)  Anyway, not what I was looking for and I hope it doesn't come down to that.  Is there an application that I can get/use that will easily let me add items to the applications (and Places while I am at it) menu?

Thanks,

xeddog

That's odd.

When I right click on Applications and select 'edit menus' I get a panel with a 'new menu' option and a 'new item' option.

---

### Post by ubername on 2008-09-07
> **sefs said:**
> Hmmm....

I just tried right clicking on my Edit Menus, and they have opitons to add new menus (circled in red) and items (circled in black).

Yours does not have that as well?

snap!

---

### Post by Elfy on 2008-09-07
Run alacarte from a terminal, highlight the office menu - then use the add item option - top right.

Openoffice 3 installs to the /opt/openoffice.org3 folder, I just have a launcher to

/opt/openoffice.org3/program/soffice

which then gives choices

---

### Post by xeddog on 2008-09-07
> **sefs said:**
> Hmmm....

I just tried right clicking on my Edit Menus, and they have opitons to add new menus (circled in red) and items (circled in black).

Yours does not have that as well?
WTF?!?!?!   I don't have any of those options.  My window stops at the list of items.

---

### Post by sefs on 2008-09-07
move your cursor to the right edge of the window until it becomes a right pointing arrow with a vertical bar... hold down left mouse button and drag edge of window to right.  It may be that you just need to expand the window to the right?

---

### Post by xeddog on 2008-09-07
> **sefs said:**
> move your cursor to the right edge of the window until it becomes a right pointing arrow with a vertical bar... hold down left mouse button and drag edge of window to right.  It may be that you just need to expand the window to the right?
I already tried that.  NFG.

I have downloaded and installed alacarte as per another reply, and that works great.  Now I get the 5 options on the right side.  But I still wonder why I don't get them by just "edit menus" the way you have. . . .

btw,  I have two Hardy installations that are like this.  Both installed on the same physical machine, but two separate disks.

Xeddog

---

### Post by xeddog on 2008-09-07
OK wait a minit.  This is getting too weird for me.  I have tried three different ways to edit the menus, and here is what I see.

1.  Right-click Applications and select "Edit Menus".  when I do this all I can do is select/deselect items to display.  The options to add items, etc.,  are not displayed.  (Also noticed that the Help button is grayed out too.)

NOTE:  More on this option later.

The next thing I did was to install alacarte.  I ran this from a terminal, and I ran it from a "root" terminal with differing results.

2.  When I open a normal terminal window and enter the command "sudo alacarte", I get the window that everyone else has said they have.  I select "Office" from the list on the right, and then select add new item from the right side of the screen.  I add the item I want, click "OK" and it seems to work.  I can go to the Applications menu and sure enough, there is my icon and the application works.  Kool.  BUT! The item does not show up in the items list in alacarte.  Not even after restart of alacarte, or even a reboot.

3.  OK, so now I use a root terminal window.  after giving the root password I get the terminal window and just give the command "alacarte", and the menu editor window opens.  As with #2 above, I have all the options to add and delete items.  But the  items that I just installed using method #2 above are not listed anywhere in the menu editor.  They are still in the Applications menu itself, just not in this editor window.  So I add another new item.  This time it shows up in the Items list of the menu editor like it should, BUT, it does NOT show up in the Applications menu anywhere.  As a a test, I also used the command "sudo alacarte" with the same results. 

Now back to Option #1.  Now when I right-click Applications and select Edit Menus, I get nothing.  At all.  No application opens.

I'm so confused.  What the . . . .???

xeddog

---

### Post by Elfy on 2008-09-07
You don't need to run it as sudo, nor in a root terminal.

Just run it as ```
alacarte
```

I'll post scrnshot of how I have the oo3 launcher, check that you have the same - after checking that the path on your system is right.

Not sure why it was necessary to install alacarte I thought it was a default package. I don't remember installing it as I am under the impression that it is the same as the right click edit menu options.

---

### Post by xeddog on 2008-09-07
In that case forestpixie, that may be a clue as to what is wrong.  When I just issue the command without sudo I get:

[IMG]file:///home/twoblues/Desktop/Screenshot-twoblues@Stealth:%20~.png[/IMG]

(hope this works.  I've never tried to include a screenshot before.  Bottom line is that I get permission denied).

---

### Post by Elfy on 2008-09-07
No it didn't :)

[http://ubuntuforums.org/showpost.php?p=4527031&postcount=4](http://ubuntuforums.org/showpost.php?p=4527031&postcount=4)

and have another go

---

### Post by Elfy on 2008-09-07
CAn you run this in a terminal and post the output

```
ls -al /usr/bin/alacarte
```

---

### Post by xeddog on 2008-09-07
ls -al /usr/bin/alacarte yields:

-rwxr-xr-x 1 root root 1211 2008-03-10 17:24 /usr/bin/alacarte


Xeddog

---

