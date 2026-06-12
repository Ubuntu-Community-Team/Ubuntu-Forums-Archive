---
title: "Battery critical shutdown not working?"
date: 2007-12-10
forum: Hardware &amp; Laptops
---

### Post by Pichu0102 on 2007-12-10
I'm at 3% battery right now, and I've gotten no notification or anything that the battery is low. My computer is about to die without shutting down.

I have an Inspiron E1705 if that helps. Also running 7.10.

Gotta go quickly, sorry for little info

---

### Post by MoToR on 2007-12-11
Same problem here.

IBM ThinkPad X20, relatively fresh Ubuntu 7.10, yesterday I worked on my laptop till only %1 of battery charge left, but I had got no notification, no Hibernate (as configured in Power Management window). I didn't want to take risks and plugged a power cord in.

Today I decided to try it to the end to know if I can trust the power management to Hibernate the laptop when the battery gets critical. After almost an hour on %1 of battery charge my laptop just "died" suddenly, no beep, no notification, no Hibernate, just an hdd click, spinning down sound and silence.

Expecting such an end I wasn't doing anything serious on the laptop when it lost its power, so I didn't lose any data of mine. But there was a terminal window open and a File Browser window open; being new to Linux and experienced with Windows I'd like to ask - should I take any system/file system maintenance steps after such sudden power loss like in Windows running "chkdsk". Can there be any orphaned files left? Any damage to file system or OS data loss?

I ran "sudo shutdown -r -F now", is that sufficient?

Thanks in advance.

---

### Post by MoToR on 2007-12-13
OMG, is this the famous crowded with Linux geeks ubuntu forum, or should I turn my phishing filter back on?

Guys? Anyone could spill some light at least at the partition maintenance part of the question please?

---

### Post by sevcsik on 2008-03-11
Hi, I have exactly the same problem with a Clevo notebook. It's kinda annoying, that my notebook just powers off. No hibernating, even no warning.

You can do filesystem check with fsck, but it can check only unmounted partitions so it has to be run on boot, or from a liveCD. I think ubuntu checks the filesystems on boot if nessecary.

---

### Post by prelude on 2008-03-11
I have the same problem with my HP Pavilion.
Fresh-ish install of ubuntu and it just stays on until it dies.

It is set to shutdown when the battery is critically low but so far all Ive ever seen happen is a text bubble on the battery applet saying the battery is critically low and I have three minutes until shutdown, which never happens.

On the bright side, due to this this laptop has set new records in how long it lasts on battery power, where it used to live for one hour and twenty minutes tops on windows 2000/xp it now lasts for more than three hours :biggrin:

---

### Post by egooey on 2008-03-20
any solution yet? I'm having the same problem and yeah i'm new to ubuntu :)

---

### Post by sayakb on 2008-03-20
Looks like a gpm bug.. Same problem here, with a little difference that frequent "dying" of the laptop has gifted me a special tendency.. the battery doesn't begin charging when the charge goes below 10% each time (yesterday, even at 42%, it wasn't charging. So I had to pull it off from my laptop and charge it with my dad's laptop which has Vista (yeah, same models)

---

### Post by Ace_NoOne on 2008-03-21
I'm having the same problem with my HP Compaq 2510p.
When the battery ran empty this morning, I got no warning whatsoever, resulting in a hard shutdown - not pretty!

I've [read]("http://litenverden.org/?p=12") about the following script to read out the battery status:
```
echo `hal-device | grep charge_level.percentage | awk '{print $3}'`%
```
But there must be a better (GUI-y) way... !?

**Update:**
I've added the Battery Charge Monitor applet to my panel, and it seems I do get warnings now.
More testing is required, but this might be worth having a second battery/AC indicator there (in addition to the one in the notification area)...

---

### Post by Hero of Time on 2008-04-01
I don't use Gnome, I run Xfce. In my panel, I also have a battery applet. I set it to warn me when it reaches 10%, does that just fine. I also set it to display a message when it's on critical, 4%, just fine. When I change the critical message to the command 'hibernate', it does not work. I noticed that when I saw my battery indicator flashing red, meaning it's below 6% (it was at 2% when I noticed the led flashing). It displayed the critical message just fine, but it never went to hibernate. I quickly plugged in the power cord so it would charge as I intended.
When I run 'hibernate' from a terminal, I get the error that I have to run it as root. This is very strange, as I can shutdown, reboot, and hibernate from the quit window. In windows, any user can shutdown, reboot and hibernate, why not on Linux. You have to run things as root do be able to either shutdown, reboot or hibernate. This is ridiculous. I think this is also why the gnome power management fails, it probably runs as user instead of root. Then why it works on KDE as it should, I have no idea, perhaps that does run as root.

---

### Post by Ace_NoOne on 2008-04-02
> **Hero of Time said:**
> In windows, any user can shutdown, reboot and hibernate, why not on Linux. You have to run things as root do be able to either shutdown, reboot or hibernate. This is ridiculous.
That's probably because *nix is used a lot for servers - imagine any user SSH'ing into your server could shut it down...

---

### Post by Hero of Time on 2008-04-02
> **Ace_NoOne said:**
> That's probably because *nix is used a lot for servers - imagine any user SSH'ing into your server could shut it down...

You got a point there, but on a work station, why do you have to be root to shutdown the computer from terminal, if you can shut it down using the GUI? That doesn't make sense.
Anyway, does anyone know how I can run the hibernate script that I call from the battery applet as normal user?

---

### Post by Hero of Time on 2008-04-03
I got a sort of workaround for my problem. I added my username to the sudoers file with the option ALL=NOPASSWD:/usr/sbin/hibernate and it works if I type 'sudo hibernate' in a terminal. This should also happen when my battery is running low.
Perhaps this can help with the problem that is discussed here with the Gnome Power Management. Run it with root privileges, or let the commands run with root privileges.

---

### Post by hihihi on 2008-06-21
I never had to change the permission of my hibernation script to hibernate with hotkeys, eventhough I had to configure those keys by myself (sony-laptop) everything works just fine... 
of course I still need sudo to call hibernation from terminal, and you want it to be like this.
better not play around with your permission-settings,
that is most likely NOT your true problem.
your problem is somewhere around acpi, perhaps some configuration-file is not configured correctly, or not enabled at all.



I am having the same problem with my new laptop (sony vaio fz31m).
gpm gives out battery-critical-low warning, so it is working correctly.
hibernation is working correctly too.
but nevertheless it wont hibernate on critical level.
so we need to change the laptop-mode settings.

1.) first of all make sure laptop-mode is enabled on battery (not default)

$ sudo gedit /etc/default/acpi-support

	set line “ENABLE_LAPTOP_MODE” to “true”


from now on this will work automatically after restarting system, once you're on battery, laptop mode is activated.

to activate without restart on the fly:

	$ sudo laptop_mode start

2.) now you need to edit laptop-mode-tools:

$ sudo gedit /etc/laptop-mode/laptop-mode.conf

set the
"Disable all data loss sensitive features"-option when the battery level to 1%:

MINIMUM_BATTERY_CHARGE_PERCENT=1

to enable auto-hibernation (hibernate on battery critical-low):

ENABLE_AUTO_HIBERNATION=1

HIBERNATE_COMMAND=/etc/acpi/hibernate.sh (this is my working hibernation script, point it to the script that works for you)

AUTO_HIBERNATION_BATTERY_CHARGE_PERCENT=3 (this value has to be higher than the "MINIMUM_BATTERY_CHARGE_PERCENT"-value and has to give your battery enough time to hibernate)

I hope this helps anybody searching for the answer.
cheers

---

### Post by damis648 on 2008-06-27
> **hihihi said:**
> I never had to change the permission of my hibernation script to hibernate with hotkeys, eventhough I had to configure those keys by myself (sony-laptop) everything works just fine... 
of course I still need sudo to call hibernation from terminal, and you want it to be like this.
better not play around with your permission-settings,
that is most likely NOT your true problem.
your problem is somewhere around acpi, perhaps some configuration-file is not configured correctly, or not enabled at all.



I am having the same problem with my new laptop (sony vaio fz31m).
gpm gives out battery-critical-low warning, so it is working correctly.
hibernation is working correctly too.
but nevertheless it wont hibernate on critical level.
so we need to change the laptop-mode settings.

1.) first of all make sure laptop-mode is enabled on battery (not default)

$ sudo gedit /etc/default/acpi-support

	set line “ENABLE_LAPTOP_MODE” to “true”


from now on this will work automatically after restarting system, once you're on battery, laptop mode is activated.

to activate without restart on the fly:

	$ sudo laptop_mode start

2.) now you need to edit laptop-mode-tools:

$ sudo gedit /etc/laptop-mode/laptop-mode.conf

set the
"Disable all data loss sensitive features"-option when the battery level to 1%:

MINIMUM_BATTERY_CHARGE_PERCENT=1

to enable auto-hibernation (hibernate on battery critical-low):

ENABLE_AUTO_HIBERNATION=1

HIBERNATE_COMMAND=/etc/acpi/hibernate.sh (this is my working hibernation script, point it to the script that works for you)

AUTO_HIBERNATION_BATTERY_CHARGE_PERCENT=3 (this value has to be higher than the "MINIMUM_BATTERY_CHARGE_PERCENT"-value and has to give your battery enough time to hibernate)

I hope this helps anybody searching for the answer.
cheers

Thank you very much! I was scared because i was receiving no warning as to low battery life so i added the applet, and with your guide, auto-hibernation now works! Thanks!

---

