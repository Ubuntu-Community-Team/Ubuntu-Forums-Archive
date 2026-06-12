---
title: "Error when trying to install Epson AcuLaser c1100 drivers (CUPS)"
date: 2009-09-01
forum: Hardware
---

### Post by Jarige on 2009-09-01
I'm trying to install drivers for an Epson AcuLaser c1100, connected trough SAMBA from Linux to Windows XP.
Whenever I select the printer from the driver list, it gives this error:
Missing Driver
Printer 'AL-C1100-' requires the 'pstoalc1100.sh' program but it is not currently installed.  Please install it before using this printer.

I donwnloaded 'Epson-ALC1100-filter-1.2.tar.gz' and executed these commands (in the directory of extracted tar) so far:

./configure
sudo make
sudo make install

As said, whenever I try to install the printer, it gives a 'Missing Driver' error. The required 'pstoalc1100.sh' is in the directory of extracted tar, and of course inside the tar itself.

What can I do to fix this?

---

### Post by Marc Higgins on 2010-01-02
9.10 seems to be missing libstdc++5_3.3.6-17ubuntu1_i386.deb

In order to install the Epson C1100 under 9.10 on the standard i386 platform please open an terminal via ACCESSORIES > TERMINAL & make a directory as explained below to store your installation files;


```
mkdir epson_install
```

move to the installation directory you just created;

```
cd epson_install
```

get the installation files from our website [000it.com]("http://000it.com")

```
wget [http://000it.com/files/epson_c1100/epson_c1100_install.tar.gz](http://000it.com/files/epson_c1100/epson_c1100_install.tar.gz)
```

extract the compressed file;

```
tar -zxvf epson_c1100_install.tar.gz
```

install the deb installation files you have just extracted;

```
sudo dpkg -i *.deb
```

from here you can install your Epson C1100 just as you would normally install any other printer using the SYSTEM > ADMINISTRATION > PRINTERS menu. When/if called for the ppd (PostScript® printer description) file, please point to the "epson_install" directory & select the file Epson-AL-C1100-fm3.ppd

This has worked on +20 machines in our group without failure, so please let me know if you have a better way, &/or if this didn't work for you.

---

### Post by Jarige on 2010-01-22
Thanks for your reply. I forgot about this thread :S
I've found a more simple solution:
[http://qld.yi.org/it_i/epson-alc1100-filter_1.2-1_i386.deb]("http://qld.yi.org/it_i/epson-alc1100-filter_1.2-1_i386.deb")
[http://qld.yi.org/it_i/epson-alc1100-filter-cups_1.2-1_i386.deb]("http://qld.yi.org/it_i/epson-alc1100-filter-cups_1.2-1_i386.deb")

These two files will install the same thing you just did, only faster and simpler :)
And I think I installed that libstdc++5_3.3.6-17ubuntu1_i386.deb either, cause I still have it in my downloads map :P

I've found the links here btw:
[http://ubuntuforums.org/archive/index.php/t-597629.html]("http://qld.yi.org/it_i/epson-alc1100-filter-cups_1.2-1_i386.deb")

I hope anyone will find these links useful :)

---

### Post by FreeThinker_GB on 2010-03-09
:KS:KS:KS:KS:KS Many thanks worked a treat!

---

### Post by stewartv on 2010-04-30
This method doesn't work for me in Ubuntu 10.04 64-bit but it worked fine in 32-bit. I get a /usr/lib/cups/filter/foomatic-rip failed error message.

Can anyone help? The reading I've done doesn't address this specific printer or ubuntu version and suggests problems with the .ppd file or its location.

Any ideas?

I've pointed other Al-C1100 users at this solution previously because it works so well. We AL-C1100 users need all the help we can get!

Thanks

---

### Post by pe7er on 2010-05-25
> **Marc Higgins said:**
> 9.10 seems to be missing libstdc++5_3.3.6-17ubuntu1_i386.deb

In order to install the Epson C1100 under 9.10 on the standard i386 platform please open an terminal via ACCESSORIES > TERMINAL & make a directory as explained below to store your installation files;
Thank you very much for this explanation!
It works okay at Ubuntu 10.04 (32 bit version).

---

### Post by JLich on 2010-06-08
I had installed 10.04 x64, and c1100 don't ran in it. 
  I got c1100 to run with AVASYS official driver. After installing with configure, make, make install, i installed cups and then configured the printer. But printer don't printed any page.
  After seeking i had seen an error in /usr/local/bin/alc1100 execution that don't found libstdc++5.
Browsing i found someone that installed in 10.04 libstdc++5, but 32 bit version.

---- original post ---
The original libstdc++5 package is no longer available with the Ubuntu 9.10 repos. So for 32 bit system you would have to get it from Jaunty Repository.

Install it and you are good to go if you are on 32 bit machine.

For 64 bit it is a bit complicated, first install libstdc++5 64bit and then do the following:

    wget http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu6.1_amd64.deb

    dpkg-deb -x ia32-libs_2.7ubuntu6.1_amd64.deb ia32-libs

    sudo cp ia32-libs/usr/lib32/libstdc++.so.5.0.7 /usr/lib32/

    cd /usr/lib32

    sudo ln -s libstdc++.so.5.0.7 libstdc++.so.5

---  end post  ----

after install libstdc++5 in 32bit and restarting cups the printer runs ok.

pd.  ia32-libs_2.7ubuntu6.1_amd64.deb ia32-libs was to slow through wget and i had to downloaded it from web.

---

