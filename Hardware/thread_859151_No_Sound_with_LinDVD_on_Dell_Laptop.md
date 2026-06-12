---
title: "No Sound with LinDVD on Dell Laptop"
date: 2008-07-14
forum: Hardware
---

### Post by isuzucrewcab on 2008-07-14
Hi,

I upgraded from 7.10 to 8.04 on a Dell Inspiron 1420 and tried LinDVD for the first time today.

It plays the video ok, but I get no sound.  I get sound with other apps so I know it is a LinDVD issue.

Any assistance would be appreciated.

Thanks

Steve

---

### Post by Afkpuz on 2008-07-15
I would recommend trying a different player.  Try vlc or xine

For vlc
```
sudo apt-get install vlc
```

For xine
```
sudo apt-get install xine-ui
```

I can help you with those too if you need help

---

### Post by isuzucrewcab on 2008-07-15
Hi,

I tried both of those and got the following:
> steve@Calypsonians:~$ sudo apt-get install xine-ui
[sudo] password for steve:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xine-ui: Depends: libxine1 (>= 1.1.4) but it is not installable
           Depends: libxine1-ffmpeg but it is not going to be installed
E: Broken packages


steve@Calypsonians:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 0.8.6.release.c-0ubuntu5) but it is not going to be installed
       Depends: libsdl-image1.2 (>= 1.2.5) but it is not going to be installed
E: Broken packages
steve@Calypsonians:~$ 




I have tried with vlc before and each time I try to install one of the dependencies, I get further errors about other dependencies.

Thanks for any help.

---

### Post by Afkpuz on 2008-07-15
ok, try to install those via synaptic.

System>Administration>Synaptic Package Manager

---

### Post by secristr on 2009-01-10
I tried "sudo apt-get install xine-ui" and while xine did install correctly, it wouldn't read the encryption on the DVD.  Installing xine did however fix whatever was wrong with the sound, and then LinDVD started working again, which is what I wanted in the first place -- so the suggestion still helped -- thanks!

Note that I am still under 7.10 myself, because that is what came with my 1525, and to date I've been able to load everything I care about (including Firefox3, Netbeans, MySQL, Oracle, etc.) so there has been no compelling reason to go for 8.04 or 8.10 yet (especially since that means potentially losing LinDVD).

If xine isn't installing for you, check to see what repos you have up, and consider some of the less strict repos.  It looks like my installs included [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports for 'main' and 'universe' (e.g. not just the default gutsy repository).

Regards,
rcs

---

### Post by DaleEMoore on 2009-10-16
Y'all might be happy to know that this is a problem with Dell Studio Laptops on Ubuntu 9.10. All other sound works fine, it's LinDVD and Skype that work for a few updates, then fail for a few updates.

I thought you might like to know.

I went looking for a "Submit Bug" but neither products have the standard Help, Submit Bug feature.

---

