---
title: "Root Help"
date: 2008-09-12
forum: General Help
---

### Post by majikhotline on 2008-09-12
Hello Ubuntu Country,

I have been work on Howto Samba instructions and it ask me to ```
sudo chown root.smbcredentials

``` the problem is that this file is hidden and it says that there is no such file.  I dont know how to change owner of this file using command line if its hidden.  Is there another option?

---

### Post by mb_webguy on 2008-09-12
> **majikhotline said:**
> Hello Ubuntu Country,

I have been work on Howto Samba instructions and it ask me to ```
sudo chown root.smbcredentials

``` the problem is that this file is hidden and it says that there is no such file.  I dont know how to change owner of this file using command line if its hidden.  Is there another option?

First of all, there should be a space between "root" and ".smbcredentials".

Second, have you created the file yet?  The instructions I pulled up when I googled "smbcredentials" indicate you have to create the file.  

Also, in Linux, a dot (.) at the beginning of a filename makes the file hidden.  You can see hidden files in Nautilus with Ctrl-H, and in the terminal with the command "ls -a".  And that has nothing to do with this problem.

---

### Post by majikhotline on 2008-09-12
so....how do i change owership of the file

---

### Post by Frogbarf on 2008-09-12
You have left out a space between "root" and ".smbcredentials".

If that doesn't correct your problem, then two more possibilities:

1. Are you logged in as your admin user? Sudo doesn't work if you're logged in with a non-admin user id.

2. Are you in the right directory, namely the one where .smbcredentials is? If not, you can go "cd /home/majikhotline" to change to that directory (CD = change directory), assuming that majikhotline is the user id that will be the main user of your samba setup.

---

### Post by Frogbarf on 2008-09-12
> **majikhotline said:**
> so....how do i change owership of the file

That's what "chown" is all about.

*sudo chown root .smbcredentials*

means...

*super-user-do change-owner (to) "root" (for file) .smbcredenitals*

I hope my use of hyphens, italicization, and parenthesization is clear.

---

### Post by mb_webguy on 2008-09-12
Of course, the file actually has to *exist* in order for you to change it's owner...

---

### Post by majikhotline on 2008-09-19
of course the file is there I put it there, buy cant change the ownership of the file

---

### Post by Shazaam on 2008-09-19
Gui way (but you won't learn anything doing it this way)...
Enter this in terminal-
```
gksudo nautilus
```
(this opens nautilus as ROOT, be careful).
Hit CTRL+H to show hidden files. Surf to your file, right-click it, choose "Properties" then go to the "Permissions" tab. Change permissions. Close nautilus.

---

