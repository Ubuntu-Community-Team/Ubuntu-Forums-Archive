---
title: "failed upgrade from 8.04 to 8.10 only boots to terminal"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by junglejuice on 2009-04-06
hi 
i tried to upgrade my current ubuntu 8.04 32 bit system via synaptic as i obtained 6 DVD's with all current official and unofficial (including universe and multiverse etc) packages for ubuntu 8.10 32 bit (i got the DVD's from a freedom toaster in south africa). i had to use synaptic as update manager would only allow me to do a partial upgrade and when i chose to do the partial upgrade option it would not let me, saying it was unable to complete the request and that i should try again later as the problem was probably transient. 
after several unsuccessful attempts with update manager i decided to try upgrading my system via synaptic. so i loaded the 6 DVD's as third party software in the software repositories section, clicked the "mark all upgrades" button and "apply". synaptic then proceeded to download 30MB from the internet (which is fine as prior to loading the DVD's this number used to be about 495MB, and that's why i chose to use the DVD's). this is when things started going wrong. 
synaptic said that it was interrupted and that i needed to run 
```
dpkg --configure -a
``` 
manually in order to fix the problem, but when i tried to open terminal it would not let me. terminal would just not start! so i tried running the command with Alt-F2 and nothing happened. 
back to synaptic i tried to continue with the upgrade but synaptic just seemed to be stuck and inactive.
at this stage i'd had enough of synaptic's unresponsiveness and decided to reboot my computer.
the problem is, now the window manager (x.org) will not start infact the only thing that happens is ubuntu boots up to a terminal display but i can't run any commands with sudo. everytime i try to run something with sudo i get the error
/lib/tls/i686/cmov/lib.so.6 GLIBC_2.8 not found
what does this mean, and can i restore my system to it's previous state?
i am typing this post because i was able to boot into ubuntu from a live CD as i do not have any other OS's on my PC. subsequently i had a look in the location of where the error is pointing to (in my normal installation) and the file it says it cannot find is actually indeed in that location. please help as i cannot do any work on my computer until i can get a proper installation of ubuntu up and running again, and i really don't want to have to go through the schlep of having to do a clean installation AGAIN (as i had similar problems upgrading from 7.04 to 7.10 and again from 7.10 to 8.04 and both times constituted me having to do clean installs).
please help
desperate
jj

---

### Post by junglejuice on 2009-04-07
bump... sorry guys this is pretty urgent
thanks
jj

---

### Post by miklcct on 2009-04-07
Please give me your /etc/apt/menu.lst here. I need this to check if the repos are correct.

After fixing /etc/apt/menu.lst , boot into recovery mode and type the following:

**dhclient** # to get networking
**aptitude** # package manager

After aptitude box is shown, type 'u'. This will update your cache. Then, type 'U' (upgrade) and type 'g' (go). If everything is OK, type 'g' again to apply. After that, type **exit** and your system should work.

---

### Post by junglejuice on 2009-04-08
hi there
correction when i type anything with sudo at terminal the error i get is 
sudo:/lib/tls/i686/cmov/libc.so.6:version 'GLIBC_2.8' not found (required by sudo)

hi miklcct
i could not find a file called menu.lst in the location you specified.
also i connect to the internet via a 3G type modem huwei E220 i use wvdial and it does not seem to work unless i have the proper wvdial.conf settings installed, should i still use this command 
```
dhclient
```
once menu.lst is corrected?
thanks for the help
jj

---

### Post by junglejuice on 2009-04-08
hi
when you say 
> boot into recovery mode
how does one do this? 
i tried starting aptitude from my user account which is the default account that ubuntu boots into, and then once in aptitude i hit F10 then choose 'Actions' and 'Become Root'. but when i try to become root this way it gives me the error
```
E: Failed to write temporary StateFile /var/lib/apt/extended_states.tmp
E:Subprocess exited with an error -- did you type your password correctly?
``` 
the problem is that it did not give me an opportunity to type my password, please could you advise?
> Please give me your /etc/apt/menu.lst here. I need this to check if the repos are correct.
as i mentioned in my previous post there is no file in the location you specified called menu.lst the is however a file called sources.list which does seem to have information about the repositories. the information in this file follows...
```
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://za.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://za.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb cdrom:[8.04 disc 01]/ hardy main multiverse restricted universe
deb cdrom:[8.04 disc 02]/ hardy main multiverse restricted universe
deb cdrom:[8.04 disc 03]/ hardy main multiverse restricted universe
deb cdrom:[8.04 disc 04]/ hardy main multiverse restricted universe
deb cdrom:[8.04 disc 05]/ hardy main multiverse restricted universe
deb cdrom:[8.04 disc 06]/ hardy main multiverse restricted universe
# deb http://repository.salutis.sk/production ./
# deb http://ppa.launchpad.net/exaile-devel/ubuntu hardy main
# deb http://wine.budgetdedicated.com/apt hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"
deb cdrom:[8.10 disc 01]/ intrepid main multiverse restricted universe
deb cdrom:[8.10 disc 2]/ intrepid main multiverse restricted universe
deb cdrom:[8.10 disc 3]/ intrepid main multiverse restricted universe
deb cdrom:[8.10 disc 4]/ intrepid main multiverse restricted universe
deb cdrom:[8.10 disc 05]/ intrepid main multiverse restricted universe
deb cdrom:[8.10 disc 6]/ intrepid main multiverse restricted universe
```
finally when you mentioned that i need to get networking up and running 
> dhclient # to get networking
does this mean that aptitude is going to try update my system by downloading packages from the internet, because this will not be possible as i do not have the bandwidth to support this option. this is why i was using the DVD's i mentioned in the original post.
thanks again for your help it is greatly appreciated.
regards
jj

---

### Post by junglejuice on 2009-04-08
bump, bump ...sorry guys this is really important
please help :-(

---

