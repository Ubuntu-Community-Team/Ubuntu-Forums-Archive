---
title: "Configure FTP server with fake root"
date: 2008-09-27
forum: General Help
---

### Post by AliTabuger7 on 2008-09-27
I would like to have an FTP server that uses what I think is called "fake root". I want it to restrict ftp users to their "home" folder. I do not want the ftp users to be able to log in and see my entire system from "/". This is for my security and user convenience.

I have installed pureftp because it has a GUI. I am willing to change to a different FTP server program.

The pureadmin gui does not seem to configure this the way I want.

How can I get an FTP "fake root"?

---

### Post by prince_niceguy on 2008-09-27
You can install proftp from repository and configure using this [thread]("http://ubuntuforums.org/showthread.php?t=79588"). I use it and proftp's root folder is the folder specified in the config. It wont allow access to the root directory.

---

