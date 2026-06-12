---
title: "problem with updating ubuntu jaunty"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by peachtree195 on 2009-09-09
When updating today the manager went almost the whole way and then this thing showed up that i do not understand how to fix it

There was a window with a "no entry" sign saying
"Could not download all repository indexes
The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct."

of course the internet connection is working, i am writing this post right now
lower down in a box there was a following info:

GPG error: [http://deb.opera.com](http://deb.opera.com) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAEGPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAAGPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC6D7D9D009ED615GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 66D5C734F6EFB904GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DEGPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4FEC45DD06899068GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6298AD34413576CBGPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7FB8BEE0A1F196A8GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D79F61BE8D31A30GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D739676F7613768DFailed to fetch [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/binary/Packages](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/binary/Packages)  Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/source/Sources](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/source/Sources)  Unable to fetch file, server said 'Failed to open file.  '
Some index files failed to download, they have been ignored, or old ones used instead.

The system is relatively new, a couple of weeks since i got rid of Windows completely, and ubuntu was succesfully updating before.

The thing is that i am a very fresh linux person, I just love the idea about freedom of software and want to be a part of it.

---

### Post by Partyboi2 on 2009-09-09
You need to add the gpg key for those repos. For the launchpad ones open a terminal and 
```
gpg --keyserver keyserver.ubuntu.com --recv  DCF9F87B6DFBCBAE
gpg --export --armor  DCF9F87B6DFBCBAE | sudo apt-key add -
```Replace the 'DCF9F87B6DFBCBAE' string with the correct ones from the output of the launchpad 'NO_PUBKEY ***********' work through the list till you have done all the launchpad ones.
Then back in the terminal
```
sudo apt-get update
```For the medibuntu one type or paste
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```For the wine repo one,
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
``````
sudo apt-get update
```Edit: For the virtualbox one use[FONT=monospace]
[/FONT]```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
``````
sudo apt-get update
```Edit2: For the Opera one[FONT=monospace]
[/FONT]```
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys F9A2F76A9D1A0061
gpg --armor --export F9A2F76A9D1A0061 | sudo apt-key add -
``````
sudo apt-get update
```

---

### Post by wojox on 2009-09-09
To add your ppa keys look at this link:

[https://help.launchpad.net/Packaging/PPA/InstallingSoftware](https://help.launchpad.net/Packaging/PPA/InstallingSoftware)

Open your terminal and enter:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 12345678

Replacing 12345678 with the key in the sources list.


For Opera:

wget -O - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -

Don't know about MySQL.

---

### Post by peachtree195 on 2009-09-09
some of the commands the system took from me, some of them he spit back at me. The first one i put

baa@baa-laptop:~$ gpg --keyserver keyserver.ubuntu.com --recv  F9A2F76A9D1A0061GPG
gpg: "F9A2F76A9D1A0061GPG" not a key ID: skipping
baa@baa-laptop:~$ 

baa@baa-laptop:~$ gpg --keyserver keyserver.ubuntu.com --recv  NO_PUBKEY F9A2F76A9D1A0061GPG
gpg: "NO_PUBKEY" not a key ID: skipping
gpg: "F9A2F76A9D1A0061GPG" not a key ID: skipping
baa@baa-laptop:~$ gpg --keyserver keyserver.ubuntu.com --recv  F9A2F76A9D1A0061GPG
gpg: "F9A2F76A9D1A0061GPG" not a key ID: skipping
baa@baa-laptop:~$ gpg --keyserver keyserver.ubuntu.com --recv  DCF9F87B6DFBCBAEGPG
gpg: "DCF9F87B6DFBCBAEGPG" not a key ID: skipping

so it seems that whatever number i put there - following your advice: from the output of the launchpad - it just does not want to work. Or I don't understand you right. Or I put something wrong in there.

btw - what is the meaning of such commands, why does the system require public keys from me?
Is it that I never had installed those public keys, I lost them, i installed them improperly, something is not working well in my system and got wrong, what is it?
Without understanding this I will just follow someone else's commands and never will know what it means.

Still willing to fight through, thus making to the end of my second post :)

---

### Post by Partyboi2 on 2009-09-10
You need to remove the GPG from the end of the string so
```
F9A2F76A9D1A0061[COLOR=Red]GPG[/COLOR]
```
becomes
```
F9A2F76A9D1A0061
```
Have a read through of [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=680292"), and [[COLOR=Blue]this[/COLOR]]("http://en.wikipedia.org/wiki/GNU_Privacy_Guard"),  it should give you a general idea about gpg keys.

---

### Post by peachtree195 on 2009-09-10
Thanks for your help. Now the only thing that stays unsolved is the mysql. When i open the update manager I see that the system has been updated 8 days ago and is up to date. When I click 'check' for updates it loads about 222 files, and stops with 221 file, cancels the process and the message I get is:

Failed to fetch [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/source/Sources](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/source/Sources)  Unable to fetch file, server said 'Failed to open file.  '
Some index files failed to download, they have been ignored, or old ones used instead.

Also from time to time there is a yellow warning triangle popping up on my desktop with a system warning

Is it the mysql that is responsible for this? What happens if i delete it? Can the system work without it?

---

### Post by Partyboi2 on 2009-09-10
Make sure that you have the correct repository address for the mysql ftp, if you don't need it I would suggest disabling it in Software Sources (System>Admin>Software Sources>3rd Party). You can always re-enable it at a later date if you need it.

Edit: I think the correct repositories for mysql workbench are
```
deb ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/ binary/
deb-src ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/ source/
```

---

### Post by peachtree195 on 2009-09-14
Thanks for helping - so far i managed to turn mysql off from updates. I can't even try out your solution with the right repo address because in the meantime i am having serious monitor backlight/inverter problems so the screen stays black - no big chances of trying anything out anymore. Waiting for replacement parts and working on a borrowed computer right now.

---

### Post by hubertofliege on 2009-09-15
the addresses you gave for the Sql sources are the addresses in my source list which aren't working.  Any other ideas?

---

### Post by Partyboi2 on 2009-09-16
> **hubertofliege said:**
> the addresses you gave for the Sql sources are the addresses in my source list which aren't working.  Any other ideas?
Looks like its a problem with the mysql repo. If you don't mind manually installing mysql workbench you can follow this through:
[https://help.ubuntu.com/community/MySqlWorkBench](https://help.ubuntu.com/community/MySqlWorkBench)

---

