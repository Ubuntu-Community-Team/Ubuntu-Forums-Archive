---
title: "3D and Dual Screen with ATI card?"
date: 2008-08-16
forum: General Help
---

### Post by Linux&amp;Gsus on 2008-08-16
Hi all.
I got some issues with my ATI card. It's a laptop, Toshiba Satellite M70-151, with a ATI Radeon Mobility X700 (PCIE). Running Kubuntu 7.10.

First problem is, it takes forever to boot and after GRUB it only shows a black screen until the Login comes up. That Login screen is sometimes only vertical and horizontal stripes, nothing to read. So, I have to reboot.

Yesterday I played around and wanted to get a 2nd screen attached to the laptop. I set up everything in the System Settings and then it needed a reboot. Driver used what ever comes with Kubuntu (flgx??) and restricted drivers enabled.
On reboot I only got the stripes on the login screen. I tried it about 5 times. Then I tried XP (dual boot), no problem at all, back to Linux only to see the stripes again. So, I booted recovery mode, did a "dpkg-reconfigure xserver-xorg" and eventually got it fixed and I'm back in Linux.
Still no Dual Screen, of course.

Next I tried was to download Linux drivers from the ATI site, installed it. I assume this driver is now used (see attachment for driver info) since the restricted driver in the System Settings is ticked as enabled anymore.
I haven't tried Dual Screen yet but at least for booting the system it doesn't make a difference. Still very slow and only black screen. How can I verify what driver is in use?

Also, I don't know how I possible could enable 3D. Is that possible, anyways? It's not so much about Compiz, I never had it therefore I don't miss it. But I can't even get a nice looking 3D Chess up.

Is there any hope to get that all working? Would it help to upgrade to Hardy (newer drivers?)?
The Dual Screen is not only to get a 2nd screen going but eventually connect a projector as well. Right now I depend on Windows for that.
Also, while trying to set up the 2nd screen it only gave me the option for 800x600 or smaller.

Is a ATI X700 really that crappy or is there any hope?

Thanks for any help.

---

### Post by Linux&amp;Gsus on 2008-08-17
No one any ideas? :(

---

### Post by Linux&amp;Gsus on 2008-08-19
bump.

---

### Post by peitschie on 2008-08-19
Hiya!

Sorry for my late arrival.  Have you checked out a project called "Envy" ([http://albertomilone.com/nvidia_scripts1.html)?](http://albertomilone.com/nvidia_scripts1.html)?)  This is a cleaner (and I've found more reliable) way to install the required ATI drivers.

These are available in the hardy repositories, so you should be able to install it by opening up a terminal and typing in:
```
sudo aptitude install envyng envyng-qt
```
It might be a good idea to do the dpkg-reconfigure on your xserver again here just to reset any changes you might have made.

Installing envyng should create a menu item, but in case it doesn't, you can launch it from the terminal by typing in:
```
envyng -k
```

Get that installed and see if that helps with your issue at all.

The black screen until the login screen is shown could be caused by an incorrect splash screen resolution.  Check the /etc/usplash.conf file by entering the following:
```
kdesu kate /etc/usplash.conf
```
I had to change the resolution on mine to match my laptop screen

Let me know if you need more information on any of these steps and tell me how you go :-)

---

### Post by Linux&amp;Gsus on 2008-08-24
Hi peitschie,
sorry for my late reply. I had a disaster here while upgrading my computer. I need it next week for teaching. Why oh why did I think upgrading (Gusty to Hardy) now is a good idea. Anyways, it got stuck, well the upgrade process froze, and I basically had to reinstall from scratch. Now I have Kubunti 8.04 w/ KDE4.1. Unfortunately I don't have the best of all backups and I dunno if I get my Firefox bookmarks back and if I get my GPG back. And I have some other issues as well.

Anyways, I didn't know about 'envy'. From reading through that website you linked I understand that 'envyng' would be the better version but I didn't quite understand why. I might try it anyways.
What I didn't really understand though is what it's doing. Is it re-installing the video card driver, installing new ones or providing a GUI to better configure the driver... Is it possible to get 3D with that and dual screen or has that nothing to do with it?
Well, I might try but since I lost so much time now I need to wait another week till I finished my teaching. I guess I have to use Windows for that. Oh, I hope it's still working, haven't booted that for ages.

I'll keep you updated how it'll go.
Thanks for your help.
Cheers.

---

### Post by peitschie on 2008-08-24
Hehe... welcome back :).  The delays are no problems lol.

Regarding envy, indeed, you will be using envyng (thats what will be installed by entering that line of code I displayed).

To explain a bit what Envy actually does for you, by default Ubuntu ships only with the open-source Ati drivers.  Now, these work fine for 2D only work, where acceleration isn't really necessary.  However, for 3D work, and compiz effects etc., the open source drivers simply don't cut it as they are still too immature.  So instead, you may want to try the closed-source Ati drivers (otherwise known as fglrx).  

This is precisely what Envy does for you.  It downloads the latest Ati drivers, and sets them up and installs them on your system, taking care of some of the basic configuration needs (such as changing the driver specified in the xorg.conf files.  The binary-only drivers provided by Ati also include a GUI that allows more detailed configuration of the Ati cards to do things such as dual-head setups etc, which I notice you already found in the screenshot you first posted!

Once you get the latest drivers, the next step is to use that Gui you posted initially to try and get the dual-head setup working.  Also, this will give us a baseline to start from so we can start fiddling around with your xorg.conf file etc. to see what gives improvements.

Regarding the other query about the 3D chess game... what game are you trying to run?

Also, a random tip for Firefox bookmarks, I'd highly recommend using a free online service called Foxmarks ([http://www.foxmarks.com/](http://www.foxmarks.com/)) for backing up your bookmarks.  I have never had any troubles with their service, and it also provides other handy things such as the ability to synch across multiple computers even (e.g., synch your bookmarks between linux and windows as well ;) )

---

