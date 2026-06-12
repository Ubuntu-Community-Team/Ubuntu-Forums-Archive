---
title: "ipod"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by vhenry on 2009-05-08
I've been unsuccessful with getting any program to recognize my ipod touch. When I plug it in, the OS recognizes and asks if I want to transfer photo's, which I don't only music, but even that doesn't work with F-spot.

So far I've tried rhythmbox, gtkpod and banshee - neither recognize the ipod. I'm a new convert to Jaunty. Any ideas?

---

### Post by pbrugs on 2009-05-08
what model of ipod?

---

### Post by pbrugs on 2009-05-08
wait nevermind my last post, i didn't see the word  "touch" after ipod.

but i don't think that ubuntu has capabilities to sync with it; i had the same results with mine

---

### Post by vhenry on 2009-05-09
Oh no, anyone else?

---

### Post by krash1220 on 2009-05-10
This is how I got mine to work. I have an Ipod Touch. Is your ipod jailbroken?

[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)


[URL="https://help.ubuntu.com/community/PortableDevices/iPod"]Go down to where it says 
[/URL][B]Syncing Music on Firmware Versions 1.x and read everything.
[/B]

---

### Post by gjoellee on 2009-05-10
You should try our Banshee. 

It can do this with your iPod:
-Sync music with your iPod
-Sync videos with your iPod
-Sync podcasts with your iPod

---

### Post by krash1220 on 2009-05-10
Well, Banshee doesn't support Ipod Touch or at least it doesn't find mine. The only ones I've been able to use on mine is Amarok 1.4 and GTKpod.

---

### Post by vhenry on 2009-05-10
Had to jailbreak my ipod touch. got everything running on vista virtual box and also in gtkpod. Thanks!!

---

### Post by krash1220 on 2009-05-11
Well, you know you don't have to use iTunes in a virtual box. I mean if that's what you want but you can just use gtkpod or amarok 1.4 and you don't have to mess with iTunes at all.

---

### Post by orange-wedge on 2009-05-11
i installed a virtual copy of XP using VMWare to run itunes.


[LIST]
[*]just go here to create your virtual machine: []("http://www.easyvmx.com/")
[/LIST]
 [http://www.easyvmx.com/](http://www.easyvmx.com/)
[LIST]
[*]add this line to your .vmx file to support the usb drivers:
[/LIST]
[HTML]
ehci.present = TRUE
[/HTML]
[LIST]
[*]install the .bundle copy of vmware player 2.5
[*]install xp
[*]and finally install itunes
[/LIST]
i setup a samba share to my music library so i could easily maintain the library across both platforms. if you do this you will only need about 2.2GB of space for the xp virtual machine.

(ps i also use this to watch netflix in ubuntu)

---

