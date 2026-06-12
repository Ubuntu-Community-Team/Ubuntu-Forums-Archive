---
title: "artec scanner problem"
date: 2005-03-01
forum: Hardware &amp; Laptops
---

### Post by molvistan on 2005-03-01
i have an artec e+48U scanner. when i start Xsane it says its searching for devices then i get an error message saying: "failed to open device 'artec_eplus48u:libusb:003:004': invalid argument"

my scanner is swtiched on and connected, but i still get this message.

any idea how to sort it


thanks

---

### Post by m4ng0 on 2005-03-01
Have you tried to unplug/replug the usb cable?  If you do so, hotplug can give your scanner the
correct permissions.

---

### Post by Second_Player on 2006-04-01
i have the same scanner and had the same problem, it be nice to be able to scan, i just gave up

---

### Post by hadrian on 2006-07-04
Same problem with artec e+ pro scanner

---

### Post by claydoh on 2006-07-04
You will need a firmware file, which according to [this manpage ]("http://www.sane-project.org/man/sane-artec_eplus48u.5.html") is called either 
Artec48.usb or 1200.usb. It can be found on your scanner's cd or if it has been installed on a windows machine, in C:\windows\system32\drivers. Put that file in your home directory, copy the file to /usr/share/sane/artec_eplus48u/:

In a terminal window:
```
sudo mkdir /usr/share/sane/artec_eplus48u
sudo cp /home/<your-username>/Artec48.usb /usr/share/sane/artec_eplus48u/
```

many scanner types need this sort of action.
you can search for scanner support [here]("http://www.sane-project.org/cgi-bin/driver.pl") and there are links to man pages with more information from there.

---

### Post by aliasfoxkde on 2008-07-14
> **claydoh said:**
> You will need a firmware file, which according to [this manpage ]("http://www.sane-project.org/man/sane-artec_eplus48u.5.html") is called either 
Artec48.usb or 1200.usb. It can be found on your scanner's cd or if it has been installed on a windows machine, in C:\windows\system32\drivers. Put that file in your home directory, copy the file to /usr/share/sane/artec_eplus48u/:

In a terminal window:
```
sudo mkdir /usr/share/sane/artec_eplus48u
sudo cp /home/<your-username>/Artec48.usb /usr/share/sane/artec_eplus48u/
```

many scanner types need this sort of action.
you can search for scanner support [here]("http://www.sane-project.org/cgi-bin/driver.pl") and there are links to man pages with more information from there.
Thanks man, I owe you!

In combination with the following thread, that fixed the issue.
[http://ubuntuforums.org/showthread.php?t=632233](http://ubuntuforums.org/showthread.php?t=632233)

aliasfoxkde

---

