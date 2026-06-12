---
title: "Problem!!! : /Home directory not listed, can't login with GNOME"
date: 2008-08-04
forum: General Help
---

### Post by florianderouck on 2008-08-04
Hello Everyone , 

I have a serious problem with permissions on my Ubuntu Laptop. When i was installing programs like virtualbox i kept getting an error known on the ubuntu forums as .dmrc issue. I tried to resolve that by changing the permissions. Accidentally i changed the whole /home permissions to 644. Now I am not even able to login using Gnome and can only acces it using terminal failsafe.
I tried : chmod 777 /home and stuff like that thinking that would allow me back in GNOME but it keeps giving me the same error :

"Your home Directory is listed as : /home/[USER] but it does not appear to exist. Do you want to log in with the root user ...ect ?"

I tried the command ls for /home and my files are still there. Also when using ls -l for /home it seems that my users has indeed got full acces to the files.

Why doesn't this make any sence !!!

Help would be very much appreciated !! I really can't lose those files by formatting!


Thx in advance ,

Florian


[UPDATE] I have found the problem but still don't have a clue how to solve it. I used Virtualbox to share my /home file. Seems like that triggered me from getting in ubuntu. How can i change this back ???

---

### Post by ajgreeny on 2008-08-04
Try ```
sudo chmod -R 755 /home/username
``` and it might work; you may not even need the sudo if you boot in recovery mode, but I'm not sure.
I can't help with the virtualbox problem as I don't know enough about it.  Also make sure you are the owner of all the /home/username files

---

### Post by florianderouck on 2008-08-04
Thx for the reply !

Sadly I already tried such a command. Still gives same error that /home/user isn't listed. 

For example : 

When i try : 
```
user@pcname :/$   ls /home
```

It gives : Permission denied.

When i login as root : 

```
root@pcname :# ls /home
```

It works.

When i check permissions using root :

```
root@pcname :# ls -l /home
```

it gives : 

drwxr-xr-x ......... User ( not root )

That means User is owner of the home directory is it not ? Then why doesn't it let me acces the directory then ! ?


**Important**: i found on the forum a person with the same problem : Deeta on this topic : [http://ubuntuforums.org/showthread.php?t=772706]("http://ubuntuforums.org/showthread.php?t=772706")

> When you get it to work, take care not to check the 'other' people checkbox when you try to share your home folder
What will happen is:

-Nautilus will ask you to change permissions
-next time you start X gdm disallows you to login as other people can 'write' to your home directory
-super newbie friendly recovery console happy time ensues.

I managed to lock myself out of gnome this way. And if it were not for a secondary computer where I asked for help in the forums it would have been the end of my fun with Ubuntu 


But it doesn't give me any anser !


Need help ! 

Florian

---

