---
title: "Acer Aspire One WLAN"
date: 2008-09-13
forum: Hardware
---

### Post by skeddon on 2008-09-13
Hello

I'm trying to convert from Windows but Linux is not making it easy for me...

I have followed many different instructions to get my WLAN driver working but I cant get it to work consistently.

in ifconfig it shows the ath0, there is also an ath:avahi with that default ip address of 169.254.23.34 etc

sometimes it shows a list of networks but doesnt connect and sometimes it just doesnt show any in the scan

Im using the madwifi drivers with wicd and hardy heron

It all works in windows, but in ubuntu its just such a pain to get working... what do i need to do??

Help!

Thanks

---

### Post by skeddon on 2008-09-13
well, not sure if it helps any but if I boot in Windows first it seems to wake the WLAN and then it works.

So perhaps its that the WLAN switch doesn't work in Linux, the one at the front-right of the laptop and running XP toggles it ON or something.

Man, this sucks...

---

### Post by donec on 2008-09-13
I have been having trouble getting my Acer Aspire One wireless to work also and I tried all the instructions I was given to no avail. Then I tried to install the OneLinux from....

[http://onelinux.org/index.php]("http://onelinux.org/index.php")

and my wireless worked as soon as I selected the proper connection from a drop down menu and entered my WPA wireless password. I really recommend if you have an AA1 (Acer Aspire One) and want to run Ubuntu to use OneLinux. It is great. The Hibernation doesn't seem to work right but the suspend does. Also I have not been able to get my system sounds to work but music and such do work. Web cam works as does everything else I have tried so far.  
**_[COLOR="Red"]Go OneLinux.org[/COLOR]_**

---

### Post by acolby on 2008-09-14
[ubuntu 8.04.1 walk-through for acer aspire one]("http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=164")

i have the aa1, 8gb ssd version, but install should be the same. read through that thread, there are some updates to the wireless driver install part, because of driver updates, but everything is there. im running 8.04.1 and it works perfectly now. wireless, audio, everything.

---

### Post by skeddon on 2008-09-14
Hi Guys

Thanks for the responses

I actually used this one, which is a newer one of the one acolby suggested (basically the same thread)

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

But I ended up totally re-installing Ubuntu HH and a few other bits namely WICD to manage the network.

So far so good! Donec, i have heard about that before - I will check it out thanks dude.

Skeddon

---

### Post by skeddon on 2008-09-14
donec... I dont' believe it, that distro is for my laptop!!!
On one hand thats good, on the other, I have wasted a lot of time installing it and all sorts of stuff...argh

For anyone else reading onelinux is an Ubuntu based OS for Acer Apire one - install it! (damn it!! hehe)

OK so, is it easy to install this as multiboot alongside my normal ubuntu?

---

### Post by skeddon on 2008-09-16
kinda talking to myself here but I thought I would share...

I installed onelinux, and in all honesty I wish I left the standard ubuntu on. Not that there is anything wrong with onelinux but I had ubuntu working just fine and thought onelinux would offer something very different and much easier. But it seems its the actually the same only more difficult to get into the USB key because its not in the different types of install in the unetbootin-windows app.

Being a windows guy this meant much messing about trying to mount/unmount and format a usb key etc, which tbh is just ridiculously complicated for a basic task.

after installing onelinux, my wireless still didnt work "out of the box" and so was back at square one when i first installed normal ubuntu.

So apart from installing less things, i'm not sure why pick it over the normal version. Although it linuxone in beta, and i have the newest model which is a "150" / 1gb / 120gb IDE / 1.6MHz jobby - I think I would just follow the AspireOne ubuntu guide and you are there, at least then you know you have the mainstream support for that version.Not to knock the linuxone, there is probably something I don't know, like it has configured some stuff in the background that I haven't tried yet.

I think perhaps the onlinux is intended for the solid state drive versions perhaps, mine is just a small laptop.

There is also some error that pops up in the boot process that happens too quickly, something about the networkmanager that never happened on normal ubuntu.

Anyway, currently running on linuxone now its installed, but it aint much different to the eye.

I hope this helps someone with there AspireOne which is a really nice netbook.

Skeddon

---

### Post by dotweb on 2009-01-25
Sorry but tryed the guide at
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

and it does not work at all.
It stops in permissions etc. Seems like it is not possible to get it to work.

//Steen

PS I really have to stop posting too fast :) It did work after rebooting a couple of times. But after the kernel update 30.01.2009 it has stopped working again - so I have to boot into the older version of the kernel. Hope someone can look into it.
Other vice every Ubuntu is working great on the aspireone.

---

