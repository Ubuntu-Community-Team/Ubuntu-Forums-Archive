---
title: "problems with ubunto 8.10"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by cirkelrundspark on 2009-02-27
Hello, i got this 3 internet stick. Its a mobile unit with a USB connection into the computer, in windows it auto installs and makes a easy program so that you can connect to the internet. My problems is that when i try to run the program it comes up with an error saying: "cant find run program", any ideas how to fix this problem?

your welcome to contact me on my messenger
[email]cirkelrundspark@gmail.com[/email]

thanks

---

### Post by InspiredIndividual on 2009-02-27
If you just installed all the software you need with the Synaptic Package manager, it should take care of the dependencies for you. I've got the feeling you may have installed everything manually, as libaudio2 for instance can be installed quite easily in Synaptic. As Ubuntu doesn't use rpm packages, you probably tried to install it in a different way. If you're new to Ubuntu, I'd advise you to use the Synaptic Package manager as much as possible. It makes installing software much easier for us noobs...

Installing libaudio2 with Synaptic should take care of your libaudio problems. For your other problems, it would be helpful if you could provide more information about them.

---

### Post by cirkelrundspark on 2009-02-28
Yes ive downloaded and installed libaudio2 manually. Same goes with wine. Im running Ubuntu 8.10. When i enter the USB drive and try to install the package only thing it says is: "Cant find autorun program".

---

### Post by InspiredIndividual on 2009-02-28
> **cirkelrundspark said:**
> Yes ive downloaded and installed libaudio2 manually. Same goes with wine. Im running Ubuntu 8.10. When i enter the USB drive and try to install the package only thing it says is: "Cant find autorun program".

I hope this doesn't sound too patronizing, but is there any particular reason you want to install libaudio and wine manually? It is possible, but it does mean you need to install the dependancies by yourself as well. If you're sure you want to do it the hard way, the libaudio2 package depends on libc6 and libxt6; wine depends on the packages procps, binfmt-support, ia32-libs, lib32asound2, libc6-i386, lib32nss-mdns on my system. Hope that helps solving your trouble with dependencies. I am interested in your reasons for going through such trouble instead of installing them the easy way, would you mind stating your reasons?

About your USB drive, I'm not certain what you want to accomplish. Is this "3 internet stick" some kind of modem? The "run program" is possibly a Windows installer, which obviously won't work. To try and help you out some additional information is necessary. What exactly are you trying to accomplish, what's the required outcome?

---

### Post by cirkelrundspark on 2009-02-28
There is no reason what so ever why im trying to do it manually, just tried to make it work. If there is any way to install the stuff the easy way, by any means please tell. Just read that i missed libaudio 2, googled it and found a file that fixed the depency error so thought it was fixed a somewhat easy way. I belive my 3 internet stick is a mobile modem, or well i would't know but atleast its a mobile internet connection. Only thing im trying to accomplish is getting my ubuntu to work without too many errors and with a internet connection so that i can work with it.

---

### Post by InspiredIndividual on 2009-02-28
Ah, that clears things up for me. Although I switched to Ubuntu quite recently, I still failed to adapt my comments to your expertise level. I'll start anew and go step by step to try and make things easier to understand. In Windows, when you need to install software, the usual procedure is to google it and try to find a setup.exe file. Of course, you cannot be sure the downloaded files are the right ones and you need to be careful you don't get a virus instead, but hey, that's where those virus scanners come in, right? 

In Ubuntu, there's almost never a need to search the web for some piece of software manually. Instead, so called 'package managers' are used to install, remove and upgrade software. Most of the time, this makes installing software incredibly easy, no need to search the web at all. Check out the most basic one: Applications > Add/Remove. You can install quite a few applications here. The only thing you have to do is check the box next to an application you want and click 'Apply changes'. Done.

The Add/Remove menu is very basic with only a few applications, so you'll probably need some software that cannot be found here. The main tool to install software is the Synaptic package manager. It can be found in System > Administration > Synaptic Package Manager. Here, you can install basically everything you need. Fortunately, it's just as easy as the Add/Remove menu: check the box next to the software you need, click apply, done. Synaptic will automatically download the software and take care of dependencies for you. 

Actually, Synaptic is similar to the Add/Remove Software menu in Windows. The single most important difference is that Windows' Add/Remove Software menu is only capable of installing/removing software that's on your harddisk. On the other hand, Synaptic searches huge software archives (called 'repositories') on the web as well. Thus, almost all software you'll ever need can be installed in this easy way. By default, Ubuntu searches only officially Canonical supported software. Most users want other software as well, so you'll probably want to enable more software archives to search in right away. In Synaptic, you can easily do this in Settings > Repositories. I'd enable all of main, restricted, universe and multiverse if I were you. You'll probably be able to find everything you need without the need to search the web, without worrying about dependencies, without the need to check your downloaded software for viruses.

More about repositories: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
You might find the following Synaptic tutorial useful: [http://www.debianadmin.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html](http://www.debianadmin.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html) .

Please tell if I was unclear somewhere, I'll be happy to elaborate if necessary. I probably won't be able to help you with your modem, as I've never used one myself. This might be a good starting point to search: [https://help.ubuntu.com/8.10/internet/C/index.html](https://help.ubuntu.com/8.10/internet/C/index.html) .

---

### Post by cirkelrundspark on 2009-03-01
f****** amazing post, think im gonna get myself an adsl connection somehow and try to reinstall ubuntu follow the "guidelines" above. Thanks alot the help was above all expectations.

---

### Post by cirkelrundspark on 2009-03-03
now, if anyone have an idea how to install a 3G turbo modem on linux, all information about this would be great. If anyone could make up a small guide explaining what to download, why and how to install the software correctly, it would be fantastic. Thanks once again.

---

