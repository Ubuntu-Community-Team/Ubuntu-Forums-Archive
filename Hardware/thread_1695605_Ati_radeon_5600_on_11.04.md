---
title: "Ati radeon 5600 on 11.04?"
date: 2011-02-26
forum: Hardware
---

### Post by JAM3SoN on 2011-02-26
Hi guys, my graphics card is Ati radeon HD 5600 Series. Yesterday I performed upgrade to Ubuntu 11.04 and I am not able to install driver.

I went to AMD page, found this download: "**AMD Catalyst&#8482; 11.2 Proprietary Linux x86 Display Driver**" but when I install it, my computer won't boot. I see loading screen, then it goes back to "console mode" and last thing I see is "Checking battery state [OK]". Then it hangs on black screen. I must uninstall this driver using recovery mode and work without it. I tried even 11.1 driver but that is not working as well.

Weird thing is that when I go to System - Additional drivers, it doesn't find anything. I don't remember exactly but it used to find some graphics driver.

What should I try? :)

Thanks in advance!

Edit: When I run installer through console it gives me error message "DKMS part of installation failed.  Please refer to /usr/share/ati/fglrx-install.log for details". This is in log:
Creating symlink /var/lib/dkms/fglrx/8.801/source ->
                 /usr/src/fglrx-8.801

DKMS: add Completed.
You can use the --kernelsourcedir option to tell DKMS where it's located, or you could install the linux-headers-2.6.38-5-generic-pae package.
[Error] Kernel Module : Failed to build fglrx-8.801 with DKMS
[Error] Kernel Module : Removing fglrx-8.801 from DKMS

------------------------------
Deleting module version: 8.801
completely from the DKMS tree.
------------------------------
Done.
[Reboot] Kernel Module : update-initramfs

---

### Post by Yellow Pasque on 2011-02-26
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Xserver_1.10_Incompatibility_Warning](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Xserver_1.10_Incompatibility_Warning)

---

### Post by JAM3SoN on 2011-02-26
Thank you, I ended on last step with following info:
$ sudo dpkg -i fglrx*.deb
Vyberá sa predtým zru&#353;ený balík fglrx-amdcccle.
(&#268;íta sa databáza ... momentálne je nain&#353;talovaných 160699 súborov alebo adresárov.
Rozba&#318;uje sa fglrx-amdcccle (z fglrx-amdcccle_8.801-0ubuntu1_i386.deb) ...
Vyberá sa predtým zru&#353;ený balík fglrx-dev.
Rozba&#318;uje sa fglrx-dev (z fglrx-dev_8.801-0ubuntu1_i386.deb) ...
Vyberá sa predtým zru&#353;ený balík fglrx-modaliases.
Rozba&#318;uje sa fglrx-modaliases (z fglrx-modaliases_8.801-0ubuntu1_i386.deb) ...
Vyberá sa predtým zru&#353;ený balík fglrx.
Rozba&#318;uje sa fglrx (z fglrx_8.801-0ubuntu1_i386.deb) ...
Nastavuje sa balík fglrx-modaliases (2:8.801-0ubuntu1) ...
[B]dpkg: problémy so závislos&#357;ami zabránili konfigurácii balíka fglrx:
 xserver-xorg-core (2:1.9.99.902-2ubuntu1) kazí fglrx (<= 2:8.801-0ubuntu2) a je in&#353;talovaný.
  Verzia fglrx, ktorá sa má konfigurova&#357;, je 2:8.801-0ubuntu1.[/B]
dpkg: chyba pri spracovávaní fglrx (--install):
 problémy so závislos&#357;ami - po necháva sa nenakonfigurované
dpkg: problémy so závislos&#357;ami zabránili konfigurácii balíka fglrx-amdcccle:
 fglrx-amdcccle závisí na fglrx; aj ke&#271;:
  Balík fglrx e&#353;te nie je nakonfigurovaný.
dpkg: chyba pri spracovávaní fglrx-amdcccle (--install):
 problémy so závislos&#357;ami - po necháva sa nenakonfigurované
dpkg: problémy so závislos&#357;ami zabránili konfigurácii balíka fglrx-dev:
 fglrx-dev závisí na fglrx; aj ke&#271;:
  Balík fglrx e&#353;te nie je nakonfigurovaný.
dpkg: chyba pri spracovávaní fglrx-dev (--install):
 problémy so závislos&#357;ami - po necháva sa nenakonfigurované
Spracúvajú sa spú&#353;&#357;a&#269;e ureadahead ...
ureadahead will be reprofiled on next reboot
Spracúvajú sa spú&#353;&#357;a&#269;e man-db ...
Vyskytli sa chyby po&#269;as spracovania:
 fglrx
 fglrx-amdcccle
 fglrx-dev

It seems that configuration mistake in fglrx broke instalation of next modules and this is simple translation of error message:
[B]dpkg: dependency problems prevented configuration of package fglrx:
 xserver-xorg-core (2:1.9.99.902-2ubuntu1) breaks fglrx (<= 2:8.801-0ubuntu2) and is installed.
  Version of fglrx, that has to be configured, is 2:8.801-0ubuntu1.[/B]

Dunno how to fix it :(

---

### Post by Yellow Pasque on 2011-02-26
fglrx is not going to work with natty/11.04 right now. That was the point of the big red warning I linked you to....
Anyway, this is how to recover: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

---

### Post by JAM3SoN on 2011-02-26
Many times thanks again. That info was quite confusing as I thought that patching will help. So I should possibly wait for 11.3 that should be compatible.

---

### Post by Yellow Pasque on 2011-02-26
Yes, wait for 11.3

---

