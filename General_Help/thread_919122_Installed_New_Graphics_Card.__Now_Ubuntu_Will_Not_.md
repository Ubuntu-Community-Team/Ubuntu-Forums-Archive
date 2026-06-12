---
title: "Installed New Graphics Card.  Now Ubuntu Will Not Start."
date: 2008-09-13
forum: General Help
---

### Post by umechanism on 2008-09-13
I have a 9 year old Compaq Presario 5000 running Ubuntu 8.04 and it runs it quite well.  I acquired a used "Nvidia Quardro NVS with AGP8X" and installed it.  Here are the steps that occurred upon starting up after installation:

[LIST=1]
[*]Ubuntu booted and let me know that restricted drivers were available.
[*]I installed restricted drivers.
[*]Rebooted Ubuntu.
[*]Noticed screen was grainy.
[*]Went to Preference>Screen Resolution but could not set higher than 1024 x 768 at 54 HZ.
[*]Decided to remove restricted drivers so I clicked the icon and disabled it.
[*]Rebooted Ubuntu (as required).
[*]Splash screen came up but the orange line never made it all the way from left-to-right.
[*]Screen went dark then flashed the below message:
[/LIST]

> Starting Up
Loading, please wait...
usplash:  Setting mode 1152 x 864 failed
usplash:  Using mode 1024 x 768
kinit:  name_to_dev_t(/dev/disk/by-uuid/994859493050-54rrfff..
da5(8,5)
kinit:  trying to resume from /dev/disk/by-uuid/994859493050-54rrfff..
af8
kinit:  no resume image, doing normal boot...

Ubuntu 8.04.1 Michael-ubuntu tty1
Michael-ubuntu Login:

Then, after the last line prompting for a login appears, the screen goes black and becomes non-responsive.  I have to manually power down.

Any ideas what is going on here?

Thanks,
Mike

---

### Post by fragos on 2008-09-13
It looks like X couldn't start which would normaly mean a video driver problem. My guess is that your card may require the "nvidia-glx-legacy" driver instead of the "nvidia-glx-new" that was probably installed. Basicaly when X fails to start you end up in terminal mode. The prompt you had above was asking you to login and expected your password. after enetering it operation would be command line. What you probably need to do now is edit /etc/X11/xorg.conf.

After loging in run "sudo nano /etc/X11/xorg.conf". If asked for password, enter yours again. The bottom of the screen shows you the commands for this editor. All cursor movements must be made with the keyboard. You want to look for a group of lines like these.

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

You want the driver to be "vesa" which shoulkd allow us to restart in graphics mode. Vesa will work for any video card but won't support the extra features of that card.

---

### Post by umechanism on 2008-09-14
Thank you for the reply.  Considering that the card itself is five or six years old, legacy drivers are probably the ones I need.  I'm using XP now and the card is working just fine for it.  I'll try your suggestion after coffee in the morning.

I'll post back the results.

Thanks!

---

### Post by Neo_The_User on 2008-09-14
I never found editing the xorg.conf file useful at all with any of my video problems. I always have to do something really stupid to get it working again like ERASING the xorg.conf file and all its backups (except ubuntu hides the xorg.conf files somewhere else)

I always download the drivers directly from the manufacturer's website because it always comes with some typeof control panel to adjust your display settings.

---

### Post by fragos on 2008-09-14
Editing xorg.conf is a last resort that may be required when X won't start. I recommend against editing xorg to configure for Nvidia cards. I read many posts on people getting themselves into trouble by not using the Ubuntu provided drivers and the standard instalation tools. No doubt these other methods can work and were required years ago. Installing a driver without using the debia package management leaves the system unaware of its existance and subject future installation or upgrade complications.

---

### Post by umechanism on 2008-09-14
Editing the Xorg file did not work.  However, I booted into safe mode and selected "Repair X11 server" from the menu that appeared.  Doing so repaired the driver problem and now Ubuntu boots fine.  I'm not sure what was repaired or why it worked but it did work for me.

Thanks for the help.

Cheers.:popcorn:

---

### Post by fragos on 2008-09-14
Haven't had to use safe mode in a long time. It didn't use to have that menu. The best way to fix issues with Ubuntu is to use the tools they provide. Some changes require multiple commands adjusting things in more than one place in the system. Ubuntu functions, mostly GUI, make all the changes with a single action on your part. Each new release of Ubuntu improves how well the system automatically does things for you. Glad it all worked out for you. You may not know what was done but now you do know how to handle this and perhaps other situations.

---

### Post by umechanism on 2008-09-14
Ubuntu could simplify this particular menu to make it more apparent as to what the "fix" was.  The menu stated to "Repair X11 Server".  That's not very helpful to a noob.  Perhaps, "Automatically Repair Graphics Issues" would have led me to try it before posting my problem.  Ubuntu is good but it is still a bit geeky around the edges.

Getting better all the time.:KS

---

### Post by fragos on 2008-09-15
No doubt it's learning to speak like a user. Progress continues in that direction. Your assessment in this case is on target. You can file a bug report and this excellent change will be considered.

---

