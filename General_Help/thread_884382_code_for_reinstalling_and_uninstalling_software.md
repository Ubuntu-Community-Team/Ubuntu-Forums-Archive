---
title: "code for reinstalling and uninstalling software?"
date: 2008-08-08
forum: General Help
---

### Post by raylistic87 on 2008-08-08
Hi guys, 
```
sudo rpm -ivh --nodeps AWCommon-10.80-15.x86_64.rpm Maya2008_0_64-2008.0-134.x86_64.rpm
```

if sudo rpm -ivh --nodeps install those 2 files, but are the code to uninstall or reinstall files?

Thanks!

:confused:

---

### Post by bdfoster on 2008-08-08
You could go to the Package Manager and uninstall them.

---

### Post by raylistic87 on 2008-08-09
> **bdfoster said:**
> You could go to the Package Manager and uninstall them.

The wierd thing is I cannot find it in the package manager.

---

### Post by the real omni on 2008-08-09
I'm fairly new to Ubu and haven't used RPM's before at all but whenever I want to uninstall/reinstall something I use 

```

sudo apt-get remove (package)

and

sudo apt-get reinstall (package)

```

See [this thread](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html) for details. (Section 3.3 - Removing Packages / Section 4.4 - Upgrading Packages) 

Not sure if this applies to RPM packages but I thought I'd throw it in there.

---

### Post by raylistic87 on 2008-08-09
> **the real omni said:**
> I'm fairly new to Ubu and haven't used RPM's before at all but whenever I want to uninstall/reinstall something I use 

```

sudo apt-get remove (package)

and

sudo apt-get reinstall (package)

```

See [this thread](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html) for details. (Section 3.3 - Removing Packages / Section 4.4 - Upgrading Packages) 

Not sure if this applies to RPM packages but I thought I'd throw it in there.

Any idea where i can get the name of the package? Cause i tried typing the name and it says couldn't find package. Usually where to they put the files that we install? Any idea on the directory? 

Thanks for the help so far.

Ray

---

### Post by jocko on 2008-08-09
> **raylistic87 said:**
> Hi guys, 
```
sudo rpm -ivh --nodeps AWCommon-10.80-15.x86_64.rpm Maya2008_0_64-2008.0-134.x86_64.rpm
```if sudo rpm -ivh --nodeps install those 2 files, but are the code to uninstall or reinstall files?

Thanks!

:confused:

If you installed it with rpm, it will not be picked up by the package manager (the package managment in ubuntu is based on apt/dpkg from debian, not rpm from redhat). 
I'm not sure how it should be done, but you should probably be able to use rpm to uninstall it.
The "correct" way to install a .rpm package in ubuntu (if you really can't find a .deb package or even source code), is to first use the program "alien" to convert it to a .deb and then use dpkg to install it. That way you would be able to uninstall it through synaptic.

---

### Post by cariboo on 2008-08-09
You should use rpm to remove the packages you installed. The way you should have installed the packages is to use alien to convert the packages to .deb:

```
alien -d packagename.rpm
```

To remove your alien rpm packages use:

```
rpm -e packagename.rpm
```

Jim

---

### Post by raylistic87 on 2008-08-09
thanks guys. I found this which helps me alot. 

[http://www.idevelopment.info/data/Unix/Linux/LINUX_RPMCommands.shtml]("http://www.idevelopment.info/data/Unix/Linux/LINUX_RPMCommands.shtml")

Basically they are RPM commands.

---

