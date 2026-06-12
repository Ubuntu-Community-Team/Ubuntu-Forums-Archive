---
title: "Usplash erros after Karmic update."
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by arturhoo on 2009-10-29
Hi guys!

I have just performed and update from Jaunty, and faced some weird problems. I got the exact same thing reported here:

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/451252](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/451252)

The exact error was this one:
usplash: Setting mode 1152x864 failed usplash: Using mode 1024x768

I have also reinstalled the proprietary drivers as suggested, but still, after the white ubuntu logo, I see the usplash error but promptly I see the NVIDIA splash screen and after that there is a new ubuntu logo, but now with a loading bar which leads me to the login screen.

I feel there is still something wrong with my configs, X, i don't know... The hole boot process seems to be taking quite some time also, as there are many parts.

If you guys could please clarify me one those matters...


Thank you!

---

### Post by cristianrosa on 2009-10-30
I'am in exactly the same situation. I have no idea why usplash can't set the right resolution, I searched a lot and it seems to be a really old issue.
By the way, how log is your usplash shown? Mine shows for ~15secs, then I see the fail messages, and after that I see the new xsplash only for a few secs.

---

### Post by rey1321 on 2009-10-30
Hey Guys,
I have exactly the same error here:

Usplash: Setting mode 1152x864 failed usplash: Using mode 1024x768

this is annoying, and it seems that
the boot process take longer,

PLEASE CAN SOMEONE HELP US!!!!!!!!!!!:(


I have Nvidia drivers, Flat screen monitor 1440X900 resolution

worked perfectly in Jaunty.

HELLLLP:(

---

### Post by mrpeachy on 2009-10-30
theres a program called startup-manager which lets you configure the boot up process. one of the options on the boot options is to disable boot splash.

this might work for you. (im far from an expert, but i use startup-manager and my boot up seems to have improved)

---

### Post by Lloydus on 2009-10-31
Hi Guys,

I am experiencing a smilar usplash error on myrecent upgrade to Karmic - my post is here 

[http://ubuntuforums.org/showthread.php?t=1306849](http://ubuntuforums.org/showthread.php?t=1306849)

Usplash: setting mode 1280X1024 failed
Usplash: setting mode 1152X864 failed
Usplash: using mode 1024X768

I hope you guys find a solution because otherwise Karmic looks pretty cool.

---

### Post by cscrieciu0 on 2009-11-01
Hi all,
 I am in the same situation as rey1321. Same messages, same resolution. Problems appeared immediately after the update. I have a Dell Vostro 1700 with Nvidia Drivers.

If anyone has a clue please post.

BR
Screech

---

### Post by cscrieciu0 on 2009-11-01
Hi,
 I just found this: [http://superuser.com/questions/63586/usplash-error-after-upgrade-to-ubuntu-9-10](http://superuser.com/questions/63586/usplash-error-after-upgrade-to-ubuntu-9-10)
 I have tried the suggestion there and it works for me. I replaced 1440x900 with 1280x800 and updated ramfs. At reboot everything seems fine, and I get no error messages.

Hope it helps!
/screech

---

### Post by c4mden on 2009-11-01
thanks for the help, screech!

i ran into this exact problem after an upgrade to karmic.  i use nvidia hardware, and have a resolution of 1440x900.  after receiving the "setting mode 1152x864 failed" message, i tried booting into safe mode and editing the /etc/usplash.conf file, and issuing the update-initramfs -u command.  this did not fix the problem at all.  i tried setting 1024x768 and 1280x800, but neither fixed it.  i tried uninstalling usplash, but still no luck.  i stopped receiving the usplash error, but my screen would start flashing, and i would drop to a command prompt.

the solution ended up being downloading and installing the latest nvidia drivers from their site.  i could still boot my system if i chose the previous kernel, just not the newest, so i used that to download the nvidia driver and install it.  after that, clean boot.

---

### Post by WoesjNL on 2009-11-02
Hi there,

I seem to be having a similar problem. (HP Pavillion dv6830, Nvidia 8400M GS)
After upgrading to Karmic, no login screen appears.

At boot:
- New ubuntu splash appears
- Usplash is having trouble getting te resulution right
- Nvidia splash appears
- Screen turns black en fans keep blowing

I have tried booting without usplash,
and I've changed the usplash.conf and updated initramfs thingy :P

I'm not getting any usplash errors anymore, but still no login screen.
I can login to the recovery mode, so now I'm going to try and install the latest Nvidia driver...

*Still no luck, latest drivers succesfully installed.

---

### Post by rey1321 on 2009-11-03
According with the nvidia web site, I have the latest Driver version
which is the 96.43.13 for linux-x86

Can someone tell us if this  is  a Bug or a driver problem.
please help!!!!


Also I noticed that this problem only happens to people
who has native 1440X900 screen resolution and  upgraded from jaunty to Karmic

probably I can try changing to a lower resolution editing the usplash.conf but that's not the point
I want to use my real resolution.
please help!!!!!

---

### Post by 2TallSwede on 2009-11-04
Same error here and I've to the same problematic resolution. I haven't pursued it much until now since it's starting to annoy me.

---

### Post by RuthlessK on 2009-11-09
> **2TallSwede said:**
> Same error here and I've to the same problematic resolution. I haven't pursued it much until now since it's starting to annoy me.

Same someone must have the answer?

Never had this issue with 9.04, might have to go back.

---

### Post by jdennis_99 on 2009-11-10
I have been suffering this problem, however, I have (seemingly) been able to solve it.

First off, there has been some mention of using startup-manager to help resolve the problem.

DON'T. startup-manager also has configuration settings for GRUB, but it assumes it is working with GRUB1, or GRUB Legacy, or whatever you want to call it. I used it on my Karmic machine, which is using GRUB2, and it caused even more error messages.

I was running proprietary nVidia drivers on my machine. First step - uninstall the proprietary drivers. Restart the machine. Reinstall the proprietary drivers and restart the machine.

I have noticed that the usplash theme for Karmic only seems to work in certain resolutions as well. I set mine to 1024x768 manually by editing /etc/usplash.conf. And then did the update-initramfs -u thing.

I don't get the error messages anymore. Hope this helps.

---

### Post by manilaph on 2009-11-16
Hi.

Does anyone have a solution to this problem already?

I did a complete re-install of Ubuntu 9.10 after my first install (not an upgrade... my upgrade failed miserably) which became completely un-usable due to the errors exactly mentioned above.

i have a 19-inch monitor which uses the 1440x900 resolution and i use the Nvidia 96 drivers as suggested on previous Ubuntu version.

what should i do to make sure that this re-install doesn't get useless again?

I need a step-by-step newbie guide to avoid these errors again.

Thanks!

---

