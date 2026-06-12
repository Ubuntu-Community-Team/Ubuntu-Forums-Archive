---
title: "ok, Now how do I Restore my /home folder???"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by morbid_bean on 2009-11-04
I backed up my /home folder and all the folders in it to my external hard drive...  installed a fresh 9.10 and aparantly its not as easy as copying it back and overwriting the current /home folder....what do i need to do? 

Thanks!

---

### Post by jjcv on 2009-11-04
I usually do it this way:

In a terminal

cd /backupfolder  {to the external drive folder where your backup is]

the run the following command

find . -print | cpio -pdmua /home/[name]

where [name} is the name of your home directory.

Once finsihed you might have to make sure the permissions are correct as follows:

cd /home

chown -R [name] [name]

There are other ways also using rsync etc.

If you get any issues with permission denied then prepend the above commands with sudo  ie.

sudo find . -print | cpio -pdmua /home/[name]

---

### Post by scared0o0rabbit on 2009-11-05
I'm about to do this myself actually (back up my home folder that is) so that I can install 9.10 on a clean install.  If I do this, will it in general keep all my settings and favorites and all that?  In particular, should I expect it to backup my firefox favorites and the plugins I have installed?  Also, with the wine programs I have installed, is backing up my .wine folder enough to ensure that when I restore it all my programs will work again?  I know for instance in windows you'd have issues with the registry, but is there some kind of pseudo registry in the .wine folder that gets backed up also, or would it be best to just try and re-install all my software?

---

### Post by irishbreakfast on 2009-11-05
Unless you have moved things around yourself all your configurations will be in /home/<yourname>. You can confirm by browsing your home folder. Firefox files are in the directory .mozilla. 

The config directories (preceeded with a dot '.') are hidden by default. To see them with the nautilus browser, use Ctl-H, to toggle the hidden files on/off. Alternatively, you can open a terminal and use "ls -a" although I like "ls -la".

As for wine, I installed it once and never spend the time to learn how to use. But it does create ".wine". 

Hope that helps.

---

### Post by jjcv on 2009-11-05
> **scared0o0rabbit said:**
> I'm about to do this myself actually (back up my home folder that is) so that I can install 9.10 on a clean install.  If I do this, will it in general keep all my settings and favorites and all that?  In particular, should I expect it to backup my firefox favorites and the plugins I have installed? ......

Yes, once you copy everything back to your home folder, check the permissions and reboot everything should work as normal.

When I do a backup I also like to keep a copy of /etc as there are some important system config files there that you might want in the future.  Not being sure what you are running cannot say much more.

---

### Post by scared0o0rabbit on 2009-11-05
I would just be going from 9.04 to 9.10.

---

### Post by Dullstar on 2009-11-05
Open your backed up home folder, and copy the contents.
Paste them into your new one.
Note:  It may work to copy the contents of /home/, but I recommend using the contents of /home/[your username here]/

---

### Post by flavanoid on 2011-01-14
I realize this is a slightly old thread but... does copying your home folder and fixing permissions still work if you're moving it to another machine with a different hardware configuration?

---

