---
title: "[SOLVED] User error message when booting."
date: 2008-08-22
forum: General Help
---

### Post by irv on 2008-08-22
I started getting an error message every time I boot into Ubuntu. I The error comes up before the desktop so I can't get a screen shot. but I took a photo of it and type in the error.
[ATTACH]82481[/ATTACH] and it says, > "User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."
I am the owner and the file is set at 644 permissions, but it still comes up with this error. Any one got any ideas what to try.

---

### Post by Elfy on 2008-08-22
Try both of these

chmod 644 .dmrc
chmod 700 ~

Edi t- this one is better I think, I used this I think, or something similar last year

[http://ubuntuforums.org/showpost.php?p=4120661&postcount=43](http://ubuntuforums.org/showpost.php?p=4120661&postcount=43)

---

### Post by irv on 2008-08-22
> **forestpixie said:**
> Try both of these

chmod 644 .dmrc
chmod 700 ~

Edi t- this one is better I think, I used this I think, or something similar last year

[http://ubuntuforums.org/showpost.php?p=4120661&postcount=43](http://ubuntuforums.org/showpost.php?p=4120661&postcount=43)

I followed the instruction at the link and I get this:
> irv@irv-old-laptop:~$ sudo chmod -R 700 /home/irv
chmod: cannot access `/home/irv/.gvfs': Permission denied
irv@irv-old-laptop:~$ 
> irv@irv-old-laptop:~$ sudo chown -R irv /home/irv
chown: cannot access `/home/irv/.gvfs': Permission denied
irv@irv-old-laptop:~$ 
The reason is because I do not have a file .gvfs.

---

### Post by Elfy on 2008-08-22
Try here then - [http://ubuntuforums.org/showthread.php?t=866726](http://ubuntuforums.org/showthread.php?t=866726)

more recent - same .gvfs problem 

The problem you had with dmrc is quite common it seems, I used a search to get the info - as I couldn't remember, I use uboontu.com to search rather than the forum.

Post back if there's a problem

---

### Post by irv on 2008-08-22
> **forestpixie said:**
> Try here then - [http://ubuntuforums.org/showthread.php?t=866726](http://ubuntuforums.org/showthread.php?t=866726)

more recent - same .gvfs problem 

The problem you had with dmrc is quite common it seems, I used a search to get the info - as I couldn't remember, I use uboontu.com to search rather than the forum.

Post back if there's a problem

After trying a few things, and i am not sure what I did, it boots now with out the error. I did run a repair on all my packages and did a reinstall on gvfs from the repository. I also change the owner and file access. one of them must of fixed the problem.
Thanks for all the help.
Irv

---

### Post by stoneage on 2008-08-22
I had the same error.
Simply chmod 644 .dmrc did the trick. It started when I enabled another user account. /home/my_account was already 700.

---

### Post by cmittle on 2008-08-22
I just did this this afternoon.  I had my harddrive in my laptop take a dump on me so I replaced it and reinstalled today.  I thought I'd be smart and copy my /etc/fstab from my old one (because it has the automounting of my server in it already) to my new one.  Low and behold when I restarted my laptop I was getting this error.  After some reading and careful thought I realized that when I replaced the default /etc/fstab on my laptop I actually changed where the current hard disk was mounting up and it was causing this problem.  Luckily before I modified the /etc/fstab I made a /etc/fstab.bak which I used to promptly replace the /etc/fstab that I had copied.

I just wanted to mention my scenario so hopefully this will help someone later.

In short do not overwrite the /etc/fstab with one saved from a different computer (or different physical drive).  And, always create backup files!!

---

