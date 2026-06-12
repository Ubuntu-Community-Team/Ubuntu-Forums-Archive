---
title: "Toshiba Satellite Laptop Success Story"
date: 2007-03-02
forum: Hardware &amp; Laptops
---

### Post by calgarystevens on 2007-03-02
I thought I'd write another linux success story for you all. I'm using a Toshiba Satellite A110-ST111 laptop, with a an ATI Xpress 200M graphics, Atheros 802.11G wireless chip, Touchpad, DVD writer and 15.4” 1280x800 widescreen.  To get it all installed I had to do a few things. First, some linux distribs wouldn't init the screen right on first livecd boot, to fix this I would choose 800x600 and then fix screen size after booting.  Ubuntu and Kubuntu (my fav now, how did I get by without it ;-) did get the screen right first boot if I remember right. 

-First up was my wireless, or all else was a moot point. For my Atheros chip, I would use ndiswrapper, and load net5211.inf up without any troubles. First, I make sure the .inf file is somewhere accessible (on old XP partition, or on a cd so you can get at it after install). Next up, open a terminal and:
sudo ndiswrapper -i /whereyouputit/net5211.inf
then check it worked with ndiswrapper -l (should show name of driver and other info)
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m  <---these last steps set it up and ensure it will work after a reboot
then go to System Settings->Networking
select wlan0 connection, configure for your router settings and click Enable.

-Next up was my ATI video (gotta have 3D for games :-)
Credit goes here to d-E-a-D @
[http://www.ubuntuforums.org/showthread.php?t=321766&highlight=ati+howto](http://www.ubuntuforums.org/showthread.php?t=321766&highlight=ati+howto)

Download ati-driver-installer-8.32.5-x86.x86_64 driver from ati.

Now, step by step:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bkp
sudo gedit /etc/X11/xorg.conf

Add this to xorg.conf:
Section "Extensions"
    Option  "Composite" "Disable"
EndSection

sudo apt-get update
sudo apt-get install module-assistant build-essential
sudo apt-get install fakeroot dh-make debhelper debconf libstdc++5 linux-headers-$(uname -r)
sudo ln -sf bash /bin/sh
bash ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/edgy
sudo ln -sf dash /bin/sh
sudo dpkg -i xorg-driver-fglrx_8.32.5-1*.deb
sudo dpkg -i fglrx-kernel-source_8.32.5-1*.deb
sudo dpkg -i fglrx-control_8.32.5-1*.deb
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo shutdown -r now
Now we have a 3d card running, beautiful thing that howto is. 

-For sound, it's a Realtek AC97 HighDef sound using the HD ATI SB alsa driver, and it works just fine.

-Now, the last thing to tweak was the hibernate/suspend quirk. It would not do it (seems to be a pretty prevalent laptop problem with linux). Well, what I did was this:
Edit "/etc/default/acpi-support" and change the following lines:
MODULES_WHITELIST="fglrx"
SAVE_VBE_STATE=false
POST_VIDEO=false
DOUBLE_CONSOLE_SWITCH=true
Also (as that didn't completely do it) I went into the bios and disabled 'legacy usb device support' and I went into the linux system services and set the powernowd service to not start up at boot. I'm not sure if  that'll work for you, but it works like a damn for me now, suspend/hibernate fires right back up. All I have to do is hit a button (screen lock is on), and type in my password and voila I'm back at my desktop. 

All that's left now is the winmodem (for faxing etc), and I'm so happy with my setup now, I'm not real worried about it yet. BTW, I can get the Toshiba Vista upgrade on this laptop for $45, what a ripoff... XP service pack 3 for money...I don't think so. Kubuntu is staying right where it is, thank you very much :-) Thanks for reading, I hope this helps someone out there, that'll make my day.

---

### Post by dishbert on 2007-03-07
Hey there Calgary.

I have a Toshiba Satellite A100.  I'm on dial-up out here in rural BC, so getting the modem working is a matter of some concern.  Did you have any luck with yours?

I ran scanModem and forwarded on the resulting ModemData.txt to the good folk at linmodems, I hope to hear back soon.  Looking at the file, it seems there might be support for the ALSA based modems.

Does your success story continue on to the modem?

dishbert

---

### Post by firedrow on 2007-03-08
I'm have a Toshiba Satellite P15-S479, nVidia Go5200 video, NEC DVD Burner, Intel P4 HT 2.8GHz, Touchpad, and Edgy (used to be Dapper, but upgraded) works great.  I haven't had any video issues, I used Automatix to grab my nVidia driver.

Wireless was the breaker for me as well.  The big problem I had was with the Atheros 802.11a/b/g.  But I found that installing KNetworkManager while wired in fixed it.  I use KNetworkManager instead of the Gnome-Network-Manager, with WPA, and it works great between work and home.  

My continuing struggle is with the built-in SD card reader.  It can't get it to recognize anything was put in the drive.  I bought a PC Card SD card reader that works fine, but the built-in is moot.

---

### Post by stealthwave on 2007-03-13
My laptop is Toshiba A105-S4004 wonder how it will run ubuntu?

---

### Post by marianom on 2007-03-16
I recently installed edgy on a Toshiba Satellite A1135-S125 with total success. However a few days later the touchpad ceased to work. That's the only problem I'm currently facing (if somebody care to share a tip for it, I'll aprreciate it).

Wireless (CNet CWC-854), hibernation, bateries: all working smooth.

---

### Post by calgarystevens on 2007-04-29
Modem, no I haven't had luck with that yet (guess that's the 5%) :) But I haven't attacked it in Feisty yet. I did notice that the reason sound didn't work on bootup was because of the modem portion of the soundcard kicking in and taking over first spot, so.... could be hope yet. If you have any luck let me know, if I discover anything I'll be sure to update everything and let you know. My suspend is still working with the settings above, which is very cool, I keep waiting for it to die on me, lol. The touchpad, hmm, mine is working great out of the box..in Edgy and Feisty. Our Toshiba's do have an on-off software setting for the touchpad though. If it was turned off in Windoze, it will remain turned off in Ubuntu. To fix that, I got ksynaptics and you have to add Option "SHMConfig" "true" to your xorg.conf under the Input Device/Synaptics touchpad section, or it won't work. I hope that helps you :-)

UPDATE: Suspend fixes!!!!!!!!!!!!!!!!!!!
sudo apt-get install uswsusp
sudo dpkg-divert --rename --divert /usr/sbin/pmi-disabled /usr/sbin/pmi
sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
and in lines that say:
elif [ -x "/sbin/s2ram" ] ; then
	    /sbin/s2ram -f       <--------Add the -f to force suspend
	   RET=$?
To go back to the old type of suspend -> sudo dpkg-divert --rename --remove /usr/sbin/pmi
Get rid of the gnome keyring password bugging you:
sudo apt-get install libpam-keyring
sudo gedit /etc/pam.d/gdm 
And add to the bottom:
auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so
Other settings are in applications->system tools->configuration editor:
look for apps/gnome-power-manager and check suspend/hibernate set to start on battery power etc.

---

### Post by lisati on 2007-06-28
> **dishbert said:**
> Hey there Calgary.

I have a Toshiba Satellite A100.  I'm on dial-up out here in rural BC, so getting the modem working is a matter of some concern.  Did you have any luck with yours?

I ran scanModem and forwarded on the resulting ModemData.txt to the good folk at linmodems, I hope to hear back soon.  Looking at the file, it seems there might be support for the ALSA based modems.

Does your success story continue on to the modem?

dishbert

I have one of the A100 line, using wireless through to broadband, and haven't had a connection problem other than my ISP slowing me down to dial-up speeds once my monthly gigabyte limit - an ISP quirk, not with ubuntu.

---

### Post by Galactic Jack on 2007-07-03
I'm running a Toshiba Satellite A110 and I'm having major issues installing the built-in wireless card. Apparently the net5211.inf driver is invalid.

Beats me.

GJ

---

### Post by mbittleston on 2007-07-08
On **Toshiba Satellite A105-S2081, ubuntu 7.04-feisty,** the above fixes to do not make suspend to ram work. It will suspend, fan turns off, pulsing light starts, but when attempting to resume, computer locks up right after hard disk light flashes. Caps lock key does not even respond after this. Holding down power button will switch off, but will not restart: Need to remove battery & power cord before it will restart. Have also tried:
[http://en.opensuse.org/S2ram](http://en.opensuse.org/S2ram)
At this point, I'd guess for this laptop, suspend to ram is a deeper issue involving kernel/BIOS issues.

---

