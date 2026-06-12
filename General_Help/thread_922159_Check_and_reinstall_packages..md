---
title: "Check and reinstall packages."
date: 2008-09-17
forum: General Help
---

### Post by JacobSteelsmith on 2008-09-17
I used sudo with the wrong program (the binary version of calibre) and, after giving it the installation location for calibre as /usr/bin, I had that location completely wiped before calibre was installed. Fun things happened immediately after that, including the maxing of 3 GB of swap and 4 GB of ram. 

I got my system back up and running by copying the files from /usr/bin on the live cd to the local file system. 

However, I have a problem with missing binaries. My package managers think the software is installed, but many, many binaries are missing. I am able to restore the binaries by removing, then installing the packages, but this is scary for some packages. And it's slow. Also, there are probably binaries that are now the wrong version, but the package managers do not know this.

So I'm sitting here, watching my raid volume sync, wondering if there is a way to automatically check a package installation and fix it. Can anyone help?

---

### Post by prshah on 2008-09-17
> **JacobSteelsmith said:**
> 
wondering if there is a way to automatically check a package installation and fix it.

Don't know about checking, but in your case, I'd suggest you simply "online" reinstall the missing binaries with the following procedure:

Boot normally.

Switch to a virtual console with Ctrl+Alt+F1. Login as normal. Take down the GUI```
sudo /etc/init.d/gdm stop
```

Re-install the basic packages```
sudo apt-get --reinstall install ubuntu-desktop
``` 

Then bring the GUI back up the the below command (though I would suggest a restart instead; just press Ctrl+Alt+Del when finished and back at the prompt.)```
sudo /etc/init.d/gdm start
```

If any other packages give you trouble, reinstall them the same way, and finally, run an update and upgrade```
sudo apt-get update && sudo apt-get upgrade
``` to bring all your packages to the latest repository versions.

---

### Post by JacobSteelsmith on 2008-09-17
Thank you very much for your reply. That is essentially what I am doing now, but your instructions will help with core systems like dbus. 

Some binaries are missing or corrupted to the point of not running. Ever since this happened, KDE 4 will not run. I get a message similar to "dbus could not start, check your installation," which I will research. Your suggestion solves that. 

The more difficult problem is old binaries or missing binaries that aren't that apparent. The package managers have no knowledge, nor do they seem to check, on the state of the binaries themselves. For example, ksensors was a binary that was wiped out:

```
jacob@jakes-desktop:~$ ksensors
The program 'ksensors' is currently not installed.  You can install it by typing:
sudo apt-get install ksensors
bash: ksensors: command not found
jacob@jakes-desktop:~$ sudo apt-get install ksensors
[sudo] password for jacob:
Reading package lists... Done
Building dependency tree
Reading state information... Done
ksensors is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jacob@jakes-desktop:~$
```

So I have to uninstall, then reinstall ksensors. 

Also, say if sudo was upgraded in between the cd release and now, I have to the version that came with the cd, but the package managers think I have the latest version. 

I'm going to try to write a bash script that will solve my problems, but if anyone has any suggestions, please let me know. Thanks!

---

### Post by JacobSteelsmith on 2008-09-17
I found two easier ways to remedy this situation. First, on individual packages, you can use:

```
$ sudo apt-get --reinstall install $PACKAGE
```

where $PACKAGE is the name of the package. I just opted to reinstall all packages, although I was able to recover *most* of what I lost using the method above. To reinstall all packages, I am following the instructions here:

[http://ubuntuforums.org/showthread.php?t=735693&highlight=reinstall+all+packages+without+reinstalling+ubuntu](http://ubuntuforums.org/showthread.php?t=735693&highlight=reinstall+all+packages+without+reinstalling+ubuntu)

The bash script probably could have been enhanced to only reinstall packages found in /usr/bin, but it probably would have taken me just as long to figure that out as it is reinstalling all packages. 

Thanks again.

---

