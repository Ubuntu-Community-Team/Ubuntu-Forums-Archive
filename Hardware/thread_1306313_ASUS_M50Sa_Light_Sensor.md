---
title: "ASUS M50Sa Light Sensor"
date: 2009-10-30
forum: Hardware
---

### Post by Nai on 2009-10-30
Hello all.

I am using an ASUS M50Sa laptop which I've seen (and experienced) always has problems with the light sensor making the brightness very dark and uncontrollable. When I was using Jaunty I was able to fix it using (if I remember correctly) the advice given by hotweiss [in this post]("http://ubuntuforums.org/showpost.php?p=6531787&postcount=9").

After updating to Karmic I suddenly lost control again. I tried to go through his commands again but the final command yields:

update-rc.d: warning: /etc/init.d/brightness missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/brightness already exist.

I'm not exactly sure what that means, so any help getting the stupid light sensor to stop messing up the brightness would be greatly appreciated.

Also, any time I hibernate or suspend, when I try to turn the computer back on it shows that it's booting up and everything looks fine, and then the screen goes black except for the mouse pointer, which I am able to move, and nothing else happens. The only way I've figured out how to get out of this is just to manually turn it off with the power button and reboot. Is there a way to fix this? I'd really like to be able to hibernate and suspend.

---

### Post by Nai on 2009-11-02
Well, I've found a way to fix it for the current session.

```
sudo su
echo 1 > /sys/devices/platform/asus_laptop/ls_switch
echo 15 > /sys/devices/platform/asus_laptop/ls_level
```

It is important to note that the location is "asus_laptop" rather than "asus-laptop" as I believe it was in previous versions of Ubuntu (that was the code that I found online, and I had to modify it).

Also, the only reason I put the "sudo su" in there is because when I tried to just do "sudo" before the command, it claimed that I did not have permission.

This fix, however, only works for the current session. Is there a way to make it automatically do it when you first boot up? Or is there perhaps a different way to do it which will be permanent?

I also still have the problem with suspend/hibernation.

Thanks!

EDIT: After making this post, I realized that in the first set of commands which I linked to, it had "asus-laptop" instead of "asus_laptop". I went through his steps again changing that one character in the code, but the last command yielded the same results as before:

update-rc.d: warning: /etc/init.d/brightness missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/brightness already exist.

---

### Post by Nai on 2009-11-04
Okay, well I'm really not sure what happened. I didn't try anything new, but after restarting one or two times (I don't remember how many times since I'm dual booting windows and had booted into that) it's suddenly working now.

Anyway, help with hibernation/suspend would still be greatly appreciated.

Thanks!

---

### Post by Darkdelusions on 2009-11-28
Nai,

Thanks for figuring out the light sensor thing it was annoying me... I have didn't even realize it change from asus-laptop to asus_laptop... 

The sad thing is i was typing in manually in the command line as asus_laptop :)

I will play with suspend and Hibernate later today and see what I can figure out.

---

