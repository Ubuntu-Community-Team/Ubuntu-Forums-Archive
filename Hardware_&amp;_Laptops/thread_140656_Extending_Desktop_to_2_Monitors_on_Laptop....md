---
title: "Extending Desktop to 2 Monitors on Laptop..."
date: 2006-03-06
forum: Hardware &amp; Laptops
---

### Post by barl0w on 2006-03-06
Hello,

I just installed Ubuntu 5.10, and after reading some posts in the forum, and finding other web pages, was able to extend my desktop to another monitor (dual head display). I wanted to post how I was able to do that, for anyone else that might have a similar desire or setup.

Hardware I have:
[LIST]Dell Latitude D600 laptop
[LIST]ATI Technologies Radeon Mobility 9000 M9 installed in laptop[/LIST][/LIST]
[LIST]Samsung SyncMaster 900NF display[/LIST]

In WindowsXP, I can simply right-click on desktop and select Properties, Settings, select the No.2 monitor and check the "Extend my Windows desktop onto this monitor" box and select OK to complete the same thing. If you want to do this in Ubuntu, please read the following website, and also my /etc/X11/xorg.conf file.

[Linux Dual Head How To]("http://www.granneman.com/techinfo/linux/installation/dualheadhowto.htm")

Instructions on how I did it.

[LIST=1]
[*] Open the /etc/X11/xorg.conf file in Text Editor
[*] Add the items from the Linux Dual Head HowTo web page (link is above, or you can from my .conf file) into the xorg.conf file
[*] Save the file into the Home directory as xorg.conf
[*] Open the Applications, Terminal application
[*] Type in the command prompt: sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.original
[*] When asked for a password, enter your user name's password (the one you're logged in as)
[*] Type again: sudo cp ./xorg.conf /etc/X11/xorg.conf
[*] Type again: exit
[*] Restart the computer
[/LIST]

\\:D/ And that was it \\:D/ 

I hope this helps someone else out there. Good luck -

Scott

---

### Post by barl0w on 2006-03-13
Hi -

This is not working though on Dapper Drake 6.04 Flight 5. Anyone know why that might be?

Thank you -

Scott

---

