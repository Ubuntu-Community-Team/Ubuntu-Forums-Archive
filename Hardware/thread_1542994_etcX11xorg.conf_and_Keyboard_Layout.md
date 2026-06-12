---
title: "/etc/X11/xorg.conf and Keyboard Layout"
date: 2010-07-31
forum: Hardware
---

### Post by ldupont on 2010-07-31
I'd like to change the keyboard layout preferences on a user basis. Looking around, it seems that the keyboard preferences are stored within /etc/X11/xorg.conf thus implying that the keyboard preferences are common to all users on a given computer. Is this correct?

Given that's the case; there's still something I don't get. There's no /etc/X11/xorg.conf on my Ubuntu 10.04 installation. Apparently, X.org doesn't use xorg.conf by default anymore but try to recognize everything automatically. However, if xorg.conf is created it will be used.

I'm actually running a Virtual Machine found on the Internet ([http://www.quotrader.org/vm/ubuntu1004t](http://www.quotrader.org/vm/ubuntu1004t)). I guess that the people at
quotrader.org are from Germany and defined the default keyboard configuration on their installation as German. How exactly would X.org recognize me as German? Is has to be set somewhere but I can't find it.

Thanks

---

### Post by simosx on 2010-07-31
The xorg.conf way is the obsolete way to configure the keyboard layout.
If you see anyone still talking about 'xorg.conf', please tell them it's obsolete.

Go to System/Preferences/Keyboard and switch to the Layouts tab. There you set the layouts per user.

You can also do this programmatically, using the command

gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

(this reads the settings). 

Google with that command to find how to set the settings.

---

### Post by ldupont on 2010-08-01
Thanks,

Not exactly what I wanted to do but it gave me a clue as to where the keyboard layout configuration is stored (~/.gconf/desktop/gnome/peripherals/keyboard/kbd/%gconf.xml). So I tried :

sudo mkdir -p /home/$lUserName/.gconf/desktop/gnome/peripherals/keyboard/kbd
sudo cp %gconf.xml /home/$lUserName/.gconf/desktop/gnome/peripherals/keyboard/kbd/%gconf.xml
sudo chown -R $lUserName /home/$lUserName/.gconf
sudo chgrp -R $lUserName /home/$lUserName/.gconf
sudo chmod -R 700 /home/$lUserName/.gconf

but I had no sucess. Among other things, it appears that I'm affected by the following bug :

[https://bugs.launchpad.net/ubuntu/+s...er/+bug/591895](https://bugs.launchpad.net/ubuntu/+s...er/+bug/591895)

So basically my question is where is the default system keyboard layout stored?

---

### Post by simosx on 2010-08-01
You do not edit the files in ~/.gconf/; these files are controlled by the gconfd service. You use gconftool so that you ask the gconfd service to make any changes.

Your first choice however would be to go to the Keyboard preferences and set the layout there. It's in the Layouts tab.

---

### Post by ldupont on 2010-08-01
As reported by [https://bugs.launchpad.net/ubuntu/+s...er/+bug/591895](https://bugs.launchpad.net/ubuntu/+s...er/+bug/591895), every time I remove the Deutsch keyboard in the layout tab of System/Preferences/Keyboard, the Deutsch configuration reappears as I logout/login. Moreover, the key combination I choose to switch between configurations is overridden. As far as gconftool is concerned, there's no Deutsch keyboard configuration :

$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [ca	multix,ca	eng,de]
 options = [lv3	lv3:ralt_switch,grp	grp:ctrl_shift_toggle]

while it reappeared in the layout tab. Thanks

---

### Post by simosx on 2010-08-02
> **ldupont said:**
> As reported by [https://bugs.launchpad.net/ubuntu/+s...er/+bug/591895](https://bugs.launchpad.net/ubuntu/+s...er/+bug/591895), every time I remove the Deutsch keyboard in the layout tab of System/Preferences/Keyboard, the Deutsch configuration reappears as I logout/login. Moreover, the key combination I choose to switch between configurations is overridden. As far as gconftool is concerned, there's no Deutsch keyboard configuration :

$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [ca	multix,ca	eng,de]
 options = [lv3	lv3:ralt_switch,grp	grp:ctrl_shift_toggle]

while it reappeared in the layout tab. Thanks

The gconftool output above show that you have three keyboard layouts enabled,
1. Canadian Multilingual
2. Canadian English (which is an alias for US English)
3. German (it's the 'de')

In addition, there are several layout options enabled.

I have read several posts that talk about layout options not being remembered during reboots (or logout+login).
I did not manage to find the cause; if it happened to my computer, I'll be able to try to figure it out.

In an Alpha version of Ubuntu 10.04 you had this problem with the layout settings, though I believe you do have the final 10.04. Confirm?

If the file /etc/X11/xorg.conf exists, then it takes precedence over the desktop settings. I believe you did not create such a file, as it does not exist anyway in 10.04.

What would be good to see is before and after examples of the output of gconftool-2.

---

