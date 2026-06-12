---
title: "Firefox Does Not Open"
date: 2008-08-19
forum: General Help
---

### Post by TreadLight on 2008-08-19
Once I select the Firefox Web Browser button, the only thing it says is that it is starting. But it never comes up as a window, and the process just ends.

I just installed Ubuntu a few hours ago, so I'm completely new to this. Please help!

---

### Post by trillions on 2008-08-19
are you connected to a network?

---

### Post by TreadLight on 2008-08-19
Yes, I am. Everything is working fine, besides Firefox not opening correctly.

---

### Post by coffeecat on 2008-08-19
Open a terminal (Application > Accessories > Terminal) and type 'firefox' (no quotes) and return. See if any error messages appear in the terminal and post them if they do.

---

### Post by TreadLight on 2008-08-19
It says:

"Could not find compatible GRE between version 1.9.8. and 1.9.8.*."

---

### Post by Loaded.len on 2008-08-19
Check this post to see if it'll help you... [http://ubuntuforums.org/showthread.php?t=570555](http://ubuntuforums.org/showthread.php?t=570555)

---

### Post by coffeecat on 2008-08-19
You say 'installed Ubuntu a few hours ago'. Have you installed anything since - updated anything? Done a partial update? Because [according to this bug]("https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/201938") and [this bug]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/201966") this could be something to do with incompatible packages.

If you haven't done so already, go to System > Adminstration > Update Manager and do a full system update. But first go to System > Administration > Software Sources > Updates tab and make sure the Proposed and Unsupported boxes are not ticked. **Do not use Proposed Updates - they will break your system.**

After a full update you will probably have to do a reboot into the new kernel.

---

### Post by TreadLight on 2008-08-19
Sorry that I did notmention this earlier, but I didn't think it'd matter:

I tried the update manager, and in the middle of Ubuntu being updated,my computer shutdown from overheatting.

Now, I just tried opening the Update Manager, but absolutelynothing happens.

---

### Post by coffeecat on 2008-08-19
It sounds as though a partial upgrade has broken several things, but this should be fixable. By the way, during an upgrade, the package/update manager downloads all the package files first, caches them and then installs them, so if the interrupted upgrade occurred during the install stage, what I'm about to suggest may not result in any packages being downloaded.

Open a terminal and:

```
sudo apt-get update
```You'll be prompted for your password and, yes, it is going in when you type it. The no feedback is a security feature, not a bug! The update simply downloads and resynchronises the package index files to make sure you get the latest. Now:

```
sudo apt-get upgrade
```Hopefully this will finish off the interrupted upgrade. Now reboot and test everything that was not working.

---

