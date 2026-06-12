---
title: "No root terminal  in 9.04?"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by brianpatrick on 2009-04-18
Hi,
I installed 9.04 on a separate hard drive from my old, mostly working 8.10. 9.04 ate all traces of 8.10. I did an install, not an upgrade. Is it normal (polite) behavior for an OS to destroy all earlier instances of itself when installing or did I do something stupid when installing? Is there any way to roll it back? 

The root terminal is gone. I had an icon for it and I just get a root password prompt and then nothing. Applications -> system -> root_terminal gives me a 10 second spinning icon and then nothing. 

Applications -> system -> terminal_super_user gives me this error message:
Could not launch 'terminal program - super user mode'
Failed to execute child proces
"konsole" no such file or directory

I used synaptic to install the konsole. Now I don't get the error message and nothing happens. The root terminal is the same. 

I (used to) use the root terminal a lot. Typing sudo on every root command and retyping my password is inconvenient. Why would ubu leave such a useful item in the menus and then remove the feature? 

When I try to su from a normal terminal, I get this error:
brianp@trex:~$ su
Password: 
su: Authentication failure

What am I missing here?

Thank you,
    Brian
    :(

---

### Post by kellemes on 2009-04-18
> **brianpatrick said:**
> Hi,
I installed 9.04 on a separate hard drive from my old, mostly working 8.10. 9.04 ate all traces of 8.10. I did an install, not an upgrade. Is it normal (polite) behavior for an OS to destroy all earlier instances of itself when installing or did I do something stupid when installing? Is there any way to roll it back? 

The root terminal is gone. I had an icon for it and I just get a root password prompt and then nothing. Applications -> system -> root_terminal gives me a 10 second spinning icon and then nothing. 

Applications -> system -> terminal_super_user gives me this error message:
Could not launch 'terminal program - super user mode'
Failed to execute child proces
"konsole" no such file or directory

I used synaptic to install the konsole. Now I don't get the error message and nothing happens. The root terminal is the same. 

I (used to) use the root terminal a lot. Typing sudo on every root command and retyping my password is inconvenient. Why would ubu leave such a useful item in the menus and then remove the feature? 

When I try to su from a normal terminal, I get this error:
brianp@trex:~$ su
Password: 
su: Authentication failure

What am I missing here?

Thank you,
    Brian
    :(


Use..
```
sudo -i
```
or
```
sudo su
```
to get to root-console

---

### Post by Tahakki on 2009-04-18
Try a sudo -i in the terminal.

It sounds like you've allowed 9.04 to use the whole filesystem by accident.

---

### Post by cariboo on 2009-04-18
> I installed 9.04 on a separate hard drive from my old, mostly working 8.10. 9.04 ate all traces of 8.10. I did an install, not an upgrade. Is it normal (polite) behavior for an OS to destroy all earlier instances of itself when installing or did I do something stupid when installing? Is there any way to roll it back?

It seems you installed Jaunty on the same partition as Intrepid was on. During an installation, it reformats the partitions, so all existing files are no longer accessable. There is no way to roll back an installation to an eariler version.

> I (used to) use the root terminal a lot. Typing sudo on every root command and retyping my password is inconvenient. Why would ubu leave such a useful item in the menus and then remove the feature?


If you are running a lot of commands that need to run as root, use:

```
sudo -i
```

this will bypass the sudo timeout.

Jim

---

### Post by brianpatrick on 2009-04-19
cariboo907,
<< It seems you installed Jaunty on the same partition as Intrepid was on. >>

I used Expert mode (fatal error?). I have a 640 GB with XP on the first 2 partitions. I put / on partition 3, sdb6. 

My Velociraptor, sda, (the world's coolest system drive) is still there. 9.04 appears to have overwritten it in the grub menu, but it still shows xp and Suse 11.1. 

It went so far as to destroy all traces of 8.10 in its own /boot/grub/menu.lst as well as Suse's previous /etc/grub.conf on sdd. Egad! 

Fortunately, I did not mount the 2 GB /boot partition used by 8.10 in the latest install so mean, old 9.04 could not vitiate it. I found my old 8.10 spec on /dev/sda1 (mounted on /boot) -> /grub/menu.lst:
title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=6779b8c1-b2a5-40ec-9a7f-94fc5358837f ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

They have also changed the format:
title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            e4309593-d822-4dee-bbb9-95ff07e205ec
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=e4309593-d822-4dee-bbb9-95ff07e205ec ro quiet splash
initrd          /boot/initrd.img-2.6.28-11-generic
quiet

If I hack menu.lst and screw up the translation between the 8.10 format and the 9.04 format will I wind up with an unbootable system? The Kernel spec in 9.04 starts with /boot, but not in 8.04. But, 8.10 has a separate /boot partition whereas 9.04 has boot on slash. 

It there a utility to test a grub/menu.lst like you can do with a Samba or Apache init file?

Can some grub expert tell me if this is the correct translation?
title           Ubuntu 8.10, kernel 2.6.27-11-generic
uuid            6779b8c1-b2a5-40ec-9a7f-94fc5358837f                          
kernel          /vmlinuz-2.6.27-11-generic root=UUID=6779b8c1-b2a5-40ec-9a7f-94fc5358837f ro quiet splash
initrd          /initrd.img-2.6.27-11-generic
quiet


Why did 9.04 leave XP and Suse while overwriting 8.04 in the boot menu?

Puzzled,

    BrianP

---

### Post by wirechief on 2009-04-19
You evidently picked the partition that your old install was on and its not
designed to muck up the other partitions or windows. ;)
until you learn a bit more about being root and its implications i recoomend
you leave su alone. just use sudo  or the sudo i  for most things you really dont need to be always root (its a security issue)

---

### Post by dcstar on 2009-04-22
> **brianpatrick said:**
> .......
I (used to) use the root terminal a lot. Typing sudo on every root command and retyping my password is inconvenient. Why would ubu leave such a useful item in the menus and then remove the feature? 

When I try to su from a normal terminal, I get this error:
brianp@trex:~$ su
Password: 
su: Authentication failure

What am I missing here?


It looks like somebody decided that root terminals were a security hazard and has changed the 9.04 security policies to prevent them being launched.

This will work:

```
gksu konsole
```

You can also enable your root account with:

```
sudo passwd root
```

---

### Post by James_Lochhead on 2009-04-22
> **dcstar said:**
> You can also enable your root account with:

```
sudo passwd root
```

This is unnecessary. sudo -i can easily be used to get a root terminal.

The reasons behind disabling the root account are good ones.

---

### Post by sefs on 2009-04-22
> **James_Lochhead said:**
> This is unnecessary. sudo -i can easily be used to get a root terminal.

The reasons behind disabling the root account are good ones.

I was wondering about this so I changed my root user password to the same as my normal user password so I could type "su" enter the password and get the root terminal.

How can I reverse this so that I an do it the proper way with "sudo -i"?

When done using sudo -i how do i undo sudo -i

Thanks.

---

### Post by phubai on 2009-04-22
Try:

```
man sudo
```

The sudo -i command will provide root terminal until you either exit or close the terminal. If you want to be root for an extended period of time, it's very useful. If you open another terminal, you will open it as the user you are logged in as, and again you can either sudo for temporary root work, or sudo -i if needed.

---

### Post by sefs on 2009-04-22
> **phubai said:**
> Try:

```
man sudo
```

The sudo -i command will provide root terminal until you either exit or close the terminal. If you want to be root for an extended period of time, it's very useful. If you open another terminal, you will open it as the user you are logged in as, and again you can either sudo for temporary root work, or sudo -i if needed.

I have entered a password for the root user so i guess i have enabled him/her.  How do i set it back to its original state.

---

### Post by Yucko on 2009-04-24
> **dcstar said:**
> It looks like somebody decided that root terminals were a security hazard and has changed the 9.04 security policies to prevent them being launched.

This will work:

```
gksu konsole
```

...

This doesn't work on my clean 9.04 installation. It just shows the rotating cursor for a few seconds and then the process terminates :(

ps. neither did gksu **c**onsole ;)

---

### Post by BryanPearson on 2009-04-28
Not to pile on, but I am finding Root Terminal in the Gnome menu only works for root.  For all others, the process just spins into the ether.  I am working with VERY CLEAN installs, with only Jaunty code.  I have tried a few GKSU commands, and they all seem to do this.  Root Terminal worked fine for me in 8.10.

I appreciate the "sudo -i" workaround - it gets me most of the way there.  Once I am root at the terminal, I can enter:

nautilus &

to get the Root File Manager, but 

/usr.bin/x-terminal-emulator &

gets "Failed to contact the GConf daemon; exiting.

I think I have seen bug-reports about this.

Thanks for the hints...

---

### Post by david-emm on 2009-04-28
I have upgraded to 9.04 from 8.10 and have the same problem.
Ran gksu -d /usr/bin/x-terminal-emulator in terminal and got the following:

david@Gemini:~$ gksu -d /usr/bin/x-terminal-emulator
No ask_pass set, using default!
xauth: /tmp/libgksu-CPxVVl/.Xauthority
STARTUP_ID: gksu/|usr|bin|x-terminal-emulator/4912-0-Gemini_TIME2483658
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: /usr/bin/x-terminal-emulator
buffer: -GNOME_SUDO_PASSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS-
brute force GNOME_SUDO_PASS ended...
Yeah, we're in...
xauth: /tmp/libgksu-CPxVVl/.Xauthority
xauth_env: /home/david/.Xauthority
dir: /tmp/libgksu-CPxVVl
david@Gemini:~$ cd /tmp
david@Gemini:/tmp$ ll
total 36
drwxr-xr-x 2 david david 4096 2009-04-28 16:30 hsperfdata_david
drwx------ 2 david david 4096 2009-04-28 16:14 keyring-zBOiRz
drwx------ 2 david david 4096 2009-04-28 16:55 orbit-david
drwx------ 2 root  root  4096 2009-04-28 16:14 pulse-PKdhtXMmr18n
drwx------ 2 david david 4096 2009-04-28 16:14 pulse-UQHIGeDEoOy7
drwx------ 2 david david 4096 2009-04-28 16:14 seahorse-UU36Wx
drwx------ 2 david david 4096 2009-04-28 16:14 ssh-dINbkE2978
drwx------ 3 david david 4096 2009-04-28 16:14 tracker-david
drwx------ 2 david david 4096 2009-04-28 16:14 virtual-david.YMdulk

Seems that the file /tmp/libgksu-CPxVVl/.Xauthority doesn't exist. Is this a problem?

---

### Post by heiowge on 2009-04-28
I get that they feel that root terminal is risky.  I do however have a problem with what they have done.

Firstly, part of linux is the freedom to choose.  Surely it would be enough to put a warning the first time you open root terminal and give you the option to remove the warning (one of the "do no show this again boxes").

Secondly, if it is so bad, why include the shortcut in the system tools bar?  It's like saying to an alcoholic: "we know you have a drinking problem, but look at all this beer you can't drink!"

I think we should have the right to choose whether or not to have access to the root terminal.

---

### Post by dhavalbbhatt on 2009-05-08
> **James_Lochhead said:**
> This is unnecessary. sudo -i can easily be used to get a root terminal.

The reasons behind disabling the root account are good ones.

While the reasons may be good ones - there no case to remove the root terminal from Ubuntu. One of the best things about Linux is that it allows the freedom to do whatever you want to do with it and there are no restrictions. If you are responsible enough, you should not have any problems using the root terminal in Ubuntu. And if the Ubuntu development team was too worried about someone hijacking the OS, then they need to be working more!!

---

### Post by war59312 on 2009-05-09
Indeed, very dumb move on part of the developers. Was like, wtf!!

gksu konsole works for me too. I upgraded from 8.10.

---

