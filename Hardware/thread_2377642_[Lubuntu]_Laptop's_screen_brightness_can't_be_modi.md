---
title: "[Lubuntu] Laptop's screen brightness can't be modified"
date: 2017-11-15
forum: Hardware
---

### Post by chexmo on 2017-11-15
Hello World.
I know it's a very common issue but i started a new thread because i've tried many ways to resolve the problem without good news.
I'm trying to make an Exo x352 (a netbook with low resources, intel cpu and gpu, 1gbram, 2,2Ghz) be able to do simple things like practice writting code (i'm a newbie lol).
The point is: 
When i install Lubuntu LTS in a clean way (format, then install from the Lubuntu 16.04LTS live ISO using a flash drive created with rufus) it all works very well, including brightness behaviour. Later, an update prompt appears and i accept it. When update finishes, the screen brightness can't be modified anymore. It seems like backlight intensity variables get locked to default values and i can't change them anymore. 
(It took me several clean installations to realise that brightness behaviour stop working well after that update)
As the LXDE battery widget have a bar to change brightness, that is the first i tried (that way is how it worked well before updates). 
Then, I've alredy tried with terminal commands and nothing. (internet)
Tried to modify grub parameters, nothing. (there is a tutorial on internet that solves this issue from grub)
Tried Xcaliber, nothing.
I don't know what to do.

I'm sorry about my english, it's not my native lenguage (it's spanish)
Thank you.

---

### Post by TheFu on 2017-11-15
Try:
```

$ sudo sh -c "/bin/echo 80 > /sys/class/backlight/intel_backlight/brightness"
```

That is working here.  I use 80 - 300 for the brightness control.  If you aren't using an on-board Intel GPU, it might be a different file. IDK.

---

### Post by uragno on 2017-11-16
You say Intel GPU (iGPU).

In addition to what has already been said in the previous post you could also try the **.conf file solution* like this one:[B] [https://askubuntu.com/a/499294](https://askubuntu.com/a/499294).
[/B]
No matter what *buntu flavor you have. That worked for me on a different laptop on: *buntu, openSUSE and Fedora. ;)

---

### Post by TheFu on 2017-11-18
Messing with an xorg file isn't fun. Often it doesn't exist as HW is discovered automatically. Plus, being forced to kill X/Windows just to modify the brightness seems a little harsh.  Whatever works is what you need.

The /sys/..... modification happens immediately.  You could search your system for any file named "brightness" under /sys/ .... that would likely be the file to be modified.  I suspect whatever GUI was working before just modified the correct "brightness" file for the GPU being used.  If those file locations changed, then the project team would appreciate a bug report, I'm certain.

---

