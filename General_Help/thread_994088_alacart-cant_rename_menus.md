---
title: "alacart-cant rename menus"
date: 2008-11-26
forum: General Help
---

### Post by otz070 on 2008-11-26
hello,

When using alacarte (menu editor) I am unable to rename menus
It all started when I clicked the revert button

When running alacarte in terminal I get when trying to edit one of the uneditable menus (anything that says "alacarte made is uneditable the rest are)
```
/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 464, in on_item_tree_row_activated
    self.on_edit_properties_activate(None)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 367, in on_edit_properties_activate
    parser.write(open(file_path))
IOError: [Errno 2] No such file or directory: 'alacarte-made.directory'



```

All of the Menus work and everything. It's just that I have a lot of applications and want to keep them better organized.
[COLOR="Red"]when i double click on a menu item/or right click properties nothing happens[/COLOR]

anyone know how to fix/workaround/alternative to alacart/ or is there a way to edit menus via a file or even directory? (I know that menus can be edited in termanal but it just seems like a lot of work that way espcially since I have so many apps.)

Thanks.:)

---

### Post by jdwilm on 2008-12-14
Bump ^^

I'm having the same issue =/

---

### Post by jellybaby on 2008-12-17
Same problem here. I can add an item to a menu but I can't add or change menus. I can also only start Alacarte from the terminal as root. A colleague told me it has to do with mucked-up permissions in my home folder but he didn't know how they should be changed. For example, there are several files that belong to root for some reason, and as they are hidden I suppose I shouldn't touch them. I don't know enough about Linux to experiment!

---

### Post by jellybaby on 2008-12-18
I have just managed to solve my problem. When I started alacarte as a user, I just got a bunch of error messages, of which one was a permission denial. The hidden directories "config" and "local" belonged to root which is why I couldn't start alacarte as a user. All other directories belonged to me as a user. I entered the following code:
```
sudo chown -R user .config/menu
``` and ```
sudo chown -R user .local
``` and now everything is fine. I can even right-click on my main menu and alacarte starts when I click on "edit menu".




Release Ubuntu 8.04 (hardy)
GNOME 2.22.3
Kernel 2.6.24-21-generic

---

### Post by ajaysutton on 2008-12-28
Thanks jellybaby!  I've been looking for this for days!

---

### Post by Meow27 on 2009-01-10
> **jellybaby said:**
> I have just managed to solve my problem. When I started alacarte as a user, I just got a bunch of error messages, of which one was a permission denial. The hidden directories "config" and "local" belonged to root which is why I couldn't start alacarte as a user. All other directories belonged to me as a user. I entered the following code:
```
sudo chown -R user .config/menu
``` and ```
sudo chown -R user .local
``` and now everything is fine. I can even right-click on my main menu and alacarte starts when I click on "edit menu".




Release Ubuntu 8.04 (hardy)
GNOME 2.22.3
Kernel 2.6.24-21-generic

doesnt work for me, it says i cant do it when i copypasta, and when i replace user with my username, it says that the place doesnt exist :/

---

### Post by otz070 on 2009-01-11
I tried the same and got got the same... no luck......

My really annoying and loooooooong workaround is this (works for me anyway) (still not a REAL fix so problem is by no means solved:()

1. Create a new menu, name it what you wish.
2. Move all of the items from the defunct menu to the newly created menu
3. Delete the old menu.

Annoying because If your like me and have say 50+ menu items to move and they have to be moved  one  at  a  time   .....:(

---

### Post by Sef on 2009-01-11
Alacarte is installed on Ubuntu as a default app.  It is called Main Menu (System > Preferences > Main Menu.)  You can delete or change the name of any app there.

---

