---
title: "ATI FGLRX Driver Question?"
date: 2009-09-27
forum: Hardware
---

### Post by Dan09 on 2009-09-27
Hi everyone!  I have a question regarding activating the proprietary ATI FGLRX graphics driver.

I have a ATI Radeon HD 3870 card and was having no luck at enabling desktop effects in my installation of Jaunty, so I tried enabling the driver in "Hardware Drivers".  After rebooting as prompted, Ubuntu went completly haywire and wouldn't boot up.  The shutdown splash screen had lines running all over it and the screen was showing some crazy things, then everything just went completly dark...?

I ended up having to complely reinstall Ubuntu via CD because I couldn't even get to a command line to disable the driver (nothing of value was lost, no worries!).

Does anyone have any idea on what is going long and/or what I could do to fix it?  Thanks very much!

EDIT :

Also, for the heck of it, here is the output of compiz when entered into the Terminal.

```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity
```

---

### Post by bell1996 on 2009-09-27
Dan09

I think I experienced the same problem just yesterday(but with Hardy). But I think the procedure should be the same.

When you install the ATI drivers you have to do one more thing. You have to edit /etc/modprobe.d/blacklist-local file. It should have one line in the file. Just comment it out, but putting a # in front of it. I just posted my procedure on another thread yesterday. I'll try and find it and re-post it for you. Otherwise, I did write it up in a text file for future reference for myself.

---

### Post by bell1996 on 2009-09-27
Dan09 -

I didn't feel like hunting down the post so I just pasted my procedure below. Let me know if this helps. Also, you should always be able to get to a prompt during boot up. Just hit the ESC key and choose recovery option. Then you'll be presented with another menu selection. The one you definitely want is the one to fix the x server. Use this is you boot up and your screen goes crazy.

Here's the steps:

After several hours of install, de-install, and troubleshooting, I finally found the solution.

I can't take take credit for the solution, because I found it here at [http://ubuntuforums.org/showthread.php?t=766699&page=5](http://ubuntuforums.org/showthread.php?t=766699&page=5)
by a post from "Isilion".

So here's what I did:

Installed the ATI drivers provided by at the [www.amd.com](www.amd.com) website:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.38&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.38&lang=English)

I have the Catalyst 9.2 version, but I think the latest version is 9.8 or 10.0 (I need to upgrade mine). Just download the latest version available.

Just follow the installer instructions. Installation application begins when you issue the following command:

sudo ./ati-driver-installer-9.2-x86_64.run

Take the defaults and it should only take about 1-2 minutes at most.

Don't forget to issue the last command: sudo /usr/bin/aticonfig --initial

Now it'll ask you to Re-boot. DON'T!! You have one other step to do.

Edit the following file (using your favorite editor. i use gedit)

sudo gedit /etc/modprobe.d/blacklist-local

Now comment out the one line but adding a "#" in front. It should look like this:

#blacklist fglrx

Now save.

Now reboot.

All should be good.

---

### Post by Dan09 on 2009-09-28
> **bell1996 said:**
> Dan09 -

I didn't feel like hunting down the post so I just pasted my procedure below. Let me know if this helps. Also, you should always be able to get to a prompt during boot up. Just hit the ESC key and choose recovery option. Then you'll be presented with another menu selection. The one you definitely want is the one to fix the x server. Use this is you boot up and your screen goes crazy.

Here's the steps:

After several hours of install, de-install, and troubleshooting, I finally found the solution.

I can't take take credit for the solution, because I found it here at [http://ubuntuforums.org/showthread.php?t=766699&page=5](http://ubuntuforums.org/showthread.php?t=766699&page=5)
by a post from "Isilion".

So here's what I did:

Installed the ATI drivers provided by at the [www.amd.com]("http://www.amd.com") website:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.38&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.38&lang=English)

I have the Catalyst 9.2 version, but I think the latest version is 9.8 or 10.0 (I need to upgrade mine). Just download the latest version available.

Just follow the installer instructions. Installation application begins when you issue the following command:

sudo ./ati-driver-installer-9.2-x86_64.run

Take the defaults and it should only take about 1-2 minutes at most.

Don't forget to issue the last command: sudo /usr/bin/aticonfig --initial

Now it'll ask you to Re-boot. DON'T!! You have one other step to do.

Edit the following file (using your favorite editor. i use gedit)

sudo gedit /etc/modprobe.d/blacklist-local

Now comment out the one line but adding a "#" in front. It should look like this:

#blacklist fglrx

Now save.

Now reboot.

All should be good.

Wow!  Thanks a ton!  I'll try this out ASAP, I'm looking forward to getting Ubuntu running the way I remember it back in Feisty Fawn (lul)!

I'll do my best to update this post after I've done everything.

Thanks again!

---

### Post by Dan09 on 2009-09-28
Wow I fail!  Haha. I managed to screw up the very first part of the process!

Here is the output of the first command :

```
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.65...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib::none:2.6.28-15-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.wHLdnG
```

---

### Post by bell1996 on 2009-09-28
I can't help you there. I don't know how to assist you with that error. Maybe someone else has a suggestion.

---

### Post by markbuntu on 2009-09-28
If that is a 3870x2 you need to jump through some hoops to get it working. There is a thread about that in the multimedia and video forum here.

---

### Post by Yellow Pasque on 2009-09-29
You can try the open-source way: [http://ubuntuforums.org/showthread.php?t=1257453](http://ubuntuforums.org/showthread.php?t=1257453)

---

