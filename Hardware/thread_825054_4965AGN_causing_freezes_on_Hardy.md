---
title: "4965AGN causing freezes on Hardy"
date: 2008-06-10
forum: Hardware
---

### Post by carl.davis on 2008-06-10
I have a wireless card reported as:

iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.25

My system freezes requiring a hard reboot when using the wireless especially when I try to use rdesktop. I currently think this might be related to the wireless card since because I used my laptop all day yesterday with Ethernet only and suffered no problems. Today on wireless it has locked up 10-15 times. I finally switched back to Ethernet and have not had a lock up issue since then.

---

### Post by stchman on 2008-06-10
> **carl.davis said:**
> I have a wireless card reported as:

iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.25

My system freezes requiring a hard reboot when using the wireless especially when I try to use rdesktop. I currently think this might be related to the wireless card since because I used my laptop all day yesterday with Ethernet only and suffered no problems. Today on wireless it has locked up 10-15 times. I finally switched back to Ethernet and have not had a lock up issue since then.

Sounds like a hardware problem.

I use hardy on my 4965 equipped laptop and it works very well.  Now by lockup do you mean the OS locks up or the app like Firefox locks up?

---

### Post by carl.davis on 2008-06-10
The CAPS lock key flashes and I have to hold in the power button type of lock up. I am running:

Linux ubuntu-laptop 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 i686 GNU/Linux

Is there some way to log a kernel panic so I can restart and see what the kernel is so unhappy with?

---

### Post by hotweiss on 2008-06-10
Try enabling the backport repositories, run an update and reboot.

---

### Post by Bartender on 2008-06-10
> **stchman said:**
> I use hardy on my 4965 equipped laptop and it works very well.

Second that.

---

### Post by jblackthorne on 2008-06-10
The Intel 4965AGN chip is probably the most common wireless chip on the market today.  Hence, it does indeed work with Linux.  In fact, I am using that very chipset againt a DLink DIR-655 router right now with flawless performance (in 802.11G). With that said, the 4965AGN linux driver version 2.0 that ships with Hardy has some well known limitations (and a number of bugs waiting in Intel's Launchpad queue).  Without any details, my best guess is that you are experiencing either router setup or router incompatibility issues.

As of version 2.0 of the iwl4965AGN linux driver, here are highlights of issues:

* Does not support the full "wi-fi Certification specification yet resulting in compatibility problems with a lot of older and off brand routers.
* 802.11n mode does not work at all (only b and g)

With the above in mind, my first questions are:
1. What brand and model router are you using?
2. Is it a newer major brand and listed as a wi-fi certified model?
3. What type of encryption are you using? WEP, WPA, WPA2, etc. 
4  Have you tested with encryption off to rule that out?
5. Have you updated your router to the latest firmware?
6. What 802.11 band are you trying to use, A, B, G, or N?
7. Have you validated that your router is not competing with other routers on the same channel?  Have you tried to change the channel?

[http://www.wi-fi.org/](http://www.wi-fi.org/)

Next, let's troubleshoot and look for error details:

Please provide the following output:
* sudo dmesg | grep iwl
* cat ~/.xsession-errors

---

### Post by carl.davis on 2008-06-11
> **jblackthorne said:**
> 

As of version 2.0 of the iwl4965AGN linux driver, here are highlights of issues:

* Does not support the full "wi-fi Certification specification yet resulting in compatibility problems with a lot of older and off brand routers.
* 802.11n mode does not work at all (only b and g)


I was using a D-Link DI-524 but did not think to replace it because I had been using it for years without any problems. I turned off WPA and still got a lock up. I replaced it with a Linksys BEFW11S4 with 128 bit WEP and have not had a lock up issue yet. I will post back with the other trouble shooting details you've asked for if I have problems again. I also need to track down another WPA capable router and see if that causes any problems, however I have high suspicions that it will be fine. Thanks!

P.S. I love it when it turns out that Ubuntu was correct and it was someone/something else's fault all along!

---

### Post by carl.davis on 2008-06-11
I used the wireless at my other office which is WPA and worked fine for two hours. I started an rdesktop session and not long (seconds) after getting connected and authenticated my machine locked up with the CAPS lock blinking again. I am going to turn off WPA and enabled 128 bit WEP and opening an rdesktop session locks up my laptop. It worked all morning with lots of rdesktop sessions running and had no problems while using the Ethernet port.

 ```
sudo dmesg | grep iwl
[   27.833922] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[   27.833924] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   28.229742] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   28.525491] iwl4965: Tunable channels: 11 802.11bg, 13 802.11a channels
[   28.525749] wmaster0: Selected rate control algorithm 'iwl-4965-rs'


```

```
cat ~/.xsession-errors
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/ubuntu-laptop:/tmp/.ICE-unix/6420
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
Shutdown failed or nothing to shut down.
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
Window manager warning: Failed to read saved session file /home/cdavis/.metacity/sessions/default0.ms: Failed to open file '/home/cdavis/.metacity/sessions/default0.ms': No such file or directory
ERROR: trackerd already running on your session dbus - exiting...
11
Initializing nautilus-share extension
evolution-alarm-notify-Message: Setting timeout for 16142 1213228800 1213212658
evolution-alarm-notify-Message:  Wed Jun 11 19:00:00 2008

evolution-alarm-notify-Message:  Wed Jun 11 14:30:58 2008

seahorse nautilus module initialized

** (nautilus:6532): WARNING **: Unable to add monitor: Not supported
  PID TTY          TIME CMD
 6512 ?        00:00:00 pulseaudio

(gnome-terminal:6549): Vte-WARNING **: No handler for control sequence `device-control-string' defined.

```

---

### Post by jblackthorne on 2008-06-11
You dmesg and X11 logs look fine.  I asked for those because sometimes the mac8011 subsystem used by the iwl4965 driver can throw errors interfacing with the kernel.  If you don't see anything in the kernel ring buffer (dmesg), then this is not a driver dump or any other kind of malfunction.

You are correct in that this error has nothing to do with Ubuntu.  These problems fall squarely onto the shoulders of Intel.  Some major compatibility bugs have been open against Intel for over a year!  

There is no point in messing with backports like the other poster suggested.  The mac80211 is compiled into the kernel.  There are no package upgrades.  However, as of the current Hardy kernel (I forget the exact revision), it is now possible to upgrade the iwl4965 driver without recompiling the kernel if you want to give that a try. (disregard most howto's out there as they are out of date.)

[http://intellinuxwireless.org/?n=Downloads](http://intellinuxwireless.org/?n=Downloads)

I have gone on sort of a quest in regards to this topic. I had an older major label DLink router that worked great for years two.  However, it did all kinds of funky things with this Intel wireless chip.  I even compiled custom kernels to try out new drivers and options. After a month of trial and error, I just gave up and bought a new router that supports the latest WPA2 spec, the Dlink DIR-655 I mentioned.  This new router never drops, gets 2mb/sec throughput even with WPA2, and works great all the way around.  

In summary, new hardware seems to be well supported and works well with the Intel iwl4965.  However, older hardware is very hit and miss.  Maybe we should start a iwl4965 router compatibility page?   Good luck in your diagnostics.  If you learn anything new or have any luck, please let us know.

Edited to add:
My mistake, the current kernel, 2.6.24.x cannot be upgraded with the Intel drivers on that web site.  I will investigate where we can obtain updates now and report back later.

---

### Post by jblackthorne on 2008-06-11
After a little research, I found that Intel has joined the Linux compat-wireless project.  This is fantastic news and definitely a ray of hope for the iwlwifi driver!  The other great news is that it is now very easy to try out driver upgrades.  There is no need to compile kernels or do anything complicated.  Best of all, if the drivers do not work out, they are easy to uninstall.  The only requirement is that you must be running kernel 2.6.24.x.  For Ubuntu users, this means you must have Hardy Heron.

I went ahead and tried out the latest bleeding edge daily package which gave me:

iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.26k

The good news is that this new driver installed in about 5 minutes and worked right away.  I have to admit, I was surprised this went so easily.  After running for 3 hours, no dropping, errors in dmesg, or any indication of other new problems.  I have no idea if this will help the poster with his problems.  Though, this might be worth a try.  You can download the package and instructions here:

[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

Note: Just wanted to confirm that 802.11n is still not working.  However, I did get an error message on make complaining about CONFIG_NETDEVICES_MULTIQUEUE.  This is a kernel flag set at the time of kernel compile.  Still, I am curious and might go ahead and try a new kernel build to see what happens.  My 802.11n finding are confirmed with this bug:

[http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1680](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1680)

Good luck poster.  Hopefully something works for you!

---

### Post by kencrudup on 2008-06-11
I've been using the compat-wireless 4965 drivers since I got this new laptop. FWIW, you don't have to be running 2.6.2**4**.X kernels, I build the stock kernels and am currently running 2.6.25.6 .

If you're having issues with authentication on WPA/WPA2, try upgrading first. I couldn't get anywhere until I did this.

---

