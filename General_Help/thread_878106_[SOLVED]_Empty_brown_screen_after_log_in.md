---
title: "[SOLVED] Empty brown screen after log in"
date: 2008-08-02
forum: General Help
---

### Post by JeremyStein on 2008-08-02
I have Ubuntu 7.10 on a Dell 530n with nVidia.  It's been working fine for a couple months now.  Today, when I turn on the computer (and it auto-logs in), I get a brown screen with the mouse cursor I can move.  No menu bars or icons.

I pressed Ctrl-Alt-Backspace and it gave me the log in prompt.  When I logged in again, I got the same thing.

The only things I can think of that have changed are that I let the update manager install some updates and it froze up, apparently during the MPlayer install, and I had to kill it.  Also, when I started the computer this morning, it ran a routine fsck on the drives.  I'm not sure whether either of these are relevant.

I'm not sure what steps to take to diagnose this issue.  Any suggestions?

---

### Post by mbarak on 2008-08-02
When you log into you're session, press Alt+F2
to return your panel (menus) enter:
```
gnome-panel
```

to return your desktop enter:
```
nautilus
```

You should then open up Synaptic to make sure your system is OK - you won't be able to update/upgrade/install new software until APT fixes itself and finishes what it started

---

### Post by JeremyStein on 2008-08-02
Nothing happens when I press Alt-F2 (or any other Alt-Function key).

---

### Post by mbarak on 2008-08-02
When you log in, type in your user name - then on the bottom left click "Actions" go to "Session" and select "Failsafe Gnome"
finish typing in your password
If everything isn't working when you log in using this method, then I hope you're not afraid of the terminal :p we have some work to do

---

### Post by JeremyStein on 2008-08-02
Thanks!  I didn't know about that trick.

I've had smatterings of *nix experience, so I'm actually more familiar with the command-line than this new-fangled UI stuff.  Ubuntu is my first exposure to Debian.

When I run Synaptic, it says:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache -> open() failed, please report.
```
When I run "dpkg --configure -a", it hangs again.  I see:
```
Setting up language-pack-fr-base (1:7.10+20080205) ...
Generating locales...
  fr_BE.UTF-8...
```

I'd be happy to go without that particular dialect of French if that's the problem!  :)

---

### Post by mbarak on 2008-08-02
don't worry, it's supposed to do that
and it isn't hanging (at least I don't think so) it just takes a while for that to finish
you might as well let it finish up since, you don't really have a choice...you can take out the french language afterwards

---

### Post by JeremyStein on 2008-08-03
I did dpkg --remove --purge --deinstall and they all froze up.  Finally after all that and some more twiddling with apt-get, somehow I got the install to work.  But then it froze up on the next one.  It's definitely frozen; I've let it go over night.  Here's what I see:

```
(Reading database ... 125848 files and directories currently installed.)
Unpacking language-pack-fr (from .../language-pack-fr_1%3a7.10+20080704_all.deb) ...
Preparing to replace language-pack-fr-base 1:7.10+20080205 (using .../language-pack-fr-base_1%3a7.10+20080205_all.deb) ...
Unpacking replacement language-pack-fr-base ...
Replaced by files in installed package language-pack-fr ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Setting up language-pack-de-base (1:7.10+20080205) ...
Generating locales...
  de_AT.UTF-8...
```

I ran pstree on the dpkg command and it appears to be stuck on a gzip command:
```
apt-get -u dselect-upgrade
  &#9492;&#9472;dpkg --status-fd 22 --configure libc6 language-pack-de-base language-pack-en-base language-pack-es-base language-pack-fr-base language-pack-fr language-pack-gnome-de-baselanguage-pack-gnome-en-base
      &#9492;&#9472;language-pack-d -e /var/lib/dpkg/info/language-pack-de-base.postinst configure 1:7.10+20071012
          &#9492;&#9472;install-languag -e /usr/share/locales/install-language-pack de  1:7.10+20071012
              &#9492;&#9472;locale-gen /usr/sbin/locale-gen de
                  &#9492;&#9472;locale-gen /usr/sbin/locale-gen de
                      &#9492;&#9472;localedef --no-archive --magic=20051014 -i de_AT -c -f UTF-8 de_AT.UTF-8
                          &#9492;&#9472;(gzip)
```

---

### Post by mbarak on 2008-08-03
perhaps when you closed the previous installation the package was corrupt
run this command
```
sudo apt-get clean
```
this will remove all downloaded packages
then. check your system, and do an update
```
sudo apt-get check
sudo apt-get update
```

just a note - once you get all this fixed up, you should look into upgrading to 8.04 (Hardy)

---

### Post by JeremyStein on 2008-08-03
I restarted the system in case there were extraneous processes from my previous attempts.

"sudo apt-get clean" ran OK.

"sudo apt-get check" gave me this:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

So I ran "sudo dpkg --configure -a" and got this:
```
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-15-generic
Setting up language-pack-gnome-en-base (1:7.10+20080205) ...
 * Reloading GNOME Display Manager configuration...
 * Changes will take effect when all current X sessions have ended.
                                                             [ OK ]

Setting up language-pack-gnome-pt-base (1:7.10+20080205) ...
 * Reloading GNOME Display Manager configuration...
 * Changes will take effect when all current X sessions have ended.
                                                             [ OK ]

Setting up language-pack-zh-base (1:7.10+20080205) ...
Generating locales...
  zh_CN.UTF-8... 

```

It's been sitting that way all day.

---

### Post by noobuntu35 on 2008-08-03
> **JeremyStein said:**
> I restarted the system in case there were extraneous processes from my previous attempts.

"sudo apt-get clean" ran OK.

"sudo apt-get check" gave me this:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

So I ran "sudo dpkg --configure -a" and got this:
```
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-15-generic
Setting up language-pack-gnome-en-base (1:7.10+20080205) ...
 * Reloading GNOME Display Manager configuration...
 * Changes will take effect when all current X sessions have ended.
                                                             [ OK ]

Setting up language-pack-gnome-pt-base (1:7.10+20080205) ...
 * Reloading GNOME Display Manager configuration...
 * Changes will take effect when all current X sessions have ended.
                                                             [ OK ]

Setting up language-pack-zh-base (1:7.10+20080205) ...
Generating locales...
  zh_CN.UTF-8... 

```

It's been sitting that way all day.

Have you tried re-running the Install disc? my .iso has A "recovery console" type option on the Install. It will allow you to re-install parts of your *nix without completely re-installing the whole system. Reading along it seems as though it hangs at the Language package. the other thing to try is the specific site for your distro. If Its a debian system go to getdeb.net you'll find the language package there
Beyond that I agree try Hardy Heron 8.04

---

### Post by mbarak on 2008-08-04
try this command
```
sudo apt-get -f install
```it should fix any dependency issues

---

### Post by mbarak on 2008-08-04
Try this in a new directory
```
sudo dpkg --force-depends --purge locales belocs-locales-bin 
wget http://archive.ubuntu.com/ubuntu/pool/main/b/belocs-locales-bin/belocs-locales-bin_2.4-2.2ubuntu7_i386.deb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/langpack-locales/locales_2.7.9-4_all.deb
sudo dpkg --install *
sudo dpkg --configure -a

```This will remove the locales and belocs-locales-bin packages which handle your language packages, download them, then re-install them.  finally, you continue with configuring your language packs
I'm thinking that perhaps those were corrupt and needed to be re-installed
if this doesn't work, then you will have to purge the individual language packs that don't work

***just so you know, it would be much easier to simply burn a new CD with Hardy and install it.  But, if you want to go through the fun of fixing your system before upgrading, I'm all for it

EDIT: BTW, to remove your packages use this command
```
sudo dpkg --purge *packagename*
```
it's really of no help to put --remove --purge and --deinstall all at the same time (feel free to send a virtual slap if thats not what you did :p )

---

### Post by JeremyStein on 2008-08-04
I'm sorry, I didn't notice your replies when they went to page 2.  I ended up following the advice on this page: [https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340](https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340)

I rebooted into kernel 2.6.22-14 and ran "dpkg --configure -a".  That resolved the problem.

Thanks so much for your help!

By the way, I've tried to upgrade (and later, fresh install) 8.04, but I couldn't get it to work.  (If I recall correctly, it got stuck on the boot up sequence.)  With all this Ubuntu support, maybe I'll feel confident enough to try it again.

Thanks again!  I really appreciate that you stuck with me through this mess.

---

### Post by mbarak on 2008-08-04
No problem - that's what these forums are for!

---

