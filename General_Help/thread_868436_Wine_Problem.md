---
title: "Wine Problem"
date: 2008-07-23
forum: General Help
---

### Post by minhdinh on 2008-07-23
i unistalled wine but i still have a problem. wine is still listed on my computer under the applications bar and all the programs i tried installing with wine is still listed there too, but all the programs and wine are deleted/uninstalled from my computer. i want to know how i can completely remove the wine section from my applications because its already deleted from my computer

---

### Post by tamoneya on 2008-07-23
use the purge option in terminal(applications -> accessories -> terminal)
```
sudo apt-get remove --purge wine
```

---

### Post by minhdinh on 2008-07-23
the purge command did not worked i got this message when i tried it 


minh@minh-laptop:~$ sudo apt-get remove --purge wine
[sudo] password for minh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-backports-modules-2.6.22-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
minh@minh-laptop:~$ 
minh@minh-laptop:~$ 


wine is still listed under my applications along with all the subfolders. please tell me wat else to do

---

### Post by tamoneya on 2008-07-23
okay first lets remove all the wine files: ```
rm -r ~/.wine
```
Then we remove it from the menu.  Right click on "applications" and select "edit menus".  In the left panel of this window make sure applications is selected and then look in the right half and uncheck wine.

---

### Post by minhdinh on 2008-07-23
thanks that worked. and when i reinstalled wine again and rechecked the box in the edit menu, it cleared all of the old programs and subfolders that are no longer on my computer

---

### Post by tamoneya on 2008-07-23
glad to help.  Dont forget to mark the thread solved in the thread tools menu.

---

