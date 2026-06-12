---
title: "nvidia-prime: can't switch from intel card to nvidia card"
date: 2014-05-02
forum: Hardware
---

### Post by renato3 on 2014-05-02
Hey guys, Hi, I'm using Ubuntu 14.04 on a Dell Inspiron 14R 5421. I have two cards, integrated Intel and dedicated Nvidia GT 730M. I installed the proprietay nvidia 331.38 by going on *Settings --> Softwares & update --> Additional Drivers*. After rebook, everything was fine and working, glxgears showed high FPS. Using nvidia-settings I was able to switch from Nvidia card to Intel card, [here is a screen]("http://dl.dropboxusercontent.com/u/1113424/img/nvidia-prime-profiles.jpg"). But now I can't go back to Nvidia card. nvidia-settings doesn't show me the options to switch cards anymore:


[IMG]http://s9.postimg.org/5m2ilzwdr/Screenshot_from_2014_05_02_00_19_28.png[/IMG]



I can't switch using terminal too:

 
```
$ sudo prime-select nvidia
Error: alternatives are not set up properly
Error: nvidia mode can't be enabled

```

Is someone experiencing this problem too? How do I solve it? :(

---

### Post by renato3 on 2014-05-02
[Bug #1310023]("https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1310023")

---

### Post by renato3 on 2014-05-02
[COLOR=#333333][FONT=Ubuntu Mono]At least for now, a workaround for me was to use bumblebee + primus following this guide:[/FONT][/COLOR]
[http://www.muktware.com/2013/12/install-nvidia-331-bumblebee-optimus-cards/18271](http://www.muktware.com/2013/12/install-nvidia-331-bumblebee-optimus-cards/18271)

---

### Post by renato3 on 2014-05-03
up!

---

