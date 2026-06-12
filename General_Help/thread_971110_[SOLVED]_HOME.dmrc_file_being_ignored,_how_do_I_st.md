---
title: "[SOLVED] HOME/.dmrc file being ignored, how do I stop this?"
date: 2008-11-04
forum: General Help
---

### Post by Happibun on 2008-11-04
Hi,

I have been getting an annoying error message telling me that my User&#347; $HOME/.dmrc file is being ignored every time I boot up the computer and just after I have logged in.

It has been happening ever since I started backing up my home folder to an external hard drive. Ie just imported my home folder in to a fresh install of Ubuntu 8.10, and the error message is still happening.

I bet there is a really easy way to stop it, but I don have a clue.

Please help.

Thank you.

---

### Post by sisco311 on 2008-11-04
open a terminal and type:
```
chmod 0600 ~/.dmrc
```

---

### Post by Happibun on 2008-11-04
Thanks Sisco,

Unfortunately that did not work, I&#7743; not even sure what the command was, but I pasted it in to the terminal so I know I did not mistype it.

Anyway, I have got a picture of the error message now. Had to take a photo and i&#7743; sorry the quality is so bad but it did not like being shrunk..

[http://ubuntuforums.org/picture.php?albumid=675&pictureid=2238](http://ubuntuforums.org/picture.php?albumid=675&pictureid=2238)

Any ideas?

Thanks, Jo

---

### Post by sisco311 on 2008-11-04
ok.copy/past this(line by line) in a terminal:
```
sudo chown -R $USERNAME: $HOME
chmod 755 $HOME
chmod 644 $HOME/.dmrc

```

---

### Post by Happibun on 2008-11-04
Yay!

Success. Thank you very much. I changed $USERNAME to my user name BTW

Just to satisfy my curiosity, what exactly did those commands do? 

Cheers, Jo

---

### Post by sisco311 on 2008-11-04
the commands are restoring the default settings (permissions and owner) on your home folder. 

*chown -R $USERNAME: $HOME* - change the owner of home folder(/home/username) to your user.

*chmod 755 $HOME* - set the permissions of the home folder to 755 (read/write/execute for owner, read/execute for group and others)

*chmod 644 $HOME/.dmrc* - set the permissions of the .dmrc file to 644 (read/write for owner, read for group and others)

more about permissions here:[https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by Happibun on 2008-11-04
[I]Sisco311,

You are a star. Thank you.

:guitar:
[/I]

---

### Post by cb34 on 2009-01-05
> **sisco311 said:**
> 
```
sudo chown -R $USERNAME: $HOME
chmod 755 $HOME
chmod 644 $HOME/.dmrc

```
the commands are restoring the default settings (permissions and owner) on your home folder. 

*chown -R $USERNAME: $HOME* - change the owner of home folder(/home/username) to your user.

*chmod 755 $HOME* - set the permissions of the home folder to 755 (read/write/execute for owner, read/execute for group and others)

*chmod 644 $HOME/.dmrc* - set the permissions of the .dmrc file to 644 (read/write for owner, read for group and others)

more about permissions here:[https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

Thank you very much for this proper fix!!

(i've got to be more careful with chmod in the future! :p)

---

### Post by Asday on 2009-01-07
According to the output, ~/.dmrc doesn't exist, and a quick look at the hidden files in nautilus confirms this.  I'm guessing a blank file called .dmrc in my home folder won't work?  (Seems kinda over-user friendly for Ubuntu to write the file, should it be empty...)  =P

Also, I chmod 777'd the partition I use as ~ before installation, which is probably what caused this problem.

---

### Post by RealG187 on 2009-04-23
> **sisco311 said:**
> open a terminal and type:
```
chmod 0600 ~/.dmrc
```

I'll try that. I started getting that error message on my old laptop when I moved all the file from my home folder to another account and I had to change permissions of it.

Not sure what caused it to come up on my new laptop. But I do backup my home folder to a USB hard drive...

---

### Post by Asday on 2009-04-23
Could someone at least post the contents of their .dmrc for me?  Assuming it's plaintext.

---

### Post by RealG187 on 2009-04-24
> **Asday said:**
> Could someone at least post the contents of their .dmrc for me?  Assuming it's plaintext.

I think there is nothing wrong with the file, just the permissions of it. The file is the same, just the permissions aren'...

---

### Post by Asday on 2009-04-24
No, for *me*.  I'm not saying yours are wrong, quite the opposite.  I'm assuming they're right, and I want one, so I can stick it in my ~, and then it'll exist, because I don't have one.

---

### Post by jeffsa12 on 2009-04-24
Some more info on home folder permission issues.

[http://ubuntuforums.org/showthread.php?t=727677](http://ubuntuforums.org/showthread.php?t=727677)

Check out the noobs info on home file permission I posted there.

---

### Post by WhiteHorse on 2009-04-27
This worked for me on 9.04, it has more restrictive permissions so others can't read your files:

> sudo chmod 644 /home/ricardimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo

---

### Post by xaegis on 2009-04-30
I used the same chown and keep getting the message:

chown: cannot access `/home/$USER/.gvfs': Permission denied

How do I work around this?
I just migrated to 9.04 and now it wont accept my permissions.

Thanks in advance.

-e

---

### Post by xaegis on 2009-04-30
> **xaegis said:**
> I used the same chown and keep getting the message:

chown: cannot access `/home/$USER/.gvfs': Permission denied

How do I work around this?
I just migrated to 9.04 and now it wont accept my permissions.

Thanks in advance.

-e

Nevermind I used:
sudo aptitude reinstall gvfs gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0

Seemed to clear the problem for now.

Thanks.

---

### Post by RealG187 on 2009-05-04
It keeps coming back, the command doesn't work anymore.

Would deleting that file make it stop, or would that cause (worse) problems with my system?

---

### Post by silvagroup on 2009-05-08
> It keeps coming back
This is a problem.
Haven't had this happen for a few months, then all of a sudden happened again today.
Not the first time, so why and what keeps changing the permissions on the .dmrc file and how does one stop that terrible annoyance.

---

### Post by RealG187 on 2009-05-08
For me it's really bad, I type in that chmod command and it comes up the next time I reboot. It's like the command didn't even work, I think it made it go away before, but not now.

I recently changed my GDM login screen if that helps, is the login screen preferecnes stroed in DMRC?

---

### Post by silvagroup on 2009-05-09
I think it has something to do with user settings, so it could be that it impacts the login also.
The only thing i usually do is just change the permissions on the .dmrc file and that takes care of the problem.

---

### Post by dhughes on 2009-05-09
This is a milestone event, you know you're a real Linux/Ubuntu user when you mess up the permissions on home/.dmrc 

 It's like Bar Mitzvah for geeks.

---

### Post by silvagroup on 2009-05-09
dhughes I can't take credit for it, I don't know why it happens. It's nothing intentional on my part at all. In the old days they would blame it on gremlins, hey aren't they in the same family as gnomes. That would explain it !!!!!

---

### Post by Asday on 2009-05-09
> **dhughes said:**
> This is a milestone event, you know you're a real Linux/Ubuntu user when you mess up the permissions on home/.dmrc 

 It's like Bar Mitzvah for geeks.

Well it conveniently messed it up for me upon install.  It must have known I was awesome at compupers.  D:

---

### Post by Happibun on 2009-05-25
> This is a milestone event, you know you're a real Linux/Ubuntu user when you mess up the permissions on home/.dmrc 

 It's like Bar Mitzvah for geeks.

This makes me so happy. Finally, I am become Geek :-)

---

### Post by blucalvin on 2010-03-24
Dear friend,
I had the same problem regarding the .dmrc file being ignored.
First of all,
I would like to know how it happened. I shutdown my system one time and the next time when I opened it, I had the error message at my login screensaying .dmrc was being ignored.
How did it happen?
And second,
when I tried sudo chown -R $USERNAME: $HOME
it gave an error message as follows:
chown: cannot access `/home/USERNAME/.gvfs': Permission denied
Can someone please help me out here?

---

### Post by jimstar79 on 2010-08-19
This command completely fixed my problem - well, so far everything looks fine!

Xaegis - you are my 'Hero of The Day'!!

Thanks

edit: as in typing:

sudo aptitude reinstall gvfs gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0

ps: my problem was getting this error and not being able to access my desktop, or any files. 

so, i opened terminal using cmd-alt+f1, typed out the above command and then rebooted. Phew!

---

