---
title: "New graphics card gives Fatal error: screen not found."
date: 2013-12-08
forum: Hardware
---

### Post by Biopyro on 2013-12-08
I just installed a NVIDIA Gforce 6800 GT into my PC running ubuntu 12.04. Now when I boot up it goes to tty-1 and gives a "Fatal error: screen not found." when I type startx

I tried 
[FONT=Ubuntu Mono]apt-get install nvidia-current[/FONT]
and it said
"the package lists or status file could not be parsed or opened"
although it is connected to the internet.
sudo apt-get update gave the same error
I then used this fix `sudo apt-get update` but it gave the same error again.

W: Not using locking for read only lock file /var/lib/dpkg/lock

and a whole load of other failed messages


Is this just a case of the drivers not being installed? 

If you need any files then let me know but I will have to give a photo

---

### Post by Yellow Pasque on 2013-12-08
You've got two issues. The first thing is you need to fix the package manager. See: [https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure#Step_5_List_of_Terminal_commands_to_execute](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure#Step_5_List_of_Terminal_commands_to_execute)

After that, hopefully, it will be a simple matter of installing nvidia driver package and rebooting.

---

### Post by Biopyro on 2013-12-09
apt-get seemed to update fine when I tried again but I am still getting the same error, despite nvidia current apparently being up to date. Any suggestions?

Could it be linked to one of my drives (partitions?) not mounting?

I also tried logging into my windows 7 partition and got a "display out of range" error, even in safe mode.

[ATTACH=CONFIG]248459[/ATTACH]

---

