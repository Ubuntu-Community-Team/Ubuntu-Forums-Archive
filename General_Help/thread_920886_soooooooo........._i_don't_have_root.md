---
title: "soooooooo......... i don't have root"
date: 2008-09-15
forum: General Help
---

### Post by schimm1 on 2008-09-15
yeah i have no root, i don't how it happened, i just tried to do some admin something and it didn't do anything

i thought i fixed the problem, but when i try and boot it says: "The GDM user 'gdm' does not exist. Please correct GDM configuration and restart GDM."

so that sucks

and i reeeeaaaally don't want to reinstall

---

### Post by prince_niceguy on 2008-09-15
login in the recovery mode and then you should be able to fix the problem by adding a new user named gdm if it is not there already.

---

### Post by whizbaby on 2008-09-15
> **schimm1 said:**
> yeah i have no root
welcome to ubuntu :) no really, root is somewhat disabled. If you want to do an admin command, try 'sudo' in front of it and give your login password when it asks for a pass, e.g.
```
sudo apt-get dist-upgrade
```
> 
 i thought i fixed the problem, 

What exactly did you do? Its unlikely to be able to break the system without root privileges. And, like mentioned above, everything is ok with no root login.

---

### Post by schimm1 on 2008-09-15
> **prince_niceguy said:**
> login in the recovery mode and then you should be able to fix the problem by adding a new user named gdm if it is not there already.

how?

---

### Post by schimm1 on 2008-09-15
> **whizbaby said:**
> welcome to ubuntu :) no really, root is somewhat disabled. If you want to do an admin command, try 'sudo' in front of it and give your login password when it asks for a pass, e.g.
```
sudo apt-get dist-upgrade
```

What exactly did you do? Its unlikely to be able to break the system without root privileges. And, like mentioned above, everything is ok with no root login.

before, when i did anything with sudo via terminal, it said something along the lines of "no passwd for root". so i went into a live cd and followed some the instructions [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/archive/index.php/t-3575.html") (the part for editing etc/passwd and shadow). now i sortof have root but still get the gdm error

---

### Post by whizbaby on 2008-09-15
Aww man, not realy...
that dusty thing is super duper old and its about a guy who accidentially(!?!) deleted (!!!!!??) his root account (oopZiedaisy).
Did *you* delete your root account? No? Then why follow hints from a completely different problem?
Ok, so you edited passwd/shadow and now its not working anymore? The easiest and possibly less time consuming thing would be to reinstall. Plus you will have a non-broken system (who knows what will disappear next :p).

---

### Post by schimm1 on 2008-09-15
> **whizbaby said:**
> Aww man, not realy...
that dusty thing is super duper old and its about a guy who accidentially(!?!) deleted (!!!!!??) his root account (oopZiedaisy).
Did *you* delete your root account? No? Then why follow hints from a completely different problem?
Ok, so you edited passwd/shadow and now its not working anymore? The easiest and possibly less time consuming thing would be to reinstall. Plus you will have a non-broken system (who knows what will disappear next :p).

ugh, i suppose you're right, but i had some good pr0n, er i mean important business documents on that i need to keep. but i think i'll do just that, but i'll back everything up. i've needed a bigger hardrive for a while now...

---

### Post by schimm1 on 2008-09-15
> **whizbaby said:**
> welcome to ubuntu :) no really, root is somewhat disabled. If you want to do an admin command, try 'sudo' in front of it and give your login password when it asks for a pass, e.g.
```
sudo apt-get dist-upgrade
```


i get "sudo: no passwd entry for root!"

---

### Post by whizbaby on 2008-09-15
What, *after* a clean reinstall?

---

### Post by schimm1 on 2008-09-16
> **whizbaby said:**
> What, *after* a clean reinstall?

no i haven't reinstalled, wait, can i reinstall without wiping?

---

### Post by mb_webguy on 2008-09-16
It depends...  How did you partition your drive when you installed the first time?  If you created a separate home partition, then you won't lose any data with a reinstall as long as you don't do something silly like reformat your home partition.

---

### Post by cariboo on 2008-09-16
I don't suppose you made backups of the files you changed?

Jim

---

### Post by forger on 2008-09-16
You just go and boot from live cd again, edit etc/passwd and add this line:
> root:x:0:0:root:/root:/bin/bash

Also, if you edited with gedit (text editor), there is a chance you have a good backup, so check out for a etc/passwd~ file (with a "tilde" at the end)

---

### Post by schimm1 on 2008-09-16
> **mb_webguy said:**
> It depends...  How did you partition your drive when you installed the first time?  If you created a separate home partition, then you won't lose any data with a reinstall as long as you don't do something silly like reformat your home partition.

no, i put it all on one partition.

---

### Post by schimm1 on 2008-09-16
> **cariboo907 said:**
> I don't suppose you made backups of the files you changed?

Jim

the changes were minimal, just added a line, no need to create a total backup

---

### Post by schimm1 on 2008-09-16
> **forger said:**
> You just go and boot from live cd again, edit etc/passwd and add this line:


Also, if you edited with gedit (text editor), there is a chance you have a good backup, so check out for a etc/passwd~ file (with a "tilde" at the end)

i have the backup with the tilde

> **cariboo907 said:**
> I don't suppose you made backups of the files you changed?

Jim

the changes were minimal, no need to create a backup if i remember everything i did

> **mb_webguy said:**
> It depends...  How did you partition your drive when you installed the first time?  If you created a separate home partition, then you won't lose any data with a reinstall as long as you don't do something silly like reformat your home partition.

nope, put it all on one

---

### Post by whizbaby on 2008-09-16
---outdated---window-open-too-long---sry----.-

---

### Post by schimm1 on 2008-09-16
SUCCESS! sort of, i have root, but it still doesn't have any GUI, just a strange unix version of dos

i'm still getting the GDM error

---

### Post by whizbaby on 2008-09-16
Hmm I dont know if that works but since the system is broken anyways you could try to add user gdm manually like **prince_niceguy** suggested.
The command would be:
```
sudo adduser gdm
```
but wait a second. The group id and the user id of gdm could be important. Mine are uid=107(gdm) gid=116(gdm) groups=116(gdm)

so you would have to

```
sudo adduser --no-create-home --uid 107 --gid 116 --disabled-password --disabled-login gdm
```

I am not quite sure if the numbers are the same on every system (but I strongly suspect them) so I'd like to ask you to wait until at least another user (yes thats one of those reding this) has cross-checked with

```
id gdm
```

I am also not so sure about the login disabled option, but why would gdm need to login? Anyone with a clearer look?

---

### Post by schimm1 on 2008-09-16
if i login as my normal username and password through the dos like thing i can enter startx and i'll get to the GUI but i have no root, not even through terminal
> 
```
:

id gdm

```
I am also not so sure about the login disabled option, but why would gdm need to login? Anyone with a clearer look?


when i enter id gdm it says no such user

---

### Post by whizbaby on 2008-09-16
Whats perhaps easier (but i didnt think of it first) is trying to reinstall the whole desktop stuff

```
sudo apt-get install ubuntu-desktop --reinstall
```

---

### Post by mb_webguy on 2008-09-16
> **schimm1 said:**
> SUCCESS! sort of, i have root, but it still doesn't have any GUI, just a strange unix version of dos

That's both the saddest and funniest thing I've read all day...

---

### Post by schimm1 on 2008-09-16
> **whizbaby said:**
> Whats perhaps easier (but i didnt think of it first) is trying to reinstall the whole desktop stuff

```
sudo apt-get install ubuntu-desktop --reinstall
```

i did that, it asked me for the password, which i changed to a wildcard, and nothing happened, i just get the schimmi@ubuntu:~$

did i mention that if i enter startx after login i get the gui but no root?


EDIT


i'm also getting a lot of fails at startup, "user syslog does not exist, aborting," "start-stop-daemon: user 'klog' not found/(success)" "shown: invalid user: 'messagebus'/*Starting OpenBSD Secure Shell server sshd/Privelage seperation user sshd does not exist"

(/ is a new line)

---

### Post by llebegue on 2008-09-17
Time for a global re-install I think !

---

### Post by forger on 2008-09-17
schimm1: you're missing the whole point of Ubuntu.
You are an administrator, you have the privileges of root by typing:
```
sudo command
```
or if you want to be "root" all the time with your user's home:
```

sudo -s
echo $HOME
```
or if you want to be root with root home dir:
```
sudo -i
echo $HOME
```

You see, you login normally with your schimmi username & password, then gain your root privileges using the sudo command

---

### Post by meganox on 2008-09-17
> **schimm1 said:**
> SUCCESS! sort of, i have root, but it still doesn't have any GUI, just a strange unix version of dos

If you don't even know what the shell is called, I think you need to slow down when doing admin tasks, or you are going to bork your system again and again.  You say you don't need to make backups when you just changed one line, but it's far easier to restore one file from the command line than it is to open a text editor when you have lost your GUI, or your root account, or can't boot at all.  Most text editors will automatically back up the file with the name and a tilde (~) added, but it will overwrite this every time you save the file, so it is best to manually back it up.

I'd suggest you reinstall, beause God knows how much damage you've done to your system already, then create a normal user account for yourself and another one for testing.  Then go and do some basic unix shell tutorials untill you understand it a bit better.  If you don't give your test account admin priviledges then the worst you can do is mess up that account.

And NEVER run a command as root unless you understand what it is going to do and you are sure you have typed it correctly.

---

### Post by meganox on 2008-09-17
> **forger said:**
> if you want to be "root" all the time with your user's home:
```

sudo -s
echo $HOME
```

This doesn't just give you your user's home, it gives you their entire environment.  This is unpredictable and insecure.  ALWAYS use ```
sudo <command>
``` for a single command and ```
sudo -i
``` for a root shell, and exit that shell as soon as you can.  Nothing else is safe.

---

