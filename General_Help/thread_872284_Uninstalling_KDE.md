---
title: "Uninstalling KDE"
date: 2008-07-27
forum: General Help
---

### Post by dstein on 2008-07-27
So I tried installing KDE the other day by typing ```
sudo aptitude install kubuntu-desktop
``` It turns out that "sudo aptitude remove kubuntu-desktop" does not remove everything that was installed. Actually it only removed a few hundred kilobytes. I am not sure why it did not remove everything that was installed in the kubuntu-desktop package. Can anyone explain the reason for this and a possible solution?

Also, on a somewhat similar note, is there any way to see where a pacakge will be installed to and what files will be installed? In the past, I have used Synaptic for the installation location, looking at the 'Installed Files' tab of the Properties menu. However, this only works for installed packages, and the directory that they will be installed to (not the files that will be installed).

Thanks.

---

### Post by tuxxy on 2008-07-27
Adding a * to the command should remove all dependant files; wise choice in uninstalling ;)

```
sudo aptitude install kubuntu-desktop*
```

---

### Post by dstein on 2008-07-28
This did not work when I tried replacing 'install' with 'remove'. Was 'install' a typo, or is that what is required. If not, what am I doing wrong. I thought the * would be used in cases like this to expand into all strings that begin with 'kubuntu-desktop'. Thanks.

---

### Post by aysiu on 2008-07-28
I don't know why it didn't work, but you can try [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) or [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce) to remove KDE.

---

### Post by dstein on 2008-07-29
Ah, is there any way that it didn't work because I have already tried removing it normally?

---

