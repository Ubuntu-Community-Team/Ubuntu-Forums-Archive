---
title: "Minimal install: accessing applications"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by jhsu802701 on 2009-09-19
I tried the default Xubuntu installation but found it to be too slow.  So now I'm trying a minimal installation (initially command line system).

What package(s) do I need to be able to access Synaptic and other applications when I download?  I installed xfce4 (for the GUI) and xorg, but right-clidking the mouse on the desktop doesn't show the full menu of programs.

I'm going to try jwm next because it's even lighter-weight than XFCE.  What package(s) do I need to install in order to access Synaptic, web browsers, Synaptic, etc.?

---

### Post by Partyboi2 on 2009-09-20
To install synaptic 
```
sudo apt-get install synaptic
```
For web browsers it all depends on which one you want to use
[https://help.ubuntu.com/community/Installation/LowMemorySystems#Browsers](https://help.ubuntu.com/community/Installation/LowMemorySystems#Browsers)

---

### Post by jhsu802701 on 2009-09-20
After I install a window manager, Synaptic, a web browser, terminal program, etc., how do I access these things from the GUI?

---

### Post by Partyboi2 on 2009-09-20
It all depends on what Desktop you have installed. What Desktop are you using?

---

### Post by jhsu802701 on 2009-09-20
OK, I reinstalled Xubuntu in the minimal command-line installation.  I downloaded and installed the following packages: idesk, xorg, jwm, menu, slim, synaptic, and seamonkey-browser.

My questions:
1.  How do I shut down the computer?  JWM -> Exit gets me from the GUI back to command line.  I tried "sudo shutdown 0", but that seemed to reboot rather than shut down.
2.  How do I get Synaptic to download and install packages?  For some reason, the sudo permissions aren't getting through, and I can only search and read the package descriptions.

---

### Post by Partyboi2 on 2009-09-21
> 1. How do I shut down the computer? JWM -> Exit gets me from the GUI back to command line. I tried "sudo shutdown 0", but that seemed to reboot rather than shut down.

From the terminal try
```
sudo shutdown -h now
```

> 2. How do I get Synaptic to download and install packages? For some reason, the sudo permissions aren't getting through, and I can only search and read the package descriptions.
Are you able to install a package from the terminal?
```
sudo apt-get update
sudo apt-get install package
```
Can you post the outputs from the terminal when you try to install a package.

---

### Post by jhsu802701 on 2009-09-21
I ended up having to install and enter XFCE just so I could properly shut down the computer.  In XFCE, I have menu access to the Seamonkey application I downloaded, but the menu doesn't show Synaptic anywhere.  Also, once I minimize the Seamonkey window in XFCE, it completely disappears.

Is there a forum somewhere specifically dedicated to minimal Ubuntu/Xubuntu installations?  I know that I'm missing some critical packages for XFCE, JWM, and fluxbox (the window managers I have installed).

---

