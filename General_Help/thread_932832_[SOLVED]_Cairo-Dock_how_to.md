---
title: "[SOLVED] Cairo-Dock how to"
date: 2008-09-28
forum: General Help
---

### Post by yarn on 2008-09-28
can anyone please tell me how to possibly add a folder to the launcher, or a hard drive, or is this even possible...i have only been able to get programs to show up. Also...whenever i close a program the icon on the launcher disappears? Can anyone tell me why this happens...i just want to be able to put my programs, folders, and hard drives on the launcher without having them open...thank you in advance.

---

### Post by fabounet on 2008-09-29
I'm not sure what you exactly want to do, but you can try to drag'n'drop it into the dock.

---

### Post by zzzzz1 on 2008-09-29
in the applets menu you can add launchers which you then can configure by right clicking the icon on the bar.

---

### Post by yarn on 2008-09-29
i have tried to drag things to the launcher and that didnt work...i will have to try to configure the applets. But will i be able to put folders on it that way?    thanks for the replys

---

### Post by Iwannakillyou on 2008-09-29
I have been waiting for about 5 days now but the shipping times are 10-19 days. As soon as I get them I will let you know. I have not seen you on that forum for a long time now and I was wondering where you are? How did it go with the collection that you got? Here is the link to the beads again [http://www.liangdianup.com/beadscrafts_1.htm](http://www.liangdianup.com/beadscrafts_1.htm) and here is the link to the Swarovski beads [http://www.liangdianup.com/inventory/900020.htm](http://www.liangdianup.com/inventory/900020.htm) if those links don't work then you can goto [www.lducompany.com](www.lducompany.com) and click on the beads picture, that should take you right there. I hope you see this message and get back to me cause I miss talking to you :)

---

### Post by fabounet on 2008-09-30
"the applets menu" ??
which applets are you talking about ? the Stack one ?
you can dnd anything into this one.

---

### Post by yarn on 2008-10-03
sorry i got cairo-dcok confused with AWN...but when i drag folders to cairo dock they dont go on there...does anybody know how i can put a folder on cairo dock...like as if the directory was /home/Desktop/MUSIC   ...THANKS IN ADVANCE

---

### Post by yarn on 2008-10-08
How can i add folders to cairo dock?  Please help.

---

### Post by fabounet on 2008-10-09
drag'n'drop
Shortcuts applet
Stack applet

---

### Post by yarn on 2008-10-09
i dont see a shortcut applet or stack applet in the settings...sorry still a little new to linux...only been using it for a coupled months.  can you give me more in depth instructions...thanks for the reply

---

### Post by onero on 2008-10-09
What version of cairo-dock are you using? Drag and drop works for me. The latest version is 1.6.2.3.

About the icons disappearing after you close the program, that's because ypu haven't added them as launchers in your dock. The dock can have program launchers, currently opened programs, folders,  and also various applets.

To add a folder, you have to drag a folder (say, from nautilus) to the launcher area, and you should see an arrow animation indicating that you can drop the folder there. You need to drop this into the launcher area, so be sure to have a program launcher present first. To do this, you can also drag and drop program shortcuts (for example, from the Applications menu) to the dock.

---

### Post by yarn on 2008-10-09
it shows the arrows when i drag and drop but it doesnt go on there....i am not using that version maybe that is what is wrong...can u tell me how to update cairo dock...or do i just have to uninstall it and reinstall the new version...thank you for the help!!!

---

### Post by fabounet on 2008-10-10
are you under KDE ?
is there any useful debug info in the terminal when you launch the dock with "cairo-dock -l debug" ?

---

### Post by yarn on 2008-10-10
there is no errors...everything seems like it works fine except dragging a folder into cairo-dock....thank you for the reply...i realize im not using the newest version of ubuntu...how can i update it to see if that fixes it?

---

### Post by fabounet on 2008-10-13
add the cairo-dock's repository to your sources list, and it will be automatic then.
not sure it will fix your problem, but it worth trying.

---

### Post by whitethorn on 2008-10-13
I'm not really sure this is what you need.  But you could try this.  

Right click on Cairo-dock -> Add a manual launcher -> Command to launch on click 

```
nautilus --browser /path/to/your/folder
```
Then you could find a Icon for it.  Now when you click on it, it should open Nautilus in the folder you specified.

---

### Post by yarn on 2008-10-13
hey..i figure it out...i wasnt using the newest version and i guess there was a small bug or something..but it does let me drag and drop my folders now...and thanks whitehorn also...that idea also works for me...thanks for everything !!!

---

