---
title: "Problems after upgrade as virtualbox guest"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by user_adrian on 2009-04-26
I had problems after upgraded from Ubuntu 8.10 to 9.4.
I made the upgrade for Ubuntu as guest inside windows xp as host and virtualbox.
After upgrade I had the following messages.

Ubuntu is running in low graphics mode:
THe following errors encountered:
(ee)module major version(4) doesn't match server's version(5)
(ee)failed to load the module vboxvideo (module requirement mismatch, 0)
(ee)no drivers available


after clicking OK it shows:

-run Ubuntu in low graphic mode for just a session
-reconfigure graphics
-troubleshoot the error
-exit to console login

If I select troubleshoot it doesn't solve the problem.

If I select reconfigure graphics don't solve the problem.

So I run ubuntu in low graphics mode.

But other message appears:

There appears to be an x server running on display :0
I select to use another xserver.
another window says server was started on display 1.

I logged in.

Flash didn't work anymore but it says that the flash player is already installed.The mouse pointer doesn't allow me to arive at the upper Ubuntu menus. It blocks before reaching the menus. I have to try a couple of times until it allows me to reach the menus.

After using it another error appears and screen becomes black and white and is paused by virtualbox. If I remove the pause the error shows again so I can't use it. I have to reboot it.

What should be done. Should I download it and to make a fresh installation without upgrade?

---

### Post by user_adrian on 2009-04-26
I downloaded Ubuntu 9.4 and tried to make a fresh install on a new virtualbox virtual machine. After loading the iso cd it starts ubuntu in virtual box.

But a new error appears:

An error has occured during virtual machine execution!

Unable to allocate and lock memory. The virtual machine will be paused. Please close aplications to free up memory or close the VM.
Error ID: HostMemoryLow
Severity: Non-Fatal Error

I have 1.5 gb memory. I've put 700 MB for Ubuntu. With the previous version of ubuntu I never had this kind of problem.

What should be done?

---

### Post by oriongr on 2009-04-26
Same problem here..
I think it has to do with the virtualbox drivers...

---

### Post by user_adrian on 2009-04-26
I solved the problems. I mean I made a fresh install. It seems that it doesn't work with the upgrade inside of virtualbox. Or maybe you have to remove the vbox additions before making the upgrade. 
After the fresh install I added the vbox additions. I checked for enabling 3d accelerations, and now I have on my 22 inch screen an amazing Ubuntu at 1600*1050 pixels (16/10 aspect ratio), so the new Ubuntu is rocks!!!!!!!!!!

---

### Post by oriongr on 2009-04-26
Solved by reinstalling the Virtualbox Guest additions...

---

