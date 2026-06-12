---
title: "Nvidia GeForce Go 7400 driver"
date: 2006-10-14
forum: Hardware &amp; Laptops
---

### Post by englishmen on 2006-10-14
Ive just installed automatix so i can install various apps including the drivers for Nvidia GeForce Go 7400 graphics card. The problem im having is it gives me a error

> Video card is not detected as nvidia

Can someone please tell me why its not detecting it as nvidia card and how else i can get the required drivers?

Thanks

---

### Post by Sarcas on 2006-10-14
I don't know what automatix is, so I can't tell you why it doesn't detect the Nvidia string on your card. If you type *lspci* does the card get listed with full details?

Since I'm usually a Gentoo user, the following suggestion might not be helpful, so only follow it if you're desperate (I'm sure someone else will jump in and tell me if I'm wrong ;->). There is a thread here: [http://ubuntuforums.org/showthread.php?t=75074]("http://http://ubuntuforums.org/showthread.php?t=75074") which might be a better guide to try and follow first.

If your card is listed in the *lspci* output, you could get the drivers done the Nvidia way. From a Free Software point of view this isn't ideal for various reasons, but from an "it just works" point of view, it's usually ideal.

You'll need to get the source files for your kernel, as well as the header files. I'd imagine you can get these from the Ubuntu repositories (you always were able to from Debian, although I'm just guessing). Once you have those you should go to the [Nvidia page]("http://www.nvidia.com/object/linux_display_ia32_1.0-8774.html") and download their script.

You'll need to *chmod +x filename* before you can run it, but that's all covered in the NVidia documentation. Once the script has run you should be able to load the module using *modprobe nvidia* and restart 
X.

---

### Post by AlReece45 on 2006-10-14
Are you're tring the nvidia drivers, it might not be supported in the current release. My Nvidia GeForce Go 6500 isn't supported by it, but installing the beta drivers got me what I needed.

---

### Post by englishmen on 2006-10-15
Thanks for the suggestions i typed lspci in terminal however it listed

> 0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Grap hics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Co ntroller (rev 03)

Does that mean ubuntu is saying ive got a Intel graphics card installed?

---

### Post by louistan3 on 2006-10-15
what laptop do you use? maybe uve got double graphics cards like my sony sz.. :D

---

### Post by englishmen on 2006-10-16
My laptop is a Sony Vaio VGN-SZ1VP and i forgot its got 2 graphic chips, 1 being a Intel chip for improved battery performance and a Geforce Go 7400 for improved 3d performance. I switched to performance(Geforce Go 7400) and restarted but i get the below error and it wont boot unless i switch back to the Intel chip.
> 
Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

Any suggestions how i can fix this?

Thanks

---

### Post by gn2 on 2006-10-16
> **englishmen said:**
> My laptop is a Sony Vaio VGN-SZ1VP and i forgot its got 2 graphic chips, 1 being a Intel chip for improved battery performance and a Geforce Go 7400 for improved 3d performance. I switched to performance(Geforce Go 7400) and restarted but i get the below error and it wont boot unless i switch back to the Intel chip.


Any suggestions how i can fix this?

Thanks

Looks like the hardware newer than the software dilemma. 
There isn't a Linux driver for the GO 7300, I believe yours is newer?
Perhaps you're going to have to wait till Ubuntu catches up...
Or rather, NVidia gets it's finger out!

---

### Post by englishmen on 2006-10-16
I had a problem with my wifi as well i.e. it didn't work, i believe it was because i had it turned off(laptop switch) when installing ubuntu. I reinstalled ubuntu with it switched on and wifi worked, do you think that if i was to install ubuntu but this time with the nvidia chip switched on it will work?

Also is there some sort if officially supported hardware list i can look at?

Thanks

---

### Post by louistan3 on 2006-10-17
ive got a sony sz too as i said before.. i got mine working.. even switching automatically.. check this site [http://avilella.googlepages.com/vaiosz](http://avilella.googlepages.com/vaiosz) ..

it really helped a lot.. maybe edit a bit of the stuff cos he might have a different model.. if u got questions maybe i can answer some of em.. 

i broke X the first time i tried and had to make a clean install of ubuntu(maybe not had to, but it was better :D) so goodluck :D

EDIT: oh and btw,i use the nvidia driver.. it works with our geforce go 7400 :D not sure bout 3d accel tho.. havent tested it yet..

---

### Post by englishmen on 2006-10-18
louistan3 on that link you gave me there was a paragraph on "Dual Core" stating i need to get another kernel which will run both cores. Does this mean currently ubuntu can not handle duel-core processors? If so have you got both cores running with the the suggestion made on the link(page) you gave me?

Also you stated you can switch between the 2 graphic chips with out any errors as i get, correct? If so, did they both work straight out of the box? If not do i have to install the nvidia driver with the Intel chip selected?

Thanks

---

### Post by louistan3 on 2006-10-20
yes i have both cores running.. ubuntu does not currently support multiple processors out of the box.. you would need to install the smp kernel.. you can find the instructions to gettin smp kernel in this forums.. 

and yes.. i have the double graphics card switch working.. i just followed the instructions on the link i gave you.. it is a bit complicated at first but if you read it a few times you'll understand that its really simple and a very good solution.. 
just scroll down to the middle.. there are a lot of information about sony sz stuff on that site.. its a great site.. :D

---

### Post by englishmen on 2006-10-20
Thanks again louistan3, ill read the the page/link you gave me a few times(all tho i have already done so, very confusing) and see if i can get everything working.

---

### Post by louistan3 on 2006-10-22
maybe this page explains it better.. [http://ariel.vardi.free.fr/ariel//vaiosz.html]("http://ariel.vardi.free.fr/ariel//vaiosz.html")

the main thing is.. that you put 2 xorg config files in /etc/X11/ which are (as the website says) "xorg.conf.stamina and "xorg.conf.speed"
each config file contains a working xorg.conf for each video card which is the intel chip and the nvidia one respectively.. 

then you make a script and just copy paste >  #!/bin/sh

VIDEO=`/usr/bin/lspci |grep -c nVidia`

if [ "$VIDEO" = 1 ]; then
ln -sf /etc/X11/xorg.conf.speed /etc/X11/xorg.conf
else
ln -sf /etc/X11/xorg.conf.stamina /etc/X11/xorg.conf
fi

into the script file.. then name that "S12xorg_conf"
if i remember correctly.. and put it in /etc/rc2.d/..
then the switch should work now.. but of course you'd need to restart when u want to switch from one to the other.. 

editing the xorg.conf now would be a bit different.. mainly because you need to edit the two xorg files,speed and stamina, if u want that something to work with both cards.. if u have problems just ask again and il try to reply as soon as i can.. :D

ps: i did a > sudo dpkg-reconfigure xserver-xorg for each card to get a correct xorg.conf and just copied its contents to xorg.conf.stamina or speed depending on which one is activated..

---

### Post by englishmen on 2006-10-31
Thanks louistan3 for the simple explanation i now get it, if i only knew how to copy files to the folder you said(etc/x11). I still haven't got to grips with the sudo thing yet :-(.

Also concerning the duel core processor i atempted to do what

[http://avilella.googlepages.com/vaiosz](http://avilella.googlepages.com/vaiosz)

stated but i get the below error

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-image-2.6.15-*-686

Did it work for you?

Thanks

---

### Post by englishmen on 2006-11-11
Is anyone else able to supply some help on getting my duel core cpu and nvidia 7400 gpu working?

THanks

---

