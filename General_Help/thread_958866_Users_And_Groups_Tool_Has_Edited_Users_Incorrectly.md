---
title: "Users And Groups Tool Has Edited Users Incorrectly With Root Access Removed"
date: 2008-10-25
forum: General Help
---

### Post by digiPixel on 2008-10-25
After using the Users And Groups tool with Ubuntu I can no longer use sudo, and any tool where the Unlock button is clicked on. A dialog box pops up with the "Authentication Failed" dialog box when the Unlock button is clicked. Is the dialog box supposed to show at all? Why isn't a more appropriate message displayed to indicate what is really occurring?

These problems started when I added a new user (with full admin/root rights by checking the "Administer The System" option) with the Users And Groups tool. The original user was not adjusted in any way (it by default also had full admin/root rights). With no root access (of any sort) how do I resolve the problem since I cannot login as root :confused:

The Users And Groups tool for some reason decided to automatically deselect the "Administer The System" option under the User Privileges tab (when viewing/editing the properties for a specific user) for all users!

---

### Post by kevstar31 on 2008-10-25
Post the output of **cat /etc/fstab**

---

### Post by drs305 on 2008-10-25
You can run the "groups" command to see if you are still listed in the 'admin' group. If you are not you will not be able to use any sudo-related command.

To get yourself back into the admin group boot to recovery mode. Get to a root terminal by selecting "Drop to root shell prompt": 	
Then run the following:
```
adduser *yourusername* admin
```

---

### Post by geirha on 2008-10-25
That error message is indeed useless, and should really be reported as a bug on launchpad. And the other part were all users lost admin priviledges as well. Which ubuntu release are you running?

Anyway, to fix things, boot into recovery mode (Hit Esc at the boot prompt, and select recovery mode), get to a root shell, then run ```
sudo adduser *user* admin
``` to add *user* to the admin group, which should give that user the ability to use sudo again.

Another thing you should check is the output of ```
grep '^root' /etc/passwd /etc/group
``` which should look like 
```

/etc/passwd:root:x:0:0:root:/root:/bin/bash
/etc/group:root:x:0:

```

The root user and root group must both have an id of 0. If they don't, edit the two files accordingly.

---

### Post by digiPixel on 2008-10-25
I am currently using Ubuntu 8.04 LTS (Desktop Edition).

---

### Post by digiPixel on 2008-10-26
See the attached zip file for the contents of /etc/fstab.

---

### Post by digiPixel on 2008-10-26
Correction, see the attached fstab.tar.gz file for the contents of /etc/fstab.

---

### Post by digiPixel on 2008-10-26
The sudo command works just fine when used on the command line by the admin user. However the dialog still pops up when the Unlock button is clicked on any GUI tool/utility that contains the button. I had to wait close to 1 min before the dialog appeared.

Is there a fix for the GUI tools/utilities that require the use of sudo? I have noticed that the /etc/sudoers file is using a mode of 470 for permissions, is that ok?

---

### Post by geirha on 2008-10-26
/etc/sudoers should have mode 440, and be owned by root:root. Neither the gksu(do) or sudo should work if /etc/sudoers has incorrect permissions, so it's odd that one of them works.

---

