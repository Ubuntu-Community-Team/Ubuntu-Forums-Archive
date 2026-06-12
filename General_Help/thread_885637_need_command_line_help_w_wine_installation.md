---
title: "need command line help w/ wine installation"
date: 2008-08-10
forum: General Help
---

### Post by A2JC4life on 2008-08-10
Okay, so I have yet to figure out my internet connection (working on it; still haven't heard back from the linmodems.org list), so I can't use the package manager to install anything.  Meanwhile, the second of the two things I need to see if I can get working to make the permanent switch to Linux (the first being the internet connection) is a Windows-only program I want to try under Wine.  So I downloaded the Wine package from their website, looked up how to install a .deb package, and booted into Linux to try it.

The first problem I had was with changing the directory.  The Wine package was in /home/rachel/Desktop/Documents, but Ubuntu was telling me that this location does not exist. :confused:  When I tried running dpkg -i (and pkg name here), from right where I was, just to see what it would do, I got a message saying I could only do that as root.

So I closed the terminal and tried just going and double-clicking on the .deb icon. This was slightly more successful; it actually tried to run an installer, but I got the following message:

[INDENT]Error: Wrong architecture 'lpia'[/INDENT]

(The filename is wine_1.0.0~winehq0~ubuntu~8.04-1_lpia.deb)

So I have several questions:
1. Why can I not change to the directory mentioned above?
2. If I get a message saying that I can only perform an action as root, what options do I have?
3. Why can I not install this package of Wine, which is specifically listed as designed for Ubuntu 8.04?

---

### Post by linux_tech on 2008-08-10
Did you try sudo dpkg -i <packagename>

---

### Post by sisco311 on 2008-08-10
You downloaded the wrong version of wine.
Which version of ubuntu are you using?
32bit or 64bit?

If you are unsure, then post the output of:
```
uname -a
```

---

### Post by dexter.deepak on 2008-08-10
> **A2JC4life said:**
> 
So I have several questions:
1. Why can I not change to the directory mentioned above?
2. If I get a message saying that I can only perform an action as root, what options do I have?
3. Why can I not install this package of Wine, which is specifically listed as designed for Ubuntu 8.04?

1. are you sure you have that location ? the documents folder should be   /home/rachel/Documents

2. for running a command as root, you need sudo or gksu (for gui)
  like:
  sudo nano /etc/fstab
  gksu gedit /etc/fstab

3. what are your system specs ?

---

### Post by linux_tech on 2008-08-10
[http://wine.budgetdedicated.com/archive/ubuntu/hardy/](http://wine.budgetdedicated.com/archive/ubuntu/hardy/)

lpia.deb is for power pc; 
what kind of cpu do you have, mac, amd, intel? 
Is it 32 bit or 64 bit

You need to select the correct deb pkg

---

### Post by Yellow Pasque on 2008-08-10
> 1. Why can I not change to the directory mentioned above?
It either doesn't exist or you don't have permissions for it.

> 2. If I get a message saying that I can only perform an action as root, what options do I have?
Use the word sudo preceding the command (the password should be the same as your user account), e.g:
```
sudo dpkg -i ...
```

> 3. Why can I not install this package of Wine, which is specifically listed as designed for Ubuntu 8.04?
The package is made for a certain type of processor, which is not what you have. Most likely, you have an x86 processor. Find out with:
```
uname -a
```

Once you get the correct package and try to install it with sudo, you will most likely need other packages as dependencies. The best thing to do would be to get your internet working.

---

### Post by A2JC4life on 2008-08-10
I didn't try sudo.

Oh, and you're right about the location.  I'm not sure why I put "desktop" here.  I did it right; I typed it wrong here.  I was trying to change to /home/rachel/Documents/Programs (Programs being a folder I created, to have someplace to put the package.)

x86 sounds correct as my processor type.

So, what Wine package do I need?  Even if I get the internet working, etc., I did not see Wine in the repository list.

---

### Post by linux_tech on 2008-08-10
i386 Pkg:

wine_0.9.60~winehq0~ubuntu~8.04-1ubuntu1_i386.deb       19-Apr-2008 08:03  7.8M 

Wine deb download page:
[http://wine.budgetdedicated.com/archive/ubuntu/hardy/](http://wine.budgetdedicated.com/archive/ubuntu/hardy/)

sudo dpkg -i <packagename> to install as root

---

### Post by linux_tech on 2008-08-10
You can also download it direct from wine

[http://www.winehq.org/site/download](http://www.winehq.org/site/download)

---

### Post by sisco311 on 2008-08-10
Direct link to the file: [http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.1.2~winehq0~ubuntu~8.04-2-0ubuntu1_i386.deb]("http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.1.2%7Ewinehq0%7Eubuntu%7E8.04-2-0ubuntu1_i386.deb")

---

### Post by sisco311 on 2008-08-10
> **A2JC4life said:**
> 
So, what Wine package do I need?  Even if I get the internet working, etc., I did not see Wine in the repository list.

First add the wine repository to your system's list,
then install it with Synaptic or Add/Remove. 
> 
**Adding the WineHQ APT Repository:**

  First, open a terminal window (Applications->Accessories->Terminal).Then add the repository's key  to your system's list of trusted APT keys by copy and pasting the following:
  *wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -*
  Next, add the repository to your system's list of APT sources:
  **For Ubuntu Hardy (8.04):**
*sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list*
   Then update APT's package information by running '**sudo apt-get update**'.  
 
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by A2JC4life on 2008-08-11
Thanks!

---

