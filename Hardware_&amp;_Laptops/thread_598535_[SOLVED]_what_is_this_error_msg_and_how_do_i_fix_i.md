---
title: "[SOLVED] what is this error msg and how do i fix it"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by mrukus on 2007-10-31
im trying to activate my wireless according ot this thread



[http://ubuntuforums.org/showthread.php?t=224350](http://ubuntuforums.org/showthread.php?t=224350)



whenever i go to enter the echo command this is what i get.


```
mrukus@mrukus-laptop:~$ sudo echo "enabled: 1">/proc/acpi/acer/wireless
echo: write error: Invalid argument
```

and

```
mrukus@mrukus-laptop:~$ echo "enabled: 1">/proc/acpi/acer/wireless
bash: echo: write error: Invalid argument
enabled: 1
```

---

### Post by digitalbenji on 2007-10-31
I'm not sure... I wouldn't go trying to modify the /proc system like that, it just doesn't seem kosher to me.

---

### Post by mrukus on 2007-10-31
i am throwing caution to the wind. it might be a bad philosphy but whenever i work on anything, like resoring cars that are dead, my philosophy is if it doesn't work now, you can't break it.  i can always just reformat and start from scratch.  my ocmputer is pretty much useless to me if i can't get the interal wireless to work. i might as well use that other os..........

---

### Post by smurphy_it on 2007-10-31
mrukus@mrukus-laptop:~$ sudo echo "enabled: 1">/proc/acpi/acer/wireless

Try adding a space between 1" and > and after > so the line would be
sudo echo "enabled: 1" > /proc/acpi/acer/wireless

as it looks like a text filter you are performing.

---

### Post by mrukus on 2007-10-31
allright i get the same exact error msg.
```

mrukus@mrukus-laptop:~$ sudo echo "enabled: 1" > /proc/acpi/acer/wireless
[sudo] password for mrukus:
echo: write error: Invalid argument
```

so i decided to try and edit the file myself with a text editot and it says to make sure i have disk space and permissions to write to that.....idk what to do i thought that by doing it in the terminal under the sudo command it would give me permission

---

### Post by mrukus on 2007-10-31
been goofing around with this all day. any help would be greatly appreciated

---

### Post by mrukus on 2007-11-01
just spent some time in the irc chats, and figured out i can't wirte to the file like that in kubuntu gutsy. anybody have another way to write that file or do what that file is doing?

---

### Post by tayran on 2008-01-05
Hi. I try to apply same solution in [http://ubuntuforums.org/showthread.php?t=224350](http://ubuntuforums.org/showthread.php?t=224350)
and i have the same error as told here.
    I have installed ndiswrapper 1.51 first from source and then the 64 bit 80211g driver of my xp
I have had to blacklist bcm43xx drivers and the result:

root@ugur-dizustu:/# ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)

As told in ndiswrapper web site this it should not say (alternate driver: bcm43xx).
Anyway then I have installed acer-acpi from [http://acer-acpi-deb.googlecode.com/files/acer-acpi_0.9.1%2B2.6.22-14.46-mumbly5_amd64.deb](http://acer-acpi-deb.googlecode.com/files/acer-acpi_0.9.1%2B2.6.22-14.46-mumbly5_amd64.deb)
i am now trying to activate acpi but then i got this error:

root@ugur-dizustu:/# echo "enabled: 1">/proc/acpi/acer/wireless
bash: echo: write error: Invalid argument
enabled: 1

i cannot write to or delete this file even if i am root. I have tred to boot from live cd but the file wasn't there :( 

So anyone can be of any help?

---

### Post by Izkata on 2008-04-06
This topic is not "solved", as the previous two posts show.

And I am having the same problem with a different setting in /proc:

> izkata@Izz:~$ sudo echo -n "80:65:50:60:60" > /proc/acpi/thermal_zone/THRM/trip_points 
echo: write error: Invalid argument

Does anyone know if there's a way to make it work in the newest kernel?  Or if it'd have to be recompiled...

---

