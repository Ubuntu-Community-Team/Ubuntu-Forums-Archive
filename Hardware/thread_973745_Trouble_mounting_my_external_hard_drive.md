---
title: "Trouble mounting my external hard drive"
date: 2008-11-07
forum: Hardware
---

### Post by Neurasthenic on 2008-11-07
Hi, I'm a long-time Windows user who just today decided to give Intrepid Ibex a shot. I've used various Linux distros before, but always ran into hardware compatibility issues or various other problems that sent me back to Windows. Well, this might finally be the version to make me a full time Linux user. 

My one problem so far that I haven't found a fix for by looking through the forums - my external hard drive won't mount. I get this error:

Unable to mount the volume 'Storage'.

$LogFile indicates unclean shutdown (0, 0) Failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2: if you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g /dev/sdb1/media/Storage -o force Or add the option to the relevant row in the /etc/fstab file: /dev/sdb1/media/Storage ntfs-3g force 0 0

I tried typing that exact command and it came up with a general help list for the mount function as far as I can tell. I'm pretty inexperienced with all this.

---

### Post by Neurasthenic on 2008-11-07
Nevermind, disregard my problem. I didn't realize that not disconnecting the drive properly from Windows this morning would put it in a state where I couldn't even mount it anymore, I figured it wasn't a big deal. I just hooked it up to my friend's Windows machine and then did the "safely remove hardware" deal. Now it's mounting just fine in Ubuntu.

---

