---
title: "Epson Scanner not found"
date: 2011-05-12
forum: Hardware
---

### Post by gwilson on 2011-05-12
My Epson V300 scanner did not work in the new Mint Linux 11 Release Candidate (Ubuntu 11.04-based), and when I went back to check it in Linux Mint LMDE (Debian-based) it had ceased to function there, as well. Some upgrade or update is involved here. 

After reading a couple of threads, I have things working again. I normally use the Iscan software from Avasys [http://avasys.jp/eng/](http://avasys.jp/eng/) and so I went there, put in the model of my scanner, and downloaded the latest files. There are now three files required where there used to be only two. Make sure you pay attention to the details and download the right files for your version of Ubuntu.   Next:

1) Open Synaptic Package Manager, use the SEARCH function to find "iscan" files installed (two in my case), mark them for complete removal, and click on reply.
2) Go to the folder containing the new files you downloaded. Right-click on each file and use Gdebi Package Installer to install them.

IMPORTANT NOTE: The three files must be installed in a particular order or you will get dependency errors. In my case for the V300 it was this:

1)  iscan-data_1.8.1-1_all.deb
2)  iscan_2.26.3-1.ltdl7_i386.deb
3)  esci-interpreter-gt-f720_0.1.1-2_i386.deb

The "esci-interpreter" file seems not to have been required in the past, but it is now.

After removing the old iscan files and installing these three new ones, my V300 scanner was once again detected in Mint 10 LMDE (based on Debian) and could now be found in Mint 11 RC (based on Ubuntu 11.04). Simple Scan also works now whereas before it could not detect the scanner at all.

Hope this helps someone out.

---

### Post by isync on 2011-07-15
It worked!

Running **Ubuntu 11.04**, in my case the path was:

0. Deinstall --purge of all iscan related packaged (two were installed)
1. iscan-data_1.9.0-1_all.deb
2. iscan_2.26.4-2.ltdl7_i386.deb
3. esci-interpreter-perfection-v330_0.1.1-2_i386.deb

And now I've got my **Epson V330 Photo** back working after a dist-upgrade to Natty 11.04.

---

