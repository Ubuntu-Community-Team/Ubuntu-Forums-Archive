---
title: "[SOLVED] compaq b1200 intel965 1280x800"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by paark.s on 2007-10-22
Hello,
    As I travelling through this forum I saw a lot pf people have similar problem to mine but on a different laptop model. I cannot get to run 7.04(installed by alternateCD) and cannot even start 7.10 installation process(both liveCD and alternateCD)

    my model is compaq b1200series;
  celeron1.86
  intel965 express
  broadcom wifi(i will deal with this after i get Ubuntu to run)
  1280x800 monitor resolution

    My first problem is when I use liveCD7.04. I cannot get through because my harddisk is SATA. I turned it off in bios, problem solved.
    Next, xserver cannot start. I decided to download alternateCD and I can install 7.04, problem solved.
    Then I tried sudo dpkg-reconfigure xserver-xorg, and play with it for so many option. I get this message allthe time after selecting the bit depth, and kick me off the configuration screen:

```
xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in etc/X11/xorg.conf.20071022214858
```

   I tried install 'xserver-xorg-video-intel', '915resolution'(it say I cannot install this one), also tried new 'linux-686' kernel and sudo apt-get update and then upgrade , too.

   I still get the xserver cannot start. Any Idea? I want to give Mepis a try too but it doesn't support Thai language.

   Just to be clear, I am newbie. Please be simple on your suggestion.

Thanks very much.
Paark.

---

### Post by licefork on 2007-10-23
I have the same intel chip and screen. Ubuntu 7.04 does NOT support the 965, you must upgrade to the new 7.10. It uses the experimental "intel" driver, rather than "i810" or whatever else you are currently using in 7.04. The new version also fixes the annoying SATA errors I also used to get, so you can use the Live CD, but apparently you cannot get it to "install." Does it at least run the CD? If it's just a non-recognizable hard-drive, you can fix this. I will just need a few more details. What happens EXACTLY when you start up your computer with the Live CD or the Alternate CD ???

```
xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in etc/X11/xorg.conf.20071022214858
```

That above message just let's you know that everything in the xorg.conf file has been over-written with the settings you chose when using dpkg-reconfigure xserver-xorg. It's normal. Once you are done editing that simply "sudo shutdown -r now" to restart with your new settings.

---

### Post by paark.s on 2007-10-23
Hello, 
     Thanks for your reply. What had happened is I have the installationscreen;

install test mode
install for manufacturer
install commandline
.....

and in liveCD I've got the menu too.

  but after i chose something my monitor went blank both in alternateCD and liveCD(even when i chosememory test or check cd for defect)

I downloaded the iso with torrent and use mds5checksum to compare th hash.

thanks

---

### Post by licefork on 2007-10-23
Ok. It's probably the resolution. Press F4 where it says VGA (I *think* it's F4! - don't have the CD with me), and change it to several different resolutions. Try one that closely matches your monitor and go downwards. I had that problem on the older Ubuntu distributions on my desktop computer - my screen went blank because my resolution was out of range. I believe VESA is also a choice in that menu - try that one as well. Good luck! I'll check back here later to see your results.

---

### Post by paark.s on 2007-10-23
Thanks vermuch licefork. Now i'm typing this in my shiny new Gusty. Even my broadcom wireless works.

---

### Post by licefork on 2007-10-24
No problem, glad to know it's working! :)

---

