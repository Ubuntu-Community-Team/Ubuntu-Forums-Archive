---
title: "Reinstall 8.04 over 9.04 with separate home partition"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by Steve00 on 2009-10-03
I'm tired of fighting flash player in firefox on my 9.04 install, so I want to reinstall 8.04 which worked nicely. So I could experiment with reinstalling 8.04, I set up a similar 9.04 install in Virtualbox with separate /, swap and /home partitions. I then ran the 8.04 live cd install and unchecked /home in the manual partition and then installed 8.04. Everything seemed to go as advertised and when I rebooted I had 8.04 running and my /home partition intact. 

However, upon reboot I got an error dialog box that read "The panel encountered a problem while loading OAFIID:GNOME_IndicatorApplet." I elected to not delete the applet and nosed around on the new install. I finally figured out this applet was the one that provide shutdown and logoff options that appears when you click on the username in the upper-right hand corner of the screen. Everything else seems to work fine.

Any ideas on how I trashed the applet and how I get it back? I tried the "Add to Panel" option but could not find the appropriate applet.

I want to make sure that I can recover from this error before I try this on my "real" partitions.

Finally, I actually dual boot with WinXP. If I follow the install procedure above, am I going to hose my XP partition? That is, will grub still give me both Ubuntu and XP boot options?

Thanks!

--Steve

---

### Post by oboedad55 on 2009-10-03
> **Steve00 said:**
> I'm tired of fighting flash player in firefox on my 9.04 install, so I want to reinstall 8.04 which worked nicely. So I could experiment with reinstalling 8.04, I set up a similar 9.04 install in Virtualbox with separate /, swap and /home partitions. I then ran the 8.04 live cd install and unchecked /home in the manual partition and then installed 8.04. Everything seemed to go as advertised and when I rebooted I had 8.04 running and my /home partition intact. 

However, upon reboot I got an error dialog box that read "The panel encountered a problem while loading OAFIID:GNOME_IndicatorApplet." I elected to not delete the applet and nosed around on the new install. I finally figured out this applet was the one that provide shutdown and logoff options that appears when you click on the username in the upper-right hand corner of the screen. Everything else seems to work fine.

Any ideas on how I trashed the applet and how I get it back? I tried the "Add to Panel" option but could not find the appropriate applet.

I want to make sure that I can recover from this error before I try this on my "real" partitions.

Finally, I actually dual boot with WinXP. If I follow the install procedure above, am I going to hose my XP partition? That is, will grub still give me both Ubuntu and XP boot options?

Thanks!

--Steve

If nobody has a better answer this script will work. It will restore the default panels, so any customization you had will need to be re-done, not a big deal. Here you go:

mv $HOME/.gconf/apps/panel $HOME/.gconf/apps/panel-old 
sudo /etc/init.d/dbus restart

---

### Post by Steve00 on 2009-10-03
Thanks for the resposne, However, it didn't work. Everything appeared to run without errors until restart and then I got the same error message about the applet could not be loaded.

---

### Post by Steve00 on 2009-10-03
oops. Spoke to soon. When in doubt, reboot. Once I did a full shut down and then fired 8.04 up again, the applet was there. Thanks.

Now, will the process I followed to reinstall 8.04 play nice with my WinXP dual boot config?

Thanks for your help!

--Steve

---

### Post by oboedad55 on 2009-10-03
> **Steve00 said:**
> oops. Spoke to soon. When in doubt, reboot. Once I did a full shut down and then fired 8.04 up again, the applet was there. Thanks.

Now, will the process I followed to reinstall 8.04 play nice with my WinXP dual boot config?

Thanks for your help!

--Steve

Steve, now that you mention it I had to reboot the last time I trashed my panel and ran that script. Sorry I didn't think of it, but you got it which is the main thing. Maybe I'm dense, but I don't really understand what it is you're trying to do from here. Could you try again? Maybe my old brain will get it this time...

---

### Post by Steve00 on 2009-10-04
Thanks! My first step was to just experiment with a Virtuabox version of 9.04 with a separate  home partition and learn how to replace the OS version yet keep the home partition intact. Especially, when rolling back to an earlier version. I think I've gotten that down now.

The next step is to actually roll back Ubuntu 9.04 to 8.04 on my laptop's harddrive.

However, my actual system is a dual boot with WinXP and Ubuntu. It occurred to me that the process I tried with the Virtual install, that I didn't know what this would do to my dual boot set up. Will it monkey with grub, leaving me without the ability to boot XP? And, if so, will/how do I fix it?

---

### Post by raymondh on 2009-10-04
> **Steve00 said:**
> Thanks! My first step was to just experiment with a Virtuabox version of 9.04 with a separate  home partition and learn how to replace the OS version yet keep the home partition intact. Especially, when rolling back to an earlier version. I think I've gotten that down now.

The next step is to actually roll back Ubuntu 9.04 to 8.04 on my laptop's harddrive.

However, my actual system is a dual boot with WinXP and Ubuntu. It occurred to me that the process I tried with the Virtual install, that I didn't know what this would do to my dual boot set up. Will it monkey with grub, leaving me without the ability to boot XP? And, if so, will/how do I fix it?

Steve00,

It ought to be the same process (install in the appropriate/intended partitions and do not touch windows/NTFS).  Same tweak afterwards.  As for grub and if you run into problems, you could easily re-install GRUB using the liveCD.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Back-up your files.

Regards,

---

### Post by Steve00 on 2009-10-05
Thanks for the help! I'm up and running with 8.10 and my home directory and winxp dual boot intact.

I booted the 8.10 live install, chose install and then manual install. I edited my root parition and chose ext3, set it for / and checked the box to format the partition. 

On my home partition, I set it for ext3, /home and did not check the box for formatting the partition. From there everything installed. Upon reboot, I did get the "User's $Home/.dmrc file is being ignored..." warning. However, a forum search on the error provided plenty of instructions to allow me to fix that problem.

I have run into an issue with my external NTFS hard drive not wanting to mount, but I suspect that is a separate problem and I'll post a separate thread on that.

Thanks again!

--Steve

---

