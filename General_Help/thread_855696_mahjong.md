---
title: "mahjong"
date: 2008-07-10
forum: General Help
---

### Post by kn000bie on 2008-07-10
linux noobie

I installed andlinux which gives me gutsy

i said

apt-get install mah-jong

now how do I actually run it!?

---

### Post by MasterXandrex on 2008-07-10
The command you are looking for is 

```

sudo apt-get install mah-jong

```

it stands for "Super User DO" and will require you to retype your passoword. System level (root) commands can be performed from a normal user by prepending them with this command or you can type

```

sudo -s

```

to just become root.

However, for the novice user, I would reccoment using synaptic. You can find it in your System>Administration or type

```

sudo synaptic

```

in the terminal -- it has a nice user friendly GUI.


Xan

---

### Post by kn000bie on 2008-07-11
thanks
I guess since I am on andLinux
apt-get install mah-jong
did work for me

but it did not create any menu
so my question was

where is it installed
how do I actually run the game?

---

### Post by Vorian Grey on 2008-07-11
Have you tried typing mah-jong in a terminal to see if it runs? If so, it is easy enough to create a menu item. Right click on applications and select edit menus. From there, click on game and select new item on the right side. Give your program a name and in the command part type mah-jong. 

If typing mah-jong in a terminal doesn't work we'll have to take another approach.

---

### Post by kn000bie on 2008-07-14
I have tried

mahjong
kmahjong
mah-jong

:(

If only someone tells me where this is installed

---

### Post by confused57 on 2008-07-14
Try:
```
mahjongg
```

If this works you can  add it to the Applications---Games menu, just right-click the Applications menu, select Edit Menus, left-click on Games, left-click on New Item, then Mahjongg for the Name & mahjongg for the command.

---

### Post by fooman on 2008-07-14
try:

```
xmj
```

[http://mahjong.julianbradfield.org/use.txt](http://mahjong.julianbradfield.org/use.txt)


i think "mahjongg" is a different game that comes along with the "gnome-games" package.

---

