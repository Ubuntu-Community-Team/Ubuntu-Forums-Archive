---
title: "Help with a bash script"
date: 2008-10-14
forum: General Help
---

### Post by sauce345 on 2008-10-14
I wrote a bash script to mount a bunch of media shares that i have on a windows system.  I have 1 problem that i would like to overcome.  The script uses the sudo command and so obviously requires a password to continue, because i have like 6 sudo commands in a row.  Any here is the script:

#!/bin/sh
sudo mount.cifs //192.168.1.101/Movies /mnt/Movies cifs user=root
sudo mount.cifs //192.168.1.101/"High Def Movies" /mnt/HighDefMovies cifs user=root
sudo mount.cifs //192.168.1.101/"TV Shows" /mnt/"TV Shows" cifs user=root
sudo mount.cifs //192.168.1.101/Music /mnt/"Music" cifs user=root

It is also weird because it asks for a password from the user then the root?  But anyway how do get it so that it doesn't ask me to type a password after every line?

Also any other types to making it more efficient/better?  I have only written simple scripts that just execute consecutive commands.

I wish i didn't even have to do this, but i could not get the samba stuff working properly to see the share in Nautulis.  I can browse and see the computer with the shares fine, but none of the shares show up.

Thank you in advance.

---

### Post by Washer on 2008-10-14
yeah i never found a way to properly fix that. I got around it by using two scripts, the 2nd one to run the first one using "xterm -T script.sh"

---

### Post by /usr/bin/hacked? on 2008-10-14
Could you use the && operator? 
Like so:
```
sudo something && something else && some other thing && other cool stuff 
```

Not sure if that'll work, but it might.

---

### Post by hyper_ch on 2008-10-14
why don't you

```

#!/bin/sh
mount.cifs //192.168.1.101/Movies /mnt/Movies cifs user=root
mount.cifs //192.168.1.101/"High Def Movies" /mnt/HighDefMovies cifs user=root
mount.cifs //192.168.1.101/"TV Shows" /mnt/"TV Shows" cifs user=root
mount.cifs //192.168.1.101/Music /mnt/"Music" cifs user=root

```
and then
```

sudo script.sh

```?

---

### Post by meganox on 2008-10-14
```

#!/bin/sh

[B]# check if script is being run as root
[ "$( id -u )" != "0" ] && { echo "Must be root."; exit 1; }[/B]

mount.cifs //192.168.1.101/Movies /mnt/Movies cifs user=root
mount.cifs //192.168.1.101/"High Def Movies" /mnt/HighDefMovies cifs user=root
mount.cifs //192.168.1.101/"TV Shows" /mnt/"TV Shows" cifs user=root
mount.cifs //192.168.1.101/Music /mnt/"Music" cifs user=root

```then run it with sudo as hyper suggests.

---

### Post by alberto ferreira on 2008-10-14
#!/bin/sh


#login as sudo temporarily
sudo -i


#now you don't need sudo before each command as you're already logged in 
mount.cifs //192.168.1.101/Movies /mnt/Movies cifs user=root
mount.cifs //192.168.1.101/"High Def Movies" /mnt/HighDefMovies cifs user=root
mount.cifs //192.168.1.101/"TV Shows" /mnt/"TV Shows" cifs user=root
mount.cifs //192.168.1.101/Music /mnt/"Music" cifs user=root


#return to normal user
logout

---

### Post by taladan on 2008-10-14
Unless you just want to wait to mount your shares, why not put them in the fstab and let the system automatically mount them for you?

The syntax is:

server:/share mount_point cifs defaults 0 0

Tal

---

### Post by geirha on 2008-10-14
Add those entries to /etc/fstab. The first one would look like
```
//192.168.1.101/Movies /mnt/Movies cifs defaults,noauto,user 0 0
```

Then you can mount it as a regular user with
```
mount /mnt/Movies
```
The user that tries to mount it needs to own the mount-point first though (/mnt/Movies) in this case.

---

### Post by sauce345 on 2008-10-14
I am so impressed with this forum first of all.  On most other forums no one seems to this much interest unless the problem is hard.  I am new to the ubuntu forums as a poster, i have been using ubuntu for 2 or 3 years.

Anyway all of this information has been great.  I like the idea of putting the command in /etc/fstab but am a little confused.  Once i put them in they will auto mount on startup of ubuntu? Or will i have to still mount /mnt/Moives manually then?  

A second question that i have is that if i have them in /etc/fstab and the computer that has the shares on them is turned off, will it just not mount and throw a error or mount when the computer gets turned on?  Or will it not mount and then i have to manually mount it again?

THANKS FOR THE HELP SO FAR

---

### Post by taladan on 2008-10-14
Good questions:

1)  Yes, they will automount when you start up your system, that's the purpose of the fstab.

  1a) After you put them in your fstab you can either restart your system or type mount -aF cifs and this will mount them up for you the first time.

2) If the servers are off, they will not mount, but the system will operate normally.  To mount them after you've booted up (if any of the shares were down) simply run mount -aF cifs and it will mount them after you bring the server(s) with the shares up.

Tal

---

### Post by meganox on 2008-10-15
> **taladan said:**
> Good questions:

1)  Yes, they will automount when you start up your system, that's the purpose of the fstab.

  

Not if you use the version geirha posted, with the noauto option.  If you used noauto you could mount with "mount -aF cifs" or even just "mount -a" to mount everything in fstab, it won't cause any harm to already mounted drives.

---

