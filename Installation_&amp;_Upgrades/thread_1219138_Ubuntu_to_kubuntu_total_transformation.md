---
title: "Ubuntu to kubuntu total transformation"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by trevongilpin on 2009-07-21
When I install kubuntu  from the disk, I can not install my proprietary drivers (nvidia gt120/internal wireless g pci card). So I have to take the long way around and install ubuntu, get the drivers and transform it into kubuntu. Well...I did that and i removed all gnome applications to do a total transition, not have both GUI's. Apparently the kde desktop install didnt install the kde version of synaptic package manager or add/remove programs manager, but i removed the gnome versions. Is there any fix for this? Right now I cant add/remove programs or reinstall kde-desktop as i dont have a package manager. HELP!

---

### Post by amingv on 2009-07-21
Are you able to use apt-get or aptitude from the terminal?

If that's the case, you can easily do

```
sudo aptitude install <package_name>
```

for example

```
sudo aptitude install adept
```

for Kubuntu's default package manager.

Also, did you open the proprietary drivers manager in Kubuntu? (Under system settings) I have installed drivers with it and had no problems...

---

### Post by trevongilpin on 2009-07-21
Thank you very much. Code worked like a charm (i was doing gnome commands...lol). For some reason the kde proprietary drivers didnt pick up my video card, and wouldnt download the wirless card driver. I know, it doesnt make sense to me either. However, i still cant find the package manager thingy in the system settings menu. shouldnt there be something there along with adept, or is it only adept?

Ok, adept installed, but i am getting an error message: Could not obtain a write lock on the cache, falling back to read-only mode. You won't be able to install, remove or upgrade packages. However, you can still search in the package database and browse packages.
It appears that another process is running, which holds the write lock on the database. You first need to close that program and then restart Adept to gain write access.

Update: For some reason, that was just a temporary error. write lock or whatever and such is now avaliable, but i cant get my system updates to work. Which is why I'm really thinking that there is another program that i need. The one that is in the system settings menu. I dont know how to get it though. ANY HELP WELCOME!

---

### Post by amingv on 2009-07-21
Tell you what... maybe you'd like to do

```
sudo aptitude install --with-recommends kubuntu-desktop
```

That will install kubuntu and all of it's recommended packages. I believe it will be a lot easier just to remove unnecesary programs later than going mix and match now...
Please notice, however, that this command may take a lot of time to complete.

Also remember that only one program may install software at a time. Make sure no other package managers are running while you use adept.

---

### Post by trevongilpin on 2009-07-21
I did that code and no packages were installed. Thank you though, regardless of if it worked or not. I appreciate the fact that you are helping me. True open-source community mindset. A+ for you. lol.

```
 No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
 
```

---

### Post by trevongilpin on 2009-07-21
I thank you for your help, and greatly commend you for it. You came from heaven to save my linux experience! I have found the final fix to the problem. Thanks to you though, i recieved my very large and complicated (to me) means to an end. A triple plus times 10 to the power of 5 for you!

---

### Post by HeadHunter00 on 2009-12-02
sudo apt-get install kubuntu-desktop

---

