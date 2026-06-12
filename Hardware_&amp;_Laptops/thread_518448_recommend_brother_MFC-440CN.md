---
title: "recommend brother MFC-440CN"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by ruff on 2007-08-05
Hi All,

Just thought I would put a quick post up to recommend the Brother MFC-440CN multifuntion printer / scanner / FAX as a network printer under Ubuntu. I have a mixed network at home with windows and linux machines on it. I needed a printer that the whole network could share through my router. I connected this printer via cat-5 to my router and downloaded the .deb packages from the brother website and got things up and running flawlessly in a matter of minutes. Very good docs on the brother website to assist in setting up. No dependency problems or errors with the downloaded .deb packages. I am able to print and scan on any machine on the network.

Well done Brother. It is great to see a manufacturer of peripherals supporting linux.

Cheers,

Ruff.  :)

---

### Post by Azrael Nightwalker on 2007-10-15
I bought this printer today and the drivers from Brother site won't install on Ubuntu 7.10 (Gutsy Gibbon).

azrael@azrael-laptop:~/MyStuff/Download$ wajig force mfc440cncupswrapper-1.0.0-10.i386.deb
(Odczytywanie bazy danych ... 147558 plików i katalogów obecnie zainstalowanych.)
Przygotowanie do zast&#261;pienia mfc440cncupswrapper 1.0.0-10 (wykorzystuj&#261;c mfc440cncupswrapper-1.0.0-10.i386.deb) ...
/var/lib/dpkg/info/mfc440cncupswrapper.prerm: 3: /usr/local/Brother/Printer/mfc440cn/cupswrapper/cupswrappermfc440cn: not found
dpkg: ostrze&#380;enie - poprzedni skrypt pre-removal zwróci&#322; kod b&#322;&#281;du 127
dpkg - próba wywo&#322;ania skryptu z nowego pakietu ...
/var/lib/dpkg/tmp.ci/prerm: 3: /usr/local/Brother/Printer/mfc440cn/cupswrapper/cupswrappermfc440cn: not found
dpkg: b&#322;&#261;d przetwarzania mfc440cncupswrapper-1.0.0-10.i386.deb (--install):
 podproces new pre-removal script zwróci&#322; kod b&#322;&#281;du 127
/var/lib/dpkg/info/mfc440cncupswrapper.postinst: 3: /usr/local/Brother/Printer/mfc440cn/cupswrapper/cupswrappermfc440cn: not found
cp: nie mo&#380;na wykona&#263; stat na `/usr/share/cups/model/brmfc440cn.ppd': No such file or directory
dpkg: b&#322;&#261;d podczas czyszczenia &#347;rodowiska:
 podproces post-installation script zwróci&#322; kod b&#322;&#281;du 1
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
 mfc440cncupswrapper-1.0.0-10.i386.deb

---

### Post by Azrael Nightwalker on 2007-10-15
There are bugs filed:
[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/16704](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/16704)
[https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/25966](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/25966)
[https://bugs.launchpad.net/ubuntu/+bug/138378](https://bugs.launchpad.net/ubuntu/+bug/138378)

I've also found something in the FAQ but it didn't help:
[http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#120](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#120)
[http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#80](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#80)

---

### Post by michalroxorpl on 2007-12-02
> **Azrael Nightwalker said:**
> There are bugs filed:
Bugs filed, yet not resolved, and users wish to use their hardware, so, there is a little script, that should help you achieving the target: having Brother MFC-440CN working out of the box ;-) This script is included as attachment below the message.
```


#!/bin/bash
#    copyright: Michal Cieslicki <michal@roxor.pl>
#    This program is free software; you can redistribute it and/or
#    modify it under the terms of version 2 of the GNU General Public
#    License published by the Free Software Foundation.
#IPADDR=192.168.1.71
IPADDR=${1}
if [ "${IPADDR}" != "" ]; then
    if [ `ping -qc1 ${IPADDR} 2>&1 >/dev/null;echo $?` -eq 0 ]; then
        echo|sudo apt-get install csh tcsh sane xsane sane-utils
        for file in faxshare/brmfcfaxcups-1.0.0-1.i386.deb \
                    faxshare/brmfcfaxlpd-1.0.0-1.i386.deb \
                    sane_debian/brscan2-0.2.4-0.i386.deb \
                    cups_wrapper/mfc440cncupswrapper-1.0.0-10.i386.deb \
                    lpr_debian/mfc440cnlpr-1.0.0-9.i386.deb ; do wget -c http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/${file};done
        sudo ln -sf /etc/init.d/cupsys /etc/init.d/lpd
        sudo mkdir -p /var/spool/lpd/mfc440cn
        sudo mkdir -p /var/spool/lpd/BRFAX
        for uninstProg in mfc440cncupswrapper mfc440cnlpr brscan2 brmfcfaxlpd brmfcfaxcups ; do if [ "`dpkg -l|grep ^ii|grep ${uninstProg}`" != "" ]; then sudo dpkg -r ${uninstProg}; fi; done
        sudo dpkg -i --force-all --force-architecture mfc440cnlpr-1.0.0-9.i386.deb
        sudo dpkg -i --force-all --force-architecture mfc440cncupswrapper-1.0.0-10.i386.deb
        sudo dpkg -i brscan2-0.2.4-0.i386.deb
        echo -ne '#!'"/bin/sh\necho \"Dirty uninstall hack by michal@roxor.pl\"\n"|sudo tee /var/lib/dpkg/info/brscan2.postrm > /dev/null
        sudo dpkg -i brmfcfaxlpd-1.0.0-1.i386.deb
        sudo dpkg -i brmfcfaxcups-1.0.0-1.i386.deb
        sudo lpadmin -p MFC440CN -E -v lpd://${IPADDR}
        sudo lpadmin -p BRFAX -E -v lpd://${IPADDR}
        sudo brsaneconfig2 -a name=MFC440CN model=MFC-440CN ip=${IPADDR}
        sudo rm /etc/init.d/lpd
        sudo rmdir --ignore-fail-on-non-empty /var/spool/lpd/BRFAX 2>/dev/null
        sudo rmdir --ignore-fail-on-non-empty /var/spool/lpd/mfc440cn 2>/dev/null
        sudo rmdir --ignore-fail-on-non-empty /var/spool/lpd 2>/dev/null
    else
        echo "Printer seems not to be connected under ${IPADDR}..."
    fi
else
    echo "Please, configure ip address or pass it as cmd-line parameter..."
fi

```

If you have problem uninstalling brscan2 utility, just execute the following line before any other steps (this will disable broken brothersolutions post remove script): 
```

echo -ne '#!'"/bin/sh\necho \"Dirty uninstall hack by michal@roxor.pl\"\n"|sudo tee /var/lib/dpkg/info/brscan2.postrm > /dev/null

```

The printer should work now, to check if you have two extra printers installed, execute:
```

lpc status|grep :|sed -e s,:$,,g

```

If you wish to make things more rapidly, set the ip address of the printer:
```

IPADDR=192.168.1.71

```
After that, just paste the following command (remember to have ip address  of the printer set in the line above); it will fetch this script from my server and process the changes listed in above listing. I do not know how to make this available from ubuntuforums.org as attachments are availavle after logging in. Here is the code:
```

t=`mktemp -d`;cd ${t};wget http://b50.roxor.pl/~michal/brother_mfc-440cn_install.sh -O - |bash -s -- ${IPADDR};cd "${OLDPWD}";rm -f ${t}/*;rmdir ${t}

```

---

### Post by jaktomas1 on 2007-12-31
> **ruff said:**
> Hi All,

Just thought I would put a quick post up to recommend the Brother MFC-440CN multifuntion printer / scanner / FAX as a network printer under Ubuntu. I have a mixed network at home with windows and linux machines on it. I needed a printer that the whole network could share through my router. I connected this printer via cat-5 to my router and downloaded the .deb packages from the brother website and got things up and running flawlessly in a matter of minutes. Very good docs on the brother website to assist in setting up. No dependency problems or errors with the downloaded .deb packages. I am able to print and scan on any machine on the network.

Well done Brother. It is great to see a manufacturer of peripherals supporting linux.

Cheers,

Ruff.  :)
I'm getting ready to convert to Ubuntu and will have a mixed network with a Brother MFC440CN, any words of wisdom for finding drivers and set up? Your post seems to be the most optomistic I've read on the matter.

[email]jaktomas1@gmail.com[/email]

---

### Post by ardoaamch on 2008-03-07
I did a write up on my site for how to install this printer:
[http://adammichaelroach.com/2008/03/03/how-to-brother-mfc-440cn-on-ubuntu-linux-710-gutsy-gibbon/](http://adammichaelroach.com/2008/03/03/how-to-brother-mfc-440cn-on-ubuntu-linux-710-gutsy-gibbon/)

---

### Post by luvit on 2008-03-14
Hi. I installed my networked Brother MFC-845CW today and it seems to work well on my clean install of v7.10.  I outlined all the steps I took to install it in my blog (see my signature).

My experience is for the MFC-845CW, but I wrote the outline and provided links to Brother's files in hopes it would benefit other models.

Please let me know if the outline is easy to follow. --Thanks! ...and good luck.

I wrote this outline so that USB printers may be able to follow my directions too... just ignore the steps that mention LPR files if you are connecting via USB.;)

---

### Post by NongA_TongE on 2008-03-29
> **ardoaamch said:**
> I did a write up on my site for how to install this printer:
[http://adammichaelroach.com/2008/03/03/how-to-brother-mfc-440cn-on-ubuntu-linux-710-gutsy-gibbon/](http://adammichaelroach.com/2008/03/03/how-to-brother-mfc-440cn-on-ubuntu-linux-710-gutsy-gibbon/)

Thanks for Posting this.  

The instructions were great for finding and installing the proper drivers.  However, when I go into system > Administration > Printers > New Printer,  The printer is not seen.  I know that it is up on my network, as I can ping it. 

Does anyone have any suggestions for troubleshooting this issue?

---

### Post by luvit on 2008-03-30
> **NongA_TongE said:**
> Thanks for Posting this.  

The instructions were great for finding and installing the proper drivers.  However, when I go into system > Administration > Printers > New Printer,  The printer is not seen.  I know that it is up on my network, as I can ping it. 

Does anyone have any suggestions for troubleshooting this issue?

I have outlined steps when I setup my MFC-845CW printer.[**[COLOR="Blue"]here[/COLOR]**]("http://www.yay4u.com/2008/03/ensure-all-applications-are-closed.html") with those detailed steps.
I hope my blog helps you. ;)

---

### Post by matrix2war on 2008-05-10
Problems installing this printer undero ubuntu 8.04

this is what it shows in my console. already have tsch installed. 

fabian@fabian-desktop:~$ cd Desktop
fabian@fabian-desktop:~/Desktop$ sudo dpkg -i --force-all mfc440cnlpr-1.0.1-1.i386.deb
[sudo] password for fabian: 
(Reading database ... 154160 files and directories currently installed.)
Preparing to replace mfc440cnlpr 1.0.1-1 (using mfc440cnlpr-1.0.1-1.i386.deb) ...
Unpacking replacement mfc440cnlpr ...
Setting up mfc440cnlpr (1.0.1-1) ...
mkdir: cannot create directory `/var/spool/lpd/mfc440cn': No such file or directory
chown: cannot access `/var/spool/lpd/mfc440cn': No such file or directory
chgrp: cannot access `/var/spool/lpd/mfc440cn': No such file or directory
chmod: cannot access `/var/spool/lpd/mfc440cn': No such file or directory

fabian@fabian-desktop:~/Desktop$ sudo dpkg -i --force-all mfc440cncupswrapper-1.0.1-1.i386.deb
Selecting previously deselected package mfc440cncupswrapper.
(Reading database ... 154160 files and directories currently installed.)
Unpacking mfc440cncupswrapper (from mfc440cncupswrapper-1.0.1-1.i386.deb) ...
Setting up mfc440cncupswrapper (1.0.1-1) ...
 * Restarting Common Unix Printing System: cupsd                         [ OK ]



any suggestions? 

thanks.

---

### Post by luvit on 2008-05-11
> **matrix2war said:**
> Problems installing this printer under ubuntu 8.04
 * Restarting Common Unix Printing System: cupsd                         [ OK ]

matrix2war, are you installing on a 64bit processor?

If not, have you tried the steps from my blog?  I wrote it for Gusty Gibbon on a MFC-845CW, but I believe someone noted it helped on 8.04. and the driver installer steps are pretty universal from brother.

Lemme know.

---

