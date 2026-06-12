---
title: "Extreme short battery life with Ubuntu 9.04"
date: 2009-05-17
forum: Hardware
---

### Post by belgianfries on 2009-05-17
I have a BenQ Joybook S73G which does about 3h on Windows XP.

With Ubuntu 9.04 it does only a bit more than one hour.

It dims the display and CPU stepping seems to work as well.

I have done the following so far:
- Enabled laptop mode
- Played with PowerTOP

Nothing seems to help.

The estimated remaining battery in gnome-power-manager seems to be very accurate. Confusing is however the power history: It is about 24W with battery and 11W with AC power. So it uses more than twice as much power on battery as on AC power?

Any suggestions?

Cheers,
Torsten

---

### Post by binbash on 2009-05-17
Tweak the configs here : cd /etc/laptop-mode/conf.d/

---

### Post by belgianfries on 2009-05-17
> **binbash said:**
> Tweak the configs here : cd /etc/laptop-mode/conf.d/

Thanks for the quick reply! I just went through all the config files and enabled all that seemed to make sense to me. Will see what difference it makes and report back.

Torsten

---

### Post by belgianfries on 2009-05-19
I spent several hours on laptop mode now, and it doesn't seem to be useful at all. The power consumption is just as high. With the exception of the first minute after switching to battery, where it is about 15W, then it goes up to 27W and stays there.

But laptop mode comes with a number of issues:
- The harddisk spins up and down all the time
- The WLan occasionally disconnects
- The System sometimes goes completely sideways with heavy CPU load and disk activity
- The System sometimes completely freezes
- The console/dmesg is bombed with the message "Polling is already disabled on the given drive."

I'll spend some more time on it and try to find out what is going on, but I am not so confident.

Does anyone have more/better experience with laptop mode?

Torsten

---

### Post by belgianfries on 2009-05-27
Just a follow-up:

I have now given up on laptop mode (tools). 

What I could find out until then:

- The harddisk spins up and down all the time
=> I was unable to get this under control. Anyway, I think it is nonsense and this seems much more reasonable: [http://live.gnome.org/GnomePowerManager/FAQ#head-e6d48e4196eb363908fb71975a5311f11f8dd9e4](http://live.gnome.org/GnomePowerManager/FAQ#head-e6d48e4196eb363908fb71975a5311f11f8dd9e4)

- The WLan occasionally disconnects
=> Might have been a conflict with Gnome Power Manager, not sure

- The System sometimes goes completely sideways with heavy CPU load and disk activity
- The System sometimes completely freezes
=> Both issues seem to have been caused by very frequent restarts of syslogd: May 26 09:05:34 linus syslogd 1.5.0#5ubuntu3: restart. (about 10 times per second). Not sure why it was doing that, maybe for the same reason as the below issue

- The console/dmesg is bombed with the message "Polling is already disabled on the given drive."
=> This seems to happen after stopping and starting/restarting laptop mode with /etc/init.d/laptop-mode: "start", "stop" and "restart" seems to be broken/not implemented

After all, laptop mode did not seem to extend the battery life, but made the system slower (disk going down and up all the time), unstable (above issues) and less comfortable due to the fact that I had to disable Gnome Power Manager since it seemed to conflict with laptop mode and I was thus lacking its convenience: The applet in the panel, the ability to suspend from the menu, the convenience to change settings in the preferences or gconf-editor instead of editing numerous config files...

So I am using  Gnome Power Manager again.

Torsten

---

