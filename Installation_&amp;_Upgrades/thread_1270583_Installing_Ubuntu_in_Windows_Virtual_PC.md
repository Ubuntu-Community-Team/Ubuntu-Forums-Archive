---
title: "Installing Ubuntu in Windows Virtual PC"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by Hydrohs on 2009-09-19
I've grown tired of dual-booting but I really would like to get familiar with Linux (I've tried numerous times before, all failures.) so I figured installing Ubuntu 9.04 to a virtual machine would be a good way to go. no thing is I'm using Windows Virtual PC - which is different than Microsoft Virtual PC 2007. It's the VPC that Windows 7 uses to run XP mode. I tried to install Ubuntu in it but the machine shuts down before it even loads the drivers etc. Wondering if anyone knows how i might fix my problem.

---

### Post by noelvh on 2009-09-19
Here is what I would do, head over to [Vbox]("http://www.virtualbox.org/") and download it for windows. Install that to use for the virtual software. Then load up ubuntu or wht ever you want. The new version of Vbox has some 3d video support but start with the basics. See I do the op of you and run XP in Vbox under Ubuntu.

Noel

---

### Post by Hydrohs on 2009-09-19
Alright, got Virtual box and installed Ubuntu fine and dandy but now I'd like to change the resolution for it. Do I need to install some sort of driver to let me do that, or can I do it through VBox?

---

### Post by noelvh on 2009-09-19
There is a add on to virtual box called guest addons. From the device menu at the top of the virtual box window click devices> Mount CD image>Select  VBoxguest addons iso (some thing like that). This will mount the cd on the guest machine. It should give you an auto run box let it run. If not you will have to run it from terminal with sudo. Once installed reboot, and then you can make changes, also you will have the mouse work in both OSs with out the ctrl key.

Give it a try.

Noel

---

### Post by Hydrohs on 2009-09-19
I got the CD to appear on the desktop in Ubuntu but it needs to be run as an administrator. I'm vaguely familiar with sudo, I know I need ot naviagte to the correct directory in the terminal before I can run it with sudo but I forget how to do all that.

---

