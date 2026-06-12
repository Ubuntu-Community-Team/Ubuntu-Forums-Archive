---
title: "questions about VirtualBox"
date: 2008-09-28
forum: General Help
---

### Post by LidanJericho on 2008-09-28
VirtualBox - x86 virtualization.

I check this program on Wiki and i saw this "VirtualBox is the third most popular software package for running Windows programs on Linux desktops"

what i wanna ask it's, if i can load operations like crysis (Games) and programs like Windows Live Messenger and other stuff.

thanks for any help.

---

### Post by ju2wheels on 2008-09-28
Yes to Windows Messenger and other typical productivity apps. No to video games and any other applications that require 3D acceleration as its not supported in Virtual Machines.

---

### Post by jigsaws on 2008-09-28
I think you are looking for something like wine, not VirtualBox. 

Virtual Box is for virtualization - install operating system (Linux, Windows, etc) on virtual machine and run programs on this virtual system.

The other thing is performance ;-)

---

### Post by ju2wheels on 2008-09-28
Yes thats true, Wine has better performance but only because its not running a second operating system. Wine also will not be compatible with all your Windows applications. So if you have a fast machine and have a Windows CD, VirtualBox is a great solution to install a regular version of Windows and Windows applications and have it work as you expect. The alternative is to check to see if the application you want to use is supported by Wine (winehq.org) and install it on Linux.

---

### Post by GeoffreyBernardo on 2008-09-28
Gentlemen,

So can I install virtual box on linux and run windows xp inside virtualbox without having to restart the computer and boot windows xp from another partition?

Thanks.

---

### Post by ju2wheels on 2008-09-28
Hi GeoffreyBernardo, yes that is the purpose of VirtualBox. It allows you to run Windows on top of Linux without having to reboot or repartition your hard drive. The Windows partition is turned into a file on your Linux partition and is run out of VirtualBox.


This is demonstrating an older version of VirtualBox but its still the same thing: [http://www.youtube.com/watch?v=lA52Y7I2hCE](http://www.youtube.com/watch?v=lA52Y7I2hCE)

---

### Post by ajgreeny on 2008-09-28
You will, I think not be able to run the same copy of windows xp in virtual and actual installations as both need to be activated and that is not possible as MS will tell you that the particular copy is already in use.  There may be ways to get around that, but I don't know how.

---

### Post by zzzzz1 on 2008-09-28
@ ajgreeny

I dont think this is correct.
This is how Microsoft would like it to be but in reality it works just fine installing multible times XP (dont know about Vista )

---

