---
title: "Help! Lots of errors after forcing shutdown!"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by errormessage on 2009-04-20
Well, Ubuntu just froze up in fullscreen mode while watching a youtube video. I had to force my system to shutdown. When it started up, I noticed a red circle with a white line through the middle in my system tray, so I right-clicked on it, to my surprise, it was the system update tool! I then clicked on "install all updates", typed in my system password and got the following error:
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

       Please help, and I also get the following error when opening add/remove applications
       Failed to check for installed and available applications
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

Thanks!

---

### Post by Partyboi2 on 2009-04-20
Open a terminal and try what it suggests
```
sudo apt-get update
sudo apt-get install -f
```
If that does not work you may need to replace the status file.
```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.broke
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

---

### Post by errormessage on 2009-04-21
OMG thank you very much! Im still getting new to ubuntu, but now add/remove apps AND system update works. =)

EDIT: Rebooted pc, tried to install updates and got another error, same for when I tried to install another program.
Wow I'm having no luck with ubuntu!

Plz help. It doesn't have a error log. I just says "Not all changes or updates succeeded" after install

---

### Post by errormessage on 2009-04-21
Plz help, I need to install a program to do some work but I am unable to due to errors. Thanks

---

### Post by Partyboi2 on 2009-04-21
Open a terminal and post the output to
```
sudo dpkg --configure -a
```

---

### Post by upchucky on 2009-04-21
if in future, you have a window that freezes, or seems non responsive,

press ALT and F2

type xkill in the box that pops up

then click on the non responsive window.

---

