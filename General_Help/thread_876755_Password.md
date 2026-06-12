---
title: "Password"
date: 2008-08-01
forum: General Help
---

### Post by P4r4b014 on 2008-08-01
Hi, I just installed Ubuntu for the first time on VMWare to try it out. Only thing is, I was doing the seven steps while playing Halo 3.  Naturally I was rushing to do things between lives and mistyped my password.

Now I cannot seem to "re-miss type" it and figure it out. Any suggestions?

---

### Post by Rocket2DMn on 2008-08-01
Start the machine up and click ESC (I think) to get to the GRUB menu when it prompts, then choose the recovery mode kernel.  Choose to enter the command line / terminal.  From here, run
```
ls /home
```
That will show the user name you created (the user's home folder actually).  Then run
```
passwd <username>
```
where <username> is the user's name, without <>.  Enter the new password when prompted, twice.  Then reboot
```
reboot
```
Let it go normally, and you can use your new password to login!

---

### Post by P4r4b014 on 2008-08-01
Thank you! This worked perfectly. Also thanks for my first experience with the terminal.  Any suggestion on what I should read up on?

---

### Post by em4g.3ht on 2008-08-01
apt-get commands and simple directory browsing... also using man pages....

I am quite the noob myself, but these things sure helped me when i started


ALSO!! gedit! (or what ever text editor is your default) (remember that) sudo gedit /etc/whateveryouwanttoedit

that will help with a lot of network config and a ton of other things

---

### Post by Rocket2DMn on 2008-08-01
There are many guides to getting started with the terminal, here is one I happen to have bookmarked - [http://linuxcommand.org/](http://linuxcommand.org/)
There are many other good ones out there, a simple google search will get you more than you need, otherwise I'm sure othe users have their own favorites.

---

