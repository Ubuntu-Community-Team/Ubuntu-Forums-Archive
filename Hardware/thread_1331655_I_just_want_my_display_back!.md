---
title: "I just want my display back!"
date: 2009-11-19
forum: Hardware
---

### Post by mdcollier on 2009-11-19
I upgraded to 9.10 through the automated upgrade process. It went well, and I was feeling frisky, so I selected the Nvidia propriety driver. Now I can't get a GUI interface. DOH!

I've wrestled with the Nvidia proprietary drivers long enough. Uncle! I want the Dummy's Guide to deselecting the driver so I can get my gui interface back.

Please write your response to the 5th grade reading level. I'm trying to love Ubuntu, and this is an obstacle.

Thank you in advance for not flaming me for being a newb.

---

### Post by Yellow Pasque on 2009-11-19
Boot into recovery mode: [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
Select 'xfix'

Also, to purge the nvidia drivers: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-nvidia%20and%20reinstall%20-nv%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-nvidia%20and%20reinstall%20-nv%20from%20scratch)

---

### Post by mdcollier on 2009-11-19
Thanks for your help.

I tried (repeatedly) that but got dumped into the command line prompt. Didn't see xfix???

---

### Post by Yellow Pasque on 2009-11-19
Ok, then:
```
sudo nvidia-settings --uninstall
sudo dpkg-reconfigure xorg-xserver
```

---

### Post by mdcollier on 2009-11-19
You are so close to being a living legend. Just Google "nvidia blank screen" if you don't believe me.

--uninstall is not a valid option.

Thank you so much for helping. I don't want to reinstall. I've got everything set up just right.

---

### Post by Yellow Pasque on 2009-11-19
> You are so close to being a living legend. Just Google "nvidia blank screen" if you don't believe me.
Please explain/elaborate.

```
sudo dpkg -P nvidia*
sudo dpkg-reconfigure xorg-xserver
```

---

### Post by mdcollier on 2009-11-19
It's saying that nvidia* is not installed, tried it with nvidia, same response.

There are legions of folks having this exact problem.

---

### Post by wojox on 2009-11-19
I reset xorg.conf with this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

You can search for nvidia with:

```
dpkg -l | grep nvidia
```

---

### Post by mdcollier on 2009-11-19
Still no joy.

---

### Post by mdcollier on 2009-11-20
I found it. A well kept secret. I used the core version to uninstall the nvidia drivers since the notebook is an old dog and won't benefit from enhanced graphics.

[http://linuxers.org/howto/how-install-nvidiaati-graphic-cards-drivers-ubuntu-using-envy-ng](http://linuxers.org/howto/how-install-nvidiaati-graphic-cards-drivers-ubuntu-using-envy-ng)

---

