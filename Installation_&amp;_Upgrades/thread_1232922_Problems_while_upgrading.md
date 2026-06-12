---
title: "Problems while upgrading"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by tavi_10 on 2009-08-06
It seems that i managed to corrupt my Ubuntu instalation (and that&#539;s a bad thing).

So i have the latest stable version installed, 9.04. 

Done before getting the error:
Ran out of space, so i ran various commands found on the internet to free up some space. I don't actaully know what the commands are, i've found them on these forums, so i guess they are ok.
I've changed the disk that contains the /var directory (done a lot of faulty tries befo managing to do it right).

My problem is that i can't install anything, can't upgrade, can't run Firefox (using Opera now). Even a bigger problem is that i have Ubuntu installed in Romanian and pasting the errors will be pretty hard (and, of course, as i can't install anything, can't install the English language pack).

The errors look like: 
When using ```
sudo apt-get upgrade
```
I get: 

```
The following packaged have dependencies not satisfied:
sudo apt-get upgradefirefox-3.0-branding: Depends on: firefox-3.0 (= 3.0.13+nobinonly-0ubuntu0.9.04.1) but 3.0.12+build1+nobinonly-0ubuntu0.9.04.1 is installed
Dependencies not satisfied, try using -f
```

At ```
sudo apt-get -f install
``` (translated only the first lines as it says the same all the time, but with other package).

```
The following packages will be installed:
  firefox-3.0 libnss3-1d xulrunner-1.9
Suggested packages:
  ubufox firefox-3.0-gnome-support
The following packages will be updated:
  firefox-3.0 libnss3-1d xulrunner-1.9
3 updated, 0 newly installed, 0 to be deleted and 5 renewed.
10 packages installed or completely removed.
You need to download 0B/17,1MB in archives.
After this operation 69.6kB of disk space will be freed.
Will you continue? y
Configuring packages...
(Reading the db...
dpkg: Severe warning: The file with package list for 'dash' is missing, considering that it has no file.

dpkg: Severe warning: The file with package list for 'screen-profiles' is missing, considering that it has no file.

dpkg: Severe warning: The file with package list for 'dictionaries-common' is missing, considering that it has no file.

dpkg: Severe warning: The file with package list for 'notify-osd' is missing, considering that it has no file.

168036 files and directories currently installed.)
Preparing replacement of libnspr4-0d 4.7.3-0ubuntu2 (usiong .../libnspr4-0d_4.7.3-0ubuntu2_amd64.deb) ...
dpkg (subprocess): Could not run pre-removal old: Permission denied
dpkg: avertisment - script pre-removal old returned with error exit code 2
dpkg - trying the script from the new package instead ...
dpkg (subprocess): Could not run pre-removal new: Permission denied
dpkg: error at proecssing /var/cache/apt/archives/libnspr4-0d_4.7.3-0ubuntu2_amd64.deb (--unpack):
 subprocess script pre-removal new returned with error exit code 2
dpkg (subproces): impossible executing post-installation script: Permission denied
dpkg: error while cleaning:
 subprocesul post-installation script returns error exit code 2
Preparing for replacement of libnss3-1d 3.12.2~rc1-0ubuntu2 (using .../libnss3-1d_3.12.3.1-0ubuntu0.9.04.1_amd64.deb) ...
dpkg (subproces): impossible executing script pre-removal old: Permission denied
dpkg: avertisment - script pre-removal old returned error exit code 2
dpkg - trying the script from the new package instead ...
dpkg (subproces): impossible to execute script pre-removal new: Permission denied
dpkg: error processing /var/cache/apt/archives/libnss3-1d_3.12.3.1-0ubuntu0.9.04.1_amd64.deb (--unpack):
 subprocesul script pre-removal nou returneaz&#259; starea de eroare la ie&#537;ire 2
dpkg (subproces): imposibil a executa post-installation script: Permission denied
dpkg: eroare în timpul cur&#259;&#539;&#259;rii:
 subprocesul post-installation script returneaz&#259; starea de eroare la ie&#537;ire 2
Se preg&#259;te&#537;te înlocuirea lui xulrunner-1.9 1.9.0.12+build1+nobinonly-0ubuntu0.9.04.1 (folosind .../xulrunner-1.9_1.9.0.13+nobinonly-0ubuntu0.9.04.1_amd64.deb) ...
dpkg (subproces): imposibil a executa script pre-removal vechi: Permission denied
dpkg: avertisment - script pre-removal vechi returnat cu starea de eroare la ie&#537;ire 2
dpkg - încerc scriptul din noul pachet în loc ...
dpkg (subproces): imposibil a executa script pre-removal nou: Permission denied
dpkg: eroare la procesarea /var/cache/apt/archives/xulrunner-1.9_1.9.0.13+nobinonly-0ubuntu0.9.04.1_amd64.deb (--unpack):
 subprocesul script pre-removal nou returneaz&#259; starea de eroare la ie&#537;ire 2
dpkg (subproces): imposibil a executa post-installation script: Permission denied
dpkg: eroare în timpul cur&#259;&#539;&#259;rii:
 subprocesul post-installation script returneaz&#259; starea de eroare la ie&#537;ire 2
Se preg&#259;te&#537;te înlocuirea lui firefox-3.0 3.0.12+build1+nobinonly-0ubuntu0.9.04.1 (folosind .../firefox-3.0_3.0.13+nobinonly-0ubuntu0.9.04.1_amd64.deb) ...
dpkg (subproces): imposibil a executa script pre-removal vechi: Permission denied
dpkg: avertisment - script pre-removal vechi returnat cu starea de eroare la ie&#537;ire 2
dpkg - încerc scriptul din noul pachet în loc ...
dpkg (subproces): imposibil a executa script pre-removal nou: Permission denied
dpkg: eroare la procesarea /var/cache/apt/archives/firefox-3.0_3.0.13+nobinonly-0ubuntu0.9.04.1_amd64.deb (--unpack):
 subprocesul script pre-removal nou returneaz&#259; starea de eroare la ie&#537;ire 2
No apport report written because MaxReports is reached already
                                                              dpkg (subproces): imposibil a executa post-installation script: Permission denied
dpkg: eroare în timpul cur&#259;&#539;&#259;rii:
 subprocesul post-installation script returneaz&#259; starea de eroare la ie&#537;ire 2
Se preg&#259;te&#537;te înlocuirea lui libwbclient0 2:3.3.2-1ubuntu3 (folosind .../libwbclient0_2%3a3.3.2-1ubuntu3_amd64.deb) ...
Se dezarhiveaz&#259; pachetul înlocuitor (libwbclient0) ...
dpkg (subproces): imposibil a executa script post-removal vechi: Permission denied
dpkg: avertisment - script post-removal vechi returnat cu starea de eroare la ie&#537;ire 2
dpkg - încerc scriptul din noul pachet în loc ...
dpkg (subproces): imposibil a executa script post-removal nou: Permission denied
dpkg: eroare la procesarea /var/cache/apt/archives/libwbclient0_2%3a3.3.2-1ubuntu3_amd64.deb (--unpack):
 subprocesul script post-removal nou returneaz&#259; starea de eroare la ie&#537;ire 2
No apport report written because MaxReports is reached already
                                                              dpkg (subproces): imposibil a executa noul post-removal script: Permission denied
dpkg: eroare în timpul cur&#259;&#539;&#259;rii:
 subprocesul post-removal script returneaz&#259; starea de eroare la ie&#537;ire 2
Se preg&#259;te&#537;te înlocuirea lui libxklavier12 3.9-0ubuntu1 (folosind .../libxklavier12_3.9-0ubuntu1_amd64.deb) ...
Se dezarhiveaz&#259; pachetul înlocuitor (libxklavier12) ...
dpkg (subproces): imposibil a executa script post-removal vechi: Permission denied
dpkg: avertisment - script post-removal vechi returnat cu starea de eroare la ie&#537;ire 2
dpkg - încerc scriptul din noul pachet în loc ...
dpkg (subproces): imposibil a executa script post-removal nou: Permission denied
dpkg: eroare la procesarea /var/cache/apt/archives/libxklavier12_3.9-0ubuntu1_amd64.deb (--unpack):
 subprocesul script post-removal nou returneaz&#259; starea de eroare la ie&#537;ire 2
dpkg (subproces): imposibil a executa noul post-removal script: Permission denied
No apport report written because MaxReports is reached already
                                                              dpkg: error while cleaning up:
 subprocesul post-removal script returneaz&#259; starea de eroare la ie&#537;ire 2
Se preg&#259;te&#537;te înlocuirea lui samba-common 2:3.3.2-1ubuntu3 (folosind .../samba-common_2%3a3.3.2-1ubuntu3_amd64.deb) ...
dpkg (subproces): imposibil a executa script pre-removal vechi: Permission denied
dpkg: avertisment - script pre-removal vechi returnat cu starea de eroare la ie&#537;ire 2
dpkg - încerc scriptul din noul pachet în loc ...
dpkg (subproces): imposibil a executa script pre-removal nou: Permission denied
dpkg: eroare la procesarea /var/cache/apt/archives/samba-common_2%3a3.3.2-1ubuntu3_amd64.deb (--unpack):
 subprocesul script pre-removal nou returneaz&#259; starea de eroare la ie&#537;ire 2
No apport report written because MaxReports is reached already
                                                              dpkg (subproces): imposibil a executa post-installation script: Permission denied
dpkg: eroare în timpul cur&#259;&#539;&#259;rii:
 subprocesul post-installation script returneaz&#259; starea de eroare la ie&#537;ire 2
Se preg&#259;te&#537;te înlocuirea lui libsmbclient 2:3.3.2-1ubuntu3 (folosind .../libsmbclient_2%3a3.3.2-1ubuntu3_amd64.deb) ...
Se dezarhiveaz&#259; pachetul înlocuitor (libsmbclient) ...
dpkg (subproces): imposibil a executa script post-removal vechi: Permission denied
dpkg: avertisment - script post-removal vechi returnat cu starea de eroare la ie&#537;ire 2
dpkg - încerc scriptul din noul pachet în loc ...
dpkg (subproces): imposibil a executa script post-removal nou: Permission denied
dpkg: eroare la procesarea /var/cache/apt/archives/libsmbclient_2%3a3.3.2-1ubuntu3_amd64.deb (--unpack):
 subprocesul script post-removal nou returneaz&#259; starea de eroare la ie&#537;ire 2
No apport report written because MaxReports is reached already
                                                              dpkg (subproces): imposibil a executa noul post-removal script: Permission denied
dpkg: eroare în timpul cur&#259;&#539;&#259;rii:
 subprocesul post-removal script returneaz&#259; starea de eroare la ie&#537;ire 2
Erori întâlnite în timpul prelucr&#259;rii:
 /var/cache/apt/archives/libnspr4-0d_4.7.3-0ubuntu2_amd64.deb
 /var/cache/apt/archives/libnss3-1d_3.12.3.1-0ubuntu0.9.04.1_amd64.deb
 /var/cache/apt/archives/xulrunner-1.9_1.9.0.13+nobinonly-0ubuntu0.9.04.1_amd64.deb
 /var/cache/apt/archives/firefox-3.0_3.0.13+nobinonly-0ubuntu0.9.04.1_amd64.deb
 /var/cache/apt/archives/libwbclient0_2%3a3.3.2-1ubuntu3_amd64.deb
 /var/cache/apt/archives/libxklavier12_3.9-0ubuntu1_amd64.deb
 /var/cache/apt/archives/samba-common_2%3a3.3.2-1ubuntu3_amd64.deb
 /var/cache/apt/archives/libsmbclient_2%3a3.3.2-1ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Also, trying to rely on the info i've found, i tried to delete some files from dpkg folder, as some said that worked. It did not for me.

---

### Post by alexandari on 2009-08-06
Permission denied? how about running **apt-get install -f** with **root**?

edit: yes sorry you`r right clumsy me :<

---

### Post by tavi_10 on 2009-08-06
Well... I thought that sudo before the command means root access. Anyway, i tried sudo su then apt-get install -f and i've got premission denied again.

The /var directory is in a partition with ext3 format, maybe that is important. Also, another thing that may be important is that the archives foled is empty (i believe that the folder should have been writted with different packages by now).

---

### Post by tavi_10 on 2009-08-09
Anything, pls?

---

### Post by tavi_10 on 2009-08-10
Up...

---

### Post by drs305 on 2009-08-10
Is this a new installation? I know the title includes "upgrading". You said initially you ran out of space. A lot of new users are installing to partitions that are too small to actually run Ubuntu. Even if it's not a new install, if you have run out of space on your / partition the link to the thread below on increasing your / partition size may be helpful.

Does this command show / of about 2.3GB, or that you / is full?
```

df -h
```

If so, please refer to this post for possible solutions:
[http://ubuntuforums.org/showthread.php?t=1232257#6]("http://ubuntuforums.org/showthread.php?t=1232257#6")

---

### Post by tavi_10 on 2009-08-10
Thank you for your reply. You made me think about that fstab file that i edited, and it seems that i gave it the wrong options. I've changed that file, created back some dirs (i've deteled firefox dir from lib and some others trying to fix the problem) and now it seems to be working fine.

Strange thing this linux, it doen't seem to be idiot proof at all :D

---

