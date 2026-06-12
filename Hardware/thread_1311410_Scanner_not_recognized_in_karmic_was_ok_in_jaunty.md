---
title: "Scanner not recognized in karmic was ok in jaunty"
date: 2009-11-02
forum: Hardware
---

### Post by Axx83 on 2009-11-02
**_SOLVED: go to first reply - only works with epson2 scanner, go see this list: [http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html) and check your scanner._**

My epson dx7400 scanner was correctly recognized and run by xsane in jaunty. I just had to add its usb line (taken from lsusb) in /etc/sane.d/epson.conf file and it correctly used the sane backend.

Now in karmic the scanner is seen by sane-find-scanner but not run by xsane. It keeps on using the webcam but no matter what I can't make it to run the scanner. Running xsane with sudo does not change the behavior.

I also followed this:
[http://ubuntuforums.org/showpost.php?p=8197213&postcount=2]("http://ubuntuforums.org/showpost.php?p=8197213&postcount=2")
but its doesn't work anyway.

What should I do ?

---

### Post by Axx83 on 2009-11-02
I solved it:

run
```
sane-find-scanner
```
and write down the usb number of your scanner

now run
```
sudo gedit /etc/sane.d/epson2.conf
```
and paste that number under the usb example already given.

---

