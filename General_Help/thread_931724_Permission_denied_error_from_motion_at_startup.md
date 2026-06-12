---
title: "Permission denied error from motion at startup"
date: 2008-09-27
forum: General Help
---

### Post by t0nt042 on 2008-09-27
I got motion setup and had it running with no issues on 8.04, until I added it to my session. Now, when the session starts I can check the system log and see that it is giving me permission denied errors and failure to create folder errors. Once all the cameras fail to write,the process quits. 

The target directory is the users home directory, and if I run motion in the terminal once the login is complete, I have no issues. Any ideas?

---

### Post by lian1238 on 2008-09-27
What if you put "sleep 10 && " in front of the command in the session. It means wait 10 seconds before continuing.

---

### Post by t0nt042 on 2008-09-27
Unfortunately, that didn't seem to help. I tried increasing the delay to 60 for giggles and it didn't help either.

---

### Post by lian1238 on 2008-09-27
You could try creating a script for it. Create a new file and name it 'startmotion.sh' or something. In the file, put:
```

#!/bin/bash

sleep 20 && motion
# assuming motion is the command you use

```Then go to the properties of that file (alt+enter or right-click->properties). Under Permissions, check 'Allow executing file as program'. Then put this script in the session startup.

If that doesn't work, then I guess you could make a launcher on your panel and run it everytime you start..?

---

### Post by t0nt042 on 2008-09-28
The delay method doesn't seem to be working. To give people a little more insight, this computer will likely not be connected to keyboard/monitor and will only be accessed through vnc. Using a launcher is an undesirable solution as I'm hoping the system to be independent of user interaction for the most part.

---

### Post by lian1238 on 2008-09-28
You could try putting the script into /etc/init.d/ directory. Here's the link:

[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

Edit:
another link:
[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)
Go down to Installing custom init-scripts

Here's a good example:
[quote=samyboy]
 			You can use update-rc.d for start-only or stop-only scripts
 Start my script on startup :
# update-rc.d -f my_script start 99 2 3 4 5 .
 where
- start is the argument given to the script (start, stop).
- 99 is the start order of the script (1 = first one, 99= last one)
- 2 3 4 5 are the runlevels to start
 Dont forget the dot at the end
More info in /etc/rcS.d/README
 Start my_script on shutdown and reboot :
# update-rc.d -f my_script start 90 0 6 .
 Stop my_script on halt and reboot :
# update-rc.d -f my_script reboot 90 0 6 .
 If you want to make your own demon, you can use the skeleton file provided at
/etc/init.d/skeleton
 about runlevels :
 To know which runlevel you are running, simply type
$ runlevel
  more info about runlevels here : [http://oldfield.wattle.id.au/luv/boot.html#init](http://oldfield.wattle.id.au/luv/boot.html#init)
happy scripting[/quote]

---

### Post by t0nt042 on 2008-09-28
When that failed with the same result, I decided to setup a crontab to make sure the process was going once every hour. In the end, this is probably a better solution in the event that the process stops. 

Thank you for trying lian, it seems I'll never know whats causing this oddity, but at this point, I'm fine with that.

---

### Post by lian1238 on 2008-09-28
Even the script failed? It's supposed to execute with super user powers..

Oh well, glad you found a way. You won't have multiple instances, right?

---

