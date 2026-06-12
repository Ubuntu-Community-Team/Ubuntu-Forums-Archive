---
title: "New to Linux, problems getting started!"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by grandkodiak on 2009-05-09
I downloaded the windows installer for the latest ubuntu and it ran fine, i set a password and set the install to 30gb (im assuming this is the partition size it wants to make?)... everything went fine, and it said reboot.
 
i rebooted, got the prompt to pick windows or ubuntu, i select ubuntu, it loads a nice little graphic and then goes to a black screen that says "busybox" or something like that and leaves me at a command prompt with the prompt being (initramfs): and a message above it saying type help to see useable commands.
 
i checked every folder there is like root, usr, bin, etc and none of them seem to have anything that is "run-able" to start the ubuntu gui! (gnome or x i think?)
 
what am i doing wrong? i tried typing "root" to log in but it doesnt seem to be valid, and the root folder only has another folder in it called cdrom.
 
anyone?
 
here are my basic specs if that matter!
 
2 250gb hd's in raid 0 ntfs with vista ultimate installed (where i chose the 30gb install location from in wubi)
1 1tb hd ntfs for storage/backup
asus p5w dh deluux board w/4gb ddr sys ram
2 ati radeon crossfire x1900 videcards
usb mouse/keyboard
use mb for ethernet/sound so there really arent any other major hardware components...
 
thanks all!

---

### Post by damis648 on 2009-05-09
Busybox is a fallback shell when Ubuntu cannot start correctly. Try the following:
Press 'e' at the Ubuntu option at the bootloader. Go down to the second line and press 'e' again. Backspace and remove the words 'quiet' and 'splash' from the end of the line, then press enter, followed by 'b'. Wait for busybox to show up again, and post any errors that appeared right before it.

---

### Post by apparle on 2009-05-09
I some times get that problem. Wait for around 30 sec and then type 'exit'
That works for me.
If that doesn't work for you then you can try what 'damis648' said.

---

### Post by grandkodiak on 2009-05-09
I press esc and get 5 options to edit, none of them have those words listed in them.
 
The list is:
 
Normal mode
Safe graphic mode
acpi workarounds
verbose mode (think thats what it said)
demo mode
 
i looked at each and none of them have that listed inside.
 
also noticed... i tried the "safe graphics mode" option and instead of all black i get white text while loading, and the last lines it says are "sr1 cdr drive not ready make sure a cd is in the drive" or something like that and it goes to the same command line after.
 
 
 
 
and typing exit does nothing, it will just hang for a few minutes and let you type whatever you want before it comes back to the initramfs promt.

---

### Post by grandkodiak on 2009-05-10
anyone? id like to get this up everyone talks about ubunto and i dont feel like waiting another 2 weeks for the new fedora!

---

### Post by grandkodiak on 2009-05-14
update... have gotten this far now... halts here indefinatly:
 
 
[IMG]http://68.37.131.101/linux%20boot.jpg[/IMG]

---

