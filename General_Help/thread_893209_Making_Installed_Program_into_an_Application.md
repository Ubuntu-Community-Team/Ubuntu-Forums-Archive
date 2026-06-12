---
title: "Making Installed Program into an Application"
date: 2008-08-18
forum: General Help
---

### Post by Paul Baumann on 2008-08-18
How do I make a program executable?
The program dc which is a RPM Calculator is listed as being installed on my system. The executable file is in /usr/bin but only the "root" has permission to use / or assign others. How do I make this (and others) available for use as an Application.
Thanks for your help.
Paul

---

### Post by Thingymebob on 2008-08-18
Only root needs write permissions so:
```
sudo chmod 755 /usr/bin/*executableName*
sudo chmod +x /usr/bin/*executableName*
```
would give permission rwxr-xr-x so everyone can read and execute

---

### Post by cariboo on 2008-08-18
If you look in /usr/bin you will see that all the files are owned by root and they are all executable.

Jim

---

### Post by Paul Baumann on 2008-08-18
Thanks for the inputs,
I must not understand something the "chmod" command and switches didn't work. I either didn't do it right or I am missing something. I see that most of the listings in /usr/bin are executable and all are owned by root.
How do I make them work when logged on as a user?
There must be some way to use them without resorting to difficult terminal mode commands. The program I am trying to make usable is dc, a RPN calculator.
Paul

---

### Post by Too Late on 2008-08-18
Try this:
```
ls -l /usr/bin/dc
```
It shows the permissions that the program 'dc' has.

---

### Post by LinuxRocks713 on 2008-08-18
You mean trying to launch the program? Try doing Alt-F2 (ubuntu equiv of Win+R) and then type /usr/bin/dc.

---

### Post by Paul Baumann on 2008-08-19
I have given up on the program "dc", a RPN calculator program. I'm not sure this program really works? None of the suggestions were successful.
I used The Synaptic Package Manager and found another RPN calculator program called galculator which was not installed on my system. With   the Synaptics Help menu, I downloaded and installed the program and it works.
I may try to completely remove "dc" and try a complete reinstall, but for now I don't want to mess up the best working Linux system I have ever had going.
 Over many years, I have tried Red Hat, Mandrake, and Suse with various degrees of success. Each has some positive features but I could never have everything working. I now have Internet, Email, LAN, File sharing with Windows, CD burning and so on all working, I've never been this far before.
Ubuntu is my first Linux OS that has me thinking that I could live with this!
Thanks for all the advice, I have learned some new commands.
Paul

---

