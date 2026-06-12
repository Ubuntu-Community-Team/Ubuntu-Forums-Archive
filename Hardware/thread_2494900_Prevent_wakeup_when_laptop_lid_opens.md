---
title: "Prevent wakeup when laptop lid opens"
date: 2024-01-30
forum: Hardware
---

### Post by siersmak on 2024-01-30
Hello, I would like to prevent wakeup from suspend when my laptop lid opens. I'm running 22.04.  I have seen in many places on the internet - usually in reference to older versions of Ubuntu - that you can toggle this in /proc/acpi/wakeup, and it seems that usually the device name in that file for the laptop lid is "LID" or "LID0".  No such device of that name exists in my /proc/acpi/wakeup.  I've also gone through and one by one disabled every device that is listed as enabled in /proc/acpi/wakeup to try to determine if one of the devices I can't identify corresponds to the lid, but I have not been successful in figuring out which device is the lid, if any.  

Does anyone know how to prevent wakeup from suspend on 22.04?  Or, does anyone have any pointers on how I can troubleshoot this?

Thank you

---

### Post by #&amp;thj^% on 2024-01-30
Have you looked in " /etc/systemd/logind.conf"?
They have made this near impossible to help everyone and all hardware.
```
tac  /etc/systemd/logind.conf | grep HandleLidSwitch
#HandleLidSwitchDocked=ignore
#HandleLidSwitchExternalPower=suspend
#HandleLidSwitch=suspend

```
There is more to that file so read it completly

Mine just works on XFCE4.

---

### Post by MAFoElffen on 2024-01-30
> **siersmak said:**
> Hello, I would like to prevent wakeup from suspend when my laptop lid opens. I'm running 22.04. 
As 1fallen mention with his being on "XFCE4"... You did not mention which desktop you are using. For Gnome based, that would be different.

It is possible by disabling recognizing the lidswitch signal, but that comes at a cost, and can get complicated real fast.

So that points to the "why" you want to do that... And to weigh whether the cost of what that means will satisfy and add value to what you what to do. Does that make sense?

I can blurt out an answer to that, but it might lock you out of your system if it goes into suspend or to sleep... Because it would not receive a signal to wake, unless that was added elsewhere. Such as changing it to accept some other input to wake from.

---

### Post by siersmak on 2024-01-30
> **1fallen said:**
> Have you looked in " /etc/systemd/logind.conf"?
They have made this near impossible to help everyone and all hardware.
```
tac  /etc/systemd/logind.conf | grep HandleLidSwitch
#HandleLidSwitchDocked=ignore
#HandleLidSwitchExternalPower=suspend
#HandleLidSwitch=suspend

```
There is more to that file so read it completly

Mine just works on XFCE4.

Thank you.  Yes, I did look into logind.conf, and since you pointed me to it I've looked into it more closely.

I added a file to /usr/lib/systemd/logind.conf.d that contains the following lines:

```
[Login]
# trying to prevent waking up from suspend when laptop lid is opened
HandleLidSwitchExternalPower=ignore
HandleLidSwitch=ignore
```

And I then restarted systemd with ```
sudo systemctl daemon-reload
```

But, it still wakes up from suspend when I open the lid.

---

### Post by siersmak on 2024-01-30
> **MAFoElffen said:**
> As 1fallen mention with his being on "XFCE4"... You did not mention which desktop you are using. For Gnome based, that would be different.

It is possible by disabling recognizing the lidswitch signal, but that comes at a cost, and can get complicated real fast.

So that points to the "why" you want to do that... And to weigh whether the cost of what that means will satisfy and add value to what you what to do. Does that make sense?

I can blurt out an answer to that, but it might lock you out of your system if it goes into suspend or to sleep... Because it would not receive a signal to wake, unless that was added elsewhere. Such as changing it to accept some other input to wake from.

Thank you.  

The desktop - good point.  I am using Gnome Flashback (Metacity).

The reason I am trying to disable recognizing the lidswitch signal is that my laptop is poorly designed in that it opens very easily and it opens when it's in my bag.  It then stays on, despite that I have the power settings set to automatically suspend when on battery in Gnome's system settings, until the battery is exhausted and it dies.  So I basically have two problems, and I'm pursuing getting it to stop waking up when the lid opens first.  

I'm operating under the assumption that I should be able to ignore the lid switch, but not ignore waking up with keyboard presses or by tapping the power button.  Of course I will make sure that I can do that before I configure a permanent fix.

---

### Post by MAFoElffen on 2024-01-30
Try this to try to get systemd to control the events:
```

sudo sed -i 's/#HandleLidSwitch=suspend/HandleLidSwitch=ignore/g' /etc/systemd/logind.conf
sudo sed -i 's/#HandleLidSwitchExternalPower=suspend/HandleLidSwitchExternalPower=ignore/g' /etc/systemd/logind.conf
sudo sed -i 's/#HandleLidSwitchDocked=ignore/HandleLidSwitchDocked=ignore/g' /etc/systemd/logind.conf
sudo systemctl daemon-reload

```
Then the only input devices with the "power-switch" udev tag will be watched for key/lid switch events...

But other applications may still intervene with that and try to assign lower-level overrides to that. But we shall see, right? That would mean you would also have to set the User's gsettings dconf db setting for the lidswitch to ignore.

But since the lidswitch will be ignored, that also means it will not go into suspend or hibernation until you put it into that state manually via the commandline or via the power off menu.

---

### Post by siersmak on 2024-01-30
> **MAFoElffen said:**
> Try this to try to get systemd to control the events:
```

sudo sed -i 's/#HandleLidSwitch=suspend/HandleLidSwitch=ignore/g' /etc/systemd/logind.conf
sudo sed -i 's/#HandleLidSwitchExternalPower=suspend/HandleLidSwitchExternalPower=ignore/g' /etc/systemd/logind.conf
sudo sed -i 's/#HandleLidSwitchDocked=ignore/HandleLidSwitchDocked=ignore/g' /etc/systemd/logind.conf
sudo systemctl daemon-reload

```
Then the only input devices with the "power-switch" udev tag will be watched for key/lid switch events...


Well, that's essentially the same thing I said I tried in my response to 1fallen, except I made my own file in /usr/lib/systemd/login.conf.d, which is the systemd recommended method of doing such a thing.  Nevertheless I tried it your way too, with 'sudo systemctl daemon-reload', but it still wakes up when opening the lid. 

> 
But other applications may still intervene with that and try to assign lower-level overrides to that. But we shall see, right? That would mean you would also have to set the User's gsettings dconf db setting for the lidswitch to ignore.

But since the lidswitch will be ignored, that also means it will not go into suspend or hibernation until you put it into that state manually via the commandline or via the power off menu.

Yep, I have the lidswitch set to ignore in dconf as well.

---

### Post by #&amp;thj^% on 2024-01-30
Dang I told you they have made this next to impossible, What make and model is your lappy?

---

### Post by siersmak on 2024-01-30
> **1fallen said:**
> Dang I told you they have made this next to impossible, What make and model is your lappy?

Yep, it seems that way.  The laptop I'm testing this on is an HP ENVY 16-h1055c1.  This laptop technically isn't the one that opens when it's in my bag, it's the laptop I'm testing this functionality on before I pursue implementing it on the actual problem child - a VAIO S13-VJS132C11L (NOT a sony vaio).

---

### Post by #&amp;thj^% on 2024-01-30
Well I might have you going down another rabbit hole but we've tried almost everything but your Bio's: [https://community.frame.work/t/bios-guide/4178](https://community.frame.work/t/bios-guide/4178)

---

### Post by siersmak on 2024-01-30
> **1fallen said:**
> Well I might have you going down another rabbit hole but we've tried almost everything but your Bio's: [https://community.frame.work/t/bios-guide/4178](https://community.frame.work/t/bios-guide/4178)

I had the exact same idea and was kicking myself when I found there is an Auto Resume option that was set to Enabled.  The BIOS help area says "This feature automatically turns on the system by opening the lid when the computer is in a Hibernation state".

So I enabled hibernation successfully on the HP and tried disabling the Auto Resume option.

Now, when I hibernate and close the lid, it does NOT come back on when I open the lid.  That's something.

It makes no difference for Suspend.  Still comes back on after closing and reopening the lid.  So that seems to indicate that Ubuntu is controlling this, not the BIOS.

At some point I'll check the BIOS on the VAIO, but that's a tough ask because the user of it always has a million things open and is pretty resistant to reboots, ugh...

---

### Post by #&amp;thj^% on 2024-01-30
LOL Possible bug? I would file one  just in case.

---

### Post by siersmak on 2024-01-30
> **1fallen said:**
> LOL Possible bug? I would file one  just in case.

I suppose, but I'm thinking since it specifically says Hibernate and it works with Hibernate but not Sleep that it's not a bug.

---

### Post by #&amp;thj^% on 2024-01-30
Well this one is bit hard to triage, but it's up to you.

Brainstorm, tie a bungee around Vaio when it's in your backpack.....LOL

---

### Post by MAFoElffen on 2024-01-30
Large rubber band?

---

### Post by siersmak on 2024-01-30
Sure, yes :)  Just hoping for a long term permanent solution.  There has to be a way.

---

### Post by MAFoElffen on 2024-01-30
I found something that might work... I didn't test it. but...

'powertop2tuned' is prvided by Ubuntu package 'tuned-utils'
```

sudo apt install tuned-utils

```
RE: 
[https://www.reddit.com/r/gnome/comments/evbz3u/ignore_lid_switch/](https://www.reddit.com/r/gnome/comments/evbz3u/ignore_lid_switch/)

Pertinent Man Pages:
[https://manpages.ubuntu.com/manpages/jammy/man8/powertop.8.html](https://manpages.ubuntu.com/manpages/jammy/man8/powertop.8.html)
[https://manpages.ubuntu.com/manpages/jammy/en/man7/tuned-profiles.7.html](https://manpages.ubuntu.com/manpages/jammy/en/man7/tuned-profiles.7.html)

Worth a try?

---

