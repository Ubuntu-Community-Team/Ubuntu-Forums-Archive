---
title: "Configuring a static IP address in Gentoo?"
date: 2007-02-22
forum: Gentoo and derivatives
---

### Post by Cloudy on 2007-02-22
How would I go about doing this from a terminal prompt? I'm assigned a static IP, DNS server, default gateway etc. and I just thought I'd learn how to configure it all from a terminal prompt in Gentoo just.. well, because I wanted to know how. 

Would something like entering "ip address 192.0.0.0" in the terminal prompt work?

---

### Post by mips on 2007-02-22
From the terminal you can run:

```
net-setup
```or manually edit the config file 

```
kdesu kate /etc/conf.d/net
```

or you could maybe use ifconfig (never tried it so I dont really know)

Check the gentoo wiki and official documentation.

---

### Post by zaratustra on 2007-02-22
cleanest method is this
```
ifconfig eth0 192.168.1.101
``` where eth0 can be arbitrary interface

---

### Post by Cloudy on 2007-02-22
Ahhh, cheers guys, I'm just dumb though. I just noticed that there's documentation provided within Gentoo that tells you how to do exactly what I'm wanting to do. It's

```

net-setup eth0
```

Do you think dualbooting XP and Gentoo on a 20gb laptop hdd would be a stretch?

---

### Post by zaratustra on 2007-02-23
Depends what do you have or need installed inside. If you don't clean disfiles and using buildpkg option, gentoo can't grow to 10 GB, but if you maintain it (see documentation) properly, it should stay in about 5 GB. You must know that you need some empty space for compiling. For example, huge thing like openoffice won't start compiling if you don't have at least 5 GB of empty space, so maybe you will have to use binary packages for something like that. This space is temporarily used. On the other side, do not count that you will have full Visual Studio (or something big like that) installed in Windows. I would buy a bigger disk, but in case I had no money, I would make an 6-7 GB ext (or reiser) and all other would be NTFS, used for Windows and for data (music, pics) readed by ntfs-3g from Gentoo. In that way, you will get some flexibility on Windows (delete some data if you need big program:-). No flexibility with ext because it is not readable from Windows(AFAIK).

---

### Post by Cloudy on 2007-02-23
> **zaratustra said:**
> Depends what do you have or need installed inside. If you don't clean disfiles and using buildpkg option, gentoo can't grow to 10 GB, but if you maintain it (see documentation) properly, it should stay in about 5 GB. You must know that you need some empty space for compiling. For example, huge thing like openoffice won't start compiling if you don't have at least 5 GB of empty space, so maybe you will have to use binary packages for something like that. This space is temporarily used. On the other side, do not count that you will have full Visual Studio (or something big like that) installed in Windows. I would buy a bigger disk, but in case I had no money, I would make an 6-7 GB ext (or reiser) and all other would be NTFS, used for Windows and for data (music, pics) readed by ntfs-3g from Gentoo. In that way, you will get some flexibility on Windows (delete some data if you need big program:-). No flexibility with ext because it is not readable from Windows(AFAIK).

Thanks for the opinion, **zaratustra**. I'm seriously considering replacing my current HDD with a $70, 60GB Hitachi drive but I have no idea how reliable Hitachi is. I may just go with a larger Fujitsu ATA hdd since the drive I have in right now is a 20gb ATA hdd.

What I wound up doing is resizing my Windows partition with QTParted to about 11gb and using about 6.5gb for Gentoo.

However, I am either dumb or have done something wrong.. I can't get xdm to start on my Gentoo partition. 

When I do startx I get a clock and 3 terminal windows. Is that normal?

---

### Post by zaratustra on 2007-02-24
maybe you should install gdm (exapmle), append/edit this line ```
DISPLAYMANAGER="gdm"
``` to /etc/rc.conf file, and execute this ```
rc-update add xdm default
``` to add xdm(this will add gdm, or whichever you have) to runlevel, or maybe you want to do it in gentoo way ```
eselect rc add xdm
```.
If you don't want X to start at boot time, ignore what I have wrote above and read this. Don't "startx", maybe you could try "gdm" or whichever display manager you have. (slim, kdm...)

---

### Post by mips on 2007-02-24
> **Cloudy said:**
> Thanks for the opinion, **zaratustra**. I'm seriously considering replacing my current HDD with a $70, 60GB Hitachi drive but I have no idea how reliable Hitachi is. I may just go with a larger Fujitsu ATA hdd since the drive I have in right now is a 20gb ATA hdd.

What I wound up doing is resizing my Windows partition with QTParted to about 11gb and using about 6.5gb for Gentoo.

However, I am either dumb or have done something wrong.. I can't get xdm to start on my Gentoo partition. 

When I do startx I get a clock and 3 terminal windows. Is that normal?

I would take hitachi over fujitsu anyday. My first choice would be Seagate/WD for desktops & for laptops Hitachi only.

---

### Post by Cloudy on 2007-02-24
> **zaratustra said:**
> maybe you should install gdm (exapmle), append/edit this line ```
DISPLAYMANAGER="gdm"
``` to /etc/rc.conf file, and execute this ```
rc-update add xdm default
``` to add xdm(this will add gdm, or whichever you have) to runlevel, or maybe you want to do it in gentoo way ```
eselect rc add xdm
```.
If you don't want X to start at boot time, ignore what I have wrote above and read this. Don't "startx", maybe you could try "gdm" or whichever display manager you have. (slim, kdm...)

"gdm" worked. However, I am still having some problems.

First off, I have duplicate entries in GRUB: Gentoo and Windows are both listed twice. When I check the bootloader options, both are listed twice -- is it alright to delete the second Windows & Gentoo entries? I just want to make sure before I do anything. >_>

Second, and most importantly:

Whenever I try to login as my user I get this:

```

User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

```

What's that all about? :-k

And thanks for the opinion, **mips**.

---

### Post by mips on 2007-02-24
> **Cloudy said:**
> "gdm" worked. However, I am still having some problems.

First off, I have duplicate entries in GRUB: Gentoo and Windows are both listed twice. When I check the bootloader options, both are listed twice -- is it alright to delete the second Windows & Gentoo entries? I just want to make sure before I do anything. >_>


Just backup the file first before you delete anything. Should be ok though.



> **Cloudy said:**
> 
Second, and most importantly:

Whenever I try to login as my user I get this:

```

User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

```What's that all about? :-k


Some sort of problem with permissions. You should be able to use **chown** & **chmod** to correct it.

---

### Post by Cloudy on 2007-02-24
> Some sort of problem with permissions. You should be able to use **chown** & **chmod** to correct it.


Thanks, **mips**.

I googled the exact error text and the first result was this:

[http://ubuntuforums.org/archive/index.php/t-91455.html](http://ubuntuforums.org/archive/index.php/t-91455.html)

I tried what was suggested in the second post there -- 

```

sudo chown (your user name) /.dmrc

```

However, I'm told there is no /.dmrc file. :?

---

### Post by zaratustra on 2007-02-24
maybe omit dmrc and as root do this... Something  similar or maybe the same happened to me
```
chown -hR _username_ /home/_username_
```

```
chmod -R 06XX /home/_username_
``` where X could be arbitrary permissions you want to give to group and other users. If you have any binaries in homedir, do chmod +x for every bin file

I am not sure, but I think that dmrc is created everytime you login into X session, and you don't have it because it could not been created, and it could not been created because you did not had permissions to write into /home/_username_

---

### Post by Cloudy on 2007-02-24
Thank you, **zaratustra**.

However, now I get this whenever I login in under my user:

```

Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.

```

I don't think I'm out of diskspace.. I'm pretty sure I'm not. There's also an error log:

```

/etc/X11/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/X11/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/gdm:20.Xservers" -h "" -l ":20" "travis"
/etc/X11/gdm/Xsession: Beginning session setup...
/etc/X11/gdm/Xsession: Setup done, will execute: /usr/bin/ssh-agent -- gnome-session

(gnome-session: 9325): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: Permission denied
Could not create per-user gnome configuration directory /home/travis/.gnome2/': Permission denied

```

And then when I click "OK" it logs me in as root.




And for whatever bizarre reason, I keep getting dupes on GRUB. Gentoo is listed 4 times now, and Windows 4 times as well. I can't figure out why..

---

### Post by zaratustra on 2007-02-24
Maybe this is my mistake.... try putting or 0666 permissions on /home/_username_ 
If this doesn't work, I really have no idea what could cause this

For grub issue, it could be this stupid tool in gnome which is always doing some backups, so every time you change something, it writes down old and new version in same file. Avoid it and manually edit /boot/grub/menu.lst like all of us l33t wannabe's :)

---

### Post by Cloudy on 2007-02-24
> **zaratustra said:**
> Maybe this is my mistake.... try putting or 0666 permissions on /home/_username_ 
If this doesn't work, I really have no idea what could cause this

For grub issue, it could be this stupid tool in gnome which is always doing some backups, so every time you change something, it writes down old and new version in same file. Avoid it and manually edit /boot/grub/menu.lst like all of us l33t wannabe's :)


Thanks, I'll try that **zaratustra**.

And that's probably what I will wind up doing.

---

### Post by Cloudy on 2007-02-25
Editing menu.lst worked like a charm.

However, changing permissions to 0666 didn't work. I'm still getting the same errors. Do you think a fresh install might change anything?

---

### Post by zaratustra on 2007-02-26
Like you might know, installing gentoo is a like walking through mine fileld. Even if it wasn't, you should not reinstall whole system because of one user. Try to remove the current user and his home dir and add it again with useradd command (not adduser, there is some SKEL difference... my friend told me that, i have no clue what skel is anyway, but there is difference) and try to login. If this would not work, then try tips I gave you above. Maybe even better option would be to remove and re-add user through gui tool in gnome.

---

### Post by Cloudy on 2007-02-26
Hm. Good advice, **zaratustra**. I didn't really think of it until now, but I *did* use adduser (as opposed to useradd). I don't know, it may make a difference.

I'm curious as to what "skel" is now.

---

