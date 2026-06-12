---
title: "reiser4 root trouble"
date: 2005-12-04
forum: General Help
---

### Post by ram32 on 2005-12-04
I have an Ubuntu 5.10 + kernel 2.6.14.3 custom with reiser4 support. I want to set reiser4 partition as root (/boot on ext2).

I created reiser4 partition with Gparted, loaded from live cd, mounted all what i need, copied all from my old reiserfs root to it, edited /etc/fstab and /etc/mtab.

Reboot. And after i edited grub my gnome says to me something like that
"Failed to find internet address for "(none)". It will prevent gnome to work correctly. You may to liquidate the problem by adding "(none)" to file /etc/hosts" and two buttons "Start anyway" and "Try again"

If i push "Start anyway", then system load, but only ones. Second boot fails - it appears brown screen of gnome and nothing else.

Help me, please. And sorry for my English :)

---

### Post by ram32 on 2005-12-05
Nobody knows? :eek:

---

### Post by pheitman on 2005-12-05
Just a guess, but the (none) implies to me that /etc/hostname isn't correct. Does that file exist? What is its contents? Also, what do you have in /etc/hosts?

Peter

---

### Post by ram32 on 2005-12-05
ram32@cel850:~$ cat /etc/hosts
127.0.0.1       localhost.localdomain   localhost       cel850

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by pheitman on 2005-12-06
Does /etc/hostname exist? Does it contain the string cel850? If it doesn't exist, I'd create one that contained the line 

cel850

That should certainly help.

Peter

---

### Post by ram32 on 2005-12-06
/etc/hostname exists.
Thanks for trying :)

---

### Post by pheitman on 2005-12-06
So when you run the hostname command, it prints out cel850?

The next thing I'd check is to make sure that /etc/rcS.d/S40hostname.sh exists and points to /etc/init.d/hostname.sh and that /etc/init.d/hostname.sh contains

#
# hostname.sh   Set hostname.
#
# Version:      @(#)hostname.sh  1.10  26-Feb-2001  [email]miquels@cistron.nl[/email]
#

if [ -f /etc/hostname ]
then
        hostname --file /etc/hostname
fi

Peter

---

