---
title: "upgrading through a clean install"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by ubiqe on 2008-12-22
Hello,
I would like to upgrade from 7.10 to 8.10 but without doing partial upgrades... In fact, I cannot get the upgrade manager to work properly so I thought it better to get rid of Gutsy Gibbon and install from scratch. 
I have a dual boot with Vista running on a separate partition (Ubuntu is on 2 - swap and root+home). Will it be ok if I simply format the Ubuntu partitions from gparted and then install 8.10? Will it mess anything if I resize the partitions after formatting (I need more space for Vista)? While browsing the forums I found something about windows mbr file - what is it and will I need to fix it at any point?

Any help will be appreciated :)

---

### Post by DieB on 2008-12-22
if u install your ubuntu it should take care about other systems.

as home and root are on the same partition u would lose all your data if u format that partition (there is also an opportunity to install without reformatting, but mostly caused trouble for me). So u might follow this link:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

while u do this take a look at your partitioning-table, where u could get the space for vista.

[INDENT]Before u start to reinstall, open synaptic, and mark the installed (on bottom left there are some buttons, one says status -click this and then choose installed) to be reinstalled (you can simply mark one in the list press ctrl-a right click on the selection and mark for reinstallation)  and save that (File-save marked) to your desktop. [if  all this takes some time don't worry].
This should make it easier to get all your apps in place again.[/INDENT]

when u reinstall mark the created home as home again (be aware that u mark it for NOT been reformated) and use the same username as u already got and all should look and feel similar to before.

Feel free to ask.

---

