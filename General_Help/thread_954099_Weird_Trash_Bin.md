---
title: "Weird Trash Bin"
date: 2008-10-20
forum: General Help
---

### Post by Dougo007 on 2008-10-20
My Trash Bin icon says that there are icons in the bin, and says that there are two files in it when I "hover" my mouse over the icon.  When I open the folder there are no files there at all!!!!!

I tried attempts such as "cd  ~/.Trash" and then "sudo  rm -rf    *"

and other such attempts to act as the root, but since there are no files to delete, noone and noting can be done

Can I "reset" the icon and what it "thinks" is in the trash bin?

---

### Post by kerry_s on 2008-10-20
i think i've had that happen, just create a file and delete it, then empty the trash from inside nautilus

---

### Post by Dougo007 on 2008-10-28
I discovered a "trend" with the problem.  Everytime I delete a file and the empty the trash, it clears the icon.  When I logoff and log back in again the icons resets and thinks that there is trash in the bin where there is nothing there at all.  Is this a glitch I'll just have to deal with (its not's not affecting anything else, just an annoyance) or is there some .ini file that I can edit to fix this.

P.S.  When mentioning a file name, say EXACTLY where it is in the FileSystem and EXACTLY where in the file to fix this problem.  I do know how to do sudo nautilus so if I need root permissions, I do know how to do that.

---

### Post by alienprdkt on 2008-10-28
could see if this helps 

#sudo bash
#rm -rf ~/.local/share/Trash/files

(external drive)

#sudo bash
#rm -rf /media/disk/.Trash-1000/files

---

