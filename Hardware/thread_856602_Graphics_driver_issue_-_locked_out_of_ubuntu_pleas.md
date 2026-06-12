---
title: "Graphics driver issue - locked out of ubuntu please help!"
date: 2008-07-11
forum: Hardware
---

### Post by durfff on 2008-07-11
Hey there, 

I ran a software update the other day without really checking what was being updated (d'oh!), and I've ran into real graphics driver trouble... I'm getting the white screen after logon, and the only way I can access the drive is with command line... Pretty stuck!

My graphics card is an ATI x300 on IBM t43 laptop. Until recently I was running the ATI proprietary driver without a glitch, 3d acceleration and everything working. But a couple of days ago the logon screen wouldn't load and eventually gave me a dialog box asking to reconfigure my graphics set up... Weirdly it was set to VESA, and after changing back to the ATI driver and rebooting it worked and I could login a couple of times. But since the problem has started again and now I only get the blank screen... Could anyone help me and give me some hints on how to check that I have nothing but the right drivers installed, and how to get them to work again? I've tried a few things but I'm lost, keep having to reboot into XP to find some answers but I'm getting stuck!

I'm thinking of fresh install but it's really hacking my faith in ubuntu. I've never been able to get a machine to run it for more than 2 months without that can of problem cropping up... Damn, hope someone can restore some of the faith!

Cheers!

---

### Post by durfff on 2008-07-12
In the GUI graphics setup utility I've tried a few options and nothing works - keeps reverting back to vesa on boot and showing me this ugly graphics setup GUI in 800x600, set to vesa and generic plug-and-play monitor.

I've tried reverting to an old stable backup of xorg.conf but that didn't work either - I've the feeling the proprietary drivers are not installed, or not properly... But I still can't log on to the desktop (white screen of death) and I'm pretty rubbish at command line, so any help would be greatly appreciated!

Please?...

---

### Post by matt$2 on 2008-07-12
oh It's time to tackle the command line.
First
sudo lsmod
This list your modules currently loaded.  Chances are the desired drivers will be absent.  Then try

sudo modprobe 'drivername'
and chances are you'll get an error message ibforming the modules don't exist.  A blank line means success.

So, with success, log out and back in or shut down the X and login from a shell.  Then enter
startx
 and presto  else:

Now do you know the exact package name of the drivers.
When you get that. Enter either 

sudo apt-get remove  packagename
 and then 
sudo apt-get install packagename
which amounts to reinstalling.

OR

just
sudo dpkg --configure package name.

If you look up the man page on dpkg there are some other switches you might add.
but that should get you some whwere close.

then post.

---

### Post by durfff on 2008-07-13
Thanks man - unfortunately I'd already tried all that (I mean the reinstalling and modprobing part), decided to clean install anyway, cheap way out but I also wanted to clean up that system...

Anyway I've reinstalled now - going to proceed with reinstalling some of the stuff I used to have, it'll be good command-line practice! ;)

Cheers anyway!

---

