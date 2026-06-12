---
title: "Asus M50Sa Light Sensor after Hibernate"
date: 2010-01-23
forum: Hardware
---

### Post by Nai on 2010-01-23
Hello, everybody. I figured out how to fix the light sensor on my Asus M50Sa so the screen is not painfully dark using a modified version of the advice given by hotweiss [in this post]("http://ubuntuforums.org/showpost.php?p=6531787&postcount=9"). I had to modify it in order to get it to work in Karmic, since hotweiss wrote that post a year ago. Here is the modified version:

> **A)** Open Terminal (Menu->Accessories), and type the following:
```
sudo nano brightness 
```

**B)** Now paste the following in the Terminal window:
```
#!/bin/sh
echo 1 > /sys/devices/platform/asus_laptop/ls_switch
echo 15 > /sys/devices/platform/asus_laptop/ls_level
```

**C)** Hit Ctrl-O to save and then Ctrl-X to exit.

**D)** Now we will copy our new shell script to the appropriate directory, make it executable and add the following links by typing the following in Terminal:
```
sudo mv brightness /etc/init.d 
```

and then
```
sudo chmod 755 /etc/init.d/brightness 
```

and then
```
sudo update-rc.d brightness defaults 90 
```

**E)** Reboot, and you will have regained control of your brightness level.

That code, however, only causes the light sensor to shut off when the computer is booting from off. When I wake up my computer from hibernation, it doesn't follow the script, which means that the screen is horridly dark again and in order to fix it I have to go enter a code in order to fix it for the current session:
```
sudo su
echo 1 > /sys/devices/platform/asus_laptop/ls_switch
echo 15 > /sys/devices/platform/asus_laptop/ls_level
```

Is there some way to make it so that the computer will do this automatically upon return from hibernation, just like it does when first booting up?

---

### Post by liedan on 2010-01-24
Hi Nai,

thanks a lot, works great. But you have a mistake in your post. If you want to turn the light sensor off, it should be:

echo 0 > /sys/devices/platform/asus_laptop/ls_switch
instead of 
echo 1 > /sys/devices/platform/asus_laptop/ls_switch 
Cheers.

---

### Post by Nai on 2010-01-24
Well, first of all, I would just like to say thanks for replying and proofreading my code. I appreciate it.

Second, the original version posted by hotweiss had that. I couldn't get it to work, however, and I found [another method]("http://www.linlap.com/wiki/asus+m50sa") of fixing the brightness which are the two lines that I substituted. I knew that they worked because when I entered them it would be immediately fixed, though only until the next time I would boot up. Therefore I put that code into the boot-up file and it now works for me. Did what you said work for you?

---

