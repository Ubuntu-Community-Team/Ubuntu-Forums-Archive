---
title: "Having a few problems with Ubuntu 8.10"
date: 2008-11-19
forum: General Help
---

### Post by 5oviet on 2008-11-19
I installed Ubuntu 8.10 64-bit and I am having a few problems with it. 
Here are my specs:
HP Pavilion a6000n
AMD Athlon X2 64 4200+ 2.2 GHz
3 GB RAM
XFX GeForce 8600 GT XXX

My first problem is my printer. No matter what I try I cannot get it working. The printer is an HP PSC 1210 which is connected to a Windows XP computer on the network. I have tried installing the printer through System>Administration>Printing>New>Windows Printer Via Samba. It can see the printer and can connect to it no problem, and sends the print jobs as well. But when my printer receives the job, it makes all the clicking and whirring noises it always does, and then just stops completely right before actually printing. I have also tried installing the printer via HPLIP. If I go to terminal and do "sudo hp-setup" the setup utility can't find any printers at all no matter what I try. If I try opening it through System>Preferences>HPLIP Toolbox nothing happens at all when I click on the icon. This is really frustrating.

My second problem is that suspend and hibernate don't work at all. When I click on either, the screen goes black, then a flashing cursor appears in the top left corner of the screen, and nothing happens after that. It just sits there with the flashing cursor until I press the power button and turn the computer off.

My third problem is the emerald theme manager. Whenever I open it and choose a different theme, it freezes. If I go to edit the theme I am currently using, it works fine. This started after I installed one theme, but I can't delete it because it freezes whenever I click the delete button. Can I delete the themes manually? I don't know what folder they are kept in.

One last thing, a minor annoyance for me. In the Open Office word processor it draws the margins on the page. I was wondering if there is a way to disable that?

Any help is appreciated. :)

---

### Post by dexter on 2008-11-19
> **5oviet said:**
> 
One last thing, a minor annoyance for me. In the Open Office word processor it draws the margins on the page. I was wondering if there is a way to disable that?


Uncheck "Text Boundaries" under "View".

---

### Post by fooman on 2008-11-19
> **5oviet said:**
> 

My third problem is the emerald theme manager. Whenever I open it and choose a different theme, it freezes. If I go to edit the theme I am currently using, it works fine. This started after I installed one theme, but I can't delete it because it freezes whenever I click the delete button. Can I delete the themes manually? I don't know what folder they are kept in.



open your home folder and in the toolbar go to view... put a check next to "show hidden files"

then find the .emerald folder.  open it and look in the "themes" folder.  right click on the newly added theme that you wish to delete and choose "move to trash".

---

### Post by 5oviet on 2008-11-19
> Uncheck "Text Boundaries" under "View".
I feel stupid now, it's so obvious. Thanks.

> open your home folder and in the toolbar go to view... put a check next to "show hidden files"

then find the .emerald folder. open it and look in the "themes" folder. right click on the newly added theme that you wish to delete and choose "move to trash".

Did that, deleted useless themes, but emerald still freezes. I'll try a reinstall.

Now onto the harder problems, lol.

---

### Post by 5oviet on 2008-11-19
Emerald is working now.

---

