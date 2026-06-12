---
title: "Nvidia + Intel GPU Ubuntu crash when selecting Intel GPU"
date: 2017-10-19
forum: Hardware
---

### Post by nasher2 on 2017-10-19
Hi all!

I've got and ASUS ROG laptop with the annoying Nvidia optimus. All of the distributions I've recently tried fail to boot into the desktop environment when I've switched over to using the Intel GPU instead of the Nvidia GPU. 
To get my DE back, I have to go into recovery mode and select my Nvidia GPU again. Because I've tried various distributions with no luck, I'm starting to think if it's an issue Linux wide other than a distribution.

When I switch over to my Intel GPU and I reboot my computer, I get a black screen then the fans run at full speed. I have to hard reset my laptop and go into recovery.

Is there a way I can switch between the Nvidia and the Intel GPU without these issues? I don't have an option within the BIOS to switch between GPUs.

I really would love somebody to help me. I'm currently dual booting with Windows 10 and I don't particular like it

Thanks

---

### Post by Bashing-om on 2017-10-19
nasher2; Hello;

What is the hardware ?
```

lspci -k | grep -EA2 'VGA|3D'
sudo lshw -C display

```

what nvidia driver(s) are installed ?
```

dpkg -l | grep nvidia*

```

What controls the graphic's sets ?
```

cat /var/log/gpu-manager.log
cat /etc/X11/xorg.conf 

```

these results posted back to us Between Code Tags. please .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We see what tale gets told and 
see what can be done.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by efflandt on 2017-10-21
I don't believe you should have any /etc/xorg.conf if you have dual hybrid graphics, since anything in that specific to Nvidia would not work with Intel graphics. My gaming laptop no longer turns on properly, but when it was working, when switching **Nvidia to Intel** using **NVIDIA X Server Settings**, I simply had to log out of X and log back in. If I switched **Intel to Nvidia**, I had to reboot.

---

