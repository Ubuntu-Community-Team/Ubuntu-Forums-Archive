---
title: "[SOLVED] trash dosent work and Im not a newbe to linux!"
date: 2008-10-31
forum: General Help
---

### Post by rylangrayston on 2008-10-31
my trash dosent work ubuntu 8.08

apon deleting something I get this message

"Cannot move file to trash, do you want to delete immediately?"

I read a couple of forms on this seemingly simple problem

I checked for the .Trash folder in my home directory found none, 
so I made one with a right click make folder .Trash with a capital T

no cigar

then I tryed login out and in again 

no cigar 

then I marked nautilus for re installation and applied

still nothing


then I loged on as a diferent user wher the trash works 

deleted some file and cliked the trash applet - found the file- works!

here where it gets wird in the user home directory(where the trash works) there was no file named .Trash and yes I had the view hiden files tab chequed!

so I made that .Trash file and wasent asked to replace an existing file 
conferming that I didnt just miss it.

when I open the .Trash file I just made there is nothing in it despite the trash applet showing many files!

I browsed the root user home folder and there is a .Trash folder there

It would seem that nautilus is useing a different directorie than 
.Trash and what ever dir that is its mising in the first user is spoke of
but not the second

I tryed to find the location of this folder by right clicking 
properties on the trash icon in the second user and came up with the path

trash:/// 

any Ideas anyone?

---

### Post by ThrobbingBrain66 on 2008-10-31
The location of the trash folder is ~/.local/share/Trash

---

### Post by Meow27 on 2008-10-31
what happends when you try to access computer?

does it give something like cannot access computer/// locations   ?

---

### Post by anil_robo on 2008-11-01
I'm returning to Ubuntu after many years, and it seems they changed the default trash location from ~/.Trash to ~/.local/share/Trash

I come to this thread after searching for a similar issue "how to empty root trash". Got it solved as per ThrobbingBrain66's hint.

Finally am able to do it now. 22GB of Trash!

Note that even if you're logged in as root (sudo nautilus), the root trash doesn't show up when you click the wastebasket icon in Nautilus. A red error icon shows up instead!

Is this a bug?

---

### Post by rylangrayston on 2008-11-01
yes thank you ThrobbingBrain66 
my problem with the trash was solved buy 
changing using chmod to change the 
permitions and chown to change the owner of my ~/.local/share/Trash

like this 

$ sudo chown username ~/.local/share/Trash

$ sudo chown username ~/.local/share/Trash/files

$ sudo chown username ~/.local/share/Trash/info

$ chmod 700 ~/.local/share/Trash

$ chmod 700 ~/.local/share/Trash/files

$ chmod 700 ~/.local/share/Trash/info


that fixed it for me.



Meow27 I entered  

computer:/// 

in the nautilus url and it shows all mounted and unmounted media


anil_robo I did

 $ gksudo nautilus 

and clicked the trash icon and 
had got the same result 
If this is intentional I dont know why! It may be a bug 
might want to start a thread on that.

thanks for the prompt replies everyone.

---

