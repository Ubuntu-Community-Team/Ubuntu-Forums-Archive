---
title: "Ubuntu --&gt; Ubuntu Studio"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by denbeigh2000 on 2009-07-27
Hi, I want to switch to Ubuntu Studio, but I can't seem to do it normally...

```
denbeigh@jason:~$ sudo apt-get install ubuntustudio-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntustudio-desktop: Depends: ubuntustudio-screensaver but it is not going to be installed
                        Recommends: gnome-screensaver but it is not going to be installed
E: Broken packages
```

Does anybody have any tips?

Cheers,
d2000 :)

---

### Post by denbeigh2000 on 2009-07-27
```
denbeigh@jason:~$ sudo apt-get install ubuntustudio-screensaver
[sudo] password for denbeigh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntustudio-screensaver: Depends: gnome-screensaver but it is not going to be installed
E: Broken packages
```

And...

```
denbeigh@jason:~$ sudo apt-get install gnome-screensaver
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libjpeg-progs xli totem
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  screensaver-default-images ubuntu-desktop xscreensaver xscreensaver-data
  xscreensaver-gl
The following NEW packages will be installed:
  gnome-screensaver
0 upgraded, 1 newly installed, 5 to remove and 0 not upgraded.
Need to get 0B/1777kB of archives.
After this operation, 5526kB disk space will be freed.
Do you want to continue [Y/n]?
```

Do I want to remove ubuntu-desktop?

---

### Post by jscinoz on 2009-07-27
It should be fine Denbeigh, ubuntu-desktop doesn't actually contain anything, but is just a metapackage to easy upgrades, I believe it is supposed to conflict with ubuntustudio-desktop.

---

### Post by denbeigh2000 on 2009-07-27
Cheers Jack, I'm on Level 3 right now... But the proxy won't authenticate with the school network outside firefox... *sadface*

Shall do it when I get home.

Thanks for the support :)

---

### Post by denbeigh2000 on 2009-07-28
Hmm... That didn't work either.

```
udodenbeigh@jason:~$ sudo apt-get autoremove xscreensaver
[sudo] password for denbeigh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libjpeg-progs xli
The following packages will be REMOVED:
  libjpeg-progs xli xscreensaver
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 2851kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 151903 files and directories currently installed.)
Removing libjpeg-progs ...
Removing xli ...
Removing xscreensaver ...
Processing triggers for man-db ...
denbeigh@jason:~$ sudo apt-get autoremove xscreensaver-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  totem
The following packages will be REMOVED:
  screensaver-default-images totem ubuntu-desktop xscreensaver-data
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 2327kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 151825 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing screensaver-default-images ...
Removing totem ...
Removing xscreensaver-data ...
Processing triggers for man-db ...
denbeigh@jason:~$ sudo apt-get autoremove xscreensaver-gl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xscreensaver-gl
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 5493kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 151730 files and directories currently installed.)
Removing xscreensaver-gl ...
Processing triggers for man-db ...
denbeigh@jason:~$ sudo apt-get install ubuntustudio-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntustudio-desktop: Depends: xscreensaver-data but it is not going to be installed
                        Depends: xscreensaver-gl but it is not going to be installed
E: Broken packages
```

---

### Post by jscinoz on 2009-07-29
To anyone else reading this and horribly confused, Denbeigh and I go to the same school.

Denbeigh, it looks like there might be some other conflicts. Find me at school and bring your laptop and I'll fix it up there. Also, you need to apt-get install ntlmaps to use the school's proxy with apt-get and other things that don't support the NTLM authentication used on the school proxy.

---

