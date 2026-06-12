---
title: "Ubuntu 18.04 Hibernate feature questions"
date: 2018-08-23
forum: Hardware
---

### Post by priestnot on 2018-08-23
I am using Ubuntu 18.04 on a laptop (Lenovo X1 Carbon 6th Gen).

I am trying to make it hibernate when I close the lid.

The hibernate function is working when I go to the power switch (Gnome 3 battery icon) and press alt key (it changes from the power button to a pause button).

What I what to know is how to make the same but when I close the lid. In other words I want know what command is used when I click the hibernate button the the gnome 3 "pause" button. And if it is possible to run it on lid close.

Thank you.

---

### Post by TheFu on 2018-08-23
I'm not certain, but on my 16.04 systems there is a file ... /etc/systemd/logind.conf with settings that control it.

The manpage for that file says this:```

       HandlePowerKey=, HandleSuspendKey=, HandleHibernateKey=,
       HandleLidSwitch=, HandleLidSwitchDocked=
           Controls whether logind shall handle the system power and sleep
           keys and the lid switch to trigger actions such as system power-off
           or suspend. Can be one of "ignore", "poweroff", "reboot", "halt",
           "kexec", "suspend", "hibernate", "hybrid-sleep", and "lock". If
           "ignore", logind will never handle these keys. If "lock", all
           running sessions will be screen-locked; otherwise, the specified
           action will be taken in the respective event. Only input devices
           with the "power-switch" udev tag will be watched for key/lid switch
           events.  HandlePowerKey= defaults to "poweroff".  HandleSuspendKey=
           and HandleLidSwitch= default to "suspend".  HandleLidSwitchDocked=
           defaults to "ignore".  HandleHibernateKey= defaults to "hibernate".
           If the system is inserted in a docking station, or if more than one
           display is connected, the action specified by
           HandleLidSwitchDocked= occurs; otherwise the HandleLidSwitch=
           action occurs.
```
There are other related settings in that file and described in the manpage as well.

---

### Post by priestnot on 2018-08-23
Thank you TheFu.

I have tried that solution and it does not work. the computer shutdown, or at least does not maitain the state.
I have tried with HandleLidSwitch = hibernate and HandleLidSwitch = hybrid-sleep

---

### Post by TheFu on 2018-08-23
I don't use hibernate for security reasons, but suspend options definitely work on 16.04.

Gotta ask - did you reboot before expecting it to work?  The file is only read at boot up, as part of the systemd login management process.

I suppose the DE might control those settings. I don't use a DE.

I'd guess that pm-hibernate is the command to hibernate, but don't actually know.  18.04 is too new for my needs.  The pm-hibernate manpage has a few caveats. Appears some hardware needs some extra options, if the included quirk database isn't correct for the current hardware.
```

DEBUGGING
       Debugging suspend/resume can be a tricky process, and is covered in
       more detail in /usr/share/doc/pm-utils/README.debugging.
``` according to that manpage.

Update 2: systemd has completely replaced pm-utils in 18.04, so the pm-hibernate won't work.
[https://askubuntu.com/questions/1031633/enable-hibernate-in-ubuntu-18-04-lts](https://askubuntu.com/questions/1031633/enable-hibernate-in-ubuntu-18-04-lts) says:
> 
```
sudo systemctl hibernate
```

This did not work for me. I try pm-hibernate which did not work for me either until I added missing package uswsusp
```
sudo apt install uswsusp
```

This link [http://tipsonubuntu.com/2018/04/28/change-lid-close-action-ubuntu-18-04-lts/](http://tipsonubuntu.com/2018/04/28/change-lid-close-action-ubuntu-18-04-lts/)  basically says to use pm-utils, which is deprecated, but it does mention some checks that may not be true for all systems.

---

