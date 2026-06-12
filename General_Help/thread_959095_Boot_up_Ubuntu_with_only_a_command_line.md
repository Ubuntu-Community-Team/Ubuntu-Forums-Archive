---
title: "Boot up Ubuntu with only a command line?"
date: 2008-10-26
forum: General Help
---

### Post by crazyfuturamanoob on 2008-10-26
I like Ubuntu. It boots up faster than windows and works faster.
But I want it to boot even faster. And I need only terminal to use it.

Could I make a launch parameter entry in grub? So Ubuntu would start in 1 second and use only terminal?

---

### Post by kevstar31 on 2008-10-26
post your /etc/inittab

---

### Post by crazyfuturamanoob on 2008-10-26
> **kevstar31 said:**
> post your /etc/inittab

I don't have it.

---

### Post by kevstar31 on 2008-10-26
In a Terminal type:
ls /etc/init.d/

---

### Post by crazyfuturamanoob on 2008-10-26
> 
rho@ohra-laptop:~$ ls /etc/init.d/
acpid               hotkey-setup                     rcS
acpi-support        hwclockfirst.sh                  readahead
alsa-utils          hwclock.sh                       readahead-desktop
anacron             keyboard-setup                   README
apmd                killprocs                        reboot
apparmor            klogd                            rmnologin
apport              laptop-mode                      rsync
atd                 libpam-foreground                screen-cleanup
avahi-daemon        linux-restricted-modules-common  sendsigs
binfmt-support      loopback                         single
bluetooth           makedev                          skeleton
bootclean           module-init-tools                stop-bootlogd
bootlogd            mountall-bootclean.sh            stop-bootlogd-single
bootmisc.sh         mountall.sh                      stop-readahead
brltty              mountdevsubfs.sh                 sysklogd
checkfs.sh          mountkernfs.sh                   udev
checkroot.sh        mountnfs-bootclean.sh            udev-finish
console-screen.sh   mountoverflowtmp                 ufw
console-setup       mtab.sh                          umountfs
cron                networking                       umountnfs.sh
cupsys              nvidia-kernel                    umountroot
dbus                pcmciautils                      urandom
dhcdbd              policykit                        usplash
dkms_autoinstaller  powernowd                        vbesave
dns-clean           powernowd.early                  waitnfs.sh
gdm                 pppd-dns                         winbind
glibc.sh            procps                           wpa-ifupdown
hal                 pulseaudio                       x11-common
halt                rc                               xserver-xorg-input-wacom
hostname.sh         rc.local
arho@ohra-laptop:~$ /etc/init.d/inittab
bash: /etc/init.d/inittab: No such file or directory
arho@ohra-laptop:~$ /etc/init.d/inittab

not found

---

### Post by kevstar31 on 2008-10-26
```
sudo su
mkdir /backup
mv /etc/init.d/gdm /backup
update-rc.d gdm remove
exit 
```

---

### Post by crazyfuturamanoob on 2008-10-26
> **kevstar31 said:**
> ```
sudo su
mkdir /backup
mv /etc/init.d/gdm /backup
update-rc.d gdm remove
exit 
```

But I don't want to completely uninstall gnome! I want a grub launch parameter that will launch ubuntu only with console.

---

### Post by ghost_ryder35 on 2008-10-26
> **crazyfuturamanoob said:**
> But I don't want to completely uninstall gnome! I want a grub launch parameter that will launch ubuntu only with console.

edit your grub kernel line to have a 
" 3" at the end of it
and yes that is a space before the 3

---

### Post by lswb on 2008-10-26
> **crazyfuturamanoob said:**
> I like Ubuntu. It boots up faster than windows and works faster.
But I want it to boot even faster. And I need only terminal to use it.

Could I make a launch parameter entry in grub? So Ubuntu would start in 1 second and use only terminal?

It still won't start in 1 second :) but expect it to start a bit faster than it now takes to just get to the graphical login screen. Because of the way ubuntu has implemented the upstart system, a few changes must be made besides just adding another grub menu entry. See
[http://ubuntuforums.org/showthread.php?t=863539#8](http://ubuntuforums.org/showthread.php?t=863539#8)
for more details.

---

### Post by agathian on 2008-10-26
what exactly is the intended use of this system?

May be you should use the server distribution... Desktop version intentionally includes lot of additional stuff to improve user experience

You could disable login/window managers as indicated in the previous replies, if you just want to get to the command line. Update-rc.d just disables the startup, doesnt remove the package - you can use it to turn it back on as well [I think..]

If your goal is to minimize boot time, you might want to check out bootchart to analyze what is taking up time.

Also, there are plenty of other distros, stripped down versions targeting specific use models. If any fits your bill, that may be an option as well.

---

### Post by Xiong Chiamiov on 2008-10-26
> **agathian said:**
> May be you should use the server distribution... Desktop version intentionally includes lot of additional stuff to improve user experience
...
Also, there are plenty of other distros, stripped down versions targeting specific use models. If any fits your bill, that may be an option as well.
He's right.  Server is kinda nice as you still get Ubuntu, but it installs as a fairly basic system, without all of the extra stuff that the normal desktop installs give you.

You can achieve this fast boot time with Ubuntu, but you're fighting against it.  Ubuntu is a distro that includes a lot of things that you don't really need, so that if you do need them, they'll be there and work very easily.  If you want a system that you have a lot of control over, then you should be trying something like Gentoo, Slackware, or my personal favorite, [Arch]("http://archlinux.org").

---

### Post by kevstar31 on 2008-10-26
> **ghost_ryder35 said:**
> edit your grub kernel line to have a 
" 3" at the end of it
and yes that is a space before the 3
I do not think runlevel 3 has networking.

---

### Post by hictio on 2008-10-26
> **kevstar31 said:**
> I do not think runlevel 3 has networking.

Shouldn't that be a '2' instead of a '3'?
As I understand, Ubuntu's Runlevel '3' is the equivalent of, say, Red Hat's '5'.

Personally, I boot onto the CLI, and my runlevel is reported as '2'.
If you are going to use the CLI a lot, aside from using Server or plain vanilla, you might want to use a high resolution console.

---

