---
title: "Hardy Heron Freezes on Logout"
date: 2008-09-01
forum: General Help
---

### Post by john8791 on 2008-09-01
Ever since I installed Hardy Heron (clean install), Logout turns the screen black and locks up my computer completely.  Alt-bkspc, Alt-FX, etc does nothing.  I can't even ssh into the machine when it is in this state.  I updated to the latest kernel (2.6.24-19-generic) with no change.

I read in a bug report [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/237531](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/237531) that it could be an NVIDIA problem.  I even tried disabling bootsplash in menu.lst per Alberto Milone but that did not work either.  Any ideas?  Thanks

---

### Post by Peter09 on 2008-09-01
Control-Alt-Backspace will move the process along, Short term until the bug is fixed.

---

### Post by speed32219 on 2008-09-01
Same darn problem here.  I even have problems where once that starts, soon I lose my boot up Bios(MB) screen.  I then have to remove video card and use integrated video to get back to my bios screen.  Third or fourth install in two days and last night with 95% of issues fixed I installed Xine (Trying to get the 5.1 AC3 passthrough spidf optical working, which has been a major thorn) and re-booted and now I am right back to the gray/black screen for shutdown or re-boot.  Using the latest Nvidia drivers from Envy. (173.XX.XX)

This evening I'm going to pull the GEforce 6200 card and connect to the integrated VGA port and try and get it working again beffore I put the Nvidia AGP card back in.

All this work trying to get Alsa to pass AC3 through the Spidf otpical to my stereo.  Sound is a major pain in the **** with this release.  I might need to move to Gutsy or some other.

---

### Post by john8791 on 2008-09-01
> **Peter09 said:**
> Control-Alt-Backspace will move the process along, Short term until the bug is fixed.

Ctrl-Alt-Backspace kills the X server and then locks up the computer just as if I had done Logout.

---

### Post by john8791 on 2008-09-02
UPDATE:
I downloaded the latest iso of Ubuntu and did a clean reinstall and the problem went away.  However this is not the solution because without the proper NVIDIA driver for my Gforce 5200 card, the display is shifted to the right by a half inch.  The default driver ignores the Modelist line in xorg.conf I generated with xvidtune to correct for the shift.
With either the non-free driver installed through Ubuntu or Envyng, the problem comes back.

---

### Post by Ken4000 on 2008-09-07
Hi I have the same problem.
When I'm logging out, I get a black screen :( My computer is a Dell Inspiron 8600 1.7GHz with a Ati Radeon 9600 Turbo Pro graphic card and it's running Ubuntu 8.04 Gnome.
I have tryed all this without any result:

System freezes after logout with GDM or KDM

If you use GDM modify
File: /etc/X11/gdm/gdm.conf (/usr/share/gdm/defaults.conf for me)
AlwaysRestartServer=true

If you use KDM add to the [X-:*-Core] section the following
File: /usr/kde/3.x/share/config/kdm/kdmrc
TerminateServer=true

Edit /etc/X11/xorg.conf to use "ati" instead of "fglrx"? fixed the problem for me, but then compiz doesn't work.

If you experience hangs when logging out (of X) it is probably due to the /etc/ati/authatieventsd.sh script looking for X authorisation files in the wrong place when it starts up.
You can kill the hanging authatieventsd.sh processes from a console tty to allow the shutdown of the X server. This can be fixed permanently with:

sudo mkdir -p /var/lib/xdm/authdir
sudo ln -s /var/run/xauth /var/lib/xdm/authdir/authfiles

If that doesn't work then you can disable atieventsd with this command:
sudo /usr/sbin/update-rc.d -f atieventsd remove

I have also tryed all of this described here: 
[http://www.kalaj.org/blog/2008/05/23/solved-blank-screen-on-logoutreboot-with-ubuntukubuntu-hardy-heron-804-on-t60-with-ati-card/](http://www.kalaj.org/blog/2008/05/23/solved-blank-screen-on-logoutreboot-with-ubuntukubuntu-hardy-heron-804-on-t60-with-ati-card/)

[https://bugs.launchpad.net/ubuntu/+bug/38915](https://bugs.launchpad.net/ubuntu/+bug/38915)

[http://www.phoronix.com/forums/showthread.php?t=10090](http://www.phoronix.com/forums/showthread.php?t=10090)

Does anyone else have a solution for the problem?

It sounds like a BIG problem in Ubuntu that is very commen in this new release! :(
I hope Ubuntu will fix it soon!

Best regards
Kenneth

---

### Post by Ken4000 on 2008-09-07
Hi again
I haven't tryed this: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/118605/comments/32](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/118605/comments/32)

I'm running Gnome and don't know what to change...


Best regards
Kenneth

---

### Post by Ken4000 on 2008-09-07
Hi again
I have now tryed PCLinuxOS and it doesn't have that problem, so it must be a problem with Ubuntu Hardy. It's not related only to ati, people with nvidia also have the problem.
I have tryed to change from "ati" instead of "fglrx" in xorg.conf and then the problem disappeared, but then I can't use any 3D or Compiz, so I changed it back.

Have anybody solved this problem???
Does anybody know where I can report it or if it is already reported???

...I'm totally new to Ubuntu, but have worked a little with Linux and I'm NOT going back to WinDoze... ;)

Best regards
Kenneth

---

### Post by Ken4000 on 2008-09-08
> **Peter09 said:**
> Control-Alt-Backspace will move the process along, Short term until the bug is fixed.

Peter09 do you know if there is a bug report some where? I wnat to follow the process...

Best regards
Kenneth

---

### Post by Ken4000 on 2008-09-08
Am I the only one that have this problem now?
When I logout or want to switch user it's going in black screen. I can't do nothing except pushing the power button!

Best regards
Kenneth

---

### Post by Ken4000 on 2008-09-08
Hi again
I have made a reply on these bug and hope it will be fixed! :(
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/119635](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/119635)
[https://bugs.launchpad.net/ubuntu/+bug/38915](https://bugs.launchpad.net/ubuntu/+bug/38915)

Best regards
Kenneth

---

### Post by Lego Dragon Rider on 2008-09-08
Unfortunately, you are not alone. I ( did ) get the same black screen when I try ( tried ) to logout or shutdown. As far as I know there is no workaround. 

Has it been confirmed that this is a problem only with Hardy and not in 8.10? Because if it's unique to Hardy then I'll go ahead and upgrade again.

Hardy is really giving itself a bad reputation. For an LTS version of Ubuntu it sure has some serious problems. Why hasn't a support representative said anything about it?

EDIT: I somehow fixed the logout/shutdown freeze. I have no clue how or what I did that stopped it, but it doesn't do it anymore. The only things I did to my Ubuntu were:

1) Uninstall a lot of programs that I don't use any more. I did this because I am planning on upgrading to 8.10 and I don't want to download any more than I have to. 
2) Install the Nvidia driver. ( System>Administration>Hardware Drivers )
3) Restart.

As of this writing, I do not get the lockups and everything works great. Firefox, Instant Messaging, World of Warcraft - it all runs without a hiccup. I'm still going for 8.10 but at least 8.04 is no longer out to kill me.

---

### Post by Ken4000 on 2008-09-09
> **Lego Dragon Rider said:**
> Unfortunately, you are not alone. I ( did ) get the same black screen when I try ( tried ) to logout or shutdown. As far as I know there is no workaround. 

Has it been confirmed that this is a problem only with Hardy and not in 8.10? Because if it's unique to Hardy then I'll go ahead and upgrade again.

Hardy is really giving itself a bad reputation. For an LTS version of Ubuntu it sure has some serious problems. Why hasn't a support representative said anything about it?

EDIT: I somehow fixed the logout/shutdown freeze. I have no clue how or what I did that stopped it, but it doesn't do it anymore. The only things I did to my Ubuntu were:

1) Uninstall a lot of programs that I don't use any more. I did this because I am planning on upgrading to 8.10 and I don't want to download any more than I have to. 
2) Install the Nvidia driver. ( System>Administration>Hardware Drivers )
3) Restart.

As of this writing, I do not get the lockups and everything works great. Firefox, Instant Messaging, World of Warcraft - it all runs without a hiccup. I'm still going for 8.10 but at least 8.04 is no longer out to kill me.

Hi there
I'm glad to here I'm not totally alone! :) I have tryed PCLinuxOS, OpenSuSE and Fedora and they didn't have any problem with the logout or switching user. But they make my computer more noisy and have to setup a lot, to get them to work properly. Ubuntu only have this problem, so I just have to live with it.
I'm totally new to Ubuntu, but I think it's because of the graphic card, so I will try to install the newest ATi driver.
- Does anybody know what the best driver is to install for an ATi Radeon Mobility 9600 Turbo Pro card??? 
- What is the best way to uninstall the default driver that came with Ubuntu???

Best regards
Kenneth

---

### Post by Ken4000 on 2008-09-19
Hi again
I have now installed the newest ATi driver (catalyst 8.8) and now it doesn't freeze in black screen. Now I get the login screen, but when I login again it shows the panels for a half second the only shows the orange screen of the login where it freezes :( ARGH!!!

Can someone help me here, it is so ignoring! ...please.

The only thing I have done to Ubuntu is:
- Activating 3D
- Enable compiz-fusion
- Changing to cube desktop
- Installing emerald manager
- Changing background picture and theme

Found out "Logout" and "Switch user" did not work
- Uninstalled the driver from Ubuntu
- Installing new ATI Catalyst 8.8 driver from ati's homepage.

Best regards
Kenneth

---

### Post by Ken4000 on 2008-09-20
Hi again
After I have read ALL posts in this bug: [https://bugs.launchpad.net/ubuntu/+bug/38915](https://bugs.launchpad.net/ubuntu/+bug/38915), which have existed since 2006-04-11 and tryed all the "tricks" there. 
I found out switching to "None" under System --> Preferences --> Appearance --> Visual Effects, I can logout out and switch user :) But then I have no eye-candy at all...no cube, nothing :(
 
I will try reinstall Compiz-Fusion and read some about visual effects on Gnome. Does anyone know where I can read about that???

Best regards
Kenneth

---

### Post by Ken4000 on 2008-09-20
No one have a solution or work around for that bug??? ...other than just disable the visual effect ;)

Best regards
Kenneth

---

### Post by john8791 on 2008-09-22
> **Ken4000 said:**
> No one have a solution or work around for that bug??? ...other than just disable the visual effect ;)

Best regards
Kenneth

Kenneth,
  I have gotten nothing to work other than switching back to the generic nv driver which gives me screen shifting issues.  It looks as if ATI and Nvidia have similar but not exactly the same issue.  I am running an nvidia GEForce 5200 card.

---

