---
title: "Sharing Home partition?  Pros and Cons?"
date: 2007-11-02
forum: Gentoo and derivatives
---

### Post by shane2peru on 2007-11-02
I have Ubuntu installed and have my /home on a separate partition, has been great for upgrades, for changing to other distros etc.  I wouldn't change it for anything.  I'm considering sharing my /home partition from my Ubuntu with my new Gentoo install.  Does anyone else do this?  Will it cause me problems?  In the past while checking out other distros when I mount my /home directory to access files, it changes the owner and group of the partition and I have to chown and chgrp it before I can log back into my account in Ubuntu.  Will sharing my /home partition cause me any problems that I should be aware of?  Thanks.

Shane

---

### Post by coffeecat on 2007-11-02
> **shane2peru said:**
> In the past while checking out other distros when I mount my /home directory to access files, it changes the owner and group of the partition and I have to chown and chgrp it before I can log back into my account in Ubuntu. 

Which distros did this? I don't have a shared home, but I do have a shared (ext3) data partition on this multi-boot, and I have to be careful to make sure that when I install a new distro, the UID and GID are consistent with what I already have. I should imagine it's the UID and GID that caused the problem.

If memory serves me correctly, the Debian-based distros allocate a UID of 1000 to the first created user, with a GID of 100 to the 'users' group. Suse also sets up the first user with 1000:100, but Fedora, Mandriva and PCLinuXOS give you 500:500, with a main group for the user named the same as the username.

I'm in my Gentoo install atm and I see that my UID:GID is 1000:100, but I can't remember whether I stipulated that when I first set up this install over a year ago. Of course, being Gentoo, there's no reason why you shouldn't ensure that your UID:GID are what you want - you can do that with the useradd command - so I suggest you see what they are already and use the same.

The only other thing I've read about (but have no experience of) is that different version of Gnome may have differences in their configuration files - which are hidden files in ~/. If true, that might cause problems. Gutsy comes with Gnome version 2.20, but I'm running Gnome 2.18 in Gentoo currently because 2.20 is still masked.

Of course, you could always live dangerously and unmask and install Gnome 2.20 :)

---

### Post by shane2peru on 2007-11-02
> **coffeecat said:**
> Which distros did this? I don't have a shared home, but I do have a shared (ext3) data partition on this multi-boot, and I have to be careful to make sure that when I install a new distro, the UID and GID are consistent with what I already have. I should imagine it's the UID and GID that caused the problem.

If memory serves me correctly, the Debian-based distros allocate a UID of 1000 to the first created user, with a GID of 100 to the 'users' group. Suse also sets up the first user with 1000:100, but Fedora, Mandriva and PCLinuXOS give you 500:500, with a main group for the user named the same as the username.

I'm in my Gentoo install atm and I see that my UID:GID is 1000:100, but I can't remember whether I stipulated that when I first set up this install over a year ago. Of course, being Gentoo, there's no reason why you shouldn't ensure that your UID:GID are what you want - you can do that with the useradd command - so I suggest you see what they are already and use the same.

The only other thing I've read about (but have no experience of) is that different version of Gnome may have differences in their configuration files - which are hidden files in ~/. If true, that might cause problems. Gutsy comes with Gnome version 2.20, but I'm running Gnome 2.18 in Gentoo currently because 2.20 is still masked.

Of course, you could always live dangerously and unmask and install Gnome 2.20 :)
Now that you mention that, yes, it was Fedora that gave me the problem.  I had to switch to a tty and change the group and owner of the files.  I'm not sure about this UID and GID although I assume this means User ID and Group ID.  The different versions of Gnome are what can cause me problems.  Is there a way to change the Gnome settings to a separate hidden folder such as .gnome2.20  or something of that nature?  Speculating, would it mess up my older Gnome (Gentoo side) or Newer Gnome (Ubuntu side)?  I'm living on the edge no matter what way you slice it seems like.  :)

Shane

---

### Post by Bachstelze on 2007-11-03
Sharing a /home partition is OK, sharing a home folder is a bit more troublesome, I would personnally not do it. What I do is putting them on my data storage partition, like /data/homes/firas_ubuntu, /data/homes/firas_gentoo, etc. and then just creating symlinks for the folders I want shared (.xchat2, .purple, .ssh, etc.).

---

### Post by shane2peru on 2007-11-03
> **HymnToLife said:**
> Sharing a /home partition is OK, sharing a home folder is a bit more troublesome, I would personnally not do it. What I do is putting them on my data storage partition, like /data/homes/firas_ubuntu, /data/homes/firas_gentoo, etc. and then just creating symlinks for the folders I want shared (.xchat2, .purple, .ssh, etc.).

Yeah, in that case I will just change my home to elsewhere, and link the stuff I need to my Ubuntu home.  That is probably the safest solution.  Keeps stuff cleaner.  Thanks.

Shane

---

### Post by vmsda on 2007-12-05
> **HymnToLife said:**
> Sharing a /home partition is OK, sharing a home folder is a bit more troublesome ...).

So if, in my system, I have:
1. more than one distro
2. a /home dir in a separate extended partition
3. and I have slightly different distro-specific userids (eg. vasco_u, vasco_d, and so on)

then I am ok in sharing that /home dir across all my systems?

Thank you for help.

---

### Post by tommcd on 2007-12-20
> **vmsda said:**
> So if, in my system, I have:
1. more than one distro
2. a /home dir in a separate extended partition
3. and I have slightly different distro-specific userids (eg. vasco_u, vasco_d, and so on)

then I am ok in sharing that /home dir across all my systems?

Thank you for help.

Yes, if you use different user names, the hidden config files for each distro will be kept separate according to each user name and should not conflict with each other. I just use a /data partition for my pesonal files to get around this. That way each distro's home is a folder on  the distro's root partition so the config files are separate and I can use the same user name on all distros.

---

### Post by vmsda on 2007-12-20
Thank you for your suggestion: definitely a more elegant setup (as expected!)

---

