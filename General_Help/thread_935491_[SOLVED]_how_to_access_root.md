---
title: "[SOLVED] how to access root"
date: 2008-10-01
forum: General Help
---

### Post by inxygnuu on 2008-10-01
While I was trying to access some files, It said that I could not access them, i went back and it said that "root" was the owner:evil::evil:, I went to the user file editor thing,and it said that it was a file, so I went to the login screen, and it told me that I couldn't log into it because it was an administrator account:confused::evil:. I then tried to delete it, but it said i couldn't. This really makes me angry:evil::evil:, so can anyone help me?:confused:

---

### Post by Forbees on 2008-10-01
open terminal
```
 sudo nautilus 
```

that will bring up a file browser with root abilities


BE CAREFUL

you can really **** up the system in root mode :-p

---

### Post by bodhi.zazen on 2008-10-01
To get a root shell use :

```
sudo -i
```Use gksu (kdesu for kde) for X apps

```
gksu nautilus
```

@Forbees : gksu if preferred for X apps

---

### Post by Forbees on 2008-10-01
> **bodhi.zazen said:**
> 
@Forbees : gksu if preferred for X apps

i never really figured out the point of gksu . . . i just sudo everything >,<

---

### Post by kokkus on 2008-10-01
Enable root:
```
sudo passwd root
```

disable root again
```
sudo passwd -l root
```

---

### Post by bodhi.zazen on 2008-10-01
> **Forbees said:**
> i never really figured out the point of gksu . . . i just sudo everything >,<

LOL

The point of gksu is to give sane access to X. Obviously you can use sudo.

[https://help.ubuntu.com/community/RootSudo#Graphical%20sudo](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo)

[http://linux.die.net/man/1/gksudo](http://linux.die.net/man/1/gksudo)

The problem, in a nutshell, it that if you use sudo for X apps you may change the permissions of the config (. or dot) files in $HOME => this results in an inability for the user to then log in => many users will not know what happened or how to fix it.

So please, on these forums, when advising new users, consider using gksu even if you do not understand it.

---

### Post by gus_393 on 2008-10-01
generally files that are belong to root should be edited with caution and care, hence just providing my two cents, I would not launch nautilus with those kinds of privileges or do any kind of invasive work around.

Thats like using an axe instead of a scalpel. This kind of "protection" is what makes ubuntu systems stable and reliable. Once its configured, it`ll stay that way.

long story short, my advice would be to get confortable with the command line (gnome-terminal is the command, or you can see it as an icon under application accessories).

just use
"sudo gedit *filename* &" when you need to edit system files like say your /etc/X11/* configs.

using sudo lets you run commands with admin privilieges. So this lets you lauch the gedit text editor with the permissions that when you hit save, it will actually save and not complain that it cant. Also, using the ampersand runs "jobs" in the background, so it doesnt tie up your command line (you can use subsequent commands).

If your new to linux, I`d suggest only editing things if you are following a reputable tutorial/procedure. In general, if you are coming across files that are permissioned as such, you really shouldnt be editing them unless you really know what you are doing.

the unix filesystem hierarchy is really well defined, and its one of the beautiful things about the OS. In general if your are creating docs they should be under /home/*yourUserName*. You should have permissions and ownership of most things in there.

I hope that is of some help, I might have said alot of things you already know, just trying to do my part and post some "replies" instead of always posting "questions"

---

### Post by Iowan on 2008-10-01
[RootSudo]("https://wiki.ubuntu.com/RootSudo") explains the philosophy behind **sudo**.  Perhaps it's changed since I read about it in an earlier version, but the warning was that once **root** is enabled ( even if re-disabled) the rescue mode became more difficult.

---

### Post by bodhi.zazen on 2008-10-01
> **gus_393 said:**
> just use
"sudo gedit *filename* &" when you need to edit system files like say your /etc/X11/* configs.

just use
"gksu gedit"

you can add the path to a file if you like

"gksu gedit /path/to/file_u_wish_2_edit"

Or you can navigate to the file with the menus on gedit.

The point is ***[color=blue]Please use [color=red]gksu[/color] for X appliciations***[/color]

/me hands gus_393 vim

---

### Post by exploder on 2008-10-01
> The problem, in a nutshell, it that if you use sudo for X apps you may change the permissions of the config (. or dot) files in $HOME => this results in an inability for the user to then log in => many users will not know what happened or how to fix it.

I usually just use sudo, perhaps I should give this some thought!

---

### Post by bodhi.zazen on 2008-10-01
> **exploder said:**
> I usually just use sudo, perhaps I should give this some thought!

Here is the more long winded answer :

[http://ubuntuforums.org/showpost.php?p=4636376](http://ubuntuforums.org/showpost.php?p=4636376)

:lolflag:

---

