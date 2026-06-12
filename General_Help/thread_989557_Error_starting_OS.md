---
title: "Error starting OS"
date: 2008-11-21
forum: General Help
---

### Post by penguinsrock on 2008-11-21
I have an older computer (Compaq PresarioSR1103WM, to be exact, if it helps) that I installed Ubuntu on. I get all the way through the process of formatting and copying the OS files to the hard disk, and when the it tries to run for the first time, I get a screen with a Pale (flesh colored) background, I can see and move the pointer around the screen, but nothing else. I am at a stand still as to what to do now, so any help would be appreciated. 

Thanks in advance.

---

### Post by taladan on 2008-11-21
it's a bit convoluted, but you probably need to install the correct driver for your card.  CTRL+ALT+F2 to get to a command line.  Log in then type:

```
apt-cache search `lspci|grep -i vga|cut -d' ' -f5`|grep driver
```

This should give you a list of graphics drivers (the compaq is probably running an intel, but this will make sure).

An explanation of the command(s):

apt-cache search - searches the apt repos for whatever you type after 'search'

` - back tick causes the shell to substitute the output of whatever follows it into whatever command comes before

lspci - lists devices on the pci bus

|grep -i vga - pipe the output of the previous command into grep and search for 'vga' case insensitive

|cut -d' ' -f5` - pipe it to cut using a space (' ') as the field delimiter and only return the 5th field (the name of the mfg), the back tick here returns that output to the search

|grep driver - pipe the output of the search to a grep for the word 'driver'.

This should return all the available driver files in the repos.

You can then use sudo apt-get install <whatever> to install the package you want.

Hope this helps,

Tal

---

### Post by penguinsrock on 2008-11-22
I have tired what was suggested and I couldn't even get it to a command line interface. So, my thought is that I somehow managed to get a bad install or something of the sort. I'm currently thinking that I should reinstall the OS from the current CD. If that doesn't work, I believe the next step after that is to delete my current image file and burn to a new CD and see what kind of results I get from there.


Edit: After getting to the command line interface I ran the specified command, got three results. I told it to install the one that seemed appropriate after the installation, I get a message that seems to tell me that the drivers are already installed and running.

"0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded" is the exact message that I get.

---

### Post by taladan on 2008-11-22
Well, my suggestion then would be to try and get it to start up with a vanilla xorg.conf.

From the command line try this:
```

sudo /etc/init.d/gdm stop
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo /etc/init.d/gdm start

```

This will stop the x server, move the xorg.conf file to a file named xorg.conf.bak and then restart the x server.  It will then create a base/default xorg.conf file...I don't know that this will help on a fresh install of the OS, but I know it's worked for me in the past on display issues.

Tal

---

