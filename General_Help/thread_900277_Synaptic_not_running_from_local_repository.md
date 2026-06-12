---
title: "Synaptic not running from local repository"
date: 2008-08-25
forum: General Help
---

### Post by Battalion on 2008-08-25
Hi all,

I'm still using Ubuntu 7.04 but am considering upgrading to Ubuntu 8.04.  I am a user without internet on my local pc thus i update everything on a university ftp server with repositories for all my needs in the 7.04 version, which i then take home to update my pc.  I am trying to do the same thing on 8.04 but it will not update because it cannot locate the files on the university server thus i cannot update the packages.

How do i fix this problem?  I have edited the file /etc/apt/sources.list manual as i used to on the 7.04 but this doesn't work on 8.04.

Are there any other methods to fix my problem?

Thanks

---

### Post by caljohnsmith on 2008-08-25
What is exactly is the entry for your University in sources.list? And I'm not clear, is the Ubuntu 7.10 on a different computer than your PC at home, which has 8.04? It sounds like the 7.10 computer is at your campus, and your 8.04 is at home? If so, do you know that your computer at home can even access the university repository? Even if they have an anonymous login, they might possibly filter by IPs so only university computers can use that server.

---

### Post by Battalion on 2008-08-26
Let me clearify the situation:
	Home PC: Ubuntu 7.04 HD install
	University PC: Ubuntu 8.04 Live cd

On campus there is a linux server called ftp.up.ac.za which can be accessed anywhere.  So what i usually do is update the University PC and copy the packages using AptonCD to the Home PC thus both systems are updated.  The home PC has no internet connection!

In my sources.list file, i only edit the address of the site to ftp.up.ac.za/... for the different repositories

---

### Post by caljohnsmith on 2008-08-26
So all the packages you need to update you are copying to a CD, correct? If that is true, have you tried going to System > Admin > Software Sources, click on the "Third-Party Software" tab, and using the "add CD-ROM" button to add your CD your repositories list? I think that should work.

---

### Post by Battalion on 2008-08-26
> **caljohnsmith said:**
> So all the packages you need to update you are copying to a CD, correct? If that is true, have you tried going to System > Admin > Software Sources, click on the "Third-Party Software" tab, and using the "add CD-ROM" button to add your CD your repositories list? I think that should work.

No i don't copy them to CD. AptonCD is an application for saving all installed packages by making an iso file out of them.

My problem is that i can't connect to the server in the same manner I use on 7.04.  How do i change synaptic to run from the local server or modify my sources.list file for this purpose?

---

### Post by caljohnsmith on 2008-08-26
Here's a method I've used to successfully create a "local repository" on my computer accessible to Synaptic:

[LIST=1]
[*]Create a directory in your home directory called "debs":
```
mkdir ~/debs
```
[*]Put all downloaded deb files in your new ~/debs folder
[*]Then run:
```
dpkg-scanpackages ~/debs /dev/null > ~/debs/Packages
```
Note that whenever you add more packages to your ~/debs folder, you will need to run the above command
[*]Add following line to /etc/apt/sources.list:
```
deb file:///home/<username>/debs /
```
[*]Finally, update Synaptic so it sees the repository on your computer:
```
sudo apt-get update
```
[/LIST]
You should now have your own local repository.

---

