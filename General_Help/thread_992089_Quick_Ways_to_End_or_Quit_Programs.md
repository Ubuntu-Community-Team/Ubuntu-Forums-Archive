---
title: "Quick Ways to End or Quit Programs?"
date: 2008-11-24
forum: General Help
---

### Post by iheartubuntu on 2008-11-24
Are there any quick ways to end or quit programs in Ubuntu?

Usually, I use "force quit" when need be, or I revert to CTRL+ALT+Backspace in worst case scenarios. Most of my problems usually occur when Im running a Wine installed program. Are there any shortcuts for Force Quit? That might help.

Would ALT+F4 work? Any way to create other keyboard shortcuts?

Thanx!

---

### Post by Coreigh on 2008-11-24
in a terminal:
```
top
```
will list running and failed (zombie) processes and the ID number

```
sudo kill <PID>
```
will kill the <PID> process/application. 
(<PID> is the process ID number)

command executed from the commandline can sometimes be canceled with:
Ctrl+C

but only if they are not released from the terminal.

EDIT:
```
sudo ps -A | less
```
will list _ALL_ processes

---

### Post by marshall.robert on 2008-11-24
much easier than that, is the Force Quit pannel applet (Right click on panel of choice, Add to panel)

---

### Post by iheartubuntu on 2008-11-24
I already use force quit from the panel. Im talking about alternative methods to that.

I guess I could try ALT+F2 and then type in "xkill", but I was looking for maybe a keyboard shortcut to force quit, lets say if I cant get to my force quit on my panel.

---

### Post by caljohnsmith on 2008-11-24
Using the "force quit" applet will kill the X window with the application, but if the application has other processes running, sometimes that can be a problem. You could do something like:
```
xprop | grep WM_CLASS
```
Then click on the GUI application you want to kill, and that command will show you which program name it is (most of the time it works, but not 100%). Then just kill the program with something like:
```
sudo killall <program name>
```
For instance, when you run a gnome terminal, the xprop command will return the following if you click on the gnome terminal window:
```
john@TECH3142:~/tmp$ xprop | grep WM_CLASS
WM_CLASS(STRING) = "[COLOR="Blue"]gnome-terminal[/COLOR]", "Gnome-terminal"
```
And then you could kill it with:
```
sudo killall [COLOR="Blue"]gnome-terminal[/COLOR]
```
Maybe it's too much trouble, but it's just an idea. :)

---

