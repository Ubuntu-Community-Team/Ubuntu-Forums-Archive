---
title: "gnome power management"
date: 2008-03-30
forum: Hardware &amp; Laptops
---

### Post by midlifecrisis on 2008-03-30
I'm trying to the increase the life of my laptop battery and have been looking at the settings of the gnome power manager. I've set it to suspend when the lid is closed on ac and hibernate on battery, along with the other settings.

But when I close the lid nothing happens.

Is there some way to test that the power setting are being read and active. 

It an old sony vaio pcg z600tek with ubuntu 7.10.

---

### Post by luvit on 2008-03-30
My Short Battery Life problems are solved and I have as much control of ensuring maximum power saving using ubuntu tweak, and monitoring system activities.:)
It's easy installs direct from the webpages!
I have outlined these 3 packages in the tweaking section of my **[COLOR="RoyalBlue"][Ubuntu Blog]("http://www.yay4u.com/search/label/Tweaking")[/COLOR]**. ;)

My screen brightness and hard drive power saving settings wer optimal by default in Ubuntu.

---

### Post by midlifecrisis on 2008-03-30
I like the ubuntu tweaks app, but it's the gnome-system-monitor that I'm having trouble with, i think.

I'd like to be able to close the lid and have the laptop shutdown action depend on  whether it's on ac or battery.

---

### Post by luvit on 2008-03-30
> **midlifecrisis said:**
> I'd like to be able to close the lid and have the laptop shutdown action depend on  whether it's on ac or battery.
Go back to my link and install Ubuntu Tweak. It has a Power Management section which will help you determine if those switches are in place... that will help you determine if it's a config problem or if you need to consider other PM drivers.
Let me know if it helps!:)

---

### Post by midlifecrisis on 2008-03-31
thanks for the help but I'm not sure what you are pointing me towards. I've installed the ubuntu tweak, under power management I've ticked enable hibernation and suspend, also cpu frequency. but when I add the cpu frequency app to the task bar it tells me it's not enabled.

I've checked my bios and it set to enable os control, but still it doesn't work,I guess my kit is too old for it. One thing I have noticed is that if i set it the recommended cpu setting in the bios the laptop freezes. I guess it's getting to hot and stopping.

you mention other pm drivers, how would I get them for sony hardware?

Thanks for your help.

---

### Post by luvit on 2008-03-31
> **midlifecrisis said:**
> [SIZE=1]I've ticked enable hibernation and suspend, also cpu frequency. but when I add the cpu frequency app to the task bar it tells me it's not enabled.

I've checked my bios and it set to enable os control, but still it doesn't work,I guess my kit is too old for it. One thing I have noticed is that if i set it the recommended cpu setting in the bios the laptop freezes. I guess it's getting to hot and stopping.

you mention other pm drivers, how would I get them for sony hardware?[/SIZE]  

I'm sorry I'm not much help beyond this... you did tick what I vaguely eluded to tick. The reference I made to PM drivers is also vague... it still could be a config file issue...
[LIST]
[*] What I would do next based on my skill set: ;)[LIST]
[*]look for the latest bios update from sony for your model[LIST]
[*]this may be overkill but it's what I would do[/LIST]
[*]add "Hardware Sensors Module" to your panel[LIST]
[*]this will show you the temp of your CPU to determine overheating
[*]Rt click on Panel> Add to Panel> System & Hardware> Hardware Sensors Module[/LIST][/LIST][/LIST]

---

