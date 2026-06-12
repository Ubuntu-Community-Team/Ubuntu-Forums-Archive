---
title: "Installing a Nvidia GeForce GTX 1050ti in Ubuntu 16.04.2 LTS"
date: 2017-02-25
forum: Hardware
---

### Post by wmsfoeva on 2017-02-25
So, installing a Nvidia GeForce GTX 1050ti in Ubuntu 16.04.2 LTS sounded like a good idea. Well, if you're here you know it can be a pain. After much reading and trial and error, THIS IS HOW I DID IT: 

A couple of things of know...
HP Compaq 8200 Elite SFF
i7-2600 @ 3.4G
ram coming out of my kiester
Etc
Etc
Etc

I did a fresh install with the card installed, and encrypted the drive which causes a keyboard unresponsive decrypt page if that. If you just get a plain purple screen, wait for the processing light to go out on your box and go ahead and input your decrypt password. We'll address theat issue in a sec. If you get the crap resolution non-responsive screen, ctrl-alt-delete or cycle the power. You should get the recovery screen. Go into recovery and it'll have you input the decrypt there. when you get to the options screen, just continue. Your key is in there so you'll move on fine. Your resolution might be crap at login, mine was, but it'll do. 

Login and get you a terminal. Go ahead and sudo update, upgrade, etc. 
Now we're going to fix the non reponsive decrypt screen fo eva
sudo nano /etc/default/grub
edit 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to 
GRUB_CMDLINE_LINUX_DEFAULT=""
Now save it. That'll not be a problem again unless you like the splash screen. In that case I'll leave that figuring to you because I do not care.

Pull up ye 'ol firefox and download the NVIDIA-Linux-x86_64-375.20.run driver. Go into your Downloads folder and 
sudo chmod +x NVIDIA-Linux-x86_64-375.20.run

Now you gotta break your gui to install the driver. For some reason the ctrl alt F1 thing gets nuked by the card's existence which is a big 'ol bunch of crap. 

*Dear Nvidia,
There is a problem that your card causes when you try to install the driver. Namely, it requires no xsession to do so but your card is fing kryptonite to the keyboard shortcut that lets a person do what you ask. It's been a problem going back for fing ever judging by the innumerable posts regarding this bug. Would you be a dear and get some mofing engineers to fix that so we don't think about lighting your factories on fire? 

Regards,
Me.*

Ok, you gotta break some eggs. Let's kill it! 
sudo systemctl disable lightdm.service
Your GUI is off, for now.

reboot, decrypt, login.
Hey, command line!

sudo ./NVIDIA-Linux-x86_64-375.20.run
Follow instructions, and say no the the dpkg thing or whatever.

Your driver is now installed. You're welcome.

But now you've got no GUI. Let's fix that now.
sudo dpkg-reconfigure lightdm

reboot, decrypt, login.

You will still have a text decrypt, but who cares. The login should go to lightdm as usual and your card should be up and whirring like a kitten. Again, you're welcome.

Thanks to all of the people that posted pieces of the puzzle. If I hadn't read 2389075872345 posts trying to figure it out I might remember who to give credit to. I guess just a thanks to the community will have to do. Now to find a sixer.

Cheers

---

### Post by oldfred on 2017-02-25
The disadvantage of the .run from nVidia is you have to reconfigure with dkms every new kernel update.

Better to use ppa to get newest if that is required. Ubuntu repository has recent if newest Ubuntu, but not necessarily the newest versions.

 # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
ubuntu-drivers devices 

      
 If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version. If .run version also run its uninstall.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 

   
sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you manually choose any in list.
sudo apt-get install nvidia-XXX  

    
If ppa needed for very newest:
 sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices 


       Updated driver search by nVidia model, do not download, just check correct driver version(s)
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

---

