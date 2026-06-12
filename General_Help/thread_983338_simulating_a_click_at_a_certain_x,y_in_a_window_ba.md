---
title: "simulating a click at a certain x,y in a window: bash problem PLEASE HELP"
date: 2008-11-15
forum: General Help
---

### Post by realthor on 2008-11-15
Hello, I am very new (tottaly noob) to bash scripting and I am trying to simulate a click at a certain coordinate in a nautilus window.

I can get the X,Y coordinates of the window by tho commands:

[INDENT]```
xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)" |awk -F " " {'print $5'} |xargs xwininfo -id |grep "Absolute upper-left X:" |awk -F " " {'print $4'} 

xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)" |awk -F " " {'print $5'} |xargs xwininfo -id |grep "Absolute upper-left Y:" |awk -F " " {'print $4'} 
```[/INDENT]

When I type each of them in Terminal I get the correct coordinates of the Terminal window but in a bash script I need to do this (I guess):

[INDENT]```
#!/bin/sh
x=` here comes the first command, to get X `
y=` here comes the second command, to get Y `
echo xte 'mousemove $x+50,$y+250' 'mouseclick 1' 'mousermove 300 0'
```[/INDENT]

I don't know how to escape the very long command and neither to build this simple script.

Can anybody help me?

Thanks a lot.

---

