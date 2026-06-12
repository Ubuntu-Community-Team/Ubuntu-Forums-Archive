---
title: "Video Card Drivers: ATI MOBILITY FireGL V5200(screen resolutions-refresh rates)"
date: 2006-11-23
forum: Hardware &amp; Laptops
---

### Post by kldavis4 on 2006-11-23
Hey, I just dual booted my IBM Thinkpad T60p and it has a ATI MOBILITY FireGL V5200 video card, Intel Centrino Duo processor, 2GB of RAM.  The problem is that when I go to my screen resolution application, and try to adjust my refresh rates-it wont happen at all and I have no clue what to do.](*,) .  I dont know if the problem is that I dont have drivers for my video card or if my Ubuntu 6.10 config. Does anybody have my cure for this problem?

---

### Post by amp_man on 2006-11-24
Follow the instructions [here](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_1:_Installing_Edgy.27s_Included_Driver_.288.28.8.29) to install the ati drivers and get everything configured. You may also need to run "sudo dpkg-reconfigure xserver-xorg" afterwards to get the monitor refresh rates set up.

---

### Post by hakre on 2007-06-27
well sounds easy. I have the same problem but I think I mixed something up. fglrxinfo reports my card as a ATI Mobility Radeon X1600 while this is infact a ATI Mobility FireGL V5200. I try to deinstall now the proprietary driver and then I remember I installed the other driver as well via Synaptics.

/Edit: Well, well well. As said I totally screwed up my GFX-Card Setup. Finally even Ubuntu restricted Drivers Panel didn't offer ATI any longer. But I solved that all with a little script called ENVY. You donwload a .deb file, install and use it and reboot. Well I run that script several times it has even options to uninstall the Card. But finally it works now and the right Card is displayed in the output of fglxinfo. I know this is very dirty and I strongly encourage everyone to properly uninstall the one or other driver before testing another driver or  installation method. I was just too eager to get the new laptop running ;)

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) (don't get irritated by the nvida in the name)

---

### Post by hakre on 2007-07-08
**My current best practise:**

After a week or so trying ubuntu, kubuntu and diverse ati drivers I (finally?) ended up with this combination of tutorials that helped me to provide all the needed information and guidance:

[LIST=1]
[*]**Installation of ATI Video Driver (Kubuntu):** [ATI driver in Kubuntu Feisty]("http://www.darkartistry.com/content/view/67/41/") (Ubuntu has this more accessable through the menus).
[*]**Get Beryl and XGL working (Kubuntu/Ubuntu):** [Install Beryl on Ubuntu Feisty with XGL]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL")
[/LIST]

Remark: After the first tutorial fglrxinfo identifies my card as *ATI Mobility Radeon X1600*.

Additionally I found the following resources usefull that are partially bound to Lenovo ThinkPad Z61p because that is the Computer Model contaning the ATI FireGL V5200:

[LIST]
[*][Modeline Tool]("http://www.bohne-lang.de/spec/linux/modeline/")
[*][HARDWARE IBM ThinkPad Z61P in the Gentoo Wiki]("http://gentoo-wiki.com/HARDWARE_IBM_ThinkPad_Z61P")
[*][Fc5 on ThinkPad z61p: fglrx, suspend2 etc]("http://forums.fedoraforum.org/showthread.php?t=123002")
[*][ThinkWiki - ATI Mobility FireGL V5200]("http://www.thinkwiki.org/wiki/ATI_Mobility_FireGL_V5200")
[/LIST]

I hope this information helps someone.

---

