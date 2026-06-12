---
title: "HOW-TO choose next reboot partition with GRUB"
date: 2008-10-03
forum: General Help
---

### Post by plh on 2008-10-03
Hi,

I was looking for something that could let me choose next reboot partition (in my case, ubuntu or windows) before shutting down, in order not to be stuck to my PC during GRUB boot phase.

I found many interesting things in an old post by knn, see [http://ubuntuforums.org/showpost.php?p=1786749&postcount=9]("http://ubuntuforums.org/showpost.php?p=1786749&postcount=9"), whom I thank very much for the clarity of his explanations.

Once my "menu.lst / sudoers" modified as indicated (remember to use visudo to edit sudoers), it worked but I still missed a more friendly command to choose from a name and not from a number (the partition rank in menu.lst.

So I wrote this script, which displays the list of existing bootable partitions together with their rank, and let the user choose next boot partition by entering the desired number:

```
#!/bin/bash
######################################################################
#
# $Id: nextBoot 919 2008-10-02 09:24:26Z phil $
# next boot will be partition <parameter> 
#
# for this script to work, 
# 1 - default saved in menu.lst
# 2 - all entries but the default one: savedefault 0
# 3 - default entry: savedefault
# 4 - /etc/sudoers: (cmd visudo) ALL ALL=NOPASSWD: /usr/sbin/grub-set-default 
# 
######################################################################

awk '$1 == "title" { printf "%d: %s\n",n++,$2}' /boot/grub/menu.lst
read ans
sudo grub-set-default $ans

######################################################################

```

Hope it helps ;-)

Plh

---

### Post by caljohnsmith on 2008-10-03
Thanks for sharing the script, I haven't actually tried it yet but it looks quite useful. Just one small comment though--it doesn't look like you have to put the "grub-set-default" command in sudoers set as no password if the user simply runs your script with "sudo". But if you want to let any user run the script without sudo, certainly your way would work. :)

---

