---
title: "Logitech webcam won't work on Virtual Box windows xp"
date: 2012-04-03
forum: Hardware
---

### Post by Lilllli on 2012-04-03
Hey I'm don't really know anything about computers, but am trying to get a webcam to work through Virtual Box which has a completley updated version of windows xp on it.  The software does not recognize the webcam no matter what I did; I tried to add the filters.  Does anybody know any other reasons why this is not working?

---

### Post by papibe on 2012-04-03
Hi Lilllli. Welcome to the forums!

How did you install VirtualBox? AFAIK, the version on the Software Center does not have support for USB. You would have to get the package (.deb) from VirtualBox's  website. Then, if I remember correctly, you have to install some 'extensions' to your guest.

Hope that helps.
Regards.

---

### Post by jayshomebrew on 2012-04-03
uninstall vbox from ubuntu software center, then run the following commands from a terminal:

```
sudo add-apt-repository ppa:debfx/virtualbox
sudo apt-get update
sudo apt-get install virtualbox
```

then download and install the extension pack here:
[https://www.virtualbox.org/wiki/Downloads]("https://www.virtualbox.org/wiki/Downloads")

add the extension pack: (ignore the version shown)
[IMG]http://img.creativemark.co.uk/uploads/images/638/12638/largeImg.png[/IMG]

then you can get usb2.0 devices to work nicely:
[IMG]http://linux.philosweb.com/drupal/system/files/SNAGHTML1c528dd.png[/IMG]

then finally add the device to your VM:
[IMG]http://mightyohm.com/blog/wp-content/uploads/2010/09/captured_but_not_responding-499x444.png[/IMG]

---

