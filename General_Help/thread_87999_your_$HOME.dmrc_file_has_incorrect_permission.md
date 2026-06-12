---
title: "your $HOME/.dmrc file has incorrect permission"
date: 2005-11-09
forum: General Help
---

### Post by nene on 2005-11-09
Hi I have a problem when I log in to Ubuntu 5.10, after I put my password appears a pop-up window with this error:

Your $HOME/.dmrc file has incorrecr permission and is being ignored. This prevents the default session and language from being saved. File sould be owned by user and have 644 permissions.

how to restore a permission?

:confused:

---

### Post by Kyral on 2005-11-09
Its a harmless error but if you want to fix it

```
sudo chown <your username> .dmrc
```

Sudo shouldn't be needed, but its there to make sure that the command works

---

### Post by ThirdWorld on 2005-11-09
well, i tried all the suggested fixes in different threads including this one, but nothing works it keeps happening at log in. Its a very annoying bug, and i mean very annoying speacially when you are trying to convince your family memebers to switch to linux and the first thing they see its this stupid bug and there is no way to ged rid of it. Im sorry im a little bit angry about it. :???:

---

### Post by Kyral on 2005-11-09
Whoops forgot the second part of the fix

Once you chown it, then

```
chmod 644 .dmrc
```

I have no clue what causes this bug...it seems to pop up randomly. I've never had it myself...

---

### Post by ThirdWorld on 2005-11-09
thank you kyral, but that fix doesnt work... i already tried it twice. dont know what to do. :(

---

### Post by Lambert on 2005-11-09
Did you try with the recursive (-R) option

```
sudo chmod -R 644 .dmrc
```

---

### Post by ThirdWorld on 2005-11-09
i log out and log in again after tried the -R stuff in the console, same thing nothing happens. I already check that file permisions are set 644. So this is really wierd. but thank you guys for try to help us anyway looks like this bug is here to stay...

---

### Post by Kyral on 2005-11-09
You could always try just deleting it

---

### Post by ThirdWorld on 2005-11-09
do you think i can delete the file safetely without mess everything up??

---

### Post by Lambert on 2005-11-09
Don't give up yet, somebody here may know the answer and just not read the thread yet.

You may want to post the output of this here and maybe somebody will see something. 

```
ls -al ~/.dmrc{,/*}
```

Somebody may have a better code to accomplish this but this should work. Not at a box to max sure my command is correct.

---

### Post by Kyral on 2005-11-09
Well, its in $HOME (BTW $HOME is another alias to your homedir, just like ~, in case people viewing the thread didn't know), so any damage done would be to your personal configs, not the system.

And also it isn't being used right now anyway. Heck I don't even have one and the computer runs fine

---

### Post by ThirdWorld on 2005-11-09
[Desktop]
Session=default

This is the only thing that the .dmrc file said, it doesnt look like an important file to me.

off topic = kyral your abatar is really cool can you tell me in what anime series is it based?

---

### Post by Kyral on 2005-11-09
Uuuh...nope. Go ahead and nuke it :D

---

### Post by ThirdWorld on 2005-11-09
i delete it, and the message appear again at log in, funny thing the .dmrc file reapear in my home directory.... :confused:

---

### Post by Kyral on 2005-11-09
It gets respawned...

Okay I found out what it DOES at least. It tells GDM what Window Manager to use as default. So mine says "XFCE4"

Try editing it and changing it to either "gnome" or whatever the command that starts gnome is (NOT startx)

---

### Post by Dr. Nick on 2005-11-09
Ive had it and have fixed it using this link [http://ubuntuforums.org/showthread.php?t=80099](http://ubuntuforums.org/showthread.php?t=80099)

try to run Chmod 700 /home/username which fixed it for me. I dont see any danger with the 700 permissions, but it is annoying when you set it to 644 and it still doesnt work

May read here aswell for explanations [http://www.ubuntuforums.org/showthread.php?p=437911#post437911](http://www.ubuntuforums.org/showthread.php?p=437911#post437911) it is linked from the other thread mentioned

---

### Post by ThirdWorld on 2005-11-09
Thank you Dr. Nick i cant believe I finally fix this bloody bug!! thank you guys so much you are an amazing community!!  

[http://www.ubuntuforums.org/showpost.php?p=437911&postcount=7](http://www.ubuntuforums.org/showpost.php?p=437911&postcount=7)

---

### Post by iluciv on 2005-11-18
I'm having the same reply after trying to log in . I have followed the tips in these forums and stilll no joy  It goes to log me into the xserver but this is also locked so it returns me to the login screen (I can log into machine though switching to command line) 
But now I stuffed it right up by trying sudo chmod 755 cause now I can't do sweet all

---

### Post by Dr. Nick on 2005-11-18
yeah the sudo really screwed you up I bet. Have you tried to redo the permission without the sudo? Can you still login to your user account through the command line? The dmrc file should not stop xorg from starting

---

### Post by ubuntuthinking on 2005-11-27
OK I've got this problem too - I accidentally messed up the permissions when messing around with my usb drive and transferring files.

My system shows the right permissions - I think, but I stll get the message at login.
"
dd@ubuntu:~$ ls -l ~/.dmrc
-rw-r--r--  1 dd dd 26 2005-10-26 10:23 /home/dd/.dmrc
dd@ubuntu:~$
"

---

### Post by MikeMM on 2007-07-30
don't know if you are all still having the problem but
chmod 644 /home/(replace with username)/.dmrc 
worked for me

---

### Post by Venoseth on 2007-12-31
I had the same trouble... someone helped me fix it here... 

[http://ubuntuforums.org/showpost.php?p=3302702&postcount=2](http://ubuntuforums.org/showpost.php?p=3302702&postcount=2)

hope that helps you too, and thank the poster if it does. ^^

---

