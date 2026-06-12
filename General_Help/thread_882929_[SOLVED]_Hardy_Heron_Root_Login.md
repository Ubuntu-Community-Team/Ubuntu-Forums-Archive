---
title: "[SOLVED] Hardy Heron Root Login"
date: 2008-08-07
forum: General Help
---

### Post by ThadeusB on 2008-08-07
I have just installed Hardy Heron 8.04. I want to change the Grub, menu.lst file to change the listing for boot choice, however, I need to be logged in as root. For the life of me I cannot find out how to login as root administrator. Can someone enlighten me please.

Thanks :confused:

[EMAIL="phil@romford44.freeserve.co.uk"]phil@romford44.freeserve.co.uk[/EMAIL]

---

### Post by snowpine on 2008-08-07
Hi ThadeusB and welcome to the forums. Ubuntu differs from other Linux distros in that the root account is disabled. You can use the 'sudo' command (command line) or 'gksu' (gui applications) to temporarily become root. For example: 'gksu gedit /boot/grub/menu.lst' to edit that file as root.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

(edit: sisco is right, I was wrong!:))

---

### Post by sisco311 on 2008-08-07
> **ThadeusB said:**
> I have just installed Hardy Heron 8.04. I want to change the Grub, menu.lst file to change the listing for boot choice, however, I need to be logged in as root. For the life of me I cannot find out how to login as root administrator. Can someone enlighten me please.

Thanks :confused:

[EMAIL="phil@romford44.freeserve.co.uk"]phil@romford44.freeserve.co.uk[/EMAIL]

To open the menu.lst file as root press Alt+F2 and type:
```
gksu gedit /boot/grub/menu.lst
```gksu = run a graphical programs as root
gedit = text editor
/boot/grub/menu.lst = path to the file

---

### Post by ThadeusB on 2008-08-08
Hmm, tried the gksu and sudo commands. Not allowed in! When using gksu I get this message:

 Failed to run gedit '/boot/grub/menu.lst' as user root.

The underlying authorisation mechanism (sudo) does not allow you to run this program. Contact the system administrator.


Or from command line:

[sudo] password for phil:
phil is not in the sudoers file.  This incident will be reported.
phil@phil-desktop:~$ gksu gedit /boot/grub/menu.lst

I need even more help guys, sorry

ThadeusB

---

### Post by iaculallad on 2008-08-08
> **ThadeusB said:**
> Hmm, tried the gksu and sudo commands. Not allowed in! When using gksu I get this message:

 Failed to run gedit '/boot/grub/menu.lst' as user root.

The underlying authorisation mechanism (sudo) does not allow you to run this program. Contact the system administrator.


Or from command line:

[sudo] password for phil:
phil is not in the sudoers file.  This incident will be reported.
phil@phil-desktop:~$ gksu gedit /boot/grub/menu.lst

I need even more help guys, sorry

ThadeusB

Try gksudo on your terminal:

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by sisco311 on 2008-08-08
post the output from:
```
id phil
```

---

### Post by sisco311 on 2008-08-08
> **iaculallad said:**
> Try gksudo on your terminal:

```
gksudo gedit /boot/grub/menu.lst
```

gksudo is a symlink to gksu

---

### Post by northern lights on 2008-08-08
> **ThadeusB said:**
> Hmm, tried the gksu and sudo commands. Not allowed in! When using gksu I get this message:

 Failed to run gedit '/boot/grub/menu.lst' as user root.

The underlying authorisation mechanism (sudo) does not allow you to run this program. Contact the system administrator.

[sudo] password for phil:
phil is not in the sudoers file.  This incident will be reported.
phil@phil-desktop:~$ gksu gedit /boot/grub/menu.lst

> **iaculallad said:**
> Try gksudo on your terminal:

```
gksudo gedit /boot/grub/menu.lst
```

While it is indeed vital to run graphical applications with gksu/gksudo/kdesu rather than sudo, this is not the problem here.

Thadeus seems not to have root permissions. Is this your own machine?

Please post the output of ```
id phil
```and ```
sudo cat /etc/sudoers
```

---

### Post by ThadeusB on 2008-08-08
I still get this message:

Failed to run gedit '/boot/grub/menu.lst' as user root.

The underlying authorisation mechanism (sudo) does not allow you to run this program. Contact the system administrator.


Is there a problem with my installation? I have been into User Settings, via System/Administrations/Users & Groups. The overlay lists, my original account plus root, and an admin account I tried to set up. Originally, befopre adding the Admin account I could Unlock and authenticate, however, I now get this message when trying to Unlock:

Could not authenticate An unexpected error has occurred.

Hardy Heron seems determined not to let me in!

---

### Post by hyper_ch on 2008-08-08
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by mb_webguy on 2008-08-08
I don't think he's going to be able to "sudo cat /etc/sudoers", since his problem seems to be that he can't sudo.  ;)

---

### Post by sisco311 on 2008-08-08
login as your original user and add *phil *to the admin group:
```
sudo adduser phil admin
```

---

### Post by northern lights on 2008-08-08
If there is no other user with sudo privileges, it seems the only way to fix this is from a root shell in Recovery Mode, as you otherwise appear to have messed up your permissions.

Why did you have to change things in "Users & Groups" and what exactly did you change?

---

### Post by ThadeusB on 2008-08-08
Hi iaculallad,

Yes, it is my own machine.

phil@phil-desktop:~$ id phil
uid=1000(phil) gid=115 groups=115,0(root),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),1000(phil)
phil@phil-desktop:~$

phil@phil-desktop:~$ sudo cat /etc/sudoers
[sudo] password for phil:
phil is not in the sudoers file.  This incident will be reported.
phil@phil-desktop:~$


ThadeusB

---

### Post by ThadeusB on 2008-08-08
Thats correct, I can't

---

### Post by mb_webguy on 2008-08-08
Reboot your computer and at the GRUB menu choose to boot into recovery mode.  This will put you at a command line as root.  Type "useradd -G admin phil", then reboot.  When you boot back into Ubuntu, you should be able to use sudo and gksudo.

EDIT: Actually, while you're in recovery mode, type "cp /etc/sudoers /home/phil/sudoers; chmod 444 /home/phil/sudoers".  Then when you log back in normally, type "cat /home/phil/sudoers" and post the results here.

---

### Post by sisco311 on 2008-08-08
> **mb_webguy said:**
> Reboot your computer and at the GRUB menu choose to boot into recovery mode.  This will put you at a command line as root.  Type "useradd -G admin phil", then reboot.  When you boot back into Ubuntu, you should be able to use sudo and gksudo.

EDIT: Actually, while you're in recovery mode, type "cp /etc/sudoers /home/phil/sudoers; chmod 444 /home/phil/sudoers".  Then when you log back in normally, type "cat /home/phil/sudoers" and post the results here.

the correct command is:
```
usermod -a -G admin *phil*
```
or
```
adduser phil admin
```

---

### Post by northern lights on 2008-08-08
> **ThadeusB said:**
> phil@phil-desktop:~$ sudo cat /etc/sudoers
[sudo] password for phil:
phil is not in the sudoers file.  This incident will be reported.
phil@phil-desktop:~$

Yup that was pretty inevitable. Daft.


> **mb_webguy said:**
> Actually, while you're in recovery mode, type "cp /etc/sudoers /home/phil/sudoers; chmod 444 /home/phil/sudoers".  Then when you log back in normally, type "cat /home/phil/sudoers" and post the results here.
+1

---

### Post by ThadeusB on 2008-08-08
As I could see no obvious way of logging in as root, I added a new account called Admin and set it to have root permissions. Perhaps I should not have done this !!??

---

### Post by mb_webguy on 2008-08-08
Doh!  Sisco311's right about the correct command being "usermod" rather than "useradd".  That was a mental glitch on my part...  What can I say, it's late and I need sleep.  The rest of my post was correct, though. 

Thanks for the catch, Sisco311...   :oops:

---

### Post by ThadeusB on 2008-08-08
Just to reiterate: all I want to do is edit the menu.lst Grub file. It had been suggested that I re-boot into recovery mode to the command line. That however, requires the root password. The forum thread refered to has a clear message that I really should not be doing this for security reasons. Thats good, in that HH is protected from meddling - laudable. But itdoes not solve my simle problem.

---

### Post by northern lights on 2008-08-08
> **ThadeusB said:**
> It had been suggested that I re-boot into recovery mode to the command line. ... The forum thread refered to has a clear message that I really should not be doing this for security reasons.
The user phil has no sudo privileges, so if you want/need that for phil, they have to be added. If there was no other user with such priviliges, the root shell in Recovery Mode would be the one and only option.

However, since you're saying
> **ThadeusB said:**
> The overlay lists, my original account plus root, and an admin account I tried to set upyou might not have to go the Recovery Mode route.

Do you remember the username and password of this "admin"? If so log in with that and run
> **sisco311 said:**
> ```
usermod -a -G admin *phil*
```
or
```
adduser phil admin
```
from that account.

Sorted.

---

### Post by ThadeusB on 2008-08-08
Since this is a new installation, I think I would be bet re-installing the whole shooting match to get back to the original priveleges

---

### Post by northern lights on 2008-08-08
> **ThadeusB said:**
> Since this is a new installation, I think I would be bet re-installing the whole shooting match to get back to the original privelegesNot an elegant solution, but sometimes the less time consuming.

Good luck.

---

### Post by ByteJuggler on 2008-08-08
> **ThadeusB said:**
> Since this is a new installation, I think I would be bet re-installing the whole shooting match to get back to the original priveleges

Yes.  Although, you could also boot with the Ubuntu LiveCD, mount your installation, and fix it from there.  However, given that you're not famiiliar at all with finding your way around Ubuntu, it indeed may be easier/quicker to reinstall the machine if you have nothing important on it.  Less hassle even if it is inelegant.

---

### Post by pparks1 on 2008-08-08
> **ThadeusB said:**
> It had been suggested that I re-boot into recovery mode to the command line. That however, requires the root password.
Actually, it does NOT require the root password.   With almost any Linux distro, if you have a boot disc for the OS and physical access to the box, you can go into recovery/rescue mode and you automatically become root and have complete control over the box.  No passwords required.   This is why physical security is tremendously important.

The problem you have here is a fundamental one. During the installation of Ubuntu, you were asked to create a user account.  When you created this account, Ubuntu gave it admin level privileges by adding that account to the sudo system.   When you created your new account, you did not add that account to the admin group and thus are not specified as a user allowed to use sudo.

Your options are two-fold
#1).  just start over, format and re-install.   There is nothing wrong with this, many of us did the same thing when we were first learning Linux.

#2).  Go into recovery mode, and either add your account to the admin group, or run visudo and add the account explictly as a user who is allowed to use sudo.

If I were at your box, option #2 would take about 2 minutes...including the boot time.

---

### Post by ThadeusB on 2008-08-08
Thank you all very much, I'll post later when I have things sorted.

---

### Post by ThadeusB on 2008-08-08
Thanks guys. I have re-installed 8.04.1. Now all is well with no need now to mess with Grub

---

