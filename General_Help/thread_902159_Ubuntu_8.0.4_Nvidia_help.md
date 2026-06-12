---
title: "Ubuntu 8.0.4 Nvidia help"
date: 2008-08-27
forum: General Help
---

### Post by ^^rac on 2008-08-27
Hi guys!

Okay, i got this 2 work and is looking lovely....

I have Nvidia 7300GT, Ubuntu does not want to use the driver, or it does not see the driver....

Does anyone know, or can point me to where i will be able to get this driver?
Or what do i do?

Thanks guys!:)

---

### Post by Lazy79 on 2008-08-27
do you tried to use envyNG ?

---

### Post by Crafty Kisses on 2008-08-27
Post the results of > glxinfo

---

### Post by aman.agx on 2008-08-27
What I would suggest is install the restricted drivers. for this follow below steps.
1. Go to NVIDIA website. 
2. download latest linux drivers for your graphics card and configuration. (64 bit or 386 architecture). The instuction to run these are there on the site.
3. you might need to install some development libraries when you run the driver file.

4. After you have installed drivers open /etc/default/linux-restricted-modules-common

it should look like this 



```

# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables both the nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES=""

```

make it DISABLED_MODULES="nv"

And reboot.


This should work. Hope it helps. 

Regards
Aman

---

### Post by ^^rac on 2008-08-27
Hi guys!

I did not try Envy....

Aman, i will try as you suggest! It did install the driver, but it game me some error....

I will post details later...

Guys, must i do this in the terminal?

---

### Post by ^^rac on 2008-08-27
> **aman.agx said:**
> What I would suggest is install the restricted drivers. for this follow below steps.
1. Go to NVIDIA website. 
2. download latest linux drivers for your graphics card and configuration. (64 bit or 386 architecture). The instuction to run these are there on the site.
3. you might need to install some development libraries when you run the driver file.

4. After you have installed drivers open /etc/default/linux-restricted-modules-common

it should look like this 



```

# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables both the nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES=""

```

make it DISABLED_MODULES="nv"

And reboot.


This should work. Hope it helps. 

Regards
Aman

Aman,

Also, i cant find the exact drivers for my card?

---

### Post by aman.agx on 2008-08-27
give me your Graphics Card name and also whether you have an 64 bit or 386 architechture ubuntu. 
Most NVIDIA cards have the same drivers on the NVIDIA site.

Lets figure out your drivers file on the site then we will go through the steps to install them.

---

### Post by Garratt on 2008-08-27
> give me your Graphics Card name and also whether you have an 64 bit or 386 architechture ubuntu.
Most NVIDIA cards have the same drivers on the NVIDIA site.

Lets figure out your drivers file on the site then we will go through the steps to install them. 

dude why try to complicate things for him?

@rac:
 ok mate, usually envy can be installed via synaptic or add/remove programs BUT on fresh installs the restricted repos arn't on the system so go to

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html") 

now install envyNG  if you are using ubuntu 8.04.... legacy if using prior versions, you will see the downloads halfway down the page.

install the correct one now goto applications > system tools(i think) 

in applicaitons somwhere anyway now run that, choose automatic detection, but automatic detection never works for me, so if you get error, run it again and choose manual, now because you are running 7 series i'd say you can just choose the latest one.

but the correct one for 7 series is 173.14.12 (or whatever is closest to that in envy) 

NOTE: it doesn't matter if it is not the exact number. like my latest drivers are something like 173.14.18 but i have to go with 173.12.12 in envy...(thats just an example)... this works.


ok now click next and let it delete all the bad drivers that didn't work, and re-install the proper drivers and now your done!

---

### Post by aman.agx on 2008-08-27
Okay here are the locations of drivers.
For x86 architechture
[http://www.nvidia.in/object/linux_display_ia32_173.14.12_in.html]("http://www.nvidia.in/object/linux_display_ia32_173.14.12_in.html")

For x64 Architechture

[http://www.nvidia.com/object/linux_display_amd64_173.14.12.html]("http://www.nvidia.com/object/linux_display_amd64_173.14.12.html")

---

### Post by ^^rac on 2008-08-27
> **Garratt said:**
> dude why try to complicate things for him?

@rac:
 ok mate, usually envy can be installed via synaptic or add/remove programs BUT on fresh installs the restricted repos arn't on the system so go to

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html") 

now install envyNG  if you are using ubuntu 8.04.... legacy if using prior versions, you will see the downloads halfway down the page.

install the correct one now goto applications > system tools(i think) 

in applicaitons somwhere anyway now run that, choose automatic detection, but automatic detection never works for me, so if you get error, run it again and choose manual, now because you are running 7 series i'd say you can just choose the latest one.

but the correct one for 7 series is 173.14.12 (or whatever is closest to that in envy) 

NOTE: it doesn't matter if it is not the exact number. like my latest drivers are something like 173.14.18 but i have to go with 173.12.12 in envy...(thats just an example)... this works.


ok now click next and let it delete all the bad drivers that didn't work, and re-install the proper drivers and now your done!


Thanks for the info mate....

Im gonna try this tonight, im not at the machine tho.....
Thanks for the info!!!

Anyway, i dloaded a driver that could work.....
Its a .run file, how do i install that?

This morning i clicked on one, it gave me an error.....

Thanks guys!

---

### Post by Garratt on 2008-08-27
yea i had same problem I could not install any drivers from nvidia and when i eventually did they did not work, because of all the old crappy video drivers were still in the system and the nvidia driver does not overwrite them...

 eventually i stumbled upon envy

---

### Post by aman.agx on 2008-08-27
Ok Now that you have downloaded the file simply follow the following steps.

1. Place the file on your desktop
2. Log Off (not shut down, just log off)
3. press ctrl+alt+F1
4. Login as yourself
5. go to your desktop location. (cd /home/<your username>/Desktop )
6. run the following commands.
   sudo killall gdm
   (enter password if asked for it)
   sh <driver file name>
   
7. ok now it might prompt you for installing some development libraries. If it does that mean you have to install those. For this log on again by typing gdm on command prompt. run synaptic, search for libc development libraries. the name of the package that you have to install is something like libc6-dev. once installed go back to step one.

Ok now your drivers should install properly.

Now once drivers are installed log in again by typing gdm. and follow the steps I wrote in my initial mail. hint: chaging DISABLED_MODULES="" to DISABLED_MODULES="nv"

this last step disables some old drivers and let the new drivers work smoothly. 

Try this out when you get time. It looks a long procedure. But once I knew what I have to do it took me 3 minutes :)

Hope it works for you.

---

### Post by aman.agx on 2008-08-27
> **Garratt said:**
> yea i had same problem I could not install any drivers from nvidia and when i eventually did they did not work, because of all the old crappy video drivers were still in the system and the nvidia driver does not overwrite them...

 eventually i stumbled upon envy

Unfortunately I didn't. So I followed the manual procedure. I don't know Envy much thats why didnt tell him to use it. And I have read it causing issues, and my problems solved this way so didnt try it.

Thanks for the info :)

---

### Post by Strangewayz on 2008-08-27
Hi ^^rac
 
I had the same problem with my nvidia GeForce fx5200 on Ubuntu Studio 8.04 as it wouldn't recognise the drivers from nvidia or the restricted drivers. Here's what I did.
 
Install EnvyNg from using Synaptic package manager (if you do a search for envyng then install the three packages (I think that's how many packages there were)).
 
Once installed hold Control & Alt and press F1 to take you out of the GUI and into the text backend. You will have to login again.
 
Type:
 
```
sudo /etc/init.d/gdm stop
```
 
This stops the gdm as I experienced problems when trying to install without stopping the gdm.
 
Type:
 
```
sudo envyng -t
```
 
you will be presented with various install options. Select option 1 for the nvidia installation.
 
Towards the end of the installation it will try to install nvidia-settings. It tell you at this stage that it was unable to download nvidia-settings and do you want to reboot (I use a wireless adapter and the drivers were reset during the nvidia installation - if this happens to you just reboot).
 
Once rebooted login as normal.
 
If the nvidia-settings did not download (if they did then you can skip this step) open a terminal and type:
 
```
sudo apt-get install nvidia-settings
```
 
Once installed type:
 
```
sudo nvidia-settings
```
 
This will open the settings window in super mode so that any changes can be written to your xorg.conf file (there is a save button in the nvidia-settings window).

---

### Post by Garratt on 2008-08-27
> Hi Aman/^^rac

I had the same problem with my nvidia GeForce fx5200 on Ubuntu Studio 8.04 as it wouldn't recognise the drivers from nvidia or the restricted drivers. Here's what I did.

Install EnvyNg from using Synaptic package manager (if you do a search for envyng then install the three packages (I think that's how many packages there were)).

Once installed hold Control & Alt and press F1 to take you out of the GUI and into the text backend. You will have to login again.

i dont think envy is in synaptic on a fresh install, i'm currently on live cd, cause i got boot problems im fixing, and it isn't in my synaptic or add/remove, so im guessing it's not on fresh installs either, it might be in restricted extras, or some other packages.

which is why i directed to website

actually i just check 3rd party sources and theres nothing in there on live cd, so im probably wrong :P

---

### Post by aman.agx on 2008-08-27
I am running on Mint nowadays and it comes on the live CD. So you get it already installed on a fresh install

---

