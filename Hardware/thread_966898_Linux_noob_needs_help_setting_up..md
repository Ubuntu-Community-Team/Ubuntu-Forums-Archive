---
title: "Linux noob needs help setting up."
date: 2008-11-01
forum: Hardware
---

### Post by Justin Letchford on 2008-11-01
Howdy all,

I'm starting on Ubuntu because I want to produce open-source animated films.

I'm just having some trouble setting up.

First off is my wireless adapter, Ubuntu help says I can use Windows drivers for it but I don't know how to do that without running the Windows .exe which you can't do in Ubuntu (to the best of my knowledge)

Help said to install an ".inf" file which I tried (I downloaded the Windows drivers and found the only two in there and tried them both) but it didn't work.

Second are my graphics card drivers, I downloaded the Linux version from ATI's website but it says I need to run as super-user to install it.

Please be patient with me, I have absolutely no idea what I'm doing with Linux.

Computer specs:

AMD Turion 64bit 1.6 ghz
ATI Mobility Radion X700
512 RAM

---

### Post by explainer on 2008-11-01
First: super-user privileges.  The 'sudo' command is a prefix to put you into super-user mode for the duration of the command, like this:

sudo apt-get install <<some package>>

The sudo command will prompt you for your password, the one you picked when you set up your account.  Put it in when sudo asks for it.  Then the command is run at super-user privileges.  This is generally necessary when you are attempting to directly modify any part of the file system outside of your 'home' directory.  If you logged in as 'jim', your home directory is /home/jim.

Second: networking.  Do you have any access to the internet at all?  If so, then you should be able to get the tools you need off the ubuntu package repository to complete your install.  If not, then things get a bit ugly.  I will assume you have network connectivity.

Use the Synaptic package manager to find the package 'wicd' and install it.  NOTE: you will be prompted for a password, it is the same one as above.  Wicd is a friendly gui tool that can help you configure your wifi.  It is better than the standard stuff that ships with ubunto, IMHO.

Good luck and keep posting.:)

---

### Post by Justin Letchford on 2008-11-01
> **explainer said:**
> First: super-user privileges.  The 'sudo' command is a prefix to put you into super-user mode for the duration of the command, like this:

sudo apt-get install <<some package>>

The sudo command will prompt you for your password, the one you picked when you set up your account.  Put it in when sudo asks for it.  Then the command is run at super-user privileges.  This is generally necessary when you are attempting to directly modify any part of the file system outside of your 'home' directory.  If you logged in as 'jim', your home directory is /home/jim.

:confused:

I'm a noob sorry, I have no idea how to enter a command.

> **explainer said:**
> Second: networking.  Do you have any access to the internet at all?  If so, then you should be able to get the tools you need off the ubuntu package repository to complete your install.  If not, then things get a bit ugly.  I will assume you have network connectivity.

Use the Synaptic package manager to find the package 'wicd' and install it.  NOTE: you will be prompted for a password, it is the same one as above.  Wicd is a friendly gui tool that can help you configure your wifi.  It is better than the standard stuff that ships with ubunto, IMHO.

Good luck and keep posting.:)

I will try that thanks :)

---

