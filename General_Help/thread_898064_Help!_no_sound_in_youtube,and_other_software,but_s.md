---
title: "Help! no sound in youtube,and other software,but sound in system sounds"
date: 2008-08-22
forum: General Help
---

### Post by Hyper Tails on 2008-08-22
hi i have vista and hardy installed but in hardy when i want to play my super mario hacks theres no sound comes out of the emulator,and also no sound in other software like in konqueror when i want to watch like fred in youtbe no sound at all.

please help me because i realy,really need help with this issue:frown:
laptop-Acer apsire 5715-4740

---

### Post by Hyper Tails on 2008-08-22
please help.....

---

### Post by iaculallad on 2008-08-22
Try installing the sound wrapper if it could help:

```
sudo apt-get install libflashsupport
```

---

### Post by mb_webguy on 2008-08-22
Sounds like a PulseAudio compatibility problem.  You can fix the YouTube problem by installing the Flash 10 plugin from the backports repository (see the link in my signature).  I'm not familiar with the emulator you're using, so I don't know exactly how to fix it.  If it has the option of using different output modules, try a different one and see if it helps.

---

### Post by Hyper Tails on 2008-08-22
nope still no sound

any more tricks that will work?

---

### Post by mb_webguy on 2008-08-22
Try [this]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472").

---

### Post by Hyper Tails on 2008-08-23
okay having audio detect make the whole os have no sound but this is what i did


```
[sudo] password for liam:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package nspluginwrapper
liam@Liam-Laptop:~$  sudo apt-get remove libflashsupport
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libflashsupport is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
liam@Liam-Laptop:~$ sudo rm ~/.pulse/* ~/.asoundrc* /etc/asound.conf
rm: cannot remove `/home/liam/.pulse/*': No such file or directory
rm: cannot remove `/home/liam/.asoundrc*': No such file or directory
rm: cannot remove `/etc/asound.conf': No such file or directory
liam@Liam-Laptop:~$ sudo apt-get install padevchooser libao-pulse libasound2-plugins libsdl1.2debian-pulseaudio
Reading package lists... Done
Building dependency tree
Reading state information... Done
padevchooser is already the newest version.
The following packages will be REMOVED:
  libsdl1.2debian-alsa
The following NEW packages will be installed:
  libao-pulse libasound2-plugins libsdl1.2debian-pulseaudio
0 upgraded, 3 newly installed, 1 to remove and 0 not upgraded.
Need to get 318kB of archives.
After this operation, 496kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ca.archive.ubuntu.com hardy/universe libao-pulse 0.9.3-1 [7158B]
Get:2 http://ca.archive.ubuntu.com hardy/main libasound2-plugins 1.0.15-1ubuntu3 [106kB]
Get:3 http://ca.archive.ubuntu.com hardy/universe libsdl1.2debian-pulseaudio 1.2.13-1ubuntu1 [206kB]
Fetched 318kB in 1s (168kB/s)
dpkg: libsdl1.2debian-alsa: dependency problems, but removing anyway as you request:
 libsdl1.2debian depends on libsdl1.2debian-alsa (= 1.2.13-1ubuntu1) | libsdl1.2debian-all (= 1.2.13-1ubuntu1) | libsdl1.2debian-esd (= 1.2.13-1ubuntu1) | libsdl1.2debian-arts (= 1.2.13-1ubuntu1) | libsdl1.2debian-oss (= 1.2.13-1ubuntu1) | libsdl1.2debian-nas (= 1.2.13-1ubuntu1) | libsdl1.2debian-pulseaudio (= 1.2.13-1ubuntu1); however:
  Package libsdl1.2debian-alsa is to be removed.
  Package libsdl1.2debian-all is not installed.
  Package libsdl1.2debian-esd is not installed.
  Package libsdl1.2debian-arts is not installed.
  Package libsdl1.2debian-oss is not installed.
  Package libsdl1.2debian-nas is not installed.
  Package libsdl1.2debian-pulseaudio is not installed.
(Reading database ... 109963 files and directories currently installed.)
Removing libsdl1.2debian-alsa ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package libao-pulse.
(Reading database ... 109955 files and directories currently installed.)
Unpacking libao-pulse (from .../libao-pulse_0.9.3-1_i386.deb) ...
Replaced by files in installed package libao2 ...
Selecting previously deselected package libasound2-plugins.
Unpacking libasound2-plugins (from .../libasound2-plugins_1.0.15-1ubuntu3_i386.deb) ...
Selecting previously deselected package libsdl1.2debian-pulseaudio.
Unpacking libsdl1.2debian-pulseaudio (from .../libsdl1.2debian-pulseaudio_1.2.13-1ubuntu1_i386.deb) ...
Setting up libao-pulse (0.9.3-1) ...
Setting up libasound2-plugins (1.0.15-1ubuntu3) ...
Setting up libsdl1.2debian-pulseaudio (1.2.13-1ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
liam@Liam-Laptop:~$ gksudo gedit /etc/apt/sources.list
The program 'gksudo' is currently not installed.  You can install it by typing:
sudo apt-get install gksu
bash: gksudo: command not found
liam@Liam-Laptop:~$ PulseAudio Fixes - http://ubuntuforums.org/showthread.php?p=5587712
bash: PulseAudio: command not found
liam@Liam-Laptop:~$ deb http://ppa.launchpad.net/psyke83/ubuntu hardy main
bash: deb: command not found
liam@Liam-Laptop:~$ deb-src http://ppa.launchpad.net/psyke83/ubuntu hardy main
bash: deb-src: command not found
liam@Liam-Laptop:~$ sudo apt-get update
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_CA
Hit http://ca.archive.ubuntu.com hardy Release.gpg
Ign http://ca.archive.ubuntu.com hardy/main Translation-en_CA
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_CA
Ign http://security.ubuntu.com hardy-security/universe Translation-en_CA
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_CA
Hit http://security.ubuntu.com hardy-security Release
Ign http://ca.archive.ubuntu.com hardy/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com hardy-updates Release.gpg
Ign http://ca.archive.ubuntu.com hardy-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy-updates/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy-updates/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com hardy Release
Hit http://ca.archive.ubuntu.com hardy-updates Release
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://ca.archive.ubuntu.com hardy/main Packages
Hit http://ca.archive.ubuntu.com hardy/restricted Packages
Hit http://ca.archive.ubuntu.com hardy/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://ca.archive.ubuntu.com hardy/restricted Sources
Hit http://ca.archive.ubuntu.com hardy/universe Packages
Hit http://ca.archive.ubuntu.com hardy/universe Sources
Hit http://ca.archive.ubuntu.com hardy/multiverse Packages
Hit http://ca.archive.ubuntu.com hardy/multiverse Sources
Hit http://ca.archive.ubuntu.com hardy-updates/main Packages
Hit http://ca.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://ca.archive.ubuntu.com hardy-updates/main Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://ca.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://ca.archive.ubuntu.com hardy-updates/universe Packages
Hit http://ca.archive.ubuntu.com hardy-updates/universe Sources
Hit http://ca.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://ca.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists... Done
liam@Liam-Laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
liam@Liam-Laptop:~$ asoundconf set-pulseaudio
liam@Liam-Laptop:~$ echo "default_driver=pulse" >~/.libao
liam@Liam-Laptop:~$    
```

---

### Post by mb_webguy on 2008-08-23
It doesn't look like you added his repositories...  Did you type "sudo apt-get update" after adding the repositories?

---

### Post by Hyper Tails on 2008-08-23
yes i did

---

### Post by mb_webguy on 2008-08-23
Ooohhh.  You're using Kubuntu, so the commands are going to be a bit different for you.  Look at this section of what you posted:```
liam@Liam-Laptop:~$ gksudo gedit /etc/apt/sources.list
The program 'gksudo' is currently not installed.  You can install it by typing:
sudo apt-get install gksu
bash: gksudo: command not found
liam@Liam-Laptop:~$ PulseAudio Fixes - http://ubuntuforums.org/showthread.php?p=5587712
bash: PulseAudio: command not found
liam@Liam-Laptop:~$ deb http://ppa.launchpad.net/psyke83/ubuntu hardy main
bash: deb: command not found
liam@Liam-Laptop:~$ deb-src http://ppa.launchpad.net/psyke83/ubuntu hardy main
bash: deb-src: command not found

```

Kubuntu doesn't use gksudo or gedit, so you didn't actually do anything there.

Here's what you should do... (Some of this you've already done, but it won't hurt to do it again, especially since it's all cut-and-paste.)  Enter the following commands in the terminal:```
sudo apt-get remove nspluginwrapper
sudo apt-get remove libflashsupport
sudo rm ~/.pulse/* ~/.asoundrc* /etc/asound.conf
sudo apt-get install padevchooser libao-pulse libasound2-plugins libsdl1.2debian-pulseaudio
kdesu kate /etc/apt/sources.list
```
You should now have opened a file containing a lot of lines beginning with "deb" in the text editor.  Paste the following lines at the end of that file:```
# PulseAudio Fixes - http://ubuntuforums.org/showthread.php?p=5587712
deb http://ppa.launchpad.net/psyke83/ubuntu hardy main
deb-src http://ppa.launchpad.net/psyke83/ubuntu hardy main
```
Now save and close the file, and type the following commands:```
sudo apt-get update
sudo apt-get upgrade
asoundconf set-pulseaudio
echo "default_driver=pulse" >~/.libao
```
Now go to System->Preferences->Sound and make sure all of the playback entries are set to "Autodetect".  Now either logout or reboot.

---

### Post by Hyper Tails on 2008-08-23
question:
do i replace
```
#deb cdrom:[Kubuntu 8.04.1 _Hardy Heron_ - Release i386
```

with that code?

---

### Post by Hyper Tails on 2008-08-23
no one knows?

---

### Post by mb_webguy on 2008-08-23
No, you don't want to *replace* anything.  Just add those lines to the end of the file.

---

### Post by Hyper Tails on 2008-08-23
i got the appucations sound working now but now the system sounds work work and the emulator roms will open and not responde or close:confused:

any codes will help?

---

### Post by Hyper Tails on 2008-08-24
help?

---

### Post by Hyper Tails on 2008-08-24
Please help me...

---

### Post by Hyper Tails on 2008-08-25
I need help big time please...

---

### Post by Hyper Tails on 2008-08-25
I don't want to bump anymore i just need one answer for this problem
please:(:(:(

---

### Post by iamcims on 2008-08-25
i used to have a problem where i could only really be using my sound from one program so like lets say i had amarok running my mp3s, i couldnt go to youtube and watch a video unless amarok was closed. I fixed this by going to my sound options and using ALSA, now i have no problems running multiple sound/video with websites and programs etc.

Not sure if this will help but maybe worth a shot to see if it does anything beneficial for ya

---

### Post by Hyper Tails on 2008-08-25
question: i got the files downloaded but how do i install it?

---

### Post by Hyper Tails on 2008-08-26
no ones knows...

---

### Post by Hyper Tails on 2008-08-26
what am i going to do when the first day back to school come and i have this issue??

and yes i use my laptop in school

---

### Post by Hyper Tails on 2008-08-28
no more bumps please.....

---

### Post by Hyper Tails on 2008-08-28
Fine i don't care anymore...

---

### Post by wgargan on 2009-10-06
typ this in your konsol: alsamixer -Dhw

use the arrow keys to adjust.

---

