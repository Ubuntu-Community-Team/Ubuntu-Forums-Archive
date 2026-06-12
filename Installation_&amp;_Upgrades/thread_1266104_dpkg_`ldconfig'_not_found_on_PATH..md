---
title: "dpkg: `ldconfig' not found on PATH."
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by Aldimann on 2009-09-14
After some trouble I had with some packages yesterday, apt-get and aptitude now only show the following when I try to install new packages, upgrade etc.

```
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
dpkg: `ldconfig' not found on PATH.
dpkg: 1 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
mitja@cube:~$ printenv PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

"echo $PATH" and "sudo echo $PATH" both show me
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

How can I fix this mess?

---

### Post by Aldimann on 2009-09-15
I solved the problem by just copying dpconfig and dpconfig.real from another Ubuntu-installation to /sbin/ - I have know idea why it was missing.

---

### Post by Arand on 2009-09-27
I had a very similar problem, the cause of which was rather obvious: Trying to install Karmic packages in jaunty, which in turn pulled in libc updates which threw a fit.

N.B. this is on an amd64 (jaunty) system.

Now, to solve this, my steps were:
(0. Disable karmic repos)
> [B]EDIT: As has been noted in following posts, ldconfig have been moved from libc6 to libc-bin on newer versions, if this is the case, you will probably want to replace libc6 -> libc-bin in these commands

I have written an updated version of the guide [[COLOR="RoyalBlue"]HERE[/COLOR][/B]]("http://ubuntuforums.org/showpost.php?p=11767830&postcount=19")
1. Get hold of ldconfig & ldconfig.real from the correct version:```
aptitude download libc6
```unpack it:```
dpkg-deb -x libc6*.deb libc6-unpacked/
```copy them out:```
sudo cp libc6-unpacked/sbin/ldconfig* /sbin/
```
At this point I did:```
sudo apt-get -f install
sudo dpkg-reconfigure libc6
sudo dpkg-reconfigure libc6-i386
sudo apt-get install --reinstall libc6
sudo apt-get install --reinstall libc6-i386
```Of which the reinstalls seemed to be the crucial ones. Now all errors seem to be gone.

- Arand

---

### Post by alexxroche on 2009-10-05
This entry **really** helped me. I pressed the 'Upgrade' button in update manager when I had an up-to-date version of 8.10. It seemed to try to leap from 8.10 and fell on its face before it reached 9.04, (I thought that with 9.10 almost out 9.04 would be a safe bet by now.) 
  I could reboot, (my fear was that grub had been munged and that I would have to start from scratch,) but apt-get update; apt-get -f upgrade gave me this ldconfig error and perl complained about regional settings missing,

LANGUAGE = ""   
LC_ALL = ""
LC_LANG = "en_GB.UTF-8"

After following the instructions on this page I had to do the following to get my X11 (I'm using the default Gnome as the manager) to work again:

# connect using ethernet to my router because wireless in my Latitude D420 no longer worked [0]
# Then in terminal (pts/0)

aptitude upgrade;
reboot

# After that almost everything worked, (as a desktop should) [1]
# I have to say that I'm a fan of Ubuntu but a normal user would be very upset by pressing a button that their system invited them to press and then finding that their OS no longer worked. I know that upgradeing libc isn't trivial but having the ability to roll back 9.04 -> 8.10 if it does not work would be good.

# I also saw some error about speedstep-centrino.ko but I have not found the exact log entry
# (root@laptop:/var/log# grep -i speedstep *; grep -i centrino *; zgrep -i centrino *.gz; zgrep -i speedstep *.gz; # this found nothing)
 
alexx

# [0] Linux detected the device and I could set an ESSID but it would not associate 
# [1] I run apache on my laptop so I can test things while offline. After this upgrade, (and telling aptitude to leave my apache2 config as is) apache2 no longer interprets my cgi code and just displays it, (but I think this is more of a debian problem than an ubuntu one.)

---

### Post by Agnaramasi on 2010-03-20
Your instructions have saved me, thank you.

---

### Post by Trismegister on 2010-08-08
@Arand. Thanks for your help. Downloading, unpacking and copying libc6 sorted out the mess I'd made!
In my case I'd caused the mess by trying to force through an upgrade from Hardy LTS to lynx LTS on a Virtual Server that I am looking after for a customer who rents it from a provider that prevents the upgrading from one LTS to another. 
i.e. I couldn't complete upgrade as was not permitted to update boot sector to boot up upgraded kernel.

---

### Post by schef on 2010-08-27
Hey. I'm working on a debian server but it helped me too. Thanks!

---

### Post by SammyIAm on 2010-10-18
Tried to upgrade my SheevaPlug to 9.10 before learning that it doesn't support 9.10.  Registered an account here just to thank you for saving me a lot of hassle trying to reformat/reinstall.

---

### Post by ereallstaff on 2010-10-19
Hi I have just done your procedure but in downloaded pack there is no sbin ldconfig file!!

Please help!!!

---

### Post by slovy88 on 2010-10-25
> **ereallstaff said:**
> Hi I have just done your procedure but in downloaded pack there is no sbin ldconfig file!!

Please help!!!
you can do the same with libc-bin package just change libc6 to libc-bin in the codes from the previous post

---

### Post by nibsa1242 on 2011-01-23
Thank you, this seems to be fixing a problem I had on my Debian box.  I installed something from unstable and my system got hosed (uninstalled Gnome and a million other things).

---

### Post by rafiks on 2011-09-05
> **Aldimann said:**
> After some trouble I had with some packages yesterday, apt-get and aptitude now only show the following when I try to install new packages, upgrade etc.

```
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
dpkg: `ldconfig' not found on PATH.
dpkg: 1 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
mitja@cube:~$ printenv PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

"echo $PATH" and "sudo echo $PATH" both show me
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

How can I fix this mess?

By any chance ,you were using sudo?

there was a change in /etc/sudoers that makes it impossible for a sudoer to get access to /usr/sbin and /sbin.

What I did is I went su to root and reinstall sudo and accept YES to the prompt when it says config has change and just add myself again to the sudoers.

HTH

---

### Post by harveyp on 2011-09-09
Hi,
dpkg gives me this error when I am trying to install libc6 glibc libc-bin eglibc - all of which are supposed to install ldconfig ldconfig.real.

Unfortunately a small person has removed the twig from my wifi card ... I am working offline. I have been unable to get apt-get to do anything except gripe so I have been using dpkg. My sole success has been with tzdata which used to conflict with libc6.

I am using the Freespire distro, KDE 3.5.6, kernel 2.6.20-16-lowlatency, on AMD Athlon, i686

Thanks in advance for any help.

Harvey

---

### Post by JamieKitson on 2011-09-14
> **rafiks said:**
> By any chance ,you were using sudo?

there was a change in /etc/sudoers that makes it impossible for a sudoer to get access to /usr/sbin and /sbin.

What I did is I went su to root and reinstall sudo and accept YES to the prompt when it says config has change and just add myself again to the sudoers.

HTH

Thanks rafiks, I think that's the correct answer :)

---

### Post by Maelvon on 2011-09-17
> **rafiks said:**
> By any chance ,you were using sudo?

there was a change in /etc/sudoers that makes it impossible for a sudoer to get access to /usr/sbin and /sbin.

What I did is I went su to root and reinstall sudo and accept YES to the prompt when it says config has change and just add myself again to the sudoers.

HTH

Thanks Rafiks!

---

### Post by reaper_rr on 2011-10-05
I have encountered the same problem on Kubuntu 11.10 (Development version) and in my case the problem was not linked with the paths in the sudoers file. The ldconfig binaries were literally missing from my installation.

Arand's [post]("http://ubuntuforums.org/showpost.php?p=8014915&postcount=3") helped me a lot solving the problem, but I must note that for the latest Ubuntu versions you should replace libc6 in Arand's post with libc-bin and it will work smoothly. :)

---

### Post by loserock on 2011-10-09
After years for the original solve, this helped me too!
My ubuntu 11.10b2 had same problem (when I tried multiarch support), and the woraround worked! (just need download libc-bin, and not libc6)

Lot of thanks for You!

---

### Post by josephpmh on 2012-03-15
I downloaded and extracted the libc deb, but there is not a folder in the extracted folder /libc6-unpacked/sbin so I cannot copy 

> **Arand said:**
> I had a very similar problem, the cause of which was rather obvious: Trying to install Karmic packages in jaunty, which in turn pulled in libc updates which threw a fit.

N.B. this is on an amd64 (jaunty) system.

Now, to solve this, my steps were:
(0. Disable karmic repos)

1. Get hold of ldconfig & ldconfig.real from the correct version:```
aptitude download libc6
```unpack it:```
dpkg-deb -x libc6*.deb libc6-unpacked/
```copy them out:```
sudo cp libc6-unpacked/sbin/ldconfig* /sbin/
```
At this point I did:```
sudo apt-get -f install
sudo dpkg-reconfigure libc6
sudo dpkg-reconfigure libc6-i386
sudo apt-get install --reinstall libc6
sudo apt-get install --reinstall libc6-i386
```Of which the reinstalls seemed to be the crucial ones. Now all errors seem to be gone.

- Arand

---

### Post by Arand on 2012-03-15
> **josephpmh said:**
> I downloaded and extracted the libc deb, but there is not a folder in the extracted folder /libc6-unpacked/sbin so I cannot copy

As has been mentioned before, ldconfig has moved to the 'libc-bin' package.

Since this seems to help every now and then...
Here is an updated version of the steps (which may or may not work) corresponding to the way the packages are structured nowadays:

Download and extract the package
```
apt-get download libc-bin
dpkg -x libc-bin*.deb unpackdir/
```

Copy the file to your system
```
sudo cp unpackdir/sbin/ldconfig /sbin/
```

Make sure the package and package system is in a good state.
```
sudo apt-get install --reinstall libc-bin
sudo apt-get install -f
```
Futher errors after this indicates something else is wrong.

---

### Post by ODF on 2012-04-12
> **Arand said:**
> As has been mentioned before, ldconfig has moved to the 'libc-bin' package.

Since this seems to help every now and then...
Here is an updated version of the steps (which may or may not work) corresponding to the way the packages are structured nowadays:

Download and extract the package
```
apt-get download libc-bin
dpkg -x libc-bin*.deb unpackdir/
```

Copy the file to your system
```
sudo cp unpackdir/sbin/ldconfig /sbin/
```

Make sure the package and package system is in a good state.
```
sudo apt-get install --reinstall libc-bin
sudo apt-get install -f
```
Futher errors after this indicates something else is wrong.

I wanted to thanks this post. It solved my problems.

---

### Post by zielot on 2012-10-08
> **ODF said:**
> I wanted to thanks this post. It solved my problems.

Same for me - Thanks.

---

