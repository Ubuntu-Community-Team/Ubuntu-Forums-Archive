---
title: "Users, Multimedia, and Default Apps"
date: 2005-12-05
forum: General Help
---

### Post by acerX on 2005-12-05
I recently installed Breezy on a family friends computer and finally got it working in most respects.  I am trying to setup their user accounts and such.  However, several of the user account gave me errors, so I deleted them from the Users and Groups setup box.  When I go into the home folder their $Home folders are still there.  I tried changing the owners to my own and deleting them but no luck.  How can i get rid of these folders/files, so I can finish creating their accounts?

************

I used automatix to install all the non-free plug-ins and media players, etc. As far as I can tell they all play the media files however, they dont have any controls in firefox.  IE: play/stop, skip, back, etc.  This leads to them all playing at the same time.  Is there any way to get the media controls in firefox?

************

Finally I tried installing a couple additional media player, cd players, etc.  But when I put a CD in the drive SoundJuicer opens. I would perfer to be able to specify a different default program.  Is this possible?

---

### Post by newuser111 on 2005-12-05
you can use  **rm -r** to delete a directory and all the files it contains, you may have to sudo the command to delete the directories you want to, be careful with that command however


are you using mplayer to play video in firefox?  right clicking on the playing video and select show controls


run gnome-control-center from terminal and chose "removable drives and media" then "multimedia" here you can chose which app plays audio cds

---

### Post by acerX on 2005-12-05
[QUOTE=newuser111]you can use  **rm -r** to delete a directory and all the files it contains, you may have to sudo the command to delete the directories you want to, be careful with that command however
[/QUOTE]

that worked nicely thank you

> 
are you using mplayer to play video in firefox?  right clicking on the playing video and select show controls


I thought I was but apparently I am not because I cannot right click on the movie.  Any way to find out what i amusing to play videos?

> 
run gnome-control-center from terminal and chose "removable drives and media" then "multimedia" here you can chose which app plays audio cds

is there any way to make these preferences universal for all users, rather than changing each one individually

---

### Post by Bandit on 2005-12-05
> I recently installed Breezy on a family friends computer and finally got it working in most respects. I am trying to setup their user accounts and such. However, several of the user account gave me errors, so I deleted them from the Users and Groups setup box. When I go into the home folder their $Home folders are still there. I tried changing the owners to my own and deleting them but no luck. How can i get rid of these folders/files, so I can finish creating their accounts?
"sudo chown (your user name) /home/(their user name)"
I.e:  "sudo chown bandit /home/jane" were as Bandit is my user name and the other user account directory I want to control of so I can delete is jane.
Hope this helps.
Cheers,
Joey

---

### Post by acerX on 2005-12-05
I got rid of the excess of folders/files so that problem has been taken care of.  Thanks all who helped!

---

