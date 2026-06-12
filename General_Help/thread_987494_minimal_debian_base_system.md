---
title: "minimal debian base system"
date: 2008-11-19
forum: General Help
---

### Post by belaviyo on 2008-11-19
Hi,

I want to find a minimal Linux system with apt-get, I think the lightest one is Debian etch, but it is nearly 800MB after installation, I want something nearly 100Mb, can any body help ?

P.S: I want apt-get works on this distribution

---

### Post by cmay on 2008-11-19
on the download page for debianetch you can find as small as possible netinstall ,minimal base install and singel cd intall media for debian. i use the minimal intall cd which is i think around 100 mb light. the point is to install the system over the net using apt-get.
hope it helped.
edit:
added a link
[http://ftp.nl.debian.org/debian/dists/etch/main/installer-i386/current/images/](http://ftp.nl.debian.org/debian/dists/etch/main/installer-i386/current/images/)

---

### Post by snowpine on 2008-11-19
I do not think you will find a smaller Debian-based system than a Debian Etch minimal install. Certainly not eight times smaller. :)

My favorite tiny distro is SliTaz. The iso is under 30mb and the installed system is right around 100mb. It is an excellent distro--but it does not use apt-get.

ps What is your goal here? Do you have a super-tiny hard drive or something?

---

### Post by bodhi.zazen on 2008-11-19
100 mb installed is a very very minimal system.

I suggest slitaz

[http://www.slitaz.org/en/](http://www.slitaz.org/en/)

alternates on that scale include puppy linux and DSL.

If you wish to stay with Ubuntu, go for a debootstrap install (this is the smallest) or user the minimal CD.

[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

See also: [http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

---

### Post by darrenn on 2008-11-19
This is has been mentioned many times before but I will mention it anyway. You could try out damn small linux it's only 50meg in size.

---

### Post by kerry_s on 2008-11-19
you can do a custom install and get it how you want. i use the net installer to install the base.
[http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-businesscard.iso)

at the package selection, i uncheck everything, that gives me only the base.
log in as root
apt-get clean
apt-get install xorg xserver-xorg-video-vesa
(that gives you X, and the generic driver vesa, if you select your vid card it won't install them all)
now just install what ever window manager you want.
example:
apt-get install jwm menu
update-menu
that's enough to get you in to X
type> exit
to get out of root
log in as your user
type> startx

when you get in the gui open a terminal su to root and grab what ever else you want.

or

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)
[http://distro.ibiblio.org/pub/linux/distributions/damnsmall/current/dsl-4.4.10.iso](http://distro.ibiblio.org/pub/linux/distributions/damnsmall/current/dsl-4.4.10.iso)

---

### Post by belaviyo on 2008-11-20
can some body tell me where should I use package selector !

I use [http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-businesscard.iso) image and install it but I cant find any package selection tool!

---

### Post by cmay on 2008-11-21
it is the terminal. aptitude. i think. its been a while since my last debian install so i cant remeber if it still uses dselect or just aptitude.

---

### Post by ibuclaw on 2008-11-21
You could also attempt at compiling your own custom kernel specifically built for your machine and the devices you will most likely run.

You could cut the kernel image size down to around 10MB or less if you get things right ;)

Regards
iain

---

### Post by lemuriaX on 2008-11-21
aptitude is probably what you want - you could install synaptic from there if you wanted to but aptitude works great

[http://en.wikipedia.org/wiki/Aptitude_(program](http://en.wikipedia.org/wiki/Aptitude_(program))

---

### Post by kerry_s on 2008-11-21
> **cmay said:**
> it is the terminal. aptitude. i think. its been a while since my last debian install so i cant remeber if it still uses dselect or just aptitude.

doesn't matter there both there, you can:
apt-get install package-name
or
aptitude install package-name
or
just> aptitude
for the terminal gui installer, if you know how to use it.

---

