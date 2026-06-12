---
title: "Create Launcher for .sh"
date: 2008-09-25
forum: General Help
---

### Post by FLCL on 2008-09-25
Hey can someone please explain to me how i go about creating a launcher for a an .sh script?

*Edit* Nvm, i feel silly now haha. But I am having trouble getting this .sh script to work. It is for un-mounting and turning off an external hard drive. I found it here on the forums, someone else used this.

> 1. Create a file named eject.sh with the following contents:

#!/bin/bash
exec 2>&1
pumount $1 || umount $1
sdparm --command=sync $1
sdparm --command=stop $1

2. copy it into root folder

cd Desktop
sudo cp ~/Desktop/eject.sh /eject.sh

3. Create a launcher, which you can either dump on you desktop or have as an option in your main menu. When clicked, your drive will eject and turn off:

Option: run in terminal
command: sudo /./eject.sh /dev/sd* (mountpoint of your drive)

I am having trouble getting the launcher to work, and i do not understand the command line for step 3. The mountpoint of the drive would be under media and then the name of the drive right?

---

### Post by FLCL on 2008-09-25
bump

---

### Post by FLCL on 2008-09-25
Bump

---

### Post by aloshbennett on 2008-09-26
1. Are you able to run in from command prompt?
2. You can pass /media/MyUsbDrive as the argument to the script.
3. Make the script executable
4. Dont copy to '/'(no harm, just not neat) . Copy to ~/bin and add that folder to $PATH env variable. This way, you can access the script from anywhere by typing "eject.sh"
Or, copy the file to ~/scripts and give the command for the launcher as '/home/username/scripts/eject.sh'

First thing is to get it working from command prompt before making a launcher.

---

