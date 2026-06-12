---
title: "Very basic update/upgrade question"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by rashby3 on 2009-10-26
I have a background in Unix but not so much in Linux or Ubuntu.

I bought a Linux laptop a while back with Ubuntu 8.04 installed.

THe first time I tried to install updates using the update manager I discovered I did not have permission to do so as a normal user. I logged out and logged in as root and successfully installed updates.

Lately, I realized a few versions beyond 8.04 had come out, and my periodically running updates was not installing them--I stayed at 8.04.

I looked around on the web and found out how to install "normal" releases. Then I installed 8.10 (logged in as root, of course).

Afterwards, I decided to log in as root again to upgrade to 9.04. However, I could not do so from the initial login screen at startup. I could log in as root within a terminal session using "su root", but that did not let me get to System->Administration->Update Manager as root.

I eventually did find out how to log in to Gnome as root. However, along the way I encountered many warnings about why I should not do so, and should also never run an X application as root.

Finally, here is my question: What is the proper way to run the Update Manager without logging in as root?

Thanks.

---

### Post by TenPlus1 on 2009-10-26
As far as I'm aware you need to be root or a superuser to update the Os...

---

### Post by nerdzero on 2009-10-26
Hi rashby3,

The root account is actually disabled in Ubuntu by default.  Are you saying you have enabled it?

If you are running a command from the Administration menu, it should prompt you for your password which will escalate your privileges.  This is your "normal" password and not a different root password.
 
 If you are executing it from the command line, you should prefix the command with "sudo" which will also then prompt you for your password.  So, you can run

```
sudo update-manager
```to escalate your privileges to "root".  Does this make sense?

---

### Post by freecru on 2009-10-26
From terminal you should run
```
sudo update-manager -d
```This will prompt for you user account's password. Update-manager will appear with an option to upgrade the distribution (8.04->8.10, etc.)

When running System>Administration>Update Manager you should be getting a prompt for entering a user password. Is this not the case?

EDIT: Please be aware that currently update-manager -d will cause you to update to the RC of 9.10. Doing a normal sudo update-manager should cause the update-manager to appear with a 9.04 release being at the top of the window. For further help on updating you should read here: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) You really shouldn't ever need to log in as root user at the gdm login window. Using sudo/gksudo or entering a password at prompts should be sufficient.

---

### Post by rashby3 on 2009-10-26
To nerdzero: Yes, I enabled root login, but I am asking how everyone else runs the update manager as a normal user so that I don't have to log in as root.

To nerdzero and freecru: Yes, update manager asks for my password, but then does not accept it--gives me an error message.

I believe my problem may be because my user ID is not set up in the sudoers file. However, I just took a look at [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers) and it really seems kind of obscure. I will look at it for awhile and see if I can understand what I need to do.

Thanks.

---

### Post by nerdzero on 2009-10-26
I believe by default members of the 'admin' group have sudo privileges.  You can try adding yourself to that group as root.

---

### Post by rashby3 on 2009-10-26
Thanks, nerzero. Adding myself to the admin group did work.

---

### Post by stlsaint on 2009-10-26
> **freecru said:**
> From terminal you should run
```
sudo update-manager -d
```This will prompt for you user account's password. Update-manager will appear with an option to upgrade the distribution (8.04->8.10, etc.)

When running System>Administration>Update Manager you should be getting a prompt for entering a user password. Is this not the case?

EDIT: Please be aware that currently update-manager -d will cause you to update to the RC of 9.10. Doing a normal sudo update-manager should cause the update-manager to appear with a 9.04 release being at the top of the window. For further help on updating you should read here: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) You really shouldn't ever need to log in as root user at the gdm login window. Using sudo/gksudo or entering a password at prompts should be sufficient.


```
sudo apt-get dist-upgrade -d
```that only downloads the packages...it does not install them!

---

### Post by jheaton5 on 2009-10-26
I don't use Update manager.  I use the command line.  Yesterday I did an update from Jaunty to Karmic and it was successful.  Here is what I did:

```
$ gksudo gedit /etc/apt/sources.list
```
I edited the file changing "jaunty" to "karmic" in all instances.  Then I performed the following:```
$ sudo aptitude update
$ sudo aptitude install apt aptitude dpkg
$ sudo aptitude safe-upgrade
$ sudo aptitude full-upgrade
```

It took about 2 hours on a high speed broadband connection.

---

