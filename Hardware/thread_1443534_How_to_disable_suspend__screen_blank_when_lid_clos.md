---
title: "How to disable suspend / screen blank when lid closes ?"
date: 2010-03-31
forum: Hardware
---

### Post by birdy62 on 2010-03-31
I want to disable suspend/ screen blank so that the laptop (ASUS F6J running Karmic 9.10) _remains on_ once the lid is closed. I use a monitor plugged into the laptop when I work at home and want to stack the laptop on a small shelf. I use the machine on ac power all the time to am not worried about batteries. I have switched of the laptop screen in System/Preferences/Display but naturally enough it still suspends when the lid is closed. If possible it would be best if the screen remain off while the machine is running with the lid down.I have been able to to this using FreeBSD and did not encounter any overheating problems.

---

### Post by iponeverything on 2010-03-31
Look in:

System/Preferences/Power Management

---

### Post by birdy62 on 2010-03-31
> **iponeverything said:**
> Look in:

System/Preferences/Power Management

No this doesn't do it, it offers Blank Screen, Suspend, Hibernate or Shut Down. I want to prevent any of these happening when I shut the lid, in other words I want isolate the lid switch in some way. 'Blank Screen' blanks all displays I want to use a separate monitor while the lid is closed.

---

### Post by iponeverything on 2010-03-31
> **birdy62 said:**
> No this doesn't do it, it offers Blank Screen, Suspend, Hibernate or Shut Down. I want to prevent any of these happening when I shut the lid, in other words I want isolate the lid switch in some way. 'Blank Screen' blanks all displays I want to use a separate monitor while the lid is closed.

On my laptop it offers the option of "do nothing".

---

### Post by burton247 on 2010-03-31
By default the option is removed, i cant remember off the top of my head how to do it. Ill have a look around, i found it before

[edit]

```

gconftool-2 --type string --set /apps/gnome-power-manager/buttons/lid_ac "nothing"

```

That should add the option, When laptop lid in closed "Do nothing" 

Im 90% sure this is what i did, i have a feeling you cant use gconf GUI to do this though. Let me know if it works or not

---

### Post by birdy62 on 2010-03-31
> **burton247 said:**
> By default the option is removed, i cant remember off the top of my head how to do it. Ill have a look around, i found it before

[edit]

```

gconftool-2 --type string --set /apps/gnome-power-manager/buttons/lid_ac "nothing"

```

That should add the option, When laptop lid in closed "Do nothing" 

Im 90% sure this is what i did, i have a feeling you cant use gconf GUI to do this though. Let me know if it works or not

I ran the above code  via a terminal, it did not work. But no error message. Also there was no request to authenticate either, wouldn't this sort of command generate a request for authentication? I tried to find the directory "/apps" it does not exist on my file system. However the directory ~/.gconf/apps/gnome-power-manager exists. What do you think about the following command?
```
gconftool-2 --type string --set ~/.gconf/apps/gnome-power-manager/buttons/lid_ac "nothing"
```

---

### Post by burton247 on 2010-03-31
hmmm...I dont know about that, have you restarted your system, or at least x?

I'll see if i can find where i put my mine, need to boot up ubuntu, and I've just installed windows7 so need to fix grub.

---

### Post by burton247 on 2010-03-31
That was easy, back already :)

I've realised this will only give the option for when your laptop lid is closed and on the mains. The option wont be there if running it on battery.

```
gconftool-2 --type string --set ~/.gconf/apps/gnome-power-manager/buttons/lid_battery "nothing"
```

That should add it to the battery menu.

If you were on ac power or it hasnt worked i suggest you look at the keys there.

Run
```
gconf-editor
```

then navigate to /apps/gnome-power-manager/buttons/

if the key "lid_ac" and value "nothing" is there is should work 
or "lid_battery" and "nothing" 

or both, depending on the functionality you require

---

### Post by birdy62 on 2010-03-31
Thanks, that did it, I wanted the functionality with ac power. Setting it in gconf-editor was successful.

---

### Post by burton247 on 2010-03-31
I don't know why the command didn't work, oh well. Glad it's sorted

---

### Post by xjwellsx on 2010-07-17
Please post solved in the title

---

### Post by blackest_knight on 2010-07-21
Thanks for showing how to get the do nothing option. For the sake of completeness here are two tiny scripts littledesk.sh and bigdesk.sh which I use to switch screens on my netbook from internal to external and back again. 


littledesk.sh

xrandr  --auto
xrandr --output VGA --off

bigdesk.sh

xrandr --output VGA --mode 1440x900
xrandr --output LVDS1 --off


hope you find this useful.

---

### Post by alinawaz87 on 2010-12-12
@Burton247: GOSH!! you saved my life ;)

---

