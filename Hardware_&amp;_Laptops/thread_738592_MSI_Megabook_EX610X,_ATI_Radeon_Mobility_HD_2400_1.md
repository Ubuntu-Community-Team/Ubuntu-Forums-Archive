---
title: "MSI Megabook EX610X, ATI Radeon Mobility HD 2400 100% WORKING SOLUTION !!!"
date: 2008-03-28
forum: Hardware &amp; Laptops
---

### Post by dootzky on 2008-03-28
hi people! :)

after 5 days of agony, 13 different attempts of installing my ATI card, I've got it working. 
Then I formatted the whole Ubuntu partition, and tried out everything again, step by step, just to make sure it's working from fresh install. 

And now I present you guys with solution, hopefully it will help someone with installing ATI drivers.
* NOTE * - This is instalation for 64bit kernel, since I have 64bit laptop, it should be pretty much the same for 32bit. 

=================== SOLUTION =====================

This is just a short version of: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.3_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.3_Driver_Manually)

0. Download this file: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-3-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-3-x86.x86_64.run)
and save it to desktop. Now open the terminal, and change the working directory to your Desktop: "cd Desktop". Now follow the steps below...

1. fresh install Ubuntu Gutsy Gibbon (64 bit version!!)
2. enable all repos in synaptic (is enabled by default, but double-check it)
3. 
sudo apt-get update
sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms

4. If using 64bit make sure to collect package "ia32-libs" (??? and " libGL.so.1" before proceeding!)
5. sudo sh ati-driver-installer-8-3-x86.x86_64.run --buildpkg Ubuntu/gutsy
6. sudo gedit /etc/default/linux-restricted-modules-common
Add "fglrx" to the line "DISABLED_MODULES" (DISABLED_MODULES="fglrx")

7. gksu gedit /etc/modprobe.d/blacklist-restricted
Put a # in front of the line "blacklist fglrx", if it is present. Otherwise, the kernel module will not load automatically, and you will not get 3D acceleration. 

8. sudo rm /usr/src/fglrx-kernel*.deb
9. sudo dpkg -i xorg-driver-fglrx_8.471-0*.deb fglrx-kernel-source_8.471-0*.deb fglrx-amdcccle_8.471-0*.deb
- it will break, and throw some error, but that's ok, because we have 64bit CPU. moving on..

10. (ignore any errors in steps bellow..)
sudo apt-get install -f
sudo dpkg -i --force-overwrite xorg-driver-fglrx_8.471-0*.deb fglrx-kernel-source_8.471-0*.deb fglrx-amdcccle_8.471-0*.deb

11. reboot
12.
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

13. reboot! the END! :)

* (check if ATI is loaded with "fglrxinfo" command in terminal)  
* if all is OK, you should install compiz advanced effects:
sudo aptitude install compizconfig-settings-manager





========================================
you have libGL error ?? try this:


    * fglrxinfo gives: libGL.so.1: cannot open shared object file.
    * Check the permission of the libGL.so.1.2 file with command: 

 ls -l /usr/lib/libGL*

    * The file permission of libGL.so.1.2 should be "-rw-rw-r--". If the permission reads "-rw-rw----", do command 

 sudo chmod o+r /usr/lib/libGL.so.1.2

    * If the permission is correct, fixed with command: 

sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

=========================================

And that's it! :guitar:
Once more, for easier search on the forum, I'll write the specs for my laptop with the card name:

MSI Megabook EX610X, ATI Radeon Mobility HD 2400 

Cheers people, 
spread the Ubuntu love! :)
dootzky
Serbian Ubuntu LoCo Administrator

---

### Post by sripplinger on 2008-04-10
I've got an ATI Mobility Radeon HD2600.  This procedure seems to have worked for me as well.  Of course, it took me several tries to pull it off, but this last one seems to have done the trick.  Thanks.

---

### Post by jameskeagie on 2008-04-14
What ended up working for me is the following step by step instructions. If other things haven't worked for you you might try it - its pretty simple to try.

[http://ubuntuforums.org/showthread.php?t=754712](http://ubuntuforums.org/showthread.php?t=754712)

---

### Post by hoiquai on 2008-05-21
I've followed the instructions step by step and still get graphic corruption/reboot or blankscreen and freezing at the logon screen. Can anyone suggest something else, also tried envy.

Any assistance is appreciated as I can't afford the obvious solution of purchasing an nvidia card.:(

---

