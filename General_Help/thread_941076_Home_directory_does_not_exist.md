---
title: "Home directory does not exist"
date: 2008-10-07
forum: General Help
---

### Post by swiftstealth on 2008-10-07
I was in the administration menu, where I was editing users, and I changed the home directory for my user account from it's default to another by accident; no problem I thought, so I retyped the name of my home folder. Now I can't get access to Ubuntu. I receive the following error message

> Your home directory is listed as '/butler/home folder' but it does not appear to exist. Do you want to log in with the/root directory as your home directory? it is unlikely anything will work unless you use a failsafe session

if I try to log in anyway, I get

> 
User's $HOME/.drmc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

> Your session only lasted less than 10 seconds. If you have not logged out yourself, this could be some installation problem, or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem

View Details (~/.xsession-errors file)
/etc/gdm/presession/default: Registering your session with wtmp and utmp
/etc/gdm/presession/default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h  " " -l ":0" "butler"
/etc/gdm/Xsession: beginning session setup...
trying to create local folder //.kde: Permission denied
trying to create local folder //.kde: Permission denied
trying to create local folder //.kde: Permission denied

(gnome- session:5480) :  libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: No such file or directory

Could not create per-user gnome configuration directory '/butler/home folder/.gnome2/': No such file or directory

I can't log into the gnome failsafe, all I can log into is the terminal failsafe. I'm guessing that I need to restore my home folder to it's default, but I have no idea how to even begin fixing this from the terminal - there is only one user on my computer (named "butler") and there's a lot of data saved on this computer, that is protected, so I can't even get access to it to back it up and then reinstall ubuntu - I realize this was an idiot mistake, and I'm sorry to be a bother, but umm... help! It's been more then 2 months since my last backup and there's a LOT of information I can't afford to lose!

---

### Post by haydnc on 2008-10-07
I suspect from reading your post that you've just got the path to your home directory set wrong. Typically it wouldn't be /butler/home but instead /home/butler, but that would depend on how you've set things up.

If you open a Terminal and type:

```
cd ..
ls
```

That should tell you what directories are available under your /home directory. I'm guessing but there may be one called butler under there, in which case you'd just need to correct the information about your home folder for your user account.

Let me know if that gets you anywhere. If not we can work through re-creating or re-finding your home folder.

Edit: bugger - I just re-read your post and I'm unsure if you're able to log in to KDE or Gnome or whatever. Please let me know if you still have the GUI also.

---

### Post by Patb on 2008-10-07
Swift, go into the terminal you can open and type
```
cd /
```
Then post the output of the following two commands:
```
ls -la
ls -la /home
```
That should give enough information for someone to help you further. 

Cheers, Pat

---

### Post by swiftstealth on 2008-10-07
I ran the commands and this is what came out;

> butler@salamandastron:/$ cd
butler@salamandastron:/$ ls
bin   dev  initrd          lib        mnt   root sys  var
boot   etc  initrd.img      lost+found opt   sbin tmp  vmlinuz
cdrom  home init.rd.img.old media      proc  srv  usr  vmlinuz.old

butler@salamandastron:/$ ls /home
butler

I no longer have any access to the gui - either KDE or Gnome (I have both installed, default was gnome but I was trying KDE out)
I'm pretty sure I just have to refind the home folder, but I'm not sure how to go about that. What should I do next?

---

### Post by Patb on 2008-10-07
Great. Your /home folder seems to have the correct name. 

Please type the following commands from the terminal. If you get any error messages, please post them. They should do exactly what that error message at login says is required. 
```
sudo chmod 755 /home
sudo chmod 600 /home/butler/.dmrc
```
Then reboot. Let us know how you go.

Cheers, Pat

---

### Post by myth01 on 2008-10-07
swift, apologies if this is no help, I'm quite new on the scene myself, but while waiting to an answer to one of my problems I've been doing some Googling on your dilemma.

It seems the location of your home folder is described in the file /etc/passwd on the same line as your username.  Looking at your post it seems that your home folder still exists as /home/butler.  

Armed with this info I would have a look at the passwd file

```
nano /etc/passwd
```
(You can get to a terminal can't you?)

to see if your home folder is correct in there.

Hope that helps...

---

### Post by myth01 on 2008-10-07
Apologies PatB, you replied while I was typing :)

---

### Post by Patb on 2008-10-07
Not at all, Myth. The more the merrier! :)

Cheers, Pat

---

### Post by haydnc on 2008-10-07
Judging from the info contained in swiftstealth's posts I'd say that:

1, (S)He has no choice but to use 'terminal' since neither KDE or Gnome load for him/her.

2, Editing the /etc/passwd file is the way to go using whatever terminal based editor is available. e.g. 
```
sudo vim /etc/passwd
``` 
Assuming I'm not working off faulty information you'll probably need to look for a line that looks something like:
> butler:x:1021:1020:Some Info:/butler/home:/bin/bash
changing the bit that says "/butler/home" to read "/home/butler"

3, Check that the user butler has all the correct permissions on the proper home directory:
```
cd /home
ls -l
```
You should see butler listed with permissions something similar to this:
> butler    drw-r--r-- 
though I do admit I'm not 100% certain on that last one since I'm away from my own Ubuntu machine so can't check what permissions are on my own home directory.

4, As stated by Patb check the permissions on the .dmrc file are correct:
```
sudo chmod 600 /home/butler/.dmrc
```

5, Reboot and hope for the best... I believe you can reboot with the command: 
```
sudo shutdown -R now
```

but again, my memory might be off on the syntax.

---

### Post by swiftstealth on 2008-10-07
ehh. I tried the commands, but the first time I ran it, it let me run the commands, but told me that there was "no such file" (referring to the /home/butler/.dmrc file)

so I exited and rebooted, and tried to log in - wasn't able to - so I went back to the terminal and reentered the commands, and this time nothing happened - it didn't say it was an invalid command or anything, but it didn't give me the error message either. it kinda just sat there.

---

### Post by swiftstealth on 2008-10-07
haydnc - thankyou for your input, your analysis is correct - I'm trying the procedure you've outlined right now - will let you know how it goes asap

---

### Post by haydnc on 2008-10-07
If it doesn't work let us know what (new) error messages you get and myself or someone else will probably be able to come up with some more suggestions you could try.

If it does work you could always click the little thanks icon under the username of everyone who helped you out. :)

Edit: the thanks thing is the little blue and gold star medal at the bottom right hand corner of the useful post.

---

### Post by swiftstealth on 2008-10-07
YES!
I used the commands and it fixed it! Thankyou so much everyone!!!

---

