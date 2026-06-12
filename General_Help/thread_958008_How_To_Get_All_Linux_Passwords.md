---
title: "How To Get All Linux Passwords"
date: 2008-10-24
forum: General Help
---

### Post by Isilion on 2008-10-24
Hi!! I dont know if this should be in tips & tutorials, security or here; im not a linux guru, nor a hacker xD and how do i discovered it, was more an experience. 
I was on my Institute. During playtime, between class and class you can use some public pcs near the library. I turned one on, and surprisily it shown a Grub. Lol, it has ubuntu installed, i told myself. Great, i can use it instead windows!!
I choose one Kernel and boot starts. Login screen. Uh ohh... great... i dont know the user or the password...
...but...
Afortunately, last week I picked up from the library an old Linux manual, with the luck that its debian based (but i dont know if other way should be different, FORGIVE MY IGNORANCE)
I found the exact commandline in the book. So i rebooted into recovery mode, to gain Root login automatically, and once in console, typed:

# cat /etc/passwd 

It shows a large textfile and if you look carefully you will see all login accounts and their passwords, separated by commas. ;)

I think its not really a hack, as you must be fissicaly in front the computer. Its more like a way to recover passwords if in a pc you dont know or you forgot. The experience was unbelievable, when i gained acces to the desktop i felt really good. Linux makes you feel like that. xD

---

### Post by solitaire on 2008-10-24
> **Isilion said:**
> Hi!! I dont know if this should be in tips & tutorials, security or here; im not a linux guru, nor a hacker xD and how do i discovered it, was more an experience. 
I was on my Institute. During playtime, between class and class you can use some public pcs near the library. I turned one on, and surprisily it shown a Grub. Lol, it has ubuntu installed, i told myself. Great, i can use it instead windows!!
I choose one Kernel and boot starts. Login screen. Uh ohh... great... i dont know the user or the password...
...but...
Afortunately, last week I picked up from the library an old Linux manual, with the luck that its debian based (but i dont know if other way should be different, FORGIVE MY IGNORANCE)
I found the exact commandline in the book. So i rebooted into recovery mode, to gain Root login automatically, and once in console, typed:

# cat /etc/passwd 

It shows a large textfile and if you look carefully you will see all login accounts and their passwords, separated by commas. ;)

I think its not really a hack, as you must be fissicaly in front the computer. Its more like a way to recover passwords if in a pc you dont know or you forgot. The experience was unbelievable, when i gained acces to the desktop i felt really good. Linux makes you feel like that. xD


Ermm....

It does not show my password....

I suggest you reinstall, you're copy my be compromised...

---

### Post by scragar on 2008-10-24
It won't show passwords, the passwords are hashed...

And it's /etc/shadow on most modern systems.

---

### Post by doas777 on 2008-10-24
indeed. passwd does have account info, and in years past it also had the passwords (locked to root access only), but nowadays everything is encrypted and placed in shadow.

---

### Post by Isilion on 2008-10-24
Dont forget to run in recovery mode. Ive tryed in three computers now, and in all worked (2 Ubuntu 8.04, 1 Xubuntu 8.10 with latest kernel). 

It simply works :)

---

### Post by scragar on 2008-10-24
huh?

```
cat /etc/passwd | grep scragar
scragar:x:1000:1000:scragar,,,:/home/scragar:/bin/bash
```
I'm going to say right now that my password isn't listed there.

---

### Post by Isilion on 2008-10-25
I rebooted and typed again, and watch more careful. Youre right, not pass showed there (really i tryed the command in 3 computers, but only gave access to the one i speak of in the thread)
login and pass where 'administrador' in a Spanish install.

---

### Post by scragar on 2008-10-25
Well back on the early versions security wasn't observed as being important(infact, on the very earlest version there were no passwords at all), so being able to see the admin password on an old system is just another reason for a person to update.

---

### Post by Isilion on 2008-10-25
i believe that the kernel version was 2.6.18. Is old enough to have that security failure?

im a noob, i recognise it. But i really thought it was possible. Think in this case: You buy a 2nd hand computer with linux installed and full operational, but vendor forgets to tell you the login/pass, and its Sunday and you want to use it right now... This method will be a way (or perhaps the only?:S) to know that, isnt it?

If this way is not possible in newer versions, i suggest, in order to trully answer the theard's theme, someone could post whats the actually way to gain access to a pc, wich belongs to you, or you 'legitimately' can get access, but dont remind account?

---

### Post by Isilion on 2008-10-25
I took a look to the manual. Its printed in 2001 and is based on Linux Debian. 

file /etc/passwd : This file contains user's name, ENCRYPTED password (think its the x in my pc  isilion:x:blahblahblah..,,,isilion or something like that), User ID (UID), Group ID (GID), the name, the home directory, and the shell.

file /etc/shadow : contains user's name, ENCRYPTED password, dates of when change password, etc. 

file /etc/group : group name, ENCRYPTED password, GIDs, user's list separate by commas.

Then it explains few commands. Ive read at all, not tells how to remind passwords at all, but i think that can try something.:

Reboot as recovery mode to gain root privileges.

#useradd -d -g ? -s anonym (? should be a group name or a GID. In my /etc/group there are root:x:0 and adm:x:4:isilion. So i think that ? may be substituted with 0,4,adm or root, no?)

(this should create a user named anonym, with homedir and shell. in adm or root group, and without password)

Im gonna try this. perhaps it works.

---

### Post by Isilion on 2008-10-25
Finally, i rebooted in recovery mode, and type:

#useradd -d /home/anonym -g 4 -s /bin/bash anonym

(previosly created /home/anonym directory)And then:

#passwd anonym

and set the password. Continued normal boot and attemped to login as anonym... login ok, but it give some errors due to some permissions. After all, i can launch failsafe terminal logged as anonym. I think this has a fix, but im not too deep into linux. ill continue reading the book...
(I think i am learning with this.. and perhaps it becomes useful a day. what im trying to do is: if there is no way to know a password in linux, its possible to create a new user with root privileges? but im afraid of messing with root group. but, if i type 

#useradd -d /home/anonym -g 0 -s /bin/bash anonym 

i will not gain root privileges? :S

---

### Post by scragar on 2008-10-25
I think you need to add the user to the group admin:
```
# useradd -G admin **username**
```

---

### Post by Isilion on 2008-10-25
Thx i will try it now. Hey i've noticed that threads have been moved, and tags changed. What means yellowpress? :s

---

### Post by Isilion on 2008-10-25
It give the same errors. they are related to a file: $/HOME/.dmrc

it says it must be in user's group and have permissions 644.

i think that the chown, chgrp and chmod commands are related. but what is that file supposed to be?

---

### Post by ciscosurfer on 2008-10-25
Could be the Delhi Metro Rail Corporation [http://www.delhimetrorail.com/index.htm](http://www.delhimetrorail.com/index.htm)

---

### Post by scragar on 2008-10-25
> **Isilion said:**
> It give the same errors. they are related to a file: $/HOME/.dmrc

it says it must be in user's group and have permissions 644.

i think that the chown, chgrp and chmod commands are related. but what is that file supposed to be?

not sure what it is, but you can fix that:
```
TEHUSER=**username**
chown -R $TEHUSER:$TEHUSER /home/$TEHUSER
chmod -R 644 /home/$TEHUSER
chmod go-rw /home/$TEHUSER/.dmcr
```

---

### Post by ciscosurfer on 2008-10-25
May as well throw this [SOLVED] Ubuntu Forums Thread into the mix: [http://ubuntuforums.org/showthread.php?p=5591464](http://ubuntuforums.org/showthread.php?p=5591464)

---

### Post by Greyed on 2008-10-25
> **Isilion said:**
> i believe that the kernel version was 2.6.18. Is old enough to have that security failure?

No, for two reasons.

One, it has nothing to do with the kernel.

Two, it was addressed long before Linus every wrote one line of code for the kernel whence spawned Linux.

---

### Post by cyfur01 on 2008-10-25
Since you've mentioned earlier that you can gain root permissions via the recovery mode, why not overwrite the password of one of the existing users and give them sudo permissions, thus giving yourself access to an account with full sudo privileges?

If you're have write permissions on /etc/shadow, then generate an MD5 hash of a password like this:```
echo "r00tme" | mkpasswd -s -H MD5
```You can then paste this over the password of one of the existing users, and then you should be able to log in as them. If you want to be really discrete, copy the old MD5 hash into another file so you can revert to the old password later after properly creating a new user (this way if that person ever tries to log on, they'll have their old password).

After that, you should be able to run "visudo" to give yourself sudo permissions. (Note that this is based upon an old version of vi. You can open /etc/sudoers with vim or gedit as well, but if you mess up the file, you could really screw things up. visudo checks things before saving). Then add the user you hijacked to this file:```

# User privilege specification
hijacked  ALL=(ALL) ALL

```
This should give them full sudo permissions, meaning you can log on to a normal x-based session and start exploring.

(Can you tell I've played with this stuff before?)

---

### Post by Greyed on 2008-10-25
If you have root access why go through all that subterfuge to get root access?  ...  You have root access!  Besides, in the first case why make an MD5 has of something to paste into shadow when you can passwd user and have the tool do it for you.  Or why copy/paste old hashes back into place when you can create a new user, edit passwd and give that new user the uid of the person you're trying to mimic.  Once you have root there's no need to be kludgy about it.

---

### Post by K.Mandla on 2008-10-25
Unusual thread. I'm not really sure what's being discussed, but it has me entertained, that's for sure.

Moved to General Help.

---

### Post by dburnett77 on 2008-10-25
mine's "linux", there's one...

---

### Post by Dr Small on 2008-10-25
> **K.Mandla said:**
> Unusual thread. I'm not really sure what's being discussed, but it has me entertained, that's for sure.

Moved to General Help.
Certainly indeed.

---

### Post by Isilion on 2008-10-25
> **cyfur01 said:**
> Since you've mentioned earlier that you can gain root permissions via the recovery mode, why not overwrite the password of one of the existing users and give them sudo permissions, thus giving yourself access to an account with full sudo privileges?

If you're have write permissions on /etc/shadow, then generate an MD5 hash of a password like this:```
echo "r00tme" | mkpasswd -s -H MD5
```You can then paste this over the password of one of the existing users, and then you should be able to log in as them. If you want to be really discrete, copy the old MD5 hash into another file so you can revert to the old password later after properly creating a new user (this way if that person ever tries to log on, they'll have their old password).

After that, you should be able to run "visudo" to give yourself sudo permissions. (Note that this is based upon an old version of vi. You can open /etc/sudoers with vim or gedit as well, but if you mess up the file, you could really screw things up. visudo checks things before saving). Then add the user you hijacked to this file:```

# User privilege specification
hijacked  ALL=(ALL) ALL

```
This should give them full sudo permissions, meaning you can log on to a normal x-based session and start exploring.

(Can you tell I've played with this stuff before?)

I think this works. i had to edit sudoers long ago, when something messed and my account dissappeared frokm there. I wasn't able to use sudo nor su.. and so looked at google for help. Im not sure, but i think there was a way of editing sudoers that makes that linux not ask you passwords, isnt it? think it was uncommenting the line "%sudo ALL=NOPASSWD: ALL". Its brute but perhaps is what im looking for. **Note: uncommenting that line have serious bad security cons... 
Editing sudoers with vim was a pain in the ***. (inst there any console ascii editor more like EDIT of msdos?)


> **Greyed said:**
> If you have root access why go through all that subterfuge to get root access?  ...  You have root access!  Besides, in the first case why make an MD5 has of something to paste into shadow when you can passwd user and have the tool do it for you.  Or why copy/paste old hashes back into place when you can create a new user, edit passwd and give that new user the uid of the person you're trying to mimic.  Once you have root there's no need to be kludgy about it.


what i want its just gettin deep into linux and im learning by tryal&error. Its a good way since i have problems with my ATI Radeon (read [http://ubuntuforums.org/showthread.php?t=955783](http://ubuntuforums.org/showthread.php?t=955783) for details) and im waiting with a clean install of intrepid someone to help me, even ATI Support Spain.I have nothing to loose, as i got nothing valuable in my XUbuntu Partition.
im imagining the case i lost a windows password. since im more experienced i think i could do anything. But not in linux. So i want to know how to fix it before it happens and i have something really valuable in the comp. ;)
I wouldn't have to mess with adding an account and giving root permissions if it where possible to launch X in recovery mode and continue logged as root.

---

### Post by Dr Small on 2008-10-25
> **Isilion said:**
> doers with vim was a pain in the ***. (inst there any console ascii editor more like EDIT of msdos?)


Just saying that is enough to start a war over... especially with me.

---

### Post by Isilion on 2008-10-25
Im referring.. that at first for some reason vim doesnt lets you write the file (someone told me i must press -i or something to INS :S) and as it work with commands (:q,:w,:x, :qw etc) its difficult to understand for someone that never has used it, plus doesn't know he commands. :P

---

### Post by cyfur01 on 2008-10-26
Vim isn't that hard once you've practiced with it a bit. If you're really keen, you can always read a book like [this (link)]("http://proquest.safaribooksonline.com/9780596529833") which covers every gorey detail of vim.

Very basically, once you open vim, hit "i" to enter text, and then when you're done, hit escape, and then type ":wq" to write your changes and quit. You can also exit with ":q!" which will exit without saving changes.

I have to say vim remains one of my favorite editors for simple things. vi, on the other hand, I don't like... at least the versions from openwrt and etc, which I find are much less accessible than vim, and can be frustrating (especially since it doesn't recognize the DEL key).

> ... Besides, in the first case why make an MD5 has of something to paste into shadow when you can passwd user and have the tool do it for you...
Good point about just using passwd... I always find hard ways to do simple things.

---

### Post by ukera on 2008-10-26
the best way to get your password back is to just boot up, go into recovery mode, then click go to shell as root.  type in 

[PHP]passwd yourusername[/PHP]
then it will ask for the new password that you want and then you put it in.  or you can simply delete the password with;
[PHP]passwd -d yourusername[/PHP]

-ukera

---

