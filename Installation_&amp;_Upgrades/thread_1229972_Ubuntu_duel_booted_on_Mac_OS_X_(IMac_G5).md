---
title: "Ubuntu duel booted on Mac OS X (IMac G5)"
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by Suff on 2009-08-02
I created an Ubuntu live cd 9.04 desktop and tried to boot it from a mac computer with the "C" command the "Option" command. The "C" command did not do a thing and the "Option" command only showed the main HD to boot from.

Am I missing anything?

> STEP 1: Obtain the installation medium |
You can download a Live CD to see what Ubuntu will be like or an install CD to install it. NOTE: Live CD's are a lot slower since they keep loading things off of the CD.
After you've downloaded it. Burn the image onto a CD using your favorite app. I recommend Disk Utility or Roxio's Toast. 

STEP 2: Installing UBUNTU
After you've burned it, keep the CD it and reboot and hold the C key down to boot from the CD. When it load, keep the defaults and hit enter. Choose your language, hit enter. It'll ask you how you want to partition your hard drive. If you know these settings set them. Otherwise just wipe out the entire hard drive and whatever's left you'll have for free space. The next thing it'll prompt you for a bit is your first user and your password. NOTE: The password does not show up, so don't freak out if you start typing characters and nothing appears. Just type in your password and hit enter, verify it, hit enter. The installation will continue installing stuff and finally reboot. When it reboots it'll setup everything. Don't hold down the C key to boot from the CD, just let the setting up continue.

STEP 3: After setup
When you get to the Window where you can type in your login stuff, go ahead and type it in and login. The first thing you want to do is setup you network settings. Click System go to Administration->Networking. Configure your eth0 device as you need. If you use DHCP, you don't need to do this. If you run under a proxy do this step next. Go to System->Preferences->Network Proxy. Set your settings in there. I suggest, if you have fast internet, to upgrade what you can. Click Applications then Run (at the top). Type in xterm Xterm is easier for me to use cause I've used it a lot. Its a terminal.
FOR PROXY USERS: Type in this: export http_proxy=http://the_proxy_ip_address:your_port_number/ 
Most of the time it'll be 8080, but you've configured it how you've done it.
FOR OTHERS: You just skip that step. Now type in:  sudo apt-get update
then: sudo apt-get upgrade
Finally so you can get more stuff cd down to /etc/apt type in sudo cp sources.list.orig
then: sudo pico sources.list
remove the # from lines that start with deb or deb-src and have [http://some](http://some) site and stuff
Press CTRL+O to save it. then CTRL+X to quit.
You can now do: sudo apt-get update
again to get a full list of packages so you can install them. Congrats. You have a powerful, yet friendly OS. Under System->Administration is Synaptic Package Manager you can install a lot of upgrades. Refer to [http://ubuntuguide.org](http://ubuntuguide.org) for more information. And be sure to check out [http://www.ubuntuforums.org/](http://www.ubuntuforums.org/)Help would be great! thanks

---

### Post by pytheas22 on 2009-08-02
I believe the G5 has a powerpc processor, right?  If so, you won't be able to run Ubuntu using the CD you downloaded from ubuntu.com, because those only support x86-compatible architectures.  Ubuntu no longer officially supports powerpc (because Apple stopped using when it switched to Intel processors in 2005), but you can download a non-official build that should work from [here]("http://cdimage.ubuntu.com/ports/releases/jaunty/release/").  Click the link that says "Mac (PowerPC) and IBM-PPC (POWER5) desktop CD."

After downloading that .iso file, use it to create a CD as you did before, then try booting again.  Hopefully this will do the trick.  If not, let me know.

---

