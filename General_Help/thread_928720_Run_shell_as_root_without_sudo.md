---
title: "Run shell as root without sudo"
date: 2008-09-24
forum: General Help
---

### Post by SteelWo1f on 2008-09-24
Hi

I have created a shell that can be used for the purpose of getting the network established. For most commands I need sudo access, but I don't want them to have to type in their password. So I would basically like them to already have root privileges when the shell starts.

Any idea how to do this?

Thanks

---

### Post by russlar on 2008-09-24
There is an "Open Root Terminal" launcher hidden in the menu, you just need to put in your passwd when it launches.

---

### Post by aysiu on 2008-09-24
Is it a particular command that gets the network established? If so, you may be able to edit the /etc/sudoers file to allow people *sans* password to execute that particular command.

---

### Post by bingoUV on 2008-09-24
What aysiu says is a much safer option i.e. less chances of your messing in the root shell and injuring the system.

Read this for how to go about this: [http://ubuntuforums.org/showpost.php?p=3768173&postcount=7](http://ubuntuforums.org/showpost.php?p=3768173&postcount=7)

---

### Post by SteelWo1f on 2008-09-24
Thanks guys. Your solution would definitely work except for one little caveat. I would have to prefix every command with sudo. The shell is supposed to make it as easy as possible for the user so I dont want them typing sudo. The only solution then would be to put sudo in from of all the commands I run in the c program. But that would make the code more platform specific and I would like to avoid that. It originally came from OpenBSD where I always had root and I've since ported it to linux, so this is the only remaining issue.

I know you can enable the root account, but I want a different user name. There has to be a way to do this.

---

### Post by bingoUV on 2008-09-24
When you said this,
**I have created a shell **

I think most people here assumed that you create a shell script. Have you created a new shell, i.e. it is a c program compiled and behaves like a shell? You say it is a c program.

Running commands from within c program anyway makes it platform specific, because the command is potentially different in different programs. Any further help is impossible until you tell more details about what you want.

---

### Post by eentonig on 2008-09-24
you could also use the root account by issuing 

> sudo su
or
> sudo -i

---

### Post by SuperSonic4 on 2008-09-24
I know konsole allows you to open a shell as root and it will stay in root but since it's likely to come with KDE dependencies I'd try what others have suggested

---

### Post by SteelWo1f on 2008-09-24
Yes I have created an entirely new shell. So I changed the users login shell to my shell with vipw.

Seeing as its a c program most of the stuff is platform dependent. But I'd still like to keep it as independent as possible. For example:

#ifdef linux
        printResults("sh /etc/iptables.sh", NULL, NULL);
#elif defined BSD
        printResults("pfctl", "-e", NULL);
#endif

Would need to be changed to 

#ifdef linux
        printResults("sudo sh /etc/iptables.sh", NULL, NULL);

This is only bad because some versions of linux don't use sudo. Additionally, some of the commands dont differ between BSD and linux so I would like to not have to change them.

Basically heres what I want:

User sits down in front of the computer and does this:

User Name: adminuser
Password: easypassword

admin ~ > setip 192.168.1.1
admin ~ > firewall off
admin ~ > reboot

Each of those commands requires sudo access and I don't want them to have to retype their password... ever!

Heres what I've got so far, although its kind of a workaround:

User can sudo my shell without a password
Users default shell is a script that simply sudos my shell

While it works, it seems kind of unnecessary.

So, any ideas now?

Thanks again

---

### Post by bingoUV on 2008-09-24
Your solution seems fine, and not unnecessary. One thing you could do is, for the commands that do not need root privileges you could run them as the non-root user. Use setuid for this. The good thing about this is, that it will work on all POSIX compliant operating systems.

This is good for security reasons. It won't matter if all the commands in your shell need root privileges.

---

### Post by SteelWo1f on 2008-09-24
Thanks bingoUV. I guess my solution is kind of growing on me. I think if I was going to use your setuid suggestion I would prefer to just put sudo in front of the commands that need it. Perhaps Im just being too picky.

Thanks for all your help

---

### Post by bingoUV on 2008-09-24
No, setuid will be used by you to drop privileges from root to a normal user. So your shell will need to run as root, but for safety it will drop to ordinary user when it is possible.


sudo will be used to escalate privileges from normal user to root. If you use sudo, the shell can run as ordinary user, and sudo can escalate the privileges to root for some particular commands.

Take your pick, but running all commands as root may not be advisable.

---

### Post by kerry_s on 2008-09-24
> User Name: adminuser
Password: easypassword

admin ~ > setip 192.168.1.1
admin ~ > firewall off
admin ~ > reboot

that can be done with sudo set to "NOPASSWD" for those programs, example:

sudo visudo

username ALL=NOPASSWD: /path/to/setip, /path/to/firewall, /sbin/reboot

then for those programs, they can use sudo, with out a password, example:


admin ~ > sudo setip 192.168.1.1
admin ~ > sudo firewall off
admin ~ > sudo reboot[/QUOTE]

and all without typing in a password.

or put:

username ALL=NOPASSWD: /usr/bin/gnome-terminal

gksudo gnome-terminal 

then run your commands, there should be "Root Terminal" in the menu under accessories you can drag to the desktop for easy access.

---

