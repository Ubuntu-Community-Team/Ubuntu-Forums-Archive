---
title: "change user name"
date: 2008-09-01
forum: General Help
---

### Post by metalmaniac248 on 2008-09-01
ok,

a few months ago i stopped using my main account called "nick" for various reasons, and i moved everything to my guest account, then made guest administrator, deleted my old account and renamed "guest" to "nick"

so when i log on i type nick as the username

and in terminal it say "nick@nick-laptop"

however my home folder is still called guest 

is there a way of changing this without mucking my entire account up?

thanks

---

### Post by joenix on 2008-09-01
My first advice would be, backup your files before you start moving things around!
Ok, secondly, the location of the home directory can be changed using the Advanced tab under System -> Users and Groups, or you could edit the /etc/passwd file. However, this will only change the location of the home directory, it will not move your files to the new location. Another option is to use the usermod command. The following command will change the home directory and move the files:
```
sudo usermod -d /home/NewHomeDir -m YourUsername
```

where you substitute the homedir and username.

---

### Post by metalmaniac248 on 2008-09-01
where u say substitute do u mean do this 

> 
sudo usermod -d /home/nick/   -m nick

---

### Post by unutbu on 2008-09-01
Yes. That should move your home (and its files) from /home/guest to /home/nick.

---

### Post by metalmaniac248 on 2008-09-01
ok 

i did exactly what you said 

and i belive that it worked however,

now when i try to log in i get a dialog box saying something like,

> acces denied users must own the home directory



????????

---

### Post by unutbu on 2008-09-01
Reboot into recovery mode. This will drop you to a root shell. Then type
```

groupmod -n nick guest              # change name of guest group to nick group in /etc/group
groupmod --gid 1000 nick            # change gid of the nick group in /etc/group
usermod --uid 1000 --gid 1000 nick  # change uid and gid for nick in /etc/passwd
chown -R nick:nick /home/nick

```

---

### Post by metalmaniac248 on 2008-09-01
ok i did wot u said 

now im back into my computer but everythings wrong,


before i had compiz effects running and an emerald theme and i had compiz drawing my desktop not nautilus, however now, 


the resolution is wrong on the screen, i have no compiz effects, and no emerald theme, and nautilus is drawing my desktop again.

wt do i do???



attatched is a screenshot of my desktop if it is of any help

---

### Post by unutbu on 2008-09-01
I'm sorry. If I had anticipated this problem, I would have warned you.

The problem is that programs like compiz (and a lot of other programs) hard code the path /home/guest into their configuration files. 

You have a few options, none pleasant:

[list]
[*]You can redo all your settings. 
[*]You can run the command
```
find ~ -wholename '/home/nick/.*' -exec grep -l '/home/guest' {} \;
```
to find all files that need fixing. You would then have to edit each file listed, changing /home/guest to /home/nick
[*]You can move your home account back to /home/guest by running```

sudo usermod --home /home/guest -m nick
```
[/list]

---

### Post by metalmaniac248 on 2008-09-02
i chose the third option, and changed the home directory back to guest,

now i have the home folder not being owned by the user issue again,

im not quite sure how to modify that command you showed me earlier,



PS. whats the command to restart from recoery mode, last time i just had to press the power button

---

### Post by metalmaniac248 on 2008-09-02
erm, just incase i wasnt clear enough, i think i need this

```

groupmod -n nick guest              
groupmod --gid 1000 nick            
usermod --uid 1000 --gid 1000 nick  
chown -R nick:nick /home/nick
```


but the other way around beause i have changed the home folder back to guest.

---

### Post by unutbu on 2008-09-02
First, the easy part: to get to recovery mode, reboot the machine and press ESC to bring up the GRUB menu.
Use the arrow keys to select "recovery mode".


Now, your current problem is perplexing. The command
```

sudo usermod --home /home/guest -m nick
```

should have moved your home account back to /home/guest, but the ownership of the directory and its files should have remained being nick. You shouldn't have had any problem with ownership.

If you wish to keep the username nick: perhaps try
```
sudo chown -R nick:nick /home/guest
```

If you wish to change your username back to guest:
```

sudo usermod --login guest nick
sudo groupmod -n guest nick              
sudo groupmod --gid 1000 guest            
sudo usermod --uid 1000 --gid 1000 guest  
sudo chown -R guest:guest /home/guest
```
The sudo is necessary if you are running the commands as nick, but if you are in recovery mode you can drop the sudo or keep it, it would not matter.

If the above does not work, please post
```

ls -ld /home/guest
grep 'nick\|guest' /etc/passwd
grep 'nick\|guest' /etc/group
```

---

### Post by metalmaniac248 on 2008-09-02
im still having the ownership issues, and obviosly cant log on,


as i uderstand it i have now made the user name guest, and the home folder is guest again. 
/
so why would there be ownership issues

---

### Post by unutbu on 2008-09-02
Can you boot into recovery mode? If so, 
please do so and post the output of

```

ls -ld /home/guest
grep 'nick\|guest' /etc/passwd
grep 'nick\|guest' /etc/group

```

---

### Post by metalmaniac248 on 2008-09-02
ls -ld /home/guest
```

drwxr-xr-x 92 1001 guest 4096 Sep  1 21:29  /home/guest
```





grep 'nick\|guest' /etc/passwd
```

guest : x : 1000 : 1000 : Nick,,,, : /home/guest/ : /bin/bash
```




grep 'nick\|guest' /etc/group

```
adm : x : 4 : guest
dialout : x : 20 : cupsys, guest
fax : x : 21 : guest
cdrom : x :24 : haldaemon , guest
floppy : x :25 : haldaemon , guest
tape : x : 26 : guest
audio : x : 29 : guest
dip : x : 30 : guest
plugdev : x :46 : haldaemon , guest
scanner : x : 104 : cupsys , hplip , guest
admin : x : 117 : guest
fuse : x : 119 : guest
nick : x : 1000 :
guest : x : 1000 :
```

---

### Post by unutbu on 2008-09-02
Boot into recovery mode. Type
```
nano /etc/group
```
remove the line that says
```

nick:x:1000:
```

save and exit.

At the shell prompt type
```
chown -R guest:guest /home/guest
```
Hopefully, you should then be able to log in as guest.

---

### Post by metalmaniac248 on 2008-09-02
erm, i removed that line but when i type ^X and press enter ( to exit) nothing happens

---

### Post by metalmaniac248 on 2008-09-05
has anyone experienced this where you can not exit the "nano/etc/group" thing.

---

### Post by Elfy on 2008-09-05
Ctrl+O then enter to save and exit or Ctrl+X to exit and be prompted to save.

---

### Post by metalmaniac248 on 2008-09-07
Finally, its fixed thanks to all of you


:)

---

