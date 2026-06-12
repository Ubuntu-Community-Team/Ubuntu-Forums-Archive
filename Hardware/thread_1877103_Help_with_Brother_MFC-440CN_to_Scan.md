---
title: "Help with Brother MFC-440CN to Scan"
date: 2011-11-07
forum: Hardware
---

### Post by barrmulio on 2011-11-07
[this is a repeat of a prior thread prior to oneiric getting full release]

Ok - I simply cannot get my Brother MFC440CN to scan on oneiric x64 setup as a network printer. I really need gscan2pdf to work, but gimp and xscan cannot see the printer either.

The weird thing is it works fine on live boot of x64, and in virtualbox using x32 (I dont have virtualization to test x64). 
I did a full reinstall this weekend since the live boot worked, but unfortunately it's not working after install and updates. 

So I'm looking for any tips from folks who have gotten their network Brother printer to install correctly for scanning

Printing works mostly fine (I get 'low marker' notifications, but it prints out within a second or so). In the end I opted for brother-xxx-bh7 ones from synaptic. 

I've tried the x32 and x64 scanner drivers from Brother's site, which worked just fine in natty, but no dice on oneiric

console output
```
barrmy@oneiric:~$ dpkg  -l  |  grep  Brother
ii  brother-cups-wrapper-common              1.0.0-10-0ubuntu5                       Common files for Brother cups wrapper packages
ii  brscan-skey                              0.2.1-3                                 Brother Linux scanner S-KEY tool
ii  brscan2                                  0.2.5-1                                 Brother Scanner Driver

barrmy@oneiric:~$ brsaneconfig2  -q  |  grep  SCANNER
  0 SCANNER             "MFC-440CN"         I:192.168.1.90
```

console output of 'sudo gscan2pdf'
```
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/lib/perl5/Gtk2.pm line 138.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/lib/perl5/Gtk2.pm line 138.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/lib/perl5/Gtk2.pm line 138.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/lib/perl5/Gtk2.pm line 138.
Name "PDF::API2::Version::CVersion" used only once: possible typo at /usr/bin/gscan2pdf line 433.
Use of uninitialized value $PDF::API2::Version::CVersion{"vShort"} in concatenation (.) or string at /usr/bin/gscan2pdf line 433.
```

console output of 'sudo gscan2pdf --debug'
```
Running sane_get_devices
INFO - Sane->get_devices returned: $VAR1 = [];
```

---

### Post by barrmulio on 2011-11-07
ok - one of the items below fixed my issue, but i'm not sure which

credit on the below to rafaellaguna from [this post]("http://ubuntuforums.org/showpost.php?p=11358127&postcount=4")

edit /lib/udev/rules.d/40-libsane.rules and add this as the last scanner (after HP ones, f.ex.)
```
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

``` then run
```
sudo cp /usr/lib64/libbrscandec2.so.1.0.0 /usr/lib64/libbrcolm2.so.1.0.1 /usr/lib64/libbrcolm2.so /usr/lib64/libbrscandec2.so.1 /usr/lib64/libbrscandec2.so /usr/lib64/libbrcolm2.so.1 /usr/lib

sudo cp /usr/lib64/sane/libsane-brother2.so.1.0.7 /usr/lib64/sane/libsane-brother2.so.1 /usr/lib64/sane/libsane-brother2.so /usr/lib/sane

sudo echo 'SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"' >> /lib/udev/rules.d/50-udev-default.rules

```

i had run the third command in a sudo xterm since it kept giving me permission failures

additionally, i added by user to group scanner
```
sudo usermod -a -G scanner YOURUSERNAME
```

---

### Post by jasonxh on 2011-11-10
Thanks for the post! And to the original poster too.

For network scanners, it's the lib64 location. One just needs to move all files installed by brscan*.deb under /usr/lib64 to /usr/lib. A cleaner way could be to repack the deb. In case anyone needs brscan4 (e.g. my HL-2280DW), I've attached my repacked deb.

The other modifications are only needed for USB scanners.

---

### Post by han_u_man on 2011-12-05
Thanks. moving the files fom lib64 to lib makes brother mfc-6890cdw work.
(copying the commands above didn't work, used sudo nautilus)

---

### Post by kurt18947 on 2011-12-05
I had to do both things to get my MFC-6490CW to print via USB & scan.  Brother is aware of the problem; both solutions are mentioned on their FAQ pages.

---

