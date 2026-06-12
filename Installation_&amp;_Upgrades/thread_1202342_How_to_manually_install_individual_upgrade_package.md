---
title: "How to manually install individual upgrade packages"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by g003y on 2009-07-02
I just installed and upgraded mu Ubuntu from 8.10 to 9.04 and one of the packages failed to install during the update process and I want to try to re-install it manually. It was the kernel 2.6.29.4 package (I'm not 100% sure of the version number right now).

What happened was that the boot menu (/boot/grub/menu.lst) has become cluttered with different versions of Linux from all prior upgrades so I commented out most items from it (by adding #). The installation software didn't like my changes so it prompted me of what action to take next. To say the least I found the options quite confusing and after choosing one it hung right in the middle of the installation. I xkilled it and entered 'exit' in the terminal (in the installation dialogue) and the update continued seamlessly with the exception of this failed package.

What I can do is to revert to the unmodified version of the menu.lst, re-apply the kernel update package and then change it back after it's done but I don't know how to do that.

---

### Post by lindsay7 on 2009-07-02
Look in your boot/grub directory for a file like menu.lst.backup or something similar. Click on it to open it and look at the contents. If this is a back of your menu.lst file, you can type the following in the terminal to edit that file. It would be something like this...

sudo gedit /boot/grub/menu.lst.backup


You need to save the file with the new name being menu.lst, is should ask say that you already have a file with that name and ask if you want to overwrite it.  You should change the name of the current menu.lst file ,using the gedit command, first to be safe. Change it to something that you will remember like menu.lst.old so that if you have trouble you can rename it and get back to where you are starting from. In case everything goes wrong doing this you can reboot from the live cd and change the menu.lst.old back to menu.lst and go from there.

---

### Post by g003y on 2009-07-02
Thank you for your reply lindsay. It's not a big deal for me to manage the menu.lst file. The question I have is how do I reinstall the kernel 2.6.29.4. package manually ?

---

### Post by kilowattradio on 2009-07-02
> **g003y said:**
> Thank you for your reply lindsay. It's not a big deal for me to manage the menu.lst file. The question I have is how do I reinstall the kernel 2.6.29.4. package manually ?

Install midnight commander (mc) from the command line:
```
sudo apt-get install mc 
sudo mc /var/cache/apt/archives/

```
Find the package with the kernel in it and you can use copy F5 to copy the files in the package to the directory indicated. In the .deb file you navigate to CONTENTS and you can follow the installation path for each item. 

One thing you could also try first is to just make a blank menu.lst item in /boot/grub and see if it will install
```

sudo mv /boot/grub/menu.lst menu.lst-old
sudo touch /boot/grub/menu.lst

```

dpkg force install

This next example shows a command to force an install, ignoring dependencies and other problems: 

```
sudo dpkg --install --force-all packagename 
```


In this case, dpkg will install the package while printing a lot of error messages. In general, forcing an install is not a wise thing to do. A package which has been force-installed without its dependencies is said to be "broken". Broken packages may lead to instability. Package management tools such as synaptic will refuse to work further until they are allow to fix the broken package. So why would you resort to a force-install? 



HTH

---

### Post by kilowattradio on 2009-07-02
> **g003y said:**
> Thank you for your reply lindsay. It's not a big deal for me to manage the menu.lst file. The question I have is how do I reinstall the kernel 2.6.29.4. package manually ?

```
sudo apt-get install mc 
sudo mc /var/cache/apt/archives/

```
Find the package with the kernel in it and you can use copy F5 to copy the files in the package to the directory indicated. In the .deb file you navigate to CONTENTS and you can follow the installation path for each item. 

One thing you could also try first is to just make a blank menu.lst item in /boot/grub and see if it will install
```

sudo mv /boot/grub/menu.lst menu.lst-old
sudo touch /boot/grub/menu.lst

```
HTH

---

### Post by g003y on 2009-07-02
Thanks alot, that's what I was looking for.

When I search through the packages I cannot find any kernel package. If my memory isn't deluding me it was kernel 2.6... that failed to install.

When doing a further search with mc I find that "linux-...   .deb" might be the packages where the kernels are located. The strange thing is that the latest version number of these packages is 2.6.28.13 and not 2.6.29-4.

---

### Post by g003y on 2009-07-04
I just found out where to find the kernels. They are located at
 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
 
As of today the latest (by date) version is 2.6.29.6 either I download and open the .deb packages using Synaptics package manager or I fetch them using:
 
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)...
sudo dpkg -i <packagename.deb>

---

