---
title: "How do I apply nvidia-settings at boot?"
date: 2013-05-07
forum: Hardware
---

### Post by jdrichardson on 2013-05-07
I have a GE Force 6150 graphics chip, have installed nvidia-current as the driver, run nvidia-xconfig, and used nvidia-settings to set brightness, contrast. gamma, and digital vibrance. I am using Ubuntu 13.04, 64-bit. Everything looks great!

However, when I reboot, my settings are gone. I have to restart nvidia-settings to get them back. I have installed /usr/bin/nvidia-settings --load-config-only as a startup application but it seems to be ignored. I can run /usr/bin/nvidia-settings as a startup app and my settings are restored; of course, I have an open nvidia-settings window. 

Has anyone had this problem and found a fix for it? I would appreciate some help!

---

### Post by Shrek01 on 2013-05-07
I had this happen to me.
I found that no matter what change I made using nvidia-settings, the result config file for Xorg wasn't being read after reboot.

I use Kubuntu and what solved it for me was using the System Configuration utility -> Display and Monitors instead of using nvidia-settings.

---

### Post by jdrichardson on 2013-05-08
Well, the problem went away! Nvidia-Settings works OK now - my settings are restored at boot. 

It's not clear why this happened. In effect, all I did was re-install Ubuntu, go through the setup described above, and low and behold, it worked.

On to the next problem.

---

### Post by pendulous on 2014-02-24
Yeah, this is a PITA. 

Set the settings as desired, find .nvidia-settings-rc in /home and /home/user, remove all instances of hostname, set both files as read-only. 
Set nvidia-settings -l in startup applications 

none seem to work!! 

The only option is to manually launch Nvidia X server config. Such a pain. 

If anyone has a **working** solution PLEASE provide it.

---

### Post by Bucky Ball on 2014-02-24
Well, the bad news is that 13.04 is no longer supported so a working fix could well be upgrading to a supported version of Ubuntu; 12.04 LTS and 13.10 are both directly upgradeable to 14.04 LTS when it is released in April.

13.04 will no longer be updated, including security updates, and as time goes on it will get harder to find fixes and apps will get old and dodgy as they are no longer updated. All this quite apart from the security vulnerabilities.

If there is no clear solution to this now there is not likely to be. Unless you can dig one up or find a fix yourself.

---

