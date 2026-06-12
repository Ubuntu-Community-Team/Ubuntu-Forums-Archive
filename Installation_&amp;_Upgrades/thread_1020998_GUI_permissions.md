---
title: "GUI permissions?"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by weaslesripmyflesh on 2008-12-24
What level of permission is normal in the GUI. Let's say you wanted to use the synaptic package manager. So you open it in the GUI and you are told you aren't allowed to do that. It seems to me that it wouldn't be in the GUI if it wasn't meant to be used there. 

If you are meant to be able to use apps like this in the GUI can someone tell me how to get permission to do so. If I am in the wrong forum I am sorry, where should I go?

---

### Post by tuxxy on 2008-12-24
Synaptic may require you enter your admin/user password to continue to access the app.

---

### Post by weaslesripmyflesh on 2008-12-24
Yeah i have done that and it still won't work.

---

### Post by Skripka on 2008-12-24
> **weaslesripmyflesh said:**
> What level of permission is normal in the GUI. Let's say you wanted to use the synaptic package manager. So you open it in the GUI and you are told you aren't allowed to do that. It seems to me that it wouldn't be in the GUI if it wasn't meant to be used there. 

If you are meant to be able to use apps like this in the GUI can someone tell me how to get permission to do so. If I am in the wrong forum I am sorry, where should I go?

You have user permissions, by default.  That means that you can read/write to your Home folder/partition.  It means your can run any program which does NOT change the system files/folders.


To run Synaptic, or to install Ndiswrapper, you must have administrator permissions.  When you start Synaptic (by clicking on the menu bar etc etc), you should be prompted for your admin password.  Enter it-and you have permissions to alter the system.  For Ndiswrapper and the like, that are installed/controlled by command line, you preface your command (whatever it is) with:

```
sudo
```

as in:

```
sudo modprobe ndiswrapper
```

after pressing enter-you'll be prompted for your admin password-and BAM, modprobe is run with administrator permissions.



This idea of permissions and administrator versus regular user is what make viruses virturally non-existant in linux.  A virus needs the ability to be run with administrator permissions, i.e. it needs to be able to read and write to the system folders.  Windows until Vista-defaulted to having every process and exe file having admin permissions-------that is every executable you ran had the ability alter the system folders....and hence there were and are a million viruses that take advantage of this fundamental design flaw.

---

### Post by jerome1232 on 2008-12-24
> **weaslesripmyflesh said:**
> What level of permission is normal in the GUI. Let's say you wanted to use the synaptic package manager. So you open it in the GUI and you are told you aren't allowed to do that. It seems to me that it wouldn't be in the GUI if it wasn't meant to be used there. 

If you are meant to be able to use apps like this in the GUI can someone tell me how to get permission to do so. If I am in the wrong forum I am sorry, where should I go?

Are you not in the admin group for some reason on your computer. By default ubuntu puts the first user created in that group. Only users in that group can use applications which can have an impact on system wide settings.

can you post the output of the groups command? Just open a terminal and type in "groups" without the quotes.
To open a terminal click Applications-Accessories-Terminal
```
groups
```


---edit--- If you are in the admin group then you should be able to use synaptic, for command line programs you just need to preface the command with sudo.

---

### Post by weaslesripmyflesh on 2008-12-24
Ugh, until I get my USB wifi working this is going to be really slow. I have been at this for hours. Still sitting at my XP desktop waiting for a solution.

---

### Post by upchucky on 2008-12-24
when you go to,

system>administration>synaptic package manager

it asks you for your password to modify the system, you enter the password and your are now the sudo. (superuser mode) now this password has to be the administrater account and password, not a generic user and password. so depending on whether you are set up on login as administrater or general user it will let you do the modification. with that said ubuntu by default does not log you in as administrator, just as a user. which is why you need the sudo password to modify the machine. and you need the sudo password to change permissions on files unless you are the creator/owner of the file.

---

