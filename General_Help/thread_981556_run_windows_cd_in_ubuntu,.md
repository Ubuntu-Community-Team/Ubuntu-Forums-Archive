---
title: "run windows cd in ubuntu,"
date: 2008-11-13
forum: General Help
---

### Post by portofmiami on 2008-11-13
installed wine didnt help What can i do

---

### Post by taurus on 2008-11-13
You mean you want to run windows OS in Ubuntu?  What you need is virtualbox, [http://www.virtualbox.org/](http://www.virtualbox.org/), and fortunately, you can install it either from synaptic or from a terminal.

---

### Post by portofmiami on 2008-11-13
i have a cd from school and it will not run says autorun wont work on the cd says win/mac

---

### Post by taurus on 2008-11-13
What is the program on the CD?

---

### Post by Viranh on 2008-11-13
The autostart will not work automatically. You have to start the program or its setup program in the terminal:
cd /<cdlocation> (often /media/cdrom0)
ls   (this will list the contents of the cd)
wine <programname>.exe (replace <programname> with the actual name)

if no errors occur, you should now be able to run the program. 
cd ~/.wine/drive_c/"Program Files"/<"Folder Name">/<programname>.exe

This may also be done by going to applications>wine>programs, but the terminal will give you an error message to post if the program does not run.

You could also check to see if the program is compatible with wine in the wine appdb [http://appdb.winehq.org/](http://appdb.winehq.org/)

The page for the program may have additional tips for getting the program installed.

---

