---
title: "Reinstall Jaunty 9.04"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by measekite on 2009-09-13
Some file or part of a file got hosed in a shutdown denying me DVI but permitting VGA.  I did uninstall nvidia and then reinstalled it but that did not solve the problem.  Maybe every file and line in Xorg did not get cleaned but who knows and there is not totally and complete uninstall for it that I can find.

**I would be interested in knowing if you can do this:**

I want to be able to boot LiveCD and do a reinstall that would completely overwrite all of the system files but leave my menus, panels, colors and everything that I customized alone and in place.

I welcome ideas and thanks in advance.

---

### Post by lswb on 2009-09-13
Did you already try the "repair graphics problems" option from the recovery mode menu?

---

### Post by measekite on 2009-09-13
> **lswb said:**
> Did you already try the "repair graphics problems" option from the recovery mode menu?

I have not seen that.  Could you supply some details?

---

### Post by Sgt-Slyde on 2009-09-13
Best option I can think of is to boot from the LiveCD, copy /home/"USERNAME" to a USB drive, then when running the reinstall see if it will import user accounts?  I don't know that this will work - I've only used the import options for dual-boot machines running Microsoft.

Trouble is, some of the configuration changes you've made may be stored in configuration files for those applications (windows controllers, screensavers, web browsers, etc.) and might not be captured by just backing up your user directory.  

Good Luck!

---

### Post by lswb on 2009-09-13
> **measekite said:**
> I have not seen that.  Could you supply some details?

When you boot your machine, if the grub menu is not visible, press <escape> after the bios messages end. There should be a grub menu item that says something about "recovery mode" Select that and the system will boot to a short text-mode menu. One of the options on that menu is to repair X or repair graphics, I don't recall the exact wording.

Or, if you can boot to a command prompt, either normally or through the recovery menu, use the command:

sudo dpkg-reconfigure -phigh xserver-xorg

In recovery mode, you are already running as root so the "sudo" is not required.

---

### Post by measekite on 2009-09-13
> **lswb said:**
> When you boot your machine, if the grub menu is not visible, press <escape> after the bios messages end. There should be a grub menu item that says something about "recovery mode" Select that and the system will boot to a short text-mode menu. One of the options on that menu is to repair X or repair graphics, I don't recall the exact wording.

Or, if you can boot to a command prompt, either normally or through the recovery menu, use the command:

sudo dpkg-reconfigure -phigh xserver-xorg

In recovery mode, you are already running as root so the "sudo" is not required.

As you suggested I did find it and did choose to repair xfix graphics.  Basically once I got to my logon I did get both DVI and VGA but the resolutions and the rest of the screen looked distorted.  I went to Synaptic and uninstalled everything that said nvidia in front of it.  After a reboot I installed from synaptic nvidia 180.  After I got rebooted and followed the on screen instructions I am back where I started.  No DVI but VGA.

This is something that I do not understand.  Why should this be so difficult to uninstall and reinstall a driver.  While I no longer use and like Windows do that was easy.

Any more ideas.  I would hate to have to do a reinstall and have all of the hours of reconfiguring after I spend a bunch of time writing notes to job my memory of what I have.

If nobody has an answer I will then do a reinstall when 9.10 comes out in about 6 weeks and run VGA for now.

It seems that people who use DVI have more issues than VGA.  This I do not understand.

Also in order to make any changes using the nvidia settings control panel you need to bring it up with gksu.  This I think is ridiculuous.

---

