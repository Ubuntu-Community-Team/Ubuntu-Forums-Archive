---
title: "Update manager outdated error"
date: 2008-09-18
forum: General Help
---

### Post by vikramsharma on 2008-09-18
I have an unusual error of Update Manager never updating it's database, I update using Synaptic and Update Manager regularly but always get this error.  The message in the Update Manager states the database to be 146 days old, when just today I installed the latest updates.

---

### Post by iaculallad on 2008-09-18
Seems like your update-success-stamp and update-stamp file are not being updated, On your terminal:

```
sudo touch /var/lib/apt/periodic/update-success-stamp
sudo touch /var/lib/apt/periodic/update-stamp
```

Then retry opening your Synaptics Package Manager.

---

### Post by vikramsharma on 2008-09-18
> **iaculallad said:**
> Seems like your update-success-stamp and update-stamp file are not being updated, On your terminal:

```
sudo touch /var/lib/apt/periodic/update-success-stamp
sudo touch /var/lib/apt/periodic/update-stamp
```

Then retry opening your Synaptics Package Manager.

Thanks for helping me out there, that was really quick.  One more thing do I have to do that manually each time I want to update the update-success-stamp and update-stamp files.

---

### Post by iaculallad on 2008-09-18
> **vikramsharma said:**
> Thanks for helping me out there, that was really quick.  One more thing do I have to do that manually each time I want to update the update-success-stamp and update-stamp files.

Hopefully not if this is the first time you met that annoyance when accessing your Synaptics Package Manager.

Or if you like, you could include the commands posted above in your rc.local file so it gets executed everytime you start your PC. To do this, open your terminal and try to do the following process below:

```
gksudo gedit /etc/rc.local
```

and insert the two commands in the rc.local file:

> touch /var/lib/apt/periodic/update-success-stamp
touch /var/lib/apt/periodic/update-stamp


Output should be like this:

> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

[B][COLOR="DarkRed"]touch /var/lib/apt/periodic/update-success-stamp
touch /var/lib/apt/periodic/update-stamp
[/COLOR][/B]
exit 0

Save and Close the file.

---

### Post by vikramsharma on 2008-09-18
> **iaculallad said:**
> Hopefully not if this is the first time you met that annoyance when accessing your Synaptics Package Manager.

Or if you like, you could include the commands posted above in your rc.local file so it gets executed everytime you start your PC. To do this, open your terminal and try to do the following process below:

```
gksudo gedit /etc/rc.local
```

and insert the two commands in the rc.local file:



Output should be like this:



Save and Close the file.

Thanks a lot for this script, this script would be a great help.

---

