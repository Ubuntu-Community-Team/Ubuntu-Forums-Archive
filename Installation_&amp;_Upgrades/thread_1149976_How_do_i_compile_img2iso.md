---
title: "How do i compile img2iso"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by Awareness on 2009-05-05
how do i compile this?

i downloaded it but it doesn't seem to have any instructions :S

[http://www.t2-project.org/packages/img2iso.html](http://www.t2-project.org/packages/img2iso.html)

---

### Post by logos34 on 2009-05-05
extract isodump-0.06.00.tar.gz

then cd into folder isodump-0.06.00 and look for INSTALL text doc.

here:

> First run a
  ./configure
then a
  make
for compilation of or/and a
  make install
for compilation and installation (the last requires beeing root) of the binary
and the manual page. Edit the Makefile entries (for instance INSTALLDIR_???)
if neccessary.

you can also substitute 'sudo [checkinstall]("http://www.google.com/url?sa=t&source=web&ct=res&cd=4&url=https%3A%2F%2Fwiki.ubuntu.com%2FCheckInstall&ei=97EAStvVFZLQMqWilOoH&usg=AFQjCNHrpWsLR2OVzfkOTzK0Q2D8p6fI_w")' for the last step (makes a .deb out of it)

---

### Post by OliW on 2009-05-05
[LIST=1]
[*]Download
[*]Extract
[*]cd isodump-0.06.00
[*]./configure
[*][meet any missing dependencies and ./configure, rinse, repeat]
[*]make
[*]./isodump -h
[/LIST]

---

### Post by logos34 on 2009-05-05
on second thought, maybe an easier way would be to use [ccd2iso]("http://ubuntuforums.org/showpost.php?p=4078080&postcount=9")

> $ sudo apt-get install ccd2iso
$ ccd2iso file.img file.iso

done.

---

### Post by Awareness on 2009-05-06
> **logos34 said:**
> on second thought, maybe an easier way would be to use [ccd2iso]("http://ubuntuforums.org/showpost.php?p=4078080&postcount=9")



done.

Now i saw the INSTALL file... i read the README and saw no instructions and in the webpage said anything either...

Anyhow, i like ur answer the best logos34... thanks  ;)

---

### Post by Rodnox on 2009-08-10
Why in the world would somebody want to convert a *.img Image into an *.iso Image? Most of the Netbook's don't have a CD Drive and therefore the best option it is to create a bootable USB Stick Version and the best way to do that is by using an *.img Image. Thats why it naturally comes as such. 

Best way to make an USB Stick Image from a *.img file is:

download "linux-image-writer" from
    [http://www.jolicloud.com/downloads/linux-image-writer.py](http://www.jolicloud.com/downloads/linux-image-writer.py)

Open a Terminal and go to the directory where you downloaded the file:
           cd /the/path/to/your/directory

Change the script permissions:
              chmod a+x linux-image-writer.py

Run the Program to write ur *.img Image to USB
              sudo ./linux-image-writer.py *.img

I'd also recommend to format the USB Stick before turning it into a boot device.

---

### Post by Awareness on 2009-08-12
> **Rodnox said:**
> Why in the world would somebody want to convert a *.img Image into an *.iso Image? Most of the Netbook's don't have a CD Drive and therefore the best option it is to create a bootable USB Stick Version and the best way to do that is by using an *.img Image. Thats why it naturally comes as such. 

Best way to make an USB Stick Image from a *.img file is:

download "linux-image-writer" from
    [http://www.jolicloud.com/downloads/linux-image-writer.py](http://www.jolicloud.com/downloads/linux-image-writer.py)

Open a Terminal and go to the directory where you downloaded the file:
           cd /the/path/to/your/directory

Change the script permissions:
              chmod a+x linux-image-writer.py

Run the Program to write ur *.img Image to USB
              sudo ./linux-image-writer.py *.img

I'd also recommend to format the USB Stick before turning it into a boot device.

I dont remember why did i want to do this, but i think it was coz unetbooting only accepted .iso :S

Anyway, i dont like to use random scripts from random webs :S (thanks for the help anyway)

if its that much the natural way to burn it into usb, could you suggest something that we can find in the repositories?

---

