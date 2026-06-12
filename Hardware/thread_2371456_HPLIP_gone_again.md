---
title: "HPLIP gone again"
date: 2017-09-14
forum: Hardware
---

### Post by cmcanulty on 2017-09-14
I need at least hplip-3.16.5 to run the library hp officejet pro 8740. It was running fine and then hplip disappeared from all 16 computers. Now when I try to install hplip I get this error. I have spent all day trying to get this to work. It has to be installed as a network printer using hplip or the scanner won't work over the network. The missing dependencies I can't find anywhere. I have installed a bunch of qt5 and pyqt5 but can't find the exact file needed anywhere.Here is the exact error message. I am running xubuntu 16.04 64 bit all updated. I tried this with both hplip 3.17.7 and 3.16.11 which worked until it all disappeared.Thank you.

```
error: A required dependency 'pyqt5-dbus (PyQt 5 DBus - DBus Support for PyQt5)' is still missing.
error: A required dependency 'pyqt5 (PyQt 5- Qt interface for Python (for Qt version 4.x))' is still missing.
error: Installation cannot continue without these dependencies.
error: Please manually install this dependency and re-run this installer.
```

---

### Post by pdc on 2017-09-14
so my take from the messages you got is that you need ```
pyqt5-dbus
``` and ```
pyqt5
``` to be installed;

........... happy to be told I am wrong ...............

so what does ```
dpkg -l pyqt5-dbus
``` and ```
dpkg -l pyqt5
``` give if you paste those two commands into a terminal please?

---

### Post by cmcanulty on 2017-09-14
```
librarian@DarcyRemote:~$ dpkg -l pyqt5-dbus
dpkg-query: no packages found matching pyqt5-dbus
librarian@DarcyRemote:~$ dpkg -l pyqt5
dpkg-query: no packages found matching pyqt5
librarian@DarcyRemote:~$
```

---

### Post by oldfred on 2017-09-14
I often use synaptic so I know exact names.

Partial results show these but not exact name your error has. 
Is HPLIP using python or python3?

apt policy python-dbus*
python-dbus.mainloop.pyqt5
python-dbus

apt policy python3-dbus*
python3-dbus.mainloop.qt
python3-dbus.mainloop.pyqt5
python3-dbus

---

### Post by pdc on 2017-09-14
as old fred says, with exact names one can be clearer what is missing but with dbus our synaptic shows the options as in the thumbnail; we have hplip 3.16.3 installed,

and the command  ```
apt policy python-dbus*
``` shows ```
python-dbus: Installed: 1.2.0-3
```  and ```
python-dbus-dev: Installed: 1.2.0-3
```

---

### Post by cmcanulty on 2017-09-15
```
librarian@DarcyRemote:~$ apt policy python-dbus*
python-dbus-dbg:
  Installed: (none)
  Candidate: 1.2.0-3
  Version table:
     1.2.0-3 500
        500 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://cz.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
python-dbus-dev:
  Installed: (none)
  Candidate: 1.2.0-3
  Version table:
     1.2.0-3 500
        500 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://ca.archive.ubuntu.com/ubuntu xenial/main i386 Packages
        500 http://cz.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://cz.archive.ubuntu.com/ubuntu xenial/main i386 Packages
python-dbus-doc:
  Installed: (none)
  Candidate: 1.2.0-3
  Version table:
     1.2.0-3 500
        500 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://ca.archive.ubuntu.com/ubuntu xenial/main i386 Packages
        500 http://cz.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://cz.archive.ubuntu.com/ubuntu xenial/main i386 Packages
python-dbus.mainloop.pyqt5-dbg:
  Installed: (none)
  Candidate: 5.5.1+dfsg-3ubuntu4
  Version table:
     5.5.1+dfsg-3ubuntu4 500
        500 http://ca.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
python-dbus.mainloop.pyqt5:
  Installed: (none)
  Candidate: 5.5.1+dfsg-3ubuntu4
  Version table:
     5.5.1+dfsg-3ubuntu4 500
        500 http://ca.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
python-dbus:
  Installed: 1.2.0-3
  Candidate: 1.2.0-3
  Version table:
 *** 1.2.0-3 500
        500 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://cz.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
python-dbus-common:
  Installed: (none)
  Candidate: (none)
  Version table:
python-dbusmock:
  Installed: (none)
  Candidate: 0.16.3-1
  Version table:
     0.16.3-1 500
        500 http://ca.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        500 http://ca.archive.ubuntu.com/ubuntu xenial/universe i386 Packages
librarian@DarcyRemote:~$ 

```

Also there is so much python installed I am not sure what is missing 3 atttached screenshots show the installed python apps[ATTACH=CONFIG]276733[/ATTACH][ATTACH=CONFIG]276734[/ATTACH][ATTACH=CONFIG]276735[/ATTACH]

---

### Post by pdc on 2017-09-15
so to me when your system says > Installed: (none), I would take it that dbus is not installed; 

to me, the first error message said > A required dependency '[COLOR="#FF0000"]pyqt5-dbus[/COLOR] (PyQt 5 DBus - DBus Support for PyQt5)' [COLOR="#0000FF"]is still missing[/COLOR]. and I would have thought it reasonable to suggest installing that; what would you feel

---

### Post by cmcanulty on 2017-09-15
dbus is installed but the error asks for pyqt5-dbus, which I can't find anywhere. Thank you again

---

### Post by pdc on 2017-09-15
have a look at that thumbnail that I attached to post #5. I opened synaptic; 

you can see what I searched on; and the result I got

I wonder would you get the same result: seems to me those are what you need installed; to satisfy the demands of your system; I see you have a much more complicated setup than many of us (such as me ......... who just has a standalong desktop .....)

---

### Post by mastablasta on 2017-09-19
looks like it moved to universe repos. do you have the universe repos enabled?:

[https://packages.ubuntu.com/search?keywords=python3-dbus.mainloop.pyqt5](https://packages.ubuntu.com/search?keywords=python3-dbus.mainloop.pyqt5)

[https://packages.ubuntu.com/search?keywords=dbus%20qt](https://packages.ubuntu.com/search?keywords=dbus%20qt)

how to enable universe or check if it is enabled:
[https://askubuntu.com/questions/148638/how-do-i-enable-the-universe-repository](https://askubuntu.com/questions/148638/how-do-i-enable-the-universe-repository)

---

### Post by cmcanulty on 2017-09-19
I give up, installed [https://packages.ubuntu.com/search?keywords=python3-dbus.mainloop.pyqt5](https://packages.ubuntu.com/search?keywords=python3-dbus.mainloop.pyqt5) which isn't the pkg the install said was missing and more errors. I am going with the old version that incessantly asks me to upgrade. Thanks for all your help.

---

### Post by MSXManiac on 2017-12-13
Unfortunately it seems that Qt5 support is not fully available on Ubuntu and there are divergences of package names between Ubuntu and Debian.
The HP staff washes their hands as it is Qt5 support issues from the distros and the Qt5 developers as well.
I am using hplip 3.17.11 but without Qt5 support enabled during compilation.
For you to choose you have to choose the custom installation and not enable Qt5.
I use Zorin 12.2 which is done on Ubuntu 16.04 and I had no problem choosing the distro as Ubuntu and the version as 16.04 during the installation.

---

### Post by cmcanulty on 2017-12-13
OK thanks that helps. How would I disable the qt5 support in the installation?

---

