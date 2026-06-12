---
title: "Installing on old laptop with 256mb of ram"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by Street_Physicist on 2009-04-12
[b][EDIT]problem solved, solution in next post.
original message below:[/EDIT][/b]


I currently have Ubuntu installed, but I would like to try out linux mint on my other laptop.  However, it does not have a "alternative installation" cd, so I can't use the smaller network installation, I have to use the full live CD to install it.

I am trying to install on an old laptop with 256mb of ram.  It's not working out so well.
It loads after a long time and I can see the desktop, but the installer doesn't start (it tries to but doesn't have enough memory.)

I read some advice for this situation, to remove all icons on the gnome panels and to stop some services like pulseaudio networking bluetooth ect... in order to free up ram.
I did all that and the installer actually opened, and went through the whole thing, but had a little trouble actually installing.

Another suggestion I saw was to create a swap partition that could be used to help the installation for low ram systems.  I definitely do not know enough about partitions and the fdisk command to pull something like this off, so could someone PLEASE help me figure out how to make this temporary swap partition.
I want to overwrite the entire disk, with the new installation.

Also, I am now wondering will the installation create a new swap partition?  If not, then I would like to make sure that the swap partition I make has enough memory for when the system is actually installed.  If so, then I would also like a little help with how I could get rid of that "temporary" partition once it is all done.
also, after I make the new partition and I am starting the installation, should I select to use the entire disk?  not sure because that might overwrite the swap partition while the installation is using it, and that could be bad.

Thanks.

---

### Post by Street_Physicist on 2009-04-12
Ok, I think I found a solution!

I found that if you press F6 at the live cd startup menu and type "only-ubiquity" [without quotes] it will start up ONLY the installer, no login screen, no gnome environment or networking or anything.
I think they said if you do it this way you can install with as little as 192mb or ram.  It is installing as I write this  xD


BWT:  Why don't they make this option at least slightly visible as an option for installation.  It seems much more direct.  When I first installed Ubuntu on that old 256mb ram laptop I had similar trouble and had to burn another "minimal installation CD" that ran from the command line to get it to work.  If I had known that all I had to do was soooo simple as typing only-ubiquity it would have saved me a lot of time.  and from looking around a lot of others have the same problem, and aren't aware of this simple solution.

---

### Post by ugm6hr on 2009-04-12
> **Street_Physicist said:**
> Why don't they make this option at least slightly visible as an option for installation.

The Ubuntu LiveCDs (certainly Hardy) do have this option.

It appears below the "Try without installing" option in the list as "Install" - I have used it to install Xubuntu 8.04 on a 256MB computer.

---

### Post by lisati on 2009-04-12
One of my laptops has only 222Mb available RAM. On "Feisty" (7.04) I had to use the "alternate" install disk, but with "Intrepid" (8.10) I was able to use the Ubuntu Live CD. It's a bit slow in some aspects due to the amount of RAM but it can be done!

---

### Post by dannyboy79 on 2009-04-12
you could have used the server version and then added what you wanted or even installed using the xubuntu-alternate cd image, and then just changed the repos to match the mint repos and updated your system that way. glad you got it though.

---

