---
title: "Lightening the load on an older laptop"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by Digimer on 2007-05-14
Hi all,

  I'm a recent convert from Debian to Ubuntu, and I like what I see! So first and foremost, kudos to all those who work on this distro. :)

  My question is; Being the poor code monkey I am, I make do with an older laptop (Compaq Evo N410c, for the curious). it's biggest restriction is it only has 256MB RAM. So what I need is some tips/advice/pointers on how to lighten the load.

  What I need/use is kate (KDE code editor), PostgreSQL 8.2 and Apache 2.2 mainly. I really like Gnome, so I'd like to avoid switching to a lightweight X frontend like xfce or black/fluxbox. I have switched to the Mist minimalist theme, for what that's worth. I've also dug through '/etc/rc2.d' and rm'ed a few of the daemons I don't need (ie: bluetooth). 

  What else might I be able to do to reduce the memory requirements of Feisty? I realize I may be a bit SOL given my reluctance to leave Gnome, but here's to hoping!

Thanks all! 

Digi

---

### Post by metrolinux on 2007-05-15
I have an aged laptop (Inspiron 7000)  running Feisty and have found that BootUp-Manager is a good utility to reduce the extra load.   

[HTML]sudo apt-get install bum[/HTML]

Another way I've found to squeeze a little more power out is to setup a used desktop to aggregate all my mail with fetchmail then dish it out to my laptop with dovecot setup as an imap server.  I have multiple email addresses and spent a lot of time bumping Get Mail in Thunderbird.  It was also slowing the laptop down every 10 minutes when it automatically checked  for mail.  Now, I just keep TBird minimized and wait for the beep.

Lastly, get iptables setup so that it ignores any extra chatter from other machines on the network.  The quick way is using Firestarter.

[HTML]sudo apt-get install firestarter[/HTML]

---

### Post by kerry_s on 2007-05-15
Like debian you can start from scratch and build it to you needs using the net installer.-> [http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso](http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso)

start with gnome-core and build up from there.

Example:
server install
login
sudo su
apt-get install xorg gdm gnome-core synaptic
reboot
login and build on.

Personally i would go with xfce4(i know you don't want) since it seems you'll be running a mixed environment. xfce4 supports both gnome and kde apps, running on a fairly light desktop will help those apps have more. Building up will help, by having only what your actually going to use, which is the main thing you can to to lesson the load.

---

