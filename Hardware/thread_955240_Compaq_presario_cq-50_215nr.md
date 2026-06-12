---
title: "Compaq presario cq-50 215nr"
date: 2008-10-22
forum: Hardware
---

### Post by magusxp on 2008-10-22
Ok people I am posting this because I couldnt find anything to help me with this model so I dont what to happen to other people so Im going to describe the main issues I encountered installing Ubuntu 8.04 Hardy Heron. 
The main issues were:
1.- Video - This problem I encountered with other PC's I've installed Ubuntu and this wasn't that much problem. The video card this Laptop has is an NVIDIA GeForce 8200M this is kinda tricky.
Download the linux drivers from [www.nvidia.com](www.nvidia.com) for the GeForce M series the 8600 GTX is the one I installed and worked perfectly. First you must 
delete the restricted files because they can give problems like they did to me
press 
alt+f2 and run this gksudo nautilus to run as root then access> 
/lib/linux-restricted-modules/2.6.24-21-generic
there you will see folders with the kernels you are running in my case I was using that, delete everything related to nvidia and ath for the wifi
then

stop the gnome desktop with ctrl + alt + F1 (note: you will stop the graphical interface and get to the black screen so dont be scared but write down the next commands) then do this:

sudo /etc/init.d/gdm stop
sudo init 3

then access the folder where the file is and type

sudo sh <nvidia driver ver>

Follow the instructions and after evertything is done start gdm again with this

sudo /etc/init.d/gdm start

a nvidia screen logo should appear if the driver installed correctly and there you go, video issue solved. One thing It could happen is the resolution problem to solve this do this.

in a terminal
type this 
sudo gedit /etc/X11/xorg.conf

and in the section where it says Monitor 

modifiy the resolution at the desired resolutions of your screen.

and you are ready to go.

2.- Sound
Just follow this link and install it takes a little while so just have patience

[http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

3.- Wifi just follow this thread

[http://ubuntuforums.org/showthread.php?t=917556](http://ubuntuforums.org/showthread.php?t=917556)

Ok im updating this part. It worked but as soon you turn off the pc and restart the wifi driver stops its probably because of the button I dont know so I had to build a small script to make it work, I tried it with mine and it works Ill attach it.
Just do this

alt+F2
gksudo nautilus ( this is to be able to modify graphically a folder)
then access this location
/etc/init.d/

and paste the small script I did and there you go. Every time you boot automatically the wifi settings will load.

I think this happens because the interfaces file has two things only, its probably a broken kernel as I read in other places.


And thats all I hope this really helps...dont give up on compaqs they are good. Its hell to make them work but this is the reason im posting this. OK have fun with ubuntu

---

### Post by ardvark71 on 2008-10-22
Hi...

Thanks for posting this, perhaps it could be copied somewhere as a general reference tool. :KS

Best Regards...

---

### Post by magusxp on 2008-10-22
Im sorry here is the attachment

---

