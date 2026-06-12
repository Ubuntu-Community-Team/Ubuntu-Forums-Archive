---
title: "upgrade manager doesn't upgrade"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by UBUminJ on 2009-04-25
I just upgraded to 9.04 and have now the following problem.

I visited the upgrade manager and after checking, I get the info that a partial upgrade is necessary.

I click upgrade and start upgrade.
Nothing happens, the window just vanishes.

---

### Post by Partyboi2 on 2009-04-26
Open a terminal (Applications>Accessories>Terminal) and try[FONT=monospace]
[/FONT]```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by lunamystry on 2009-04-27
Okay I am using a proxy and apt just stopped working for some reason. It was working before but then on upgrade day just started giving me an error that proxy needs authorization and thus I am still running Intrepid. 

Some story about me: I run an acer aspire one 8G SSD. I installed Xubuntu and I didn't like it and when I was starting to get used to it It stopped logging me in and I needed to get things done so I installed GNOME using TTY1 thingy. It was workin fine and I think it was actually faster than when I had first installed GNOME. I didn't set up the Proxy myself someone did it for me and I don't know how to set it up. (/etc/bash or /etc/apt/apt.config maybe?). 

When I click update in synaptic it gives an error like TranslationZA something and it only downloads like one or two of the files that actually do download. Can I be helped. My PC seems to be working fine except for a loss in speed during start up, I think it is due to screenlets I am not sure. I didn't like the UbuntuNetbookRemix tried it for a few minutes and it was not for me. I can't use this thing without Compiz.

---

### Post by Partyboi2 on 2009-04-27
> **lunamystry said:**
> Okay I am using a proxy and apt just stopped working for some reason. It was working before but then on upgrade day just started giving me an error that proxy needs authorization and thus I am still running Intrepid. 

Some story about me: I run an acer aspire one 8G SSD. I installed Xubuntu and I didn't like it and when I was starting to get used to it It stopped logging me in and I needed to get things done so I installed GNOME using TTY1 thingy. It was workin fine and I think it was actually faster than when I had first installed GNOME. I didn't set up the Proxy myself someone did it for me and I don't know how to set it up. (/etc/bash or /etc/apt/apt.config maybe?). 

When I click update in synaptic it gives an error like TranslationZA something and it only downloads like one or two of the files that actually do download. Can I be helped. My PC seems to be working fine except for a loss in speed during start up, I think it is due to screenlets I am not sure. I didn't like the UbuntuNetbookRemix tried it for a few minutes and it was not for me. I can't use this thing without Compiz.
Can you open a terminal and post the output to
```
sudo apt-get update
```

---

### Post by lunamystry on 2009-04-28
Rather long output. Here it is. 
```
Ign http://archive.canonical.com intrepid Release.gpg
Ign http://za.archive.ubuntu.com intrepid Release.gpg
Ign http://za.archive.ubuntu.com intrepid/main Translation-en_ZA
Ign http://archive.canonical.com intrepid/partner Translation-en_ZA
Ign http://archive.canonical.com intrepid Release
Ign http://za.archive.ubuntu.com intrepid/restricted Translation-en_ZA
Ign http://archive.canonical.com intrepid/partner Packages
Ign http://za.archive.ubuntu.com intrepid/multiverse Translation-en_ZA
Ign http://archive.canonical.com intrepid/partner Sources
Ign http://za.archive.ubuntu.com intrepid/universe Translation-en_ZA
Ign http://za.archive.ubuntu.com intrepid-updates Release.gpg
Err http://archive.canonical.com intrepid/partner Packages
  407 Proxy Authentication Required
Err http://archive.canonical.com intrepid/partner Sources
  407 Proxy Authentication Required
Ign http://za.archive.ubuntu.com intrepid-updates/main Translation-en_ZA
Ign http://za.archive.ubuntu.com intrepid-updates/restricted Translation-en_ZA
Ign http://za.archive.ubuntu.com intrepid-updates/multiverse Translation-en_ZA
Ign http://za.archive.ubuntu.com intrepid-updates/universe Translation-en_ZA
Ign http://za.archive.ubuntu.com intrepid-backports Release.gpg
Ign http://za.archive.ubuntu.com intrepid-security Release.gpg
Ign http://za.archive.ubuntu.com intrepid-security/main Translation-en_ZA
Ign http://za.archive.ubuntu.com intrepid-security/restricted Translation-en_ZA
Ign http://za.archive.ubuntu.com intrepid-security/multiverse Translation-en_ZA
Ign http://za.archive.ubuntu.com intrepid-security/universe Translation-en_ZA
Ign http://za.archive.ubuntu.com intrepid Release
Ign http://za.archive.ubuntu.com intrepid-updates Release
Ign http://za.archive.ubuntu.com intrepid-backports Release
Ign http://za.archive.ubuntu.com intrepid-security Release
Ign http://za.archive.ubuntu.com intrepid/main Packages
Ign http://za.archive.ubuntu.com intrepid/restricted Packages
Ign http://za.archive.ubuntu.com intrepid/multiverse Packages
Ign http://za.archive.ubuntu.com intrepid/main Sources
Ign http://za.archive.ubuntu.com intrepid/restricted Sources
Ign http://za.archive.ubuntu.com intrepid/universe Packages
Ign http://za.archive.ubuntu.com intrepid/universe Sources
Ign http://za.archive.ubuntu.com intrepid-updates/main Packages
Ign http://za.archive.ubuntu.com intrepid-updates/restricted Packages
Ign http://za.archive.ubuntu.com intrepid-updates/multiverse Packages
Ign http://za.archive.ubuntu.com intrepid-updates/main Sources
Ign http://za.archive.ubuntu.com intrepid-updates/restricted Sources
Ign http://za.archive.ubuntu.com intrepid-updates/universe Packages
Ign http://za.archive.ubuntu.com intrepid-updates/universe Sources
Ign http://za.archive.ubuntu.com intrepid-backports/main Sources
Ign http://za.archive.ubuntu.com intrepid-backports/restricted Sources
Ign http://za.archive.ubuntu.com intrepid-backports/universe Sources
Ign http://za.archive.ubuntu.com intrepid-backports/multiverse Sources
Ign http://za.archive.ubuntu.com intrepid-security/main Packages
Ign http://za.archive.ubuntu.com intrepid-security/restricted Packages
Ign http://za.archive.ubuntu.com intrepid-security/multiverse Packages
Ign http://za.archive.ubuntu.com intrepid-security/main Sources
Ign http://za.archive.ubuntu.com intrepid-security/restricted Sources
Ign http://za.archive.ubuntu.com intrepid-security/universe Packages
Ign http://za.archive.ubuntu.com intrepid-security/universe Sources
Err http://za.archive.ubuntu.com intrepid/main Packages
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com intrepid/restricted Packages
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com intrepid/multiverse Packages
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com intrepid/main Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com intrepid/restricted Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com intrepid/universe Packages
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com intrepid/universe Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com intrepid-updates/main Packages
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com intrepid-updates/restricted Packages
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com intrepid-updates/multiverse Packages
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com intrepid-updates/main Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com intrepid-updates/restricted Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com intrepid-updates/universe Packages
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com intrepid-updates/universe Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com intrepid-backports/main Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com intrepid-backports/restricted Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com intrepid-backports/universe Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com intrepid-backports/multiverse Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com intrepid-security/main Packages
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com intrepid-security/restricted Packages
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com intrepid-security/multiverse Packages
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com intrepid-security/main Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com intrepid-security/restricted Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com intrepid-security/universe Packages
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com intrepid-security/universe Sources
  407 Proxy Authentication Required
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/intrepid/partner/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/intrepid/partner/source/Sources.gz  407 Proxy Authentication Required

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz  407 Proxy Authentication Required

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz  407 Proxy Authentication Required

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz  407 Proxy Authentication Required

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz  407 Proxy Authentication Required

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz  407 Proxy Authentication Required

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz  407 Proxy Authentication Required

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/source/Sources.gz  407 Proxy Authentication Required

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/source/Sources.gz  407 Proxy Authentication Required

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/source/Sources.gz  407 Proxy Authentication Required

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/source/Sources.gz  407 Proxy Authentication Required

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz  407 Proxy Authentication Required

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz  407 Proxy Authentication Required

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz  407 Proxy Authentication Required

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by Partyboi2 on 2009-04-28
Open up Synaptic Package Manager and go to Settings>Pref>Network and make sure the info for the proxy is correct.

---

### Post by lunamystry on 2009-04-28
The info for synaptic proxy is correct. I just checked it. I am not sure about the apt-get proxy settings though. I don't know where they are stored or how to edit them. I know synaptic can work without apt-get having proxy settings because I have used it before without having set-up apt-get for proxy.

---

### Post by lunamystry on 2009-04-28
Maybe I am missing some repo or there is a clash in my repos. I tried to stall Gnome-do from one of those PPA ones and I couldn't download the verification key. I also downloaded openoffice 3 before that but I got the authentification key then.

What are the default like repositories in /etc/apt/sources.list ?

removed openoffice, unchecked the PPA in the software source list and I try to reinstall it and I get an error that some of the packages are not authenticated. Is there a way to like revert back to the Ubuntu default settings for source list?

---

### Post by Partyboi2 on 2009-04-28
I don't know that much about proxy setup file but maybe [[COLOR=Blue]this[/COLOR]]("https://answers.launchpad.net/ubuntu/+source/synaptic/+question/1320") will be of use.

To get a clean sources.list you can generate a new one from [[COLOR=Blue]here[/COLOR]]("http://repogen.simplylinux.ch/"), just remember to backup your current one in case you need it again.

---

### Post by lunamystry on 2009-04-29
I think the authentication error I get is not due to proxy setting but authentication of the repositories. So I generated a sources list and now I need the authentication keys for all those repos. How do I get them? 

Thank you for the sources list generater site :-)

---

### Post by mangkusapi on 2009-04-29
hi all ubuntu mania,

i have some problem while i'm trying update my ubuntu. there are some error 

E: /var/cache/apt/archives/xorg-driver-fglrx_2%3a8.543-0ubuntu4.1_i386.deb: failed in buffer_write(fd) (10, ret=-1)
E: /var/cache/apt/archives/linux-image-2.6.27-11-generic_2.6.27-11.31_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.27-11-generic' before installing new version
E: /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before installing new version
E: /var/cache/apt/archives/apt_0.7.14ubuntu6.1_i386.deb: failed in buffer_write(fd) (10, ret=-1)

please....help men

---

