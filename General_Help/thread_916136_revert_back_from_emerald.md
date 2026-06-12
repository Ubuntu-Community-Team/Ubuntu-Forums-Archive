---
title: "revert back from emerald"
date: 2008-09-10
forum: General Help
---

### Post by M4rotku on 2008-09-10
Hell all,

I just tried launching emerald from the cl and it told me that another manager was already handling the windows.  Curious, i entered "emerald --help" and saw the --replace option.

"emerald --replace" did it's job and replaced the orange theme with emerald, however, now when I close the terminal, I no longer have a windows manager

---

### Post by mgmiller on 2008-09-10
First, I can tell you how to get back what you had.

Run the commands from alt/F2

To enable metacity/compiz:
  gtk-window-decorator --replace

To enable emerald:
  emerald --replace

To enable metacity with compiz turned off:
  metacity --replace

It's important to run these from alt/F2 not terminal, otherwise it dies when you close the terminal.


If you want to install a gui for all this stuff do this:

install the package fusion-icon
```
sudo apt-get install fusion-icon
```
run it from Applications > System tools > Compiz Fusion Icon

look in the top panel, right click the icon for choices.
you can now switch between metacity, compiz and emerald

---

### Post by tuxxy on 2008-09-10
You could also add the command **emerald --replace** to your system > prefs > sessions , preventing you to have to run the command at all.

---

### Post by mfeltman on 2008-09-10
Another way to enter stuff in the terminal but have it still run when you close out is to enter commands like this:
> 
%> emerald --replace && exit

---

### Post by M4rotku on 2008-09-10
Thanks guys, I guess the --replace option ran out after one session.  When I rebooted, everything was back to normal.

---

