---
title: "Install Nvidia graphics driver on Ubuntu"
date: 2008-05-06
forum: Hardware
---

### Post by seadog109 on 2008-05-06
So ive got a nVidia Ge-force 7600 GS in my system and Ubuntu is maxing my res to 800-600 O_O.....wtf..... so i googled Nvidia 7600 linux graphics drivers.

```
http://www.nvidia.com/object/linux_display_ia32_169.12.html
```


i download and install using the terminal like said under the install and it says i must be logged in as root in order to continue.. strange thing is, is im logged in as root. my username is x0vghd. thats how i made it. so i dont know if theres a default root account that im suppose to login as or what? can someone help me

[IMG]http://i27.tinypic.com/33l0awk.png[/IMG]

---

### Post by justifier on 2008-05-06
type ```
sudo <what your currently typing> 
```

just because your logged in as root doesnt mean it is runnign as root

---

### Post by seadog109 on 2008-05-06
excellent it worked, now this is what i got
[IMG]http://i32.tinypic.com/jhdgsi.png[/IMG]

i did go into my process manager. but i didnt know how to determine the x server process

---

### Post by knix on 2008-05-06
I usually boot into recovery mode. I've heard of something like "/etc/init.d/gdm stop" but havn't ha any luck

GDM is the xserver in this case

---

### Post by seadog109 on 2008-05-06
i was recommended not to do it in something something level 1 due to possible errors if i continue to install. it said to telinit 3. so i did and it just logged me into the GUI and stuff. 
```
http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/chapter-04.html
```

this is my reference im using. i need help with all of that stuff. i would like to just end the x server process if anyone can help me with that. the reference also suggests stopping all OpenGL process and switching default from X server to something else

---

### Post by lamborghiniwang on 2008-05-06
The 169.12 driver is already in the Ubuntu repo, all you have to do is go to System->Administration->Hardware Drivers to enable it and then reboot.

---

### Post by seadog109 on 2008-05-06
ive done that twice and i get this 
[IMG]http://i27.tinypic.com/2cnv7t0.png[/IMG]

i could disable it, reboot and go back to it and thats what ill get

---

### Post by lamborghiniwang on 2008-05-06
> **seadog109 said:**
> ive done that twice and i get this 
[IMG]http://i27.tinypic.com/2cnv7t0.png[/IMG]

i could disable it, reboot and go back to it and thats what ill get

Has the nvidia-glx-new package been purged?

---

### Post by seadog109 on 2008-05-06
1.) what is purged 2.) idk :confused: do i need a new package do i need to install manually?

---

### Post by seadog109 on 2008-05-06
*bump*

---

### Post by seadog109 on 2008-05-06
i need help seriously. i just updated the driver for it to the "latest" and now its stuck on ****** 600x300 it just got worse!!

---

### Post by seadog109 on 2008-05-06
never mind, i always hated this ******* OS, im just going to switch to a different one that isnt stupid as ****** ****

---

### Post by krazyd on 2008-05-06
Don't give up!

You should give EnvyNG a go. It is an awesome little app that is in the repositories that will install the right graphics driver automatically! This is how I install NVIDIA drivers.

Try running the following from a terminal.

This will install envyng:
```
sudo apt-get install envyng-core
```

Then run it using:
```
sudo envyng -t
```

You will get a menu that will let you install the right driver. Let us know how it goes! :)

---

