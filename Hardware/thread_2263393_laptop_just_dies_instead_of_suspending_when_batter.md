---
title: "laptop just dies instead of suspending when battery is depleted"
date: 2015-01-31
forum: Hardware
---

### Post by VitasLoWang on 2015-01-31
I just wonder how can such thing happen. I rarely let my work laptop Lenovo T420 drain the battery, but today it happened. When I got back to it. It was black - no moon LED icon lit, so I started it with a power button and for a brief moment there was a BIOS text message about critical battery. After I plugged it in, it started freshly from the beginning, so I just lost all my open apps along with virtualbox session! Hopefully everything was saved. It just died instead of doing some suspend or whatever. I find this behavior really silly - to run uselessly to the last breath and then die. What if I was on a train or somewhere and would really need to do something on it when I wake up or arrive at my station, but since I did not manually do suspend it just depletes every last bit of energy in battery? Syslog does not even have a clue that this is coming (last breath was around 21:12 and no message about battery level seems to be recorded)
```
Jan 24 21:09:53 T420-vitas wpa_supplicant[1532]: wlan0: CTRL-EVENT-SCAN-STARTED  
Jan 24 21:11:53 T420-vitas wpa_supplicant[1532]: wlan0: CTRL-EVENT-SCAN-STARTED  
Jan 24 21:11:58 T420-vitas wpa_supplicant[1532]: nl80211: send_and_recv->nl_recvmsgs failed: -33 
Jan 24 14:13:17 T420-vitas rsyslogd: message repeated 3 times: [ [origin software="rsyslogd" swVersion="7.4.4" x-pid="1100" x-info="http://www.rsyslog.com"] rsyslogd was HUPed] 
Jan 24 21:12:33 T420-vitas rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="1100" x-info="http://www.rsyslog.com"] exiting on signal 15. 
Jan 24 21:57:54 T420-vitas rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="656" x-info="http://www.rsyslog.com"] start
Jan 24 21:57:54 T420-vitas rsyslogd-2307: warning: ~ action is deprecated, consider using the 'stop' statement instead [try [http://www.rsyslog.com/e/2307](http://www.rsyslog.com/e/2307) ]
Jan 24 21:57:54 T420-vitas rsyslogd: rsyslogd's groupid changed to 104
Jan 24 21:57:54 T420-vitas rsyslogd: rsyslogd's userid changed to 101

```
Interesting thing is that it makes sound warning when the battery reaches certain set low percentage, but that's about it. I have checked power management settings applet and there is settings "When the battery is criticaly low". Option "Hibernate" is selected, but it is greyed out! The other option is power-off but where is suspend? Why is hibernation not working and why can't I set low battery action to suspend when I normally use suspend every time I finish work? I haven't changed any power settings since my Ubuntu 14.04 installation, so somebody tell me please how can this be a default if it is not functioning at all? Ubuntu still does not seem to be ready for mobile devices :-\

---

### Post by weatherman2 on 2015-01-31
Check this out:

[http://ubuntuforums.org/showthread.php?t=2227515](http://ubuntuforums.org/showthread.php?t=2227515)

---

### Post by VitasLoWang on 2015-01-31
> **weatherman2 said:**
> Check this out:

[http://ubuntuforums.org/showthread.php?t=2227515](http://ubuntuforums.org/showthread.php?t=2227515)

How is this related?

---

### Post by weatherman2 on 2015-01-31
When your battery runs down, you want it to suspend instead of just shutting off, don't you?

What's probably happening is that the "battery remaining" info your battery gives to Ubuntu is a higher number than what Ubuntu is set to use to go into suspend.  That is, maybe Ubuntu thinks "battery depleted" means 5% but the laptop will really shut off when it reaches only 7%.  So you tell Ubuntu "depleted" means a higher number (which means it won't last as long).

The link describes how to change the value for "depleted."

FYI, just going into suspend will still use your battery only more slowly.  Eventually, it will still shut off completely once the battery finally does run out.  A better solution would be to tell it to hibernate instead of suspend when the battery runs out.  Unfortunately, hibernation is not well supported in Linux and often does not work reliably even when you set it up.

---

### Post by coldraven on 2015-02-01
I have 14.04 but I only have the options "Power off" or a greyed out "Hibernate" in the "power critically low" setting.
If you fit a SSD it will be quicker to boot up than to resume from hibernate.
On battery power it goes into suspend when I close the lid.
My old laptop takes about three seconds to resume, including connecting to wifi.

---

### Post by VitasLoWang on 2015-02-01
I am sorry man but it is not the case at all. I wrote that after I powered on the died laptop there was a message from BIOS about critical battery and then it switched off and I could not start it and continue booting until I plugged it into AC adapter. When it booted into Ubuntu, the battery showed 0% charged, so it is not related.

---

### Post by VitasLoWang on 2015-02-04
You also don't help me at all but let me reply anyway. I do have ssd but I also have LUKS so I need to type the password after switching off. Of course boot is quite fast but you forgot about applications for my work which take time to start and login and some clicking and typing. So letting the laptop shutdown and close everything instead of suspend is a nonsense...

---

