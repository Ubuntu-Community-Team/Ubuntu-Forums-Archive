---
title: "Wine help!!!"
date: 2008-08-11
forum: General Help
---

### Post by Dan7356 on 2008-08-11
Hi, i just recently switched from Windows to Linux this week all is going well i have just been setting everything up the way i want. i installed Wine it worked fine then i changed my home directory to another partion, Wine then stopped working i have been trying to reinstall it but when it reinstalls the Wine menu doesnt apear in the applications menu and i cant run any windows programs :(

Can anyone please help me???

---

### Post by Ryadt on 2008-08-11
Go in System > Preferences > Main Menu and click on revert. This might solve it.

---

### Post by ajgreeny on 2008-08-11
Just a thought:  when you changed your /home partition, how did you move all the files from the first to the second partition?  If you just copied them or click dragged with nautilus, it is possible that you didn't also move all your hidden folders and therefore the .wine folder in your old /home did not get moved.

---

### Post by Dan7356 on 2008-08-11
i moved all my hidden files and folders but i have jest realised that my home folder is owned by the root user so i am now getting an error when i log in i think this maybe the problem, ive have been trying to change the owner of the home folder but it always changes back almost instanly :( now what?

---

### Post by ajgreeny on 2008-08-11
To change owner use ```
sudo chown -R username:username /home/username
```but change where I've put **username** to whatever your username is, of course.  Do this in recovery mode if needed, or simply go to a console in your usual login.  You may also need to change the permissions of the home by using ```
sudo chmod -R 755 /home/username
```but that may not be needed.

---

