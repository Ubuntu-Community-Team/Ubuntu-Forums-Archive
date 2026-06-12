---
title: "Solution M1210 Dell Hibernation Suspend Fix"
date: 2007-11-22
forum: Hardware &amp; Laptops
---

### Post by SoulZero on 2007-11-22
Hello, everyone! I recently came back to ubuntu and gispy had some problem with beryl/ sleeping.
I decided to go back to fiesty fawn 7.04 which was my favorite ubuntu of all time and it still is after some fixes. After doing all my research I wanted  BERYl / avant window navigator running no matter what & have my ubuntu function like a laptop.

I knew there would be hibernation and suspension issues like before. 
Here's my solution. 

First of all USB2 SWAP did  WORK FOR ME AFTER THIS SETUP!
Make sure you follow  [http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/) direction. simply replacing all the code to just hibernation won't work.

Hence I can stand by with the default. While I have to hibernation with s2disk :).

Step 1: Source :: [http://ubuntuforums.org/archive/index.php/t-428974.html](http://ubuntuforums.org/archive/index.php/t-428974.html)
"PROCEDURE:
Preparation: First of all, you need to have Beryl Manager running, since this fix relies on it. It's that little ruby tray-icon. You should set it to start when you log in, so that it's always running.

First, create the file /etc/acpi/suspend.d/06-beryl-stop.sh with the following contents:
#!/bin/sh

# SIGUSR2 tells it to switch to alternate WM
pkill -USR2 beryl-manager

# and just to make sure beryl dies
pkill '^beryl$'
pkill -KILL '^beryl$'
Then, create the file /etc/acpi/resume.d/97-beryl-start.sh with the following contents:
#!/bin/sh

# SIGUSR2 tells it to switch back to beryl
pkill -USR2 beryl-manager

Now, make both of them executable, and make sure both are owned by root:
sudo chmod +x /etc/acpi/suspend.d/06-beryl-stop.sh /etc/acpi/resume.d/97-beryl-start.sh
sudo chown root:root /etc/acpi/suspend.d/06-beryl-stop.sh /etc/acpi/resume.d/97-beryl-start.sh"


Step 2: (I can't recall the source)
Add Option "NvAGP" "1" to the Device section of xorg.conf
Set "SAVE_VBE_STATE=false" "POST_VIDEO=false" In /etc/default/acpi-support

Step3: 
NOTE now the main problem is I can't login after suspension/hibernation I can't type afterwards. but i can some how alt tab or ctrl+alt+backspace. (the background beryl was running fine).
Hence i decided to skip the log in(The lock screen) & directly go into ubuntu. inorder to do this.

Press alt+f2 & type in gconf-editor

go to apps & gnome power manager

uncheck "lock_on_blank_screen"
"lock_on_hibernation"
"lock_on_suspend"

I tested this twice. With hibernation and stand by and it works fine =]. It's just skips the lock screen where I have issue at the lock screen where I couldn't type.

If anyone have any question go for it.

---

