---
title: "Black screen after upgrade, Nvidia drive not loading?"
date: 2009-10-13
forum: Hardware
---

### Post by jpcrow on 2009-10-13
Hello,

Last night I upgraded my Kubuntu to Karmic. I used "update-manager -d." I upgraded from Kubuntu 9.04 which I had done an "apt-get dist-upgrade" the night before.

After the upgrade restarted the computer, my screen went black halfway through loading Kubuntu.

After this I shut down manually and chose "recover" from the grub list and logged in on a terminal.

I tried "startx" and received a message saying NVIDIA drivers failed to start.

I can get the exact error message, but I'm not at my house right now. 

How can I disable the NVIDIA drivers and have it use a generic driver from the terminal in "recovery" mode. If I can do this I can enter X and update my system or find some solution. Thanks.

---

### Post by dabl on 2009-10-13
Assuming you have a boot menu, when the Kubuntu line is highlighted, press "e" to edit, and then change the boot options so it is only "ro single" -- in other words backspace to delete the "quiet" and "splash" options, all the way back to "ro", and then add "single" and press Enter.  This should take you to a menu that offers a series of options.  If you want to try "Fix X", that might get you a GUI.  If you want to "Drop to root console", that will put you at the command line with a root prompt (#).

Your problem is, a new kernel was installed during the upgrade, and the Nvidia driver needs to be installed on it.  There are lots of posts on that topic -- mainly in the "multimedia/video" forum.

---

### Post by Dawei87 on 2009-10-13
im having a similar problem, except i didnt upgrade anything. i installed karmic beta on my desktop last night which has an nvidia geforce 8500 card. after i installed i did a partial upgrade, rebooted, then installed the graphics card, but when i reboot i see the white ubuntu logo after grub, thena blank screen. i have dropped to a root prompt and ran nvidia-xconfig, but no dice. any ideas to get my card working?

---

### Post by jpcrow on 2009-10-13
Thanks Dabl, I'll try editing the line in grub and then choosing "FixX" option to see if I can get X to start. Then I'll be able to search these forums with more time (at the library atm)

I'll be looking for a way to manage my video driver through Term, that seems like an important thing to know! 

Any other advice would help =)

This is for a HP dv5000 laptop btw with geforce go video card

---

### Post by dabl on 2009-10-13
If you can use "Fix X" to get a GUI (which will be a VESA display), then you can attempt to follow the official Kubuntu method to install the Nvidia driver:

KMenu > Applications > System > Hardware Drivers, and click "Install" or "OK" or whatever.

Be very patient -- it has to download the Nvidia driver in the background but it doesn't give any visual feedback, so it looks like nothing is happening.

If the official method does not work, then here is Plan "B":

[http://kubuntuforums.net/forums/index.php?topic=3100807.msg164892#msg164892](http://kubuntuforums.net/forums/index.php?topic=3100807.msg164892#msg164892)

The version numbers are obsolete, but the process is the same, except the new 9.10 command to stop/start KDM is

```
sudo service kdm stop
```

and ```
sudo service kdm start
```

---

### Post by jpcrow on 2009-10-13
Well, no dice.

I at the house running kubuntu on my live CD, but I still can't get X to start.

after removing the "quiet" and "splash" options, and adding "single" I booted to a screen that did not give an "Fix X" option. 

It listed:
'resume'
'clear' or make room
boot to prompt
boot to prompt with networking
boot to root
clean up boot menu
and I think a scan disk or check memory option\

I printed out the instructions you linked to, but he wants me to do some things from inside the GUI.

I'm looking to disable the nvidia driver and force kubuntu to use the generic driver that it was using before I enabled the nvidia driver 190 in the "Restricted Driver Manager" 

And I need to do all of this from the console, because, unfortunately, I can't get X to start. Also, without the use of the internet if possible because I suspect that my wireless isn't working when I'm in the console and if can avoid having to download anything just to turn on the generic driver that either is already installed or is on my Live CD that would be best. (I only have access to the wireless at the moment, but if absolutely necessary I could break into my roomates room.)

Now I'm guessing, but can't confirm, that there is a generic, one size fits all, video driver (whatever was running before turning on the restricted nvidia driver)

I am also guessing that there is a configuration file somewhere, and in it there is the option to turn that restricted driver off or insert the path to the previous "generic" driver.

I'm hoping that this is true, because that might be enough to get me up and running!

Thanks for all the help, please bare with me, I'm still learning.

---

### Post by jpcrow on 2009-10-13
After some reading I found a person who deleted their xorg.conf file and it fixed the problem but turned off their restricted driver (which is what I would like to happen, I think.) 

To me this sounds like risky behavior, so I wanted to get a second opinion before I went all willy nilly and started deleting stuff.

Will the kernel recreate a generic xorg.conf file if it doesn't find the old one and will this solve my problem? (or at least get me back into x?)

---

### Post by dabl on 2009-10-13
> **jpcrow said:**
> 

I at the house running kubuntu on my live CD

OK, I don't believe I said to use the Live CD ....

When you boot your PC (with no Live CD in it), do you get a boot menu, or does it go straight to the Kubuntu splash?

---

### Post by jpcrow on 2009-10-13
ok, sry, I've been running around today between school and home. 

Originally when I got home I did not use the live CD. I entered grub by hitting escape and went into the boot menu. I went to the top most boot option and edited the line to erase the quiet and splash and replaced them with single. I hit enter and booted from there, and the list menu that it booted to did not include Fix X...

Later I found my Live CD and booted it up to read up on the forums where other people are having the same issue. (nvidia driver failure after kernel upgrade leading to balck screen)

There I have seen suggestions such as:

[http://www.uluga.ubuntuforums.org/showthread.php?p=8100677&posted=1#post8100677](http://www.uluga.ubuntuforums.org/showthread.php?p=8100677&posted=1#post8100677)

and 

also simply to erase the xorg.conf file...

---

### Post by dabl on 2009-10-13
> **jpcrow said:**
> 

 I went to the top most boot option and edited the line to erase the quiet and splash and replaced them with single. I hit enter and booted from there, and the list menu that it booted to did not include Fix X...



Hmmmmmmmmmm.  Well, I just needed to do that, and I got a gray menu of about 6 choices, but oh well ...

So, if you will download the correct Nvidia driver for your GPU and architecture, and save it in your /home/jpcrow/Downloads folder, then even if you end up at a # prompt, you can go to the /tmp directory, and then install it by following this:

[http://kubuntuforums.net/forums/index.php?topic=3100807.msg164892#msg164892](http://kubuntuforums.net/forums/index.php?topic=3100807.msg164892#msg164892)

The version numbers are obsolete, but the procedure is right, except the new command to start/stop KDM is 
```

sudo service kdm stop
```

and 

```
sudo service kdm start
```

otherwise it's all the same.  :)

---

