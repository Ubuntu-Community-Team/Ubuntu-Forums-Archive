---
title: "can't adjust brightness in lenovo laptop"
date: 2012-05-01
forum: Hardware
---

### Post by carlomagn0 on 2012-05-01
[SIZE=3]Hi,
I need help with this:

laptop: lenovo v470/v570
ubuntu:  ubuntu 10.04 LTS - la versión Lucid Lynx

problem: I can not adjust the brightness of the laptop, it is too high now.

I tried: the energy manager, but it does not appear the control.

Please help me with this.

Thanks.


[/SIZE]

---

### Post by aaron.kyle on 2012-05-01
I&#8217;ve encountered this same issue on a Lenovo w510.  Others have as well:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/538256](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/538256)

Here&#8217;s a fix I used, from [http://ubuntuguide.net/change-screen-brightness-with-fn-key-in-ubuntu-11-0410-10](http://ubuntuguide.net/change-screen-brightness-with-fn-key-in-ubuntu-11-0410-10), originally from  Guskuma who posted it on [http://ubuntuforums.org/showthread.php?t=1751333&page=2](http://ubuntuforums.org/showthread.php?t=1751333&page=2)


First edit xorg.conf in terminal with the command:

```
sudo gedit /etc/X11/xorg.conf
```

And then find the Section &#8220;Device&#8221; and add the following:

```

Section &#8220;Device&#8221;
Identifier &#8220;Default Device&#8221;
Option &#8220;NoLogo&#8221; &#8220;True&#8221;
Option &#8220;RegistryDwords&#8221; &#8220;EnableBrightnessControl=1&#8243;
EndSection

```

---

### Post by flick on 2012-05-07
[http://askubuntu.com/questions/84877/lenovo-ideapad-linux-compatibility/133488#133488](http://askubuntu.com/questions/84877/lenovo-ideapad-linux-compatibility/133488#133488)

May be helpful.

---

