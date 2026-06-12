---
title: "lock and permissions"
date: 2008-11-27
forum: General Help
---

### Post by Tucatts on 2008-11-27
I copied a file from a DVD onto the desktop. It has a lock and now I can't access permission to delete it or move it. I have right clicked and gone to properties and permissions. I changed the access to read and write and then closed but nothing happens and the change I made under properties does not stay. What am I missing here? 
Thanks

---

### Post by Idefix82 on 2008-11-27
If we assume that your file is called myfile then open the terminal and do
```
cd Desktop
sudo chown $USER:$USER myfile
sudo chmod 755 myfile
```
always providing your password when asked for it. See if that helps.

---

### Post by Tucatts on 2008-11-27
no joy. right clicking on properties and changing permissions to read and write should work as well but it just does not for whatever reason.
Thanks for trying to help

---

### Post by stoneage on 2008-11-27
Try changing it in nautilus?

```
gksudo nautilus
```

Be careful what you do there though, you have root permissions.

Or try changing its permissions and owner as root.

---

### Post by neu2buntu on 2008-11-27
i had this problem before ,cant rem exactly how i got it sorted  you could try code: chmod 777 (yourfile) as root or sudo.. this gives read,write and execute to the file(full permissions)

---

### Post by Idefix82 on 2008-11-27
> **Tucatts said:**
> no joy. 

What exactly do you mean by that? What happens when you execute these commands?

---

### Post by neu2buntu on 2008-11-27
read=4 , write=2 , execute=1   chmod is change access permissions   .so you chmod plus add the numbers up for what access you want eg. 6 will be read and write    and you use the three numbers after the chmod command for user,group and others..

---

### Post by geirha on 2008-11-27
You do not need write permissions to the file in order to delete it. You do need write permission to the directory it's contained in though. That means that either your Desktop folder isn't writeable to you, or there's a filesystem error. 

Do you have write access to your Desktop folder? Check the properties from nautilus or run something like this in a terminal:
```
xdg-user-dir DESKTOP | xargs ls -ld
```

---

### Post by neu2buntu on 2008-11-27
im learning here too.... i think i need a bit more experience before i give out too much advice!!!

---

### Post by Tucatts on 2008-11-28
This is Intrepid and I can't seem to get gksudo nautilus to work. Have used this with Hardy and other versions with no problems to change permissions. 
When I use gksudo nautilus I get the following info:
Return error 255, net usershare: cannot open usershare directory. Ask system admin to enable user sharing. This seems to be the cause of my problem I think. So how do I enable user sharing?
Thanks!

---

### Post by stoneage on 2008-12-06
I don't know if that is the problem, but right click on the folder and select Sharing Options. You will probably be told that the sharing service is not installed.

cd to Desktop and post the result of ```
ls -l
```

---

