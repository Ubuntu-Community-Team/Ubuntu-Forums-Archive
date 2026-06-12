---
title: "[SOLVED] Thunderbird thinks it's already running?"
date: 2008-11-15
forum: General Help
---

### Post by Alucard-sama on 2008-11-15
Just installed Intrepid a couple days ago but it's only just now that I've tried to run Thunderbird and been faced with it refusing to run because apparently it already is.
Well as it turns out, it's not and it simply refuses to start up.
Yes I have tried killall/top/etc, they all report that there is no "thunderbird" or "mozilla-thunderbird" process running.

[IMG]http://img352.imageshack.us/img352/7316/thunderbirdissuegb6.png[/IMG]

---

### Post by ju2wheels on 2008-11-15
```

killall thunderbird
killall thunderbird-bin

```

---

### Post by Alucard-sama on 2008-11-15
> **ju2wheels said:**
> ```

killall thunderbird
killall thunderbird-bin

```

Like I said; I've already tried killall.

---

### Post by ju2wheels on 2008-11-15
You didnt mention killing thunderbird-bin which is why I added it.

What do you get as output for this:

```

ps aux | grep thunderbird

```

---

### Post by Mardoct909 on 2008-11-15
I only really have one idea that you've probably tried if you even know what killall is.

Did you reboot?

---

### Post by Alucard-sama on 2008-11-15
> **ju2wheels said:**
> 

What do you get as output for this:

```

ps aux | grep thunderbird

```

kendawg   7857  0.0  0.0    304    68 pts/0    R+   14:13   0:00 grep thunderbird

---

### Post by Alucard-sama on 2008-11-15
> **Mardoct909 said:**
> Did you reboot?

Naturally.

---

### Post by Jive Turkey on 2008-11-15
have you tried renaming /home/<user>/.thunderbird to something else before starting thunderbird?  There could be a misplaced lock file or something.

---

### Post by Alucard-sama on 2008-11-15
Okay well as it turns out for some reason one of the subfolders in ~/.mozilla-thunderbird decided it didn't like me and was sick of me having read-write access to it.
Changed the permissions and now all is right with the world :)

---

### Post by stlouisubntu on 2009-02-02
Hello, friend.  (directed to OP  Alucard-sama)

Would you please do me a favor and post exactly
what you entered to change the permissions of what thunderbird
subfolder that solved the issue and made all right with the 
world?

Did you chmod -R 777 644 or 755 ?  And to what subfolder?  

Although I am not a complete NOOB, I could sure use a little hand holding
on this one so my world could be completely right, also.

Thanks so much.

:-)

---

### Post by Alucard-sama on 2009-02-02
> **stlouisubntu said:**
> Hello, friend.  (directed to OP  Alucard-sama)

Would you please do me a favor and post exactly
what you entered to change the permissions of what thunderbird
subfolder that solved the issue and made all right with the 
world?


Alright first make sure you have ownership of the thunderbird folder (should be ~/.mozilla-thunderbird unless you changed it) with this:
NOTE: anything between and -including- these two symbols "<" ">" should be replaced with the respective information asked for
```
sudo chown <username>:<username> -R <thunderbird folder>
```

Next is to give yourself R/W/X permission:
```
chmod -R +rwx <thunderbird folder>
```

Should do the trick, if you have any problems still post it and I'll respond as soon as I'm available.

---

### Post by Nacht on 2010-02-14
I am having the same problem, I tried the suggested solutions but still no luck. I even tried removing Thunderbird and re-installing it, no luck.

When I run sudo chown I get this:
> sudo: /etc/sudoers is owned by uid 1000, should be 0
Segmentation fault

---

### Post by ju2wheels on 2010-02-14
It sounds like you changed the owner of the wrong files or paths. 

If you ls this is the output you should get:

```

$ ls -al /etc/sudoers
-r--r----- 1 root root 557 2009-12-11 11:40 /etc/sudoers

```

If it doesnt show root root as above then run this:

```

sudo chown root:root /etc/sudoers

```

And if the above command doesnt work then you may need to boot into a live cd and then chroot into your hard drive to correct it.

---

### Post by Nacht on 2010-02-14
> -r--r----- 1 ladm ladm 557 2010-02-13 11:31 /etc/sudoers

That's what it gives me.

I tried running the command you gave me, didn't seem to change anything as I ran ls again and it said the same thing.

Sorry I'm kind of new to this, but have I really messed things up? Isn't there a way for me to reset it to default? I have no idea what "to chroot" something means.

---

### Post by ju2wheels on 2010-02-14
Reboot your machine and wait until it says something like "grub..." and press ESC and follow instructions here: [http://unixlab.blogspot.com/2009/08/exploring-ubuntu-recovery-mode.html](http://unixlab.blogspot.com/2009/08/exploring-ubuntu-recovery-mode.html) . You want to choose to drop down to root shell.

Once you get the root shell, run the command I gave you again and reboot your machine. Hopefully if this is the only thing you changed this will fix it. If you changed more files than this then you may need to reinstall if you did a recursive chown.

---

### Post by Nacht on 2010-02-14
Tried it, and it gave the same response:

> sudo: /etc/sudoers is owned by uid 1000, should be 0
Segmentation fault 			 		

Not sure if I did it right?

---

### Post by ju2wheels on 2010-02-14
Boot to a Ubuntu Live CD as if you were going to install Ubuntu, when you are booted into the Live environment, open Accessories->Terminal and do the following:

```

sudo mkdir -p /mnt/ubuntu/
sudo mount /dev/sda1 /mnt/ubuntu/

sudo mount -o bind /proc /mnt/ubuntu/proc/
sudo mount -o bind /dev  /mnt/ubuntu/dev/
sudo mount -o bind /sys  /mnt/ubuntu/sys/

sudo chroot /mnt/ubuntu /bin/bash

chown root:root /etc/sudoers

```

Note that above I assumed /dev/sda1 is configured as your root partition, if you are not sure check /etc/fstab or the output fdisk -l .

---

### Post by Nacht on 2010-02-14
The first two lines work fine, but then it says:
> ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/ubuntu/proc/
mount: mount point /mnt/ubuntu/proc/ does not exist
ubuntu@ubuntu:~$ sudo mount -o bind /dev  /mnt/ubuntu/dev/
mount: mount point /mnt/ubuntu/dev/ does not exist
ubuntu@ubuntu:~$ sudo mount -o bind /sys  /mnt/ubuntu/sys/
mount: mount point /mnt/ubuntu/sys/ does not exist


---

### Post by ju2wheels on 2010-02-14
Just to confirm you have the right partition mounted, what is the output of:

```

ls -al /mnt/ubuntu/

```

and 

```

sudo fdisk -l
sudo blkid

```

You may have the wrong partition mounted. I dont recall having to make those directories by hand as I did this about a week ago myself to fix something else.

---

### Post by Nacht on 2010-02-14
Hi

Ok, I got the mistake, I did mount the wrong disk. I've now booted back to normal and get this:
```
~$ ls -al /etc/sudoers
-r--r----- 1 root root 557 2010-02-13 11:31 /etc/sudoers
```
..which is what I'm supposed to get, right?

---

### Post by ju2wheels on 2010-02-14
Yes thats correct. Just double check you dont get that sudo error by trying something that requires sudo to run like this:

```

sudo apt-get update

```

If that works and you dont get the error you got before then you are all set. Just be careful next time whenever you run a command especially ones like chmod and chown as sudo as they can really break your entire system if you do something incorrectly.

Also if you were trying to fix a problem with thunderbird that the original poster had when you caused this run (if you tried killall first):

```

sudo chown $USER:$USER -R ~/.mozilla-thunderbird/
sudo chmod o+rwx -R ~/.mozilla-thunderbird/

```

Note that most files in there only require rw permission but that covers all bases in case the permissions are really messed up.

---

### Post by Nacht on 2010-02-14
Ok, well I ran those two lines of code and haven't noticed any change (yes, killall was my first attempt at fixing this).

The one thing I do remember doing it copying and pasting the profiles.ini file in ~/.mozilla-thunderbird/ from Windows. Since then I've uninstalled and reinstalled the program but perhaps that might still be causing the problem? How do I get a default profiles.ini file?

---

### Post by ju2wheels on 2010-02-14
If you want to start fresh just delete the thunderbird profile directory and it will get recreated with a default one when you start thunderbird:

```

rm -rf ~/.mozilla-thunderbird/

```

---

### Post by Nacht on 2010-02-14
It now works fine.

Thank you so so much for all your help! Much appreciated, and has definitely convinced me that Linux is the way to go if getting help for any problems is this nice :)

---

### Post by Jeorb on 2010-12-03
Thank you!

This thread solved Thunderbird not working on my computer as well.

My .thunderbird directory was owned by root and running "sudo chown -R jeorb:jeorb ~/.thunderbird" made the "Thunderbird is already running" error go away.  Now I can run Thunderbird just fine.

---

