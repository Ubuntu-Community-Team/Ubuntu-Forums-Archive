---
title: "Surprise, upgrade to 9.10 fails!"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Grozzy on 2009-10-29
Well, hello!

I started the upgrade process from the "Update Manager" and it went well in the beginning.
Suddenly it came alot of error messages about packages that could not be downloaded (probably because very slow internet connection).

Now when I try to start the process again, it says "Could not download the release notes - Please check your internet connection.", but the internet connection is working fine!

Please help, I really need to upgrade to the new cool 9.10! ;)
Thanks!
// Grozzy

---

### Post by gdonwallace on 2009-10-29
You might try running it from terminal with the following commands:

sudo apt-get update
sudo apt-get upgrade

You can also try **update-manager -d**, sometimes that will force the upgrade to happen.  You can also run the above command with sudo.

---

### Post by Grozzy on 2009-10-29
Thanks for the reply but it did not work! (Hah, classic)

apt-get update gave me some errors like
"W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783"

...and **update-manager -d **did not work either. Any other command that could really force the upgrade to proceed?

---

### Post by thered on 2009-10-29
you could try upgrading from the alternative CD - get it from a torrent site

[http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD]("http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD")

---

### Post by denham2010 on 2009-10-29
Hi,

I see this almost every upgrade to ubuntu there is.

The solution is quite simple, yet I have never seen it documented.

The problem is the upgrade process updates your sources.list file (this is the file that holds all the repositories you use in synaptic and apt).

If you have any 3rd party repositories enabled, they are not officially supported by Ubuntu, and therefore, the upgrade process does not know how to update these entries in the sources.list file for Karmic.

To fix this, open synaptic and edit your repositories. You need to delete, yes, delete not disable, all repositories in the 3rd party tab.

Of course, make a note of them so you can put them back (updated for Karmic of course) after the upgrade is complete.

Once you have deleted these, the upgrade process should get going.

Cheers.

---

### Post by horace on 2009-10-29
> **Grozzy said:**
> 
Now when I try to start the process again, it says "Could not download the release notes - Please check your internet connection.", but the internet connection is working fine!


Same happened to me, but I think it's just a problem with the server (main uk one in my case) - try changing to a different location in the update manager; worked for me and took up the download where it had left off.

---

### Post by chrisplymouth on 2009-10-29
It is probably best to load a fresh install of Ubuntu 9.10 - upgrades rarely deliver on their promises!

I spent an hour updating Mandriva 2010 RC2 last night only to discover the updated system was more unstable than the original.

---

### Post by Acid_1 on 2009-10-29
Try

```
sudo apt-get dist-upgrade
``` from the terminal.

---

### Post by DustofDust on 2009-10-29
> **denham2010 said:**
> Hi,

I see this almost every upgrade to ubuntu there is.

The solution is quite simple, yet I have never seen it documented.

The problem is the upgrade process updates your sources.list file (this is the file that holds all the repositories you use in synaptic and apt).

If you have any 3rd party repositories enabled, they are not officially supported by Ubuntu, and therefore, the upgrade process does not know how to update these entries in the sources.list file for Karmic.

To fix this, open synaptic and edit your repositories. You need to delete, yes, delete not disable, all repositories in the 3rd party tab.

Of course, make a note of them so you can put them back (updated for Karmic of course) after the upgrade is complete.

Once you have deleted these, the upgrade process should get going.

Cheers.

it automatically deselects the 3rd party repositories like you added from launchpad. after the upgrade just change jaunty into karmic and switch them back on.

dont forget to ad [http://www.playdeb.net](http://www.playdeb.net) if you like games! ;)

---

### Post by toontastic on 2009-10-29
> **horace said:**
> Same happened to me, but I think it's just a problem with the server (main uk one in my case) - try changing to a different location in the update manager; worked for me and took up the download where it had left off.

Yep I had the same problem and this has worked. Thanks for that by the way.

---

### Post by jheaton5 on 2009-10-29
This is the very reason that I do not advocate the use of GUI tools for updating.  Here is the best way I have found to do a distribution upgrade.

First, make sure that the current dist. is fully updated.  Then perform the following commands from the command line.
Second, edit your /etc/apt/sources.list file as root.  After that, perform the following commands:```
$ sudo aptitude update
$ sudo aptitude install apt aptitude dpkg
$ sudo aptitude safe-upgrade
$ sudo aptitude full-upgrade.
```

Yes, I know it is not the Ubuntu way, but it is the Debian way and it works.

---

### Post by wilee-nilee on 2009-10-29
> **Grozzy said:**
> Well, hello!

I started the upgrade process from the &quot;Update Manager&quot; and it went well in the beginning.
Suddenly it came alot of error messages about packages that could not be downloaded (probably because very slow internet connection).

Now when I try to start the process again, it says &quot;Could not download the release notes - Please check your internet connection.&quot;, but the internet connection is working fine!

Please help, I really need to upgrade to the new cool 9.10! ;)
Thanks!
// Grozzy

  So it sounds like you have not upgraded, are you aware of the ext3-ext4 that is provided by a fresh install, but not by upgrading, as well as the grub2 inclusion in a fresh install. Here is the torrent link if you decide to fresh install, this torrent downloaded at around 200-300 KiB's just a hour ago. [http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors) If you do a fresh install backup your data on a external device or a separate partition and install fresh.

---

### Post by user333 on 2009-10-29
> **Grozzy said:**
> Well, hello!

I started the upgrade process from the "Update Manager" and it went well in the beginning.
Suddenly it came alot of error messages about packages that could not be downloaded (probably because very slow internet connection).

Now when I try to start the process again, it says "Could not download the release notes - Please check your internet connection.", but the internet connection is working fine!

Please help, I really need to upgrade to the new cool 9.10! ;)
Thanks!
// Grozzy

Same here, only I have high-speed internet. :( One of the very few, but hard to figure out, things about ubuntu.

---

### Post by davidbilla on 2009-10-29
I too have some doubts about upgrading. 

I'm not sure whether to upgrade or do a fresh install, though I'd prefer to do a fresh install.

I have Jaunty now and have separate partitions for /usr, /boot, /, /home and /opt. How do I do a fresh install, with my */home* files and my programs in */usr/* and */opt* intact? What are the partitions that I need to format and how do I make sure that all my currently installed programs are retained?

Or is upgrading better?

Oh, and I have an AMD 64-bit processor but the installed version of Ubuntu is 32-bit. Should I change to 64-bit? Does that have any caveats? Can I do a fresh install of the 64-bit version keeping all my current programs intact?

---

### Post by davidbilla on 2009-10-30
Anybody there?

---

### Post by Grozzy on 2009-10-30
You know whats funny? I went into KDE and tried it from there, and it worked! Thanks everybody!
I really like the new login screen of 9.10 :p

---

### Post by paul cooke on 2009-10-30
> **jheaton5 said:**
> This is the very reason that I do not advocate the use of GUI tools for updating.  Here is the best way I have found to do a distribution upgrade.

First, make sure that the current dist. is fully updated.  Then perform the following commands from the command line.
Second, edit your /etc/apt/sources.list file as root.  After that, perform the following commands:```
$ sudo aptitude update
$ sudo aptitude install apt aptitude dpkg
$ sudo aptitude safe-upgrade
$ sudo aptitude full-upgrade.
```

Yes, I know it is not the Ubuntu way, but it is the Debian way and it works.

you forgot the one important command at the end...
```

$ sudo shutdown -r now
```

the one we all sweat over after an upgrade...

---

### Post by leonbravo on 2009-12-23
> **jheaton5 said:**
> This is the very reason that I do not advocate the use of GUI tools for updating.  Here is the best way I have found to do a distribution upgrade.

First, make sure that the current dist. is fully updated.  Then perform the following commands from the command line.
Second, edit your /etc/apt/sources.list file as root.  After that, perform the following commands:```
$ sudo aptitude update
$ sudo aptitude install apt aptitude dpkg
$ sudo aptitude safe-upgrade
$ sudo aptitude full-upgrade.
```

Yes, I know it is not the Ubuntu way, but it is the Debian way and it works.

Hey man, what would you suggest after trying the Debian way, receiving this error:

sudo aptitude update

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                 
  Could not connect to iccache.anu.edu.au:80 (130.56.71.50). - connect (113 No route to host)


that is a cache that I use at uni, but somehow fubuntu tries to do the same way at home.

cheers, mate

---

