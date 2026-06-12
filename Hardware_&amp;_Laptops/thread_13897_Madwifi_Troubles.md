---
title: "Madwifi Troubles"
date: 2005-02-03
forum: Hardware &amp; Laptops
---

### Post by deception on 2005-02-03
I have apt-get'ed linux-686. I have installed "linux-headers-2.6.8-1-3-686" and "linux-headers-2.6-686". I have installed sharutils. 

I was wondering if anyone could tell me what's wrong here when doing the make install for madwifi, latest cvs: 

> for i in ./ath_hal ath_rate/onoe ./net80211 ./ath; do \
        (cd $i; make install) || exit 1; \
done
make[1]: Entering directory `/home/deception/madwifi/ath_hal'
test -d //lib/modules/2.6.8.1 $(shell [ ! -f .extraversion ] || cat .extraversion)/net || mkdir -p //lib/modules/2.6.8.1 $(shell [ ! -f .extraversion ] || cat .extraversion)/net
/bin/sh: line 1: shell: command not found
cat: .extraversion: No such file or directory
/bin/sh: line 1: test: //lib/modules/2.6.8.1: binary operator expected
/bin/sh: line 1: shell: command not found
cat: .extraversion: No such file or directory
strip -S ath_hal.ko
cp ath_hal.ko //lib/modules/2.6.8.1 $(shell [ ! -f .extraversion ] || cat .extraversion)/net
/bin/sh: line 1: shell: command not found
cat: .extraversion: No such file or directory
cp: omitting directory `//lib/modules/2.6.8.1'
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/deception/madwifi/ath_hal'
make: *** [install] Error 1 

Thanks very much in advance,
Matt

P.S. I posted this in laptop support as I will need help with my PCMCIA card after this installs  :D

---

### Post by flyfishin on 2005-02-03
I haven't tried the compile-from-cvs method on Hoary yet.  I took the easy route and installed the linux-restricted-modules package which contains the madwifi drivers.

---

### Post by deception on 2005-02-03
Thanks for the response. I didn't realise madwifi was already installed on my system! 

I modprobe'd wlan, ath_hal and ath_pci, all are running. I have turned off encryption. 

But the card isn't shown in "Networking" nor lspci! This seems strange to mean.. no lspci entry. I do get an error on boot about PnPBIOS, I'm guessing that's the problem? But the card works fine in Windows... 

DLINK DWL-G650 C2 with Atheros chipset  :confused:

---

### Post by blahrus on 2005-02-03
when I do a:

apt-get install linux-restricted-modules-`uname -r`

I get this:

root@chodelaptop:/home/blahrus # apt-get install linux-restricted-modules-`uname  -r`
Reading Package Lists... Done
Building Dependency Tree... Done
linux-restricted-modules-2.6.8.1-4-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another p rocess
Setting up passwd (4.0.3-28.5ubuntu6.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another p rocess
dpkg: error processing passwd (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libssl0.9.7 (0.9.7d-3ubuntu0.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another p rocess
dpkg: error processing libssl0.9.7 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openssh-client:
 openssh-client depends on libssl0.9.7; however:
  Package libssl0.9.7 is not configured yet.
dpkg: error processing openssh-client (--configure):
 dependency problems - leaving unconfigured
Setting up lvm10 (1.0.8-4ubuntu1.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another p rocess
dpkg: error processing lvm10 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ppp:
 ppp depends on libssl0.9.7; however:
  Package libssl0.9.7 is not configured yet.
dpkg: error processing ppp (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 passwd
 libssl0.9.7
 openssh-client
 lvm10
 ppp
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by flyfishin on 2005-02-03
Based on the 4th line of the output you already have the restricted modules installed.  The rest of the errors look like you already have a lock on the package database.  Did you run apt-get at a command prompt with Synaptic already open?

---

### Post by blahrus on 2005-02-04
well I think I had something wrong from the install, downloaded the daily iso for hoary and installed, than ran,

apt-get install linux-restricted-modules-`uname -r`

and all way good.

Thanks guys!

---

### Post by deception on 2005-02-04
I still cannot get my card to show in Hoary nor Warty. I have loaded the modules but lspci still shows nothing to do with the card. The card works perfect in Windows. No linux distro has been able to pick ANY card up :( 

Any ideas?

---

### Post by king20878 on 2005-02-04
I've had no problems getting my ATT 5400G pcmcia card set up under warty or the d-link (model number escapes me) pci card in my desktop set up.  Both are Atheros chipset based and use the madwifi modules.  All I did was open up networking, select "add", chose a wireless connection, chose ath0 from the interface list, enter the essid and key, and BAM away I go.  

Is there a particular reason you're rolling your own modules?

---

### Post by deception on 2005-02-04
Well I only tried loading the modules as they wern't listed in lsmod and the card wasnt being recognised, but I expect madwifi is compiled into the kernel not as a module. 

I have updated the BIOS to see if that was the issue, and still in Hoary I cannot get a connection. I cannot see where to create an interface in Hoary, so I guess I'll have to edit /etc/network/interfaces. This seems so strange to me, the card is working perfect in windows but no distros that come with madwifi work, nor does ndiswrapper. On the ubuntulinux.org website, someone with EXACTLY the same card and version with the same chipset, atheros, says it works out of the box.

I really have no idea what's wrong.

---

### Post by flyfishin on 2005-02-04
You are right, you shouldn't have to do any manual editing of files.  So let's see if this is correct:

1. You installed linux-restricted-modules-`uname -r` on your system.
2. When you do an lsmod|grep ath as root you see the ath modules.
3. You plug in the card and no lights on the card are seen and nothing shows up in lspci.

What does /var/log/messages show when you insert the card? 

Type: tail -f /var/log/messages and see if anything shows when you insert your card.

---

### Post by deception on 2005-02-04
Your 3 points are correct, although I neglected to mention the power light turns on. lsmod shows the ath modules *after* I modprobe them. var/log/messages says nothing on the insert of the card :(

---

### Post by deception on 2005-02-04
if it helps:


It's a Toshiba Equium EA60-156. Texas makes the controller.

---

### Post by flyfishin on 2005-02-04
I, unfortunately, don't know what else to try.  It is really odd that nothing shows up in lspci.  I am assuming that since lspci doesn't list the device the system doesn't know to load the ath modules but that is a guess I really don't know the specific.  Although, my curiosity of how this stuff ties together.  That still leaves the question of why lspci shows nothing. Anyone else?

---

### Post by deception on 2005-02-05
Thanks for your input :) I thought of trying a newer version of pcmcia-cs? Maybe the one in Hoary does not work properly with my controller and card  :confused:

---

### Post by deception on 2005-02-07
Tried the latest pcmcia-cs release and still no go :( is this a common theme with toshiba laptops? I cannot find anything on google  :-( {|=

---

### Post by deception on 2005-02-26
Sorry if I'm being a pain on this, I am just desperate because I'm not liking using XP! I want my Ubuntu  \\:D/ 

_What the problem is_

The power LED lights on the DWL-G650 card. 

lspci shows the *controller* (ti1410) but  *not* the card. It doesn't mention the card. Even under the controller in lspci -v. 

It says on the Ubuntulinux.org website this card works out of the box. So it must be something to do with the controller. 

The controller aparantly needs the yenta_socket module to work. I load the yenta module and nothing happens. 

Any further ideas please?
Many thanks in advance!

---

### Post by smtanner on 2005-02-26
I have that same card and it is working perfectly under Hoary.  I did not have to do anything.

---

### Post by deception on 2005-02-27
[QUOTE=smtanner]I have that same card and it is working perfectly under Hoary.  I did not have to do anything.[/QUOTE]

Thanks for the reply :) I've tried 2 other cards also, and updated the BIOS. Is anyone familiar with the Toshiba BIOS? I think it's the CMOS I need to edit and change PC Card to PCIC but I cannot find this option  :-k

---

### Post by moopere on 2005-02-27
[QUOTE=deception]Thanks for the reply :) I've tried 2 other cards also, and updated the BIOS. Is anyone familiar with the Toshiba BIOS? I think it's the CMOS I need to edit and change PC Card to PCIC but I cannot find this option  :-k[/QUOTE]
 As you've probably already determined, if you can't see your card with lspci you're SOL and its almost certainly going to be a problem with the PC card controller.

There shouldn't be anything particularly Ubuntuish about the problem or the solution however - I'd do a quick google on "linux 1410" or something similar and see what others are doing to get their controllers working under recent kernels.

I've got two DWL-G650 C2 running here, one with Warty and one with Hoary.  Interestingly, my Dell Inspiron 2500 can't run this card at all under windows 2000 (!!!!) how weird huh?  Something 'funny' with the cardbus controller (O2micro OZ6933) which Win2K just can't cope with but Ubuntu and hotplug has no problems.

Regards,
Craig

---

### Post by deception on 2005-02-27
Thanks ever-so much for the reply. I've been in contact with the Laptop vendor and they confirmed there is no PC Card Controller options in the BIOS/CMOS on their end either. The only thing I can think of is negotiating with my dad now, to swap for his dell  :p

---

