---
title: "[SOLVED] Changing permissions of all files and folders on /home at once"
date: 2008-09-09
forum: General Help
---

### Post by civillian on 2008-09-09
I just did a restore of may hard drive after a hardware upgrade, and I put the backed up files onto my new /home partition on the new hard drive. I did this from live cd mode, and now I've sorted out all the issues with drivers etc. 

I now have the issue of all of the files that I put onto my new hard drive from the backup hard drive I cannot access, because they are owned by root. 

I Can change this one folder at a time, but is it possible to change the permisisons and ownership of all the folders and files on my /home partition (/dev/sda3 for reference)?

---

### Post by iaculallad on 2008-09-09
On your terminal:

```
sudo chmod 700 /home/your_username
```

---

### Post by Rhubarb on 2008-09-09
```
sudo chown -R yourusername:yourusername /home/yourusername/
```
Just please make sure that you don't overwrite the permissions on your **/home/yourusername/.dmrc** file
As I have done so before, and it took a bit of googling for me to fix it up (it causes gnome to crash on login, I can't remember all the details of it though).

---

### Post by civillian on 2008-09-09
--edit--

Thanks rhubarb, it worked like a charm :D I'll just double check the .dmrc file but it should be okay :)

---

### Post by iaculallad on 2008-09-09
> **C!V!NT said:**
> ```
mode of `/home/john' retained as 0700 (rwx------)
```
is what comes up, but I still have vast swathes of files/folders that are owned by root. Can I use chmod to change ownership as well as just permissions?

Yes:

```
sudo chmod -R 755 /home/your_username
sudo chown your_username /home/your_username
```

and for the .dmrc file

```
sudo chmod 644 ~/.dmrc
sudo chown your_username ~/.dmrc
```

---

### Post by civillian on 2008-09-09
Thanks for the help guys, it seems to have worked well (I won't tell if I've messed up the .dmrc until I reboot, but hey ho).

---

