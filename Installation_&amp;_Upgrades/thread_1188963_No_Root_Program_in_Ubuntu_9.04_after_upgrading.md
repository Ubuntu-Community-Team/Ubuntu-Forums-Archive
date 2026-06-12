---
title: "No Root Program in Ubuntu 9.04 after upgrading"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by vern3219 on 2009-06-16
The Ubuntu 8.10 was working fine! Then along come Ubuntu 9.04 so I decided to use the latest. Put the x86 desktop disk in the computer and tried to install Ubuntu 9.04. This version of Ubuntu does not like my hardware and would not install. Then tried the x86 Alternate Ubuntu 9.04 disk. It upgraded my Ubuntu 8.10 and then gave me the first screen to log in. Could not log in because under 8.10 it was not required to log in. And so I did not have a user name and password so logging in that way was out!! Went into “recovery mode” which accepted my root password and was able to create a new user and password, then I was able to log in!!

So thinking everything was a go started to use 9.04. Looked for “add and remove packages” under Applications but it was not there! Looked around and found under “System-Administration” “Synaptic Package Manager”. So I clicked on Synaptic Package Manager” and when I entered mu root password got a return of “Failed to run /usr/sbin/synaptic as user root.” And the it said “Wrong password”. 

So I went to a terminal screen and entered
clay@eagle:~$ root 
The program 'root' is currently not installed.  To run 'root' please ask your administrator to install the package 'root-system-bin' 
bash: root: command not found
And so there is no root program installed! What happened to the one under 8.10???

Went back to “recovery mode” which thankfully still remembers my password.

In “recovery mode” choose “root shell” and then entered my root password, it was accepted! Then entered “apt-get install root-system-bin” . It tried to access the internet and nothing happened. Then it asked for the Ubuntu 9.04 disk so I put in th x86 desktop disk and it did not find any root packages. Then it said to try update or fix which neither one would work because of no internet.

Is there a way to get the “root program” installed on this OS??

Thank you
Clayton Stapletonhttp://ubuntuforums.org/images/smilies/icon_sad.gif

---

### Post by ptn107 on 2009-06-16
> **vern3219 said:**
> ...could not log in because under 8.10 it was not required to log in. And so I did not have a user name and password so loggin...

You DID have a username and password, you just weren't required to use them.  The username I see is 'clay' but you need to remember the password.

---

