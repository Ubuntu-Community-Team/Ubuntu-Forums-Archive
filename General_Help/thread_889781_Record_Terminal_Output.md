---
title: "Record Terminal Output"
date: 2008-08-14
forum: General Help
---

### Post by Eviltechie on 2008-08-14
I was going to run the my flight sim that I bought. I run it from the terminal because it works best. But when I ran it today it spewed a whole lot of text about read only, the last line being segmentation fault. It is several pages of text, too much for the terminal to display at once. I need to report this bug, but I can't include the full output. (running it as root works fine, but I don't want to do that)

This is the command I used to run it.
ivan@ivan-ubuntu:/opt/X-Plane/X-Plane 9.00 Beta-1$ ./X-Plane-i686

---

### Post by jerome1232 on 2008-08-14
Try it like this
```
./X-Plane-i686 >x-plane.log
```

this will instead of displaying information on the terminal, slap it all into a file called x-plane.log

edit: If running it as root solves the problem then I think you just don't have write access to it's directory. Now I'm not sure what you NEED access too, but running the following command will give ALL users write access to /opt/X-Plane and should solve the problem. If it does perhaps a better solution would be in order.
```
sudo chmod -o+w /opt/X-Plane
```
better solution
Maybe make the directory owned by root, and in the group x-plane.
give members of the group x-plane rw (read/write) and of course make sure the binary has x (excecute permisions) then add users you want to run this game to the x-plane group.
check out
```
man chmod
man chown
```
for details on how to do that, ask questions if your not sure

---

### Post by Eviltechie on 2008-08-14
I was thinking that, but because the permissions are wrong, I would have to run that command as root, but then the problem that I want to log wouldn't happen. I need that file to be written somewhere else.

---

### Post by jerome1232 on 2008-08-14
then run it as ./X-Plane-i686 >~/x-plane.log

---

### Post by Eviltechie on 2008-08-14
That helped, but the log is still cut off. It ends with (Wind when it should be (Windows machines typically do this).

/opt/X-Plane/X-Plane 9.00 Beta-1/Output/logbooks/X-Plane Pilot.txt

Could the file be flagged as read-only? This happens in Windows if you copy it from a CD!

Try putting this app in the background and then flag the file as NOT read-only, or creating the folder listed in the path above.

---

### Post by jerome1232 on 2008-08-14
Can you post the output of
```
ls -l /opt/X-Plane/X-Plane 9.00 Beta-1/Output/logbooks/X-Plane Pilot.txt
```

---

### Post by Eviltechie on 2008-08-14
ivan@ivan-ubuntu:/opt/X-Plane/X-Plane 9.00 Beta-1$ ls -l /opt/X-Plane/X-Plane 9.00 Beta-1/Output/logbooks/X-Plane Pilot.txt
ls: cannot access /opt/X-Plane/X-Plane: No such file or directory
ls: cannot access 9.00: No such file or directory
ls: cannot access Beta-1/Output/logbooks/X-Plane: No such file or directory
ls: cannot access Pilot.txt: No such file or directory


This is the contents of the file.
I
1 version
2  80721    KRDU     23W   2   0.1   0.0   0.0   0.1    YF19  1  Japanese Anime
2  80722     W14    6NC5   1   0.1   0.0   0.0   0.1    YF19  1  Japanese Anime
99

---

### Post by jerome1232 on 2008-08-14
so the file doesn't even exist, perhaps try creating it like the error said, Do the guys that make X-Plane have a guide for installing it? Have you had it working at all?

---

### Post by Eviltechie on 2008-08-14
The file exists, and this is the contents of the file.
I
1 version
2 80721 KRDU 23W 2 0.1 0.0 0.0 0.1 YF19 1 Japanese Anime
2 80722 W14 6NC5 1 0.1 0.0 0.0 0.1 YF19 1 Japanese Anime
99 

It is a permissions error b/c it runs fine as root.

---

### Post by jerome1232 on 2008-08-14
ok I guess you don't even have read access then, just chown the whole directory to your own user then. Replace your username here
```
sudo chown -R user:user /opt/X-Plane
```

of course if you have multiple users it would be best to do it like I said earlier and give it it's own group and add users to that group. of course replace <user> with the real usernames that you want to give access
```
sudo addgroup xplane
sudo chown -R root:xplane /opt/X-Plane
sudo chmod -R ug+rwx,o-rwx /opt/X-Plane
sudo adduser <user> xplane

```

logout then log in so the permissions take affect (adding yourself to a new group) and it should work

---

### Post by Vivaldi Gloria on 2008-08-14
Note that "script" can record terminal. To start recording use:

```
script
```

To stop recording use

```
exit
```

The output is saved to 

```
typescript
```

file in your home folder.

---

### Post by Eviltechie on 2008-08-14
The adduser thing worked. Thanks

---

### Post by jerome1232 on 2008-08-15
Hey that script program is pretty nice, it creates some garbage in text editors but from the man pages I can send the file to a printer.

---

### Post by Vivaldi Gloria on 2008-08-15
> **jerome1232 said:**
> Hey that script program is pretty nice, it creates some garbage in text editors but from the man pages I can send the file to a printer.

There are a number of ways to get documents out of man pages. I prefer

```
man -Tps program > program_man.ps
```

For example

```
man -Tps nano > nano_man.ps
```

saves the man page of nano as nano_man.ps. Now open the ps file with evince and print.

Google "printing man pages" for other methods.

---

