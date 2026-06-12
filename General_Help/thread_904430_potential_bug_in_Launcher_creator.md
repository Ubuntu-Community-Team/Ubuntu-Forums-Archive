---
title: "potential bug in Launcher creator"
date: 2008-08-29
forum: General Help
---

### Post by Tony Flury on 2008-08-29
I am not at my Ubuntu setup at the moment - but will happily post more details when requested.

I think there is a bug in the Desktop Launcher Creation tool, and i would like others to try and reproduce it, or even better acknowledge that it has already been noted and raised.

Pre conditions : Program ready to have a launcher created for it, valid PNG file for the desktop Icon

Step :  

1) Create Launcher on the Desktop, and select the Program to be executed. 
2) Choose to change the icon, and navigate to folder with PNG file.
Expected result : PNG file will be listed and can be selected.
Observed results : Sometimes the PNG file is not listed.
3) Select Icon (if it is listed)
4) Obseve in the Launcher Creation window : 
Expected result : Icon has been changed to that contained in the PNG file 
Observed result : Icon has not changed.
5) Click OK on the creator window.
Expected result : New launcher created on the desktop to the chosen program with the chosen icon.
Observed result : New launcher created on the desktop to the chosen program with the default spring icon.

It has been noted that there are two solutions to the inability to pick the correct icon : 
1) While in the creator, drag and drop the icon file from your chosen File manager onto the Spring icon.
or 
2) After creation of the launcher with the default spring icon, the launcher can be edited, and the correct icon can be chosen via the editor.

It is clear from both work arounds that PNG is a valid Icon file format, and that the icon itself is valid, but the creator wont allow it to be selected.

Any thoughts ?

---

### Post by Oldsoldier2003 on 2008-08-29
some initial thoughts here:

it does sound like a bug. I would check Launchpad to see if it has been reported and if it hasn't been reported go ahead and file a bug report.

---

