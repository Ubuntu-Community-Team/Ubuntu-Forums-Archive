---
title: "tried giving myself full permission.. goofed up.."
date: 2008-11-11
forum: General Help
---

### Post by hadoken82 on 2008-11-11
i couldnt delete files in the trash bin said i didnt have permission ect.  so i figured id go in and give myself full power.  its my own laptop afterall. well i couldnt really figure out how to do it so i went into my user and tooke out the /home/whatever

and i put /root  thinking it would give me same access as root.  which im assuming is access to everything.

well the computer loads gives me random missing files while loading and then i sit and stare at a blank default ubuntu background.  

so i restarted the computer and got into the recovery menu.  i clicked on "root" to go into the shell prompt.

and if i can fix it from here.  once it goes back to normal how do i get around not having permission to delete something in the trash bin?  it doesnt even ask for my PW  just said the generic dont have permission or whatever.

which shows... root@john-laptop:~#

im new to ubuntu so i have no clue how or what the commands would be to put my access back to the original setup. of /home

any help would be appreciated.

Update Here are the Errors im receiving.
First Eror while it loads

"User's $Home/.dmrc file is being ignored. blah blah file should be owned by user and have 644 permissions.  User's $home directory must be owned by user and not writable by other users."

2nd error

" Could not update ICEauthority file /root/.ICEauthority"

3rd Error is problem with COnfiguration server.

is it possible to login as say the root? and go in that way and fix it?  i was able to ctrl-alt-delete and bring up the log off screen so i logged off.  and im sitting at the main login screen.  is there a default root account i can log into?  if so is the user name just Root?  and what would be the default pw? if any?

---

### Post by LateNiteTV on 2008-11-11
yeah u messed up a bit. you dont want permission to change everything on your system. it IS your laptop, but clearly you dont know what youre doing and WILL mess things up... like you have.

login as root and change your home directory back to the original. 

if you MUST do something that you dont have permission to do, use sudo, or su to become root.

---

### Post by taurus on 2008-11-11
Did you really remove/delete your $HOME directory?  Or did you just either move or rename it?

---

### Post by LateNiteTV on 2008-11-11
> **taurus said:**
> Did you really remove/delete your $HOME directory?  Or did you just either move or rename it?

no, im pretty sure he  just replaced his /home/whatever with /root.

---

### Post by cariboo on 2008-11-11
To run as root use in a terminal:

```
sudo -i
```

this will drop you th a root shell and will continue until you log out using Ctrl-d or you close the terminal.

To run Natilus (Places-->Home Folder) press Alt-F2 and type:

```
gksu nautilus
```

This will open Nautilus as root and you can manipulate files any way you want.

To repair the /home/user/.dmrc problem in a terminal type

```
sudo chmod 640 .dmrc 
```

To fix the .iceauthority problem use Alt-F2

```
gksu Nautilus
```

to navigate to /root and delete the file, files with a dot at the start of the name are hidden, so to view them press Ctrl-h.

I not sure what you mean about Configuration server, so I can't suggest anything.

The root user is disables in Ubuntu, using sudo is safer and has all the power of a root user.

Jim

---

### Post by hadoken82 on 2008-11-11
all i did was when you go to the advanced properties in the users

there was Root and John

if you click one and go into the advanced options it shows like /home/john?  i guess i forget.  i remember the /home part.

well i look at the root and seen it said /root

so i just type that in place of the /home  under the user john.

did that delete it?  or is the user uh shell/ whatever just trying to find something that isnt there now?

and im not quite sure what the command in the recorvery console would be to put it back as /home/john is that was it originally.

i just started ubuntu about 2-3 days ago.  only thing i have accomplished is i installed wine. and got updates and did a few basic sudo commands.

---

### Post by hadoken82 on 2008-11-11
> **cariboo907 said:**
> To run as root use in a terminal:

```
sudo -i
```

this will drop you th a root shell and will continue until you log out using Ctrl-d or you close the terminal.

To run Natilus (Places-->Home Folder) press Alt-F2 and type:

```
gksu nautilus
```

This will open Nautilus as root and you can manipulate files any way you want.

To repair the /home/user/.dmrc problem in a terminal type

```
sudo chmod 640 .dmrc 
```

To fix the .iceauthority problem use Alt-F2

```
gksu Nautilus
```

to navigate to /root and delete the file, files with a dot at the start of the name are hidden, so to view them press Ctrl-h.

I not sure what you mean about Configuration server, so I can't suggest anything.

The root user is disables in Ubuntu, using sudo is safer and has all the power of a root user.

Jim\


Thanks ill try to slowly accomplish these tasks heh.

---

### Post by hadoken82 on 2008-11-11
> **LateNiteTV said:**
> no, im pretty sure he  just replaced his /home/whatever with /root.

yes exactly.

---

### Post by LateNiteTV on 2008-11-11
no, it didnt delete it, it just replaced it in /etc/passwd or wherever ubuntu stores that crap.

you dont have permission to change things in /root. so why do you think that by changing your home directory to /root would allow you to do so? do you know what root is?

---

### Post by hadoken82 on 2008-11-11
> **LateNiteTV said:**
> no, it didnt delete it, it just replaced it in /etc/passwd or wherever ubuntu stores that crap.

you dont have permission to change things in /root. so why do you think that by changing your home directory to /root would allow you to do so? do you know what root is?

not really.  i just read stuff people saying root is like the all access to everything prompt.

---

### Post by hadoken82 on 2008-11-11
> **cariboo907 said:**
> To run as root use in a terminal:

```
sudo -i
```

this will drop you th a root shell and will continue until you log out using Ctrl-d or you close the terminal.

To run Natilus (Places-->Home Folder) press Alt-F2 and type:

```
gksu nautilus
```

This will open Nautilus as root and you can manipulate files any way you want.

To repair the /home/user/.dmrc problem in a terminal type

```
sudo chmod 640 .dmrc 
```

To fix the .iceauthority problem use Alt-F2

```
gksu Nautilus
```

to navigate to /root and delete the file, files with a dot at the start of the name are hidden, so to view them press Ctrl-h.

I not sure what you mean about Configuration server, so I can't suggest anything.

The root user is disables in Ubuntu, using sudo is safer and has all the power of a root user.

Jim



i tried each of those command and the sudo 640 command gave me a no such file or directory.

im currently in the recorvery Menu using the Root shell Ormpt.  when i try the gksu nautilus it says cannot open display.

when i hit alt-f2 it just went to a black screen with a flashing cursor but nothing would work.

i mean i guess i can wait till home and re-install ubuntu.  but ill learn better if im able to actually correct this lol.

right now im looking at root@john-laptop:~#  on this shell promp in the recovery

---

### Post by taurus on 2008-11-11
Did you really change your $HOME directory from /home/john to /root?  What's the output of this command?

```
cat /etc/passwd
```

---

### Post by hadoken82 on 2008-11-11
> **taurus said:**
> Did you really change your $HOME directory from /home/john to /root?  What's the output of this command?

```
cat /etc/passwd
```

i typed it exactly    cat /ect/passwd

said no such file or directory

---

### Post by taurus on 2008-11-11
> **hadoken82 said:**
> i typed it exactly    cat /**[COLOR="Blue"]ect[/COLOR]**/passwd

said no such file or directory

It's 

```
cat /**etc**/passwd
```

---

### Post by hadoken82 on 2008-11-11
> **taurus said:**
> It's 

```
cat /**etc**/passwd
```\

oops k type it right this time.

a lot of stuff showed up.  
last line

John:x:1000:1000:john,,,:/root:/bin/bash

that should be : X  stupid face popped up when there together

---

### Post by taurus on 2008-11-11
> **hadoken82 said:**
> 

John:x:1000:1000:john,,,:**[COLOR="Blue"]/root[/COLOR]**:/bin/bash


That's your problem.  You need to edit /etc/passwd

```
nano -Bw /etc/passwd
```
and replace the /root with /home/john so it would look something like this.

```
John:x:1000:1000:john,,,:**/home/john**:/bin/bash
```
Save it by holding down <Ctrl> while pressing x and then enter Y for the question.  Now, reboot and see if you can log back in to your original $HOME, /home/john.

---

### Post by hadoken82 on 2008-11-11
i type it in rebooted.  and its loaded up.  it told me i needed to run in the failsafe mode.  its showing me logged into john user group.  

in the users groups its shows Home/john under home directories.

when i click on properties though.  and i dont change anyhting and just click ok it shows an error message

"incomplete path in home directory 
Please enter full path for home directory
I. E : /home/john"

---

### Post by Denestria on 2008-11-11
to change your home directory back to what it should be

```
sudo usermod -d /home/john john
```

john = whatever your username is

---

### Post by hadoken82 on 2008-11-11
im trying to load the terminal and when i do it shows it loading then dissapears

is there something i still must do?

it looks like its back to normal.  my screen saver i originally had is working ect.  though Computer and another Icon is missing form the desktop that was there.

it also wont let me drop icon to the desktop they just dissapear and when i click on the shutdown or reboot nothing happens also.

---

### Post by hadoken82 on 2008-11-11
i fixed it all :)  thanks for the help guys/girls.

i checked the user groups.  and it was home/john instead of /home/john after the editing.

a lot of trial and error.  but heh ILL never forget how to fix the issue again if someone else gets it :P

---

### Post by theacerguy on 2009-01-05
just for reference if your new to linux dont play with root it is way dangerous  you can delete anything including system files prior to ubuntu

UNLESS YOU HAVE TO DONT PLAY WITH ROOT

my message is clear

---

### Post by doooley on 2009-02-11
> **Denestria said:**
> to change your home directory back to what it should be

```
sudo usermod -d /home/john john
```

john = whatever your username is
thanks! this totally fixed my problem!

---

