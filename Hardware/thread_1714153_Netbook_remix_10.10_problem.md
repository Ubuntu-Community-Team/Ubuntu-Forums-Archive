---
title: "Netbook remix 10.10 problem"
date: 2011-03-25
forum: Hardware
---

### Post by Davisjr on 2011-03-25
I know this has probably been asked dozens of times so i apologize if i'm posting in the wrong place or something. I own an acer aspire one D250-1215 windows 7 starter i used wubi to install the ubuntu netbook remix 10.10 on it so it now dual boots. My problem is i cannot get onto the internet wireless or wired and from doing a lot of reading i understand i have to get drivers for my wireless card it is the broadcom one but although ive seen countless threads and questions similar to mine i just can't find an answer or simple soloution to how to get these drivers the closest ive come is reading that i should compile my own but i am just not knowlegeable enough to do that.
Does anyone know of a way i can get my netbook online by just downloading the drivrs somewhere onto a usb drive i have 4gb and then how to install them so it gets me online with my netbook any help would be greatly apreciated thankyou.

---

### Post by bcbc on 2011-03-25
See [this sticky thread]("http://ubuntuforums.org/showthread.php?t=1604868") in the [Networking and wireless forum]("http://ubuntuforums.org/forumdisplay.php?f=336")

---

### Post by Davisjr on 2011-03-25
Thanks for your reply however i have already tried that and when i search for the installer it does not find anything :(

---

### Post by bcbc on 2011-03-25
You should be able to download the package on a different computer with internet and then install it on your own. First generate the download script on your computer so you get the correct version: run Synaptic, search for firmware-b43-lpphy-installer, click on it, then on File, 'Generate package download script', save it on your USB.

Then boot another computer e.g. live CD/USB, connect to net, and execute the download script you saved. Then take the .deb files back to your computer and install them.

Something like that - I haven't fully executed that, but I tested the Generate package download script, and it downloaded the .deb successfully.

---

### Post by Davisjr on 2011-03-25
I'm a real noob at all this linux stuff  and cant seem to do what you told me there I searched in synaptic package manager for that and again nothing comes up at all i'm not even sure if doing this will fix my problem i'm getting more and more confused ive read dozens and dozens of threads here and all over google and there just does not seem to be anyone with a straightforward soloution i would have thought it being not a small problem that the unr people would have a download for the driver for the wireless somewhere by now 
I am not too savvy at linux as im a very new user and was hoping i could just download the drivers onto my 4 gb usb drive then install somehow on the ace running ubuntu but im totaly lost now thanks for your reply again it is apreciated

---

