---
title: "R9 290 with Catalyst 13.12 not working at all."
date: 2014-02-02
forum: Hardware
---

### Post by mjdabo on 2014-02-02
Hello, first time writing here. 

As i have made my switch over to Ubuntu now, I'm trying to install the AMD catalyst drivers from AMD's website. I did this because i found no proprietary drivers on "software and updates". I belive this is because the R9 290 GPU is still very new, so i have no choice i think. After downloading the catalyst drivers and extracting the zip. I get a .run file, which i executed from the terminal with sudo sh <filename>.run. After this a graphical window popped up with the installation of the drivers. I accepted the terms and conditions and clicked install. At the end of the installation progress it says that i had recieved an error during the installation. I checked the .log file and it said that it was unable to compile the kernel or something. No matter what, after the installation completed i had to do a reboot. After rebooting i got to the login screen, logged in and the screen is completely black. I can only see my mouse and nothing else. So at that point i reinstalled Ubuntu completely.

Any help here? Or are there any other drivers i can use for my R9 290? 

Thanks in advance :)!

---

### Post by mastablasta on 2014-02-03
you may need to upgrade kernel to latest available and then also find newer drivers. i think catalyst 14 is out. i think it's beta:

[http://news.softpedia.com/news/AMD-Catalyst-14-1-Beta-for-Linux-Arrives-with-a-Bang-and-With-Linux-3-13-Support-423025.shtml](http://news.softpedia.com/news/AMD-Catalyst-14-1-Beta-for-Linux-Arrives-with-a-Bang-and-With-Linux-3-13-Support-423025.shtml)

option 2: is to wait until about April when stuff will likely come into upcoming Ubuntu 14.04 LTS (which is now alpha stage of development).

you can also try Alpha 14.04. i hear it is relatively stable already.

also how to install drivers in GUI: [http://askubuntu.com/questions/47506/how-do-i-install-extra-drivers](http://askubuntu.com/questions/47506/how-do-i-install-extra-drivers)

but this works if curent stable drivers support your chip.

---

### Post by Yellow Pasque on 2014-02-03
You do not say what version of Ubuntu you are using.
>  I get a .run file, which i executed from the terminal with sudo sh <filename>.run
This is not a good way to install Catalyst. Always build packages when possible.
> At the end of the installation progress it says that i had recieved an error during the installation. I checked the .log file and it said that it was unable to compile the kernel or something.
The exact error message would be more helpful..

Assuming you're using Ubuntu 13.10, here's a rough guide:
```
sudo apt-get install cdbs dh-make dkms execstack dh-modaliases linux-headers-generic libqtgui4
cd ~/
mkdir catalyst-14.1beta1.3 && cd catalyst-14.1beta1.3
wget --referer='http://support.amd.com/en-us/download/desktop?os=Linux+x86' http://www2.ati.com/drivers/beta/amd-catalyst-14.1-betav1.3-linux-x86.x86_64.zip
unzip amd-catalyst-14.1-betav1.3-linux-x86.x86_64.zip
chmod +x amd-driver-installer-13.35.1005-x86.x86_64.run
sudo ./amd-driver-installer-13.35.1005-x86.x86_64.run --buildpkg Ubuntu/saucy
sudo dpkg -i fglrx*.deb
sudo amdconfig --initial -f
```

---

