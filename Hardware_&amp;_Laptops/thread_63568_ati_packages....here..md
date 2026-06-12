---
title: "ati packages....here."
date: 2005-09-08
forum: Hardware &amp; Laptops
---

### Post by floyd27 on 2005-09-08
I am still trying to get these drivers to work.
i was in synaptic and seen  under "ati driver" a bunch of fglrx and ati control center things.
I installed them but it didnt work..
Is the the official package iv been hearing about or something else?
If it is do i have to uninstall mesa drivers for it to work?
The mesa drivers want to delete a bunch of my kde things...is there a wy not to uninsatll all those things and just the mesa driver?
thanx

---

### Post by Cashel on 2005-09-09
[QUOTE=floyd27]I am still trying to get these drivers to work.
i was in synaptic and seen  under "ati driver" a bunch of fglrx and ati control center things.
I installed them but it didnt work..
Is the the official package iv been hearing about or something else?
If it is do i have to uninstall mesa drivers for it to work?
The mesa drivers want to delete a bunch of my kde things...is there a wy not to uninsatll all those things and just the mesa driver?
thanx[/QUOTE]


No you dont need to uninstall the mesa drivers... also I dont know if your using Hoary or the older versions but in Hoary the package you want is called xorg-driver-fglrx ... people swear its possible to get them to work but I've played hell with it myself...  A howto for that is available at:

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)
also...
[http://ubuntuforums.org/showthread.php?t=3567&page=1](http://ubuntuforums.org/showthread.php?t=3567&page=1)
was helpful for me... 

otherwise... 

Here's how I installed the official ATI driver 8.14.13 (under old drivers, the newest is buggy for my 9600 PRO)... :

sudo apt-get install build-essential

sudo alien fglrx_6_8_0-8.14.13-1.i386.rpm

sudo dpkg -i --force-overwrite fglrx-6-8-0_8.14.13-2_i386.deb

(some say do sudo mv /lib/modules/2.6.10-5-386/kernel/drivers/video/fglrx.ko $HOME at this point but I didnt need to)

cd /lib/modules/fglrx/build_mod/
sudo chmod 777 make.sh
sudo ./make.sh
cd ..
sudo chmod 777 make_install.sh
sudo ./make_install.sh
sudo dpkg-divert --package fglrx --add /usr/X11R6/lib/libGL.so.1.2

then run back up your old xorg.conf and let fly with fglrxconfig

Good luck to you, and do use the ubuntuforums.org and ubuntulinux.org search function for "fglrx" if you run into any more problems, theres a 100 different sets of instructions to get it to work, all a hair different as these drivers.. well.. suck... 

:)

---

### Post by floyd27 on 2005-09-09
thnax for that info there....
I will give that a tyr today.
There seems to be a little more to your way than others so hopefully it works..
I have tried oh 17 times now... And after a few reformats and alot of headeaks still nothing to be happy about but what can i say ....Iv learned a tone so at least i got something fo my efforts..
thanx again..
ill let you know how it goes... \\:D/

---

### Post by floyd27 on 2005-09-09
i assumethat i could just use the latest dirver in place of the one you used and there would be no problems there?
right?
thanx

---

### Post by floyd27 on 2005-09-10
Sorry but that didnt seem to do it either.
I tried the following

uninstalling restricted repositories.
edited my xorgconfig file to say 
fglrx instead of ati, and did the externalagpgart "no" thing as well
made sure gcc was installed.

however this was not a fresh install.
i have been messing with it for a while, could this be an issue?
i ended up with no GUI and had to dpkg-reconfigure xserver-xorg to get the GUI back.


I did uninstall the fglrx that was origionally installed "synaptic" before doing this.
when i restarted it said cant load fglrx "no driver found"

mesa drivers are still in use now.

---

