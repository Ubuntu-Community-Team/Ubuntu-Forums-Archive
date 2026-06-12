---
title: "Tux Cursor - Ubuntu Compatible?"
date: 2008-08-13
forum: General Help
---

### Post by alt3rn1ty on 2008-08-13
:confused: Does anyone know if the following...

[http://www.gnome-look.org/content/show.php/Resizeable+Tux+Cursor%21?content=5376](http://www.gnome-look.org/content/show.php/Resizeable+Tux+Cursor%21?content=5376)

.... is compatible with Ubuntu 8.04.1

I followed the install instructions (and referenced the original less cute Tux cursor for further instructions) but had some major problems.

Problems encountered, some animations not same scale/size as selected (32 gave a massive busy cursor while resize cursors (screen edge) looked probably the next size down, while main cursor was 32)

But bigger problems, my terminal would not load, and various attempts thereafter to address this problem were stopped by the odd behaviour when asked for password for root access I would input the first character and the password request immediately exits without giving me chance to enter the rest, hence any super user access was denied.

Baffled, I reverted my cursor to the previous one, restarted in recovery mode, and after various tinkering got back to normal mode with a terminal again. After more confusing problems regarding the cube not working, I found I also had to re-install graphics drivers (legacy) for my nvidia gf4 mx card.

:shock: All this from a cursor????.

I have no idea what I could have done wrong but I remember one instruction I could not do..
7. check if the index.theme contains this line: inherits=tuxcursor
I dont know what app to edit/look at this file with.

Very wary of re-trying it until someone in the know can possibly give a clue as to why it went wrong, or a better idea of how to go about safely installing this. I now have (fingers crossed) everything back to normal, but also a family clamouring for the cute penguin mouse :lolflag:

---

### Post by alt3rn1ty on 2008-08-13
I have just read after doing a few more google searches that it is possible to install a new cursor theme by just drag/dropping the tarball onto the preferences screen, would this work in this instance?

---

### Post by alt3rn1ty on 2008-08-13
One further question - Would moving the index.theme into a wrong folder have caused any of the weird problems in my op?

Sorry for so many questions on what may seem like a simple change to most (I certainly thought it should be a simple procedure), but having experienced the above problems you can probably understand my reluctance to jump in with both feet again.

I think the instructions for noobs with this cursor theme on gnome-look.org are confusing, and probably out of date.

---

### Post by alt3rn1ty on 2008-08-13
Scratch the index.theme question above, I thought I may have at one time put it in the wrong place, but having just gone through the whole thing carefully and ended up with the same precarious situation, ie no terminal again and the inability to enter a user password for root operations and having to re-install graphic driver and re-enable cube and theme settings.

So, I believe I have the right way of doing things here, after following the op's instructions then going back to the 0.4 version and reading users comments I think it should go like this...

Download tar
extract two folders
copy index.theme from his old defaults folder (apparantly not used anymore) into his tuxcursor folder.
So now I have tuxcursor folder with index.theme inside and a further cursors folder inside.
The whole tuxcursor folder then goes into my ~/.icons folder.

Then the cursor theme should be selectable from within compiz config advanced custom settings... it is, but as soon as I select it all the above mentioned weird effects then transpire against me.

Does anyone have any help for this problem?

EDIT: I have also tried dropping the tar onto the preferences screen to install it... same results

---

### Post by alt3rn1ty on 2008-08-14
:shock: No answers at all?, do I have virtual body odour or is this really unfathomable. Amazing.

Okay new tack on the problem....

Does anyone know how would I go about converting the downloaded cursor files to be compatible (and in the right size 32) for my Ubuntu.

---

