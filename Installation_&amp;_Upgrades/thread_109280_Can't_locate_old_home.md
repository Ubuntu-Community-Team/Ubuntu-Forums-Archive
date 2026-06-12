---
title: "Can't locate old /home"
date: 2005-12-28
forum: Installation &amp; Upgrades
---

### Post by Elixyr_faery on 2005-12-28
I've been using Ubuntu since july 2005 and I think it's great. The forums are quite helpful and I've been able to set everything up without ever having to post a message myself. But now I did something stupid..

I followed the wiki and tried an apt-get upgrade to breezy, but somewhere along the line something went wrong and Xorg wouldn't start after reboot. I don't know exactly what went wrong, but because I saw loads of failed processes while it was setting up, I thought I'd start fresh (had too much junk on the install anyway). So I popped in the old hoary cd, and did a fresh install so I could do a fresh upgrade (I have oodles of time and a fast connection). Now hoary's back up, but I don't see my /home partition (it was a seperate partition from my first ubuntu install, didnt mess with it this time around). I'm downloading the breezy cd now so it'll all be more straightforward for me, but how do I get my /home partition set up in that breezy install without having to format it?

---

### Post by Pablo_Escobar on 2005-12-28
You have to mount Your home partition as /home in the /etc/fstab file for system to see it.

---

### Post by Elixyr_faery on 2005-12-28
That works even if I want it set up as my default /home? Oh....and how do you do that again? (n00bness showing...):confused:

---

### Post by Pablo_Escobar on 2005-12-28
Issu in the terminal command 
fdisk -l
to show Your partitions, 
1. You need to know what files system it has to mount it properly.
2. During the installation process while partitioning You can select that partition as a /home. But remeber to keep the option "Keep data intact" (or something like it) on
3. If You wan't to change it now You'd need to mount that partition as a different mount point. Then copy over the current user folder. Then switch the mount point in the fstab file.

---

### Post by Elixyr_faery on 2005-12-28
Ok, I think I'll just hold till the breezy cds done downloading and then select that option (Saw it but didnt want to risk losing any data).

Thanks for the quick answer :D

---

### Post by Pablo_Escobar on 2005-12-28
I'd suggest using a different username when installing Breezy then the Hoary one - it can cause problems. Then You'll just copy over the data from the old user under /home to the new one. But that concerns data not settings (f.e. Gnome - it can cause trouble).

---

### Post by daschl on 2005-12-28
[QUOTE=Pablo_Escobar]I'd suggest using a different username when installing Breezy then the Hoary one - it can cause problems. Then You'll just copy over the data from the old user under /home to the new one. But that concerns data not settings (f.e. Gnome - it can cause trouble).[/QUOTE]

or take the same username and just remove the dotfiles :)

---

