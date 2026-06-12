---
title: "Toshiba M30X-113: Installation hangs"
date: 2005-02-11
forum: Hardware &amp; Laptops
---

### Post by nadador on 2005-02-11
Hi,

I'm trying to install Ubuntu on a Toshiba M30X-113, but the installation hangs on the "Installing the Ubuntu base system" window, 95% of the way, with the message "Installing extra packages...", apparently just after installing the kernel.

I've tried both the standard installation and the custom installation, but it appears that they are identical up to the point where the installation hangs.

I've also tried several boot options, including disabling PCMCIA detection that I know hangs the machine (at a much earlier point in the installation process).

BTW, I'm able to run Ubuntu from the live CD.

Any clue on how to work around this problem?

Thanks

---

### Post by mendicant on 2005-02-11
It could be a corrupt CD.

---

### Post by nadador on 2005-02-11
Burned another CD meanwhile and got exactly the same result.

The filesystem I'm using is ext2.

---

### Post by Technoviking on 2005-02-11
See if this page helps:
[http://www.alchar.org/~aedil/Toshiba-M30X.html](http://www.alchar.org/~aedil/Toshiba-M30X.html)

Mike

---

### Post by nadador on 2005-02-12
Thanks Mike, but actually it was from that page I first learned about M30X-113 problems with PCMCIA. 

As I'm disabling it, it should not be the problem, unless any extra package being installed tries to probe the PCMCIA bus.

---

### Post by nadador on 2005-02-12
Checked the md5sum of the first CD (one of those with the nice Ubuntu jacket), that I got from a friend who had previously installed it successfully. And the md5sums matched, as you can see from the following (edited) lines (the differences indicated refer to files whose md5sum is not in file md5sum.txt on the installation CD).

Is there a different interface that would allow me to pinpoint more precisely the problem?

---------------------------------------------------------------------------------------------------------------

maresia:/cdrom$ find ./ -follow -xtype f -exec md5sum \{\} \; > ~/my_md5sum.txt
maresia:~$ sort +1 /cdrom/md5sum.txt > ubuntu_md5sum_sort
maresia:~$ sort +1 my_md5sum.txt > my_ubuntu_md5sum_sort
maresia:~$ diff my_ubuntu_md5sum_sort ubuntu_md5sum_sort
15,23d14
< 4bbcc589937b0b5ff34bb13d94d25224  ./dists/stable/Release
< 7d12ecd0864179405d143f936ef552aa  ./dists/stable/main/binary-i386/Packages
< 0ccd77e5a02263822b63c0665c0dde4e  ./dists/stable/main/binary-i386/Packages.gz
< d368383e08c10f853093f9bd92b15adf  ./dists/stable/main/binary-i386/Release
< fc1c3bf4d3d06a1431e4d319e4bef857  ./dists/stable/main/debian-installer/binary-i386/Packages
< 7fe3c977a112aef2fc6e4e0f6ae33916  ./dists/stable/main/debian-installer/binary-i386/Packages.gz
< 1dab4924568dab6ecfab8441005051ea  ./dists/stable/restricted/binary-i386/Packages
< 312f8d4aaf14060a80d15e980abc3bd2  ./dists/stable/restricted/binary-i386/Packages.gz
< 835c6814050e6a403ef67de2ba59b231  ./dists/stable/restricted/binary-i386/Release
33,41d23
< 4bbcc589937b0b5ff34bb13d94d25224  ./dists/unstable/Release
< 7d12ecd0864179405d143f936ef552aa  ./dists/unstable/main/binary-i386/Packages
< 0ccd77e5a02263822b63c0665c0dde4e  ./dists/unstable/main/binary-i386/Packages.gz
< d368383e08c10f853093f9bd92b15adf  ./dists/unstable/main/binary-i386/Release
< fc1c3bf4d3d06a1431e4d319e4bef857  ./dists/unstable/main/debian-installer/binary-i386/Packages
< 7fe3c977a112aef2fc6e4e0f6ae33916  ./dists/unstable/main/debian-installer/binary-i386/Packages.gz
< 1dab4924568dab6ecfab8441005051ea  ./dists/unstable/restricted/binary-i386/Packages
< 312f8d4aaf14060a80d15e980abc3bd2  ./dists/unstable/restricted/binary-i386/Packages.gz
< 835c6814050e6a403ef67de2ba59b231  ./dists/unstable/restricted/binary-i386/Release
126,141d107
< c0aabfc52431fbe6e5d3cfbec993796e  ./isolinux/boot.cat
< ecdb27d1d047002a19ad90c59d232b72  ./isolinux/f1.txt
< 299c967950085f96deba1e14058915cb  ./isolinux/f10.txt
< 7ed26cfd274bd845c8b118d652517f79  ./isolinux/f2.txt
< ebe09ff4056c7cb21bfce2e2878ea6a9  ./isolinux/f3.txt
< 3d5369989afe3d4a8419a075ce999385  ./isolinux/f4.txt
< 8edaea48b64aafb1ea4d807e8ecb0df4  ./isolinux/f5.txt
< e7c750deffe2ab95bd3dfe141cf49ce1  ./isolinux/f6.txt
< eba97317e4e92fd1f8a3cf71f2e4e8e5  ./isolinux/f7.txt
< 087c2d9f18ac4e506d660512fcd0daca  ./isolinux/f8.txt
< a40b87cb7929c0ca360a358d579d30ed  ./isolinux/f9.txt
< b38dffaee52d81a63ab8058f25de48f7  ./isolinux/isolinux.bin
< 7fd1abfcda22de479671cd93145fbd71  ./isolinux/isolinux.cfg
< 32ede149fd43dd1a0b9fe6fb3067fb7d  ./isolinux/isolinux.txt
< a2025860ab1137f990fe026ad9c938c5  ./isolinux/splash.rle
< 742d96776e64d7873e42eaf92b606a28  ./md5sum.txt

maresia:~$  wc -l my_ubuntu_md5sum_sort
   1128 my_ubuntu_md5sum_sort
maresia:~$  wc -l ubuntu_md5sum_sort
   1094 ubuntu_md5sum_sort
maresia:~$ diff my_ubuntu_md5sum_sort ubuntu_md5sum_sort | wc -l
     37

---

### Post by barranco on 2005-10-30
has anyone gotten the pcmcia working after the install? now with breeze I didn't have to disable pcmcia detection but it doesn't work anyways...

---

