---
title: "Mac fonts for xterm"
date: 2008-11-18
forum: General Help
---

### Post by orengolan on 2008-11-18
I want xterm to use Mac fonts for my terminal (xterm).

I installed Monaco_Linux.ttf:
```
sudo mkdir /usr/share/fonts/truetype/custom
sudo mv Monaco_Linux.ttf /usr/share/fonts/truetype/custom/
sudo fc-cache -f -v

```

I know it's installed since the command 
'fc-list | grep Monaco' shows:
```
Monaco:style=Regular,Standard,Testo normale,Normaal,Normal,Común,Almindelig,Vanlig tekst,Normaali,...
```

When I type: xterm -fa Monaco_Linux
It looks ok but I want it to be the default font so I am trying to edit .Xdefaults file.

The problem is what is the correct syntax of the xterm*font line?

for example, this font works:
```
xterm*font: -*-lucidatypewriter-medium-*-*-*-17-*-*-*-*-*-*-*
```

To find the right syntax there is a command that can help- xfontsel.
I run it and can see all the installed fonts, but I can't see Monaco.

Any idea what is the correct syntax for monaco or any other solution?
I can use alias as an alternative but I prefer editing Xdefault.

Thanks!

---

