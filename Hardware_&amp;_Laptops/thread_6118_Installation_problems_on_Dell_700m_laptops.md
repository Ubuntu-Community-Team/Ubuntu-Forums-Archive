---
title: "Installation problems on Dell 700m laptops"
date: 2004-11-25
forum: Hardware &amp; Laptops
---

### Post by stanleys on 2004-11-25
I tried several times and was unable to make a successful installation of Ubuntu  on a Dell 700m Inspiron laptop.


I have 2 laptops (identical) and installation locks on both. I tried redownloading and burning another copy, but the problem was exactly the same.


The last few messages before the installation freezes:

--------------


Setting up hal (0.2.98-1ubuntu9) ...
 * Restarting system message bus ...
 * Stopping Hardware abastarcation layer... [ok]
 * Starting hardware abstaraction layer ... [ok]



Setting up libsysfs1 (1.1.0-1)...


----------------

screen stays the same and nothing happens

---

### Post by spirospr on 2004-11-25
Well i don't know which version of Ubuntu you are trying to use , but i had some problems in installing 4.10 when i choosed my local language for installation. Whe i selected english the installation was succesful. If you are trying to install the newer version of Ubuntu (Hoary) which is unstable yet , you might want to try the 4.10. 

If you make it installing Ubuntu , checking the HowTo of my Dell Latitude B800 might offer some future help....

[http://ubuntuforums.org/showthread.php?t=5464](http://ubuntuforums.org/showthread.php?t=5464)

Hope you make it.

---

### Post by stanleys on 2004-11-25
I was installing Ubuntu 4.10 so I'm positive it should've worked.
I haven't had any experience with Ubuntu (for the obvious reasons) but I've had no problems installing other distros in the past.
WIth all the wonderful things being said about Ubuntu I'm upset that I wont get to see them.

---

### Post by Spooky on 2004-12-20
The problem is the Broadcom ethernet card (HAL tries to do some stuff that the driver in the 2.6.8.1 kernel doesn't like). I managed to get an install complete by rebooting the machine after the hang (without the Ubuntu CD) and letting the install complete. I then had to disable the HAL until I could install 2.6.9 (you can get it from the hoary repository) which solves some, but not all of the problems. Using the broadcom driver (available on their website) rather than the b44 driver may also solve some of the problems, but I haven't tried yet. I am still having suspend problems which I suspect are due to the b44 driver.

---

### Post by minghua on 2005-01-09
[QUOTE=Spooky]The problem is the Broadcom ethernet card (HAL tries to do some stuff that the driver in the 2.6.8.1 kernel doesn't like). I managed to get an install complete by rebooting the machine after the hang (without the Ubuntu CD) and letting the install complete.[/QUOTE]
Spooky is right, the problem seems to be in the b44 driver.

I got the same problem (hang up during installation) on a 700m, but rebooting doesn't help and the computer hang up again at ``Starting PCMCIA''.

So I did a second fresh installation, and after stage1 (the installer eject the CD and reboot from hard disk), I stopped in the middle of base-config and remove the driver.  This solved the problem and the installation succeeded.

The detail:  After entering the first user's name and password, this user is created.  Now stop at the ``Connect to Internet for packages'' dialog, press Ctrl+Alt+F2, log in as the user you just created, run ``$ sudo -H -s'' to get a root shell, then remove the b44 driver module by ``# rmmod b44'' and ``#rmmod mii''.  I removed mii because only b44 depends on it, but maybe it's not necessary.

I didn't have time to upgrade the kernel or change the driver module as Spooky suggested.  Since the wireless network is working fine, I may choose to just disable this problematic ethernet interface.  I'll report them here when I get it done.

---

### Post by strwrsxprt on 2005-01-10
i tried this method and was able to complete installation. i dont really know where to go from here. network isn't working. day 1 of linux: moderate success. thanks to everyone thats helping out.

*edit* ive noticed that the live cd works fine and the network card is functioning.

---

### Post by mrm on 2005-02-08
I just got a new 700m and have had the problems listed above. I was able to complete the install by disabling the 10/100 card in the bios of the computer. However, once the install was done I get an error that says that X was unable to start. Bummer. Anyone else have ideas on this?

---

### Post by ryan00davis on 2005-02-08
i too have a 700m and just installed the newest release.  it would hang in the configuration after the reboot, and after some searching i discovered that you need to type custom while installing and it will just install the base system and give you a text based system.  then you need to install what you want, but dont install hal, or the 2 things that are dependent on it

[http://www.ubuntuforums.org/showthread.php?t=1342&page=2&pp=10&highlight=install+freeze](http://www.ubuntuforums.org/showthread.php?t=1342&page=2&pp=10&highlight=install+freeze)

here is the thread that had the person that figured it out and explains in a little better detail than me..

i was very pleased, this is the first distro ive seen to fully support my wireless with no aditional setup.

hope this fixes your problem as it did mine

---

