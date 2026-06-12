---
title: "Ati Drivers - .run?"
date: 2008-09-02
forum: General Help
---

### Post by LazyLlama on 2008-09-02
Hi,
I'm completely new to Ubuntu - I know virtually nothing, I just got it yesterday. I downloaded the drivers for my graphics card but - even though it was meant for linux - is a .run file. Please can anyone tell me how I can open and run this file Ubuntu?

---

### Post by WRDN on 2008-09-02
If you are new to Linux, then you may want to use EnvyNG to install the driver. The program is available in the repositories.

When installing drivers from a run file, you should stop GDM (Graphical Display Manager), so first, press Ctrl, Alt and F1. Now, login at the shell, and type:

```
sudo /etc/init.d/gdm stop
```

Now, change directory to where the driver is located:

```
cd [directory]
```

You now need to give the driver executable properties.

```
chmod +x [driver_name].run
```

Start the run file using the command:

```
sudo ./[driver_name].run
```

Remember, you can use the wildcard (*) instead of typing the name each time.

Once it has installed, start GDM again:

```
sudo /etc/init.d/gdm start
```

---

### Post by eggdeng on 2008-09-02
You will find it easier and safer to install the appropriate driver from the repos.
First go to System -> Administration -> Software Sources and tick the checkboxes for community maintained and restricted software. Click Reload at the prompt.
Now go to System -> Administration -> Hardware Drivers and you should be given an option to install / enable the ATI Proprietary driver.

---

### Post by soxs on 2008-09-02
> **WRDN said:**
> If you are new to Linux, then you may want to use EnvyNG to install the driver. The program is available in the repositories.

When installing drivers from a run file, you should stop GDM (Graphical Display Manager), so first, press Ctrl, Alt and F1. Now, login at the shell, and type:

```
sudo /etc/init.d/gdm stop
```

Now, change directory to where the driver is located:

```
cd [directory]
```

You now need to give the driver executable properties.

```
chmod +x [driver_name].run
```

Start the run file using the command:

```
sudo ./[driver_name].run
```

Remember, you can use the wildcard (*) instead of typing the name each time.

Once it has installed, start GDM again:

```
sudo /etc/init.d/gdm start
```
This is simply wrong, the ati drivers doesn't require to stop gdm or kdm.

Do you know how to change your directory in console and how relative/absolute paths "work"?

If not, ask, if you know proceed.

Make the file executbale
```
chmod +x /path/to/driver/ati.....run
```

Install requirements in order to create packages and install them:
```
sudo apt-get install cdbs build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r)
```

Start the run file using the command:
```
sudo /path/to/driver/ati.....run --buildpkg Ubuntu/hardy
```

if that is done, install the packages via (assuming only the driver debian packages are in your current folder, ./ represents your current folder):
```
sudo dpkg -i ./*.deb
```

NOTE: You will have either to edit /etc/X11/xorg.conf by hand (replace mesa with fglrx in the Device section) and save wit superuser rights or use aticonfig --initial

Ask if don't understand something or if you want to know something more.

---

### Post by LazyLlama on 2008-09-02
No, I don't know how to change the directory.
  I would love to know!

---

### Post by eggdeng on 2008-09-02
Just install from the repos, it will save you a lot of time and trouble 8-)

---

### Post by soxs on 2008-09-03
> **eggdeng said:**
> Just install from the repos, it will save you a lot of time and trouble 8-)

Depends on your state of mind, if you are willing to evolve (and get bleeding edge fglrx drivers) to do it yourself.


To change a dir, type in terminal:
Relative paths:
```
cd ..
``` This will change into the parent directory

```
cd ./
``` This will change into the current directory, so you it won't do anything

You can make quite complex path changes, e.g.:
```
cd ./../soxs/Documents
```

```
cd /home/$USER/Documents
``` This will change into the current useres home directory, the $USER is a shell variable and represents your current aktive user. (to see what var it has type "echo $USER" in a terminal) Note: this doesn't work for root, as its home dir is /root.

```
cd $HOME/Documents
``` or ```
cd ~/Documents
``` will do quite the same thing, but it works for root aswell

So you don't know which folders a subfolder contains, so there is a command to read out all files in a dir:
```
ls
``` (preferably use "ls -Al")
which will give you a list of all containing items (A switch will show you hidden and backup files (files with a trailing ~)

Play around a little and get used to it, you won't go back toGUI when you know howto do it within a terminal ;-)


Permissions:
Permissons can be changed via "chmod"
permissions are rwxrwxrwx
r=read; w=write; x=execute
the trippe is becuase of free diffrent groups:
first tripel is realted to the file owner
2nd triple is for the usergroup the file owner is in
3rd triple is for any other users

to make a file executable, simply type:
```
chmod +x ./filename
``` (maybe with "sudo" prefix, which makes it being execute with superuser rights
This will add the "x" var to all 3 tripels

There is another way to set permissions:
```
chmod 0755 ./filename
``` which will set the permissions as the following: rwxr-xr-x

If you want to know more about any command, use man <command> e.g. ```
man chmod
``` or ```
man chown
```

This seems to be dry, but it will get jiucy whenever it comes to the point you need it^^

---

### Post by Shujinko on 2008-10-09
Hi there.  I'm very new to Linux so please bear with me.  I'm following soxs' steps in post #4 for installing the ATI driver.  I got to the following step and have tried it a number of ways (thinking there was a possible typo) but it still won't build (if that's even the correct term for what I'm doing :)).

```
$ sudo ati*.run --buildpkg Ubuntu/hardy
sudo: ati-driver-installer-8-9-x86.x86_64.run: command not found
```

Appreciate the help.  Thanks!

---

### Post by soxs on 2008-10-09
> **Shujinko said:**
> Hi there.  I'm very new to Linux so please bear with me.  I'm following soxs' steps in post #4 for installing the ATI driver.  I got to the following step and have tried it a number of ways (thinking there was a possible typo) but it still won't build (if that's even the correct term for what I'm doing :)).

```
$ sudo ati*.run --buildpkg Ubuntu/hardy
sudo: ati-driver-installer-8-9-x86.x86_64.run: command not found
```

Appreciate the help.  Thanks!

It has to be ```
sudo ./ati*.run --buildpkg Ubuntu/hardy
``` without ./ ubuntu thought this was a generic command and searched /usr/bin for that command, and as it does not exist there, it reminds you about "no such file"

Btw, if you didn't knwo, there is a "thanks" button. Do what my signature says about it ;-)

---

### Post by Shujinko on 2008-10-09
Haha, I was waiting for you to respond before I did it! :)  Worked just fine.  Thanks again.

---

