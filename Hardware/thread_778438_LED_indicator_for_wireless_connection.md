---
title: "LED indicator for wireless connection"
date: 2008-05-02
forum: Hardware
---

### Post by tommyhakinen on 2008-05-02
I was using Gutsy before. Now I am running Hardy. I just realized that now in Hardy, the button on my laptop for switching on/off my wireless connection is working (not on Gutsy). But one problem is the light indicator. Even if the wireless connection is on, the light indicator on the button is always off. How do I fix this?

Thank you.

Regards,

tommy

---

### Post by subzero316 on 2008-05-02
Did u get the light indicator in gutsy????

---

### Post by tommyhakinen on 2008-05-02
No. The button was not working on Gutsy. But on Hardy it's working, only the light indicator that does not work.

---

### Post by Kirfew on 2008-05-02
Are you sure the light wasn't broken since you got the laptop?

---

### Post by subzero316 on 2008-05-02
I have never seen the light workin in Ubuntu(7.10). It happens for many so no worries on that.i Dont think there are any fixes right now.

---

### Post by subzero316 on 2008-05-02
Check [<<-----This Link----->>   ]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/55780")Its the bug report.

---

### Post by kikapu on 2008-05-02
Check here [http://ubuntuforums.org/showthread.php?p=4859841#post4859841](http://ubuntuforums.org/showthread.php?p=4859841#post4859841)

problem is solved!

---

### Post by lamborghiniwang on 2008-05-02
If you have an Intel 4965AGN wireless card, you may want to try
```

sudo apt-get install linux-backports-modules-2.6.24-16-generic
sudo rmmod iwl4965
sudo modprobe iwl4965

```
My Wifi LED works after I did this.

---

### Post by kikapu on 2008-05-02
> **lamborghiniwang said:**
> If you have an Intel 4965AGN wireless card, you may want to try
```

sudo apt-get install linux-backports-modules-2.6.24-16-generic
sudo rmmod iwl4965
sudo modprobe iwl4965

```
My Wifi LED works after I did this.

Xmmm... in my case, yes. I have the Intel 4965AGN card. I didn't do the last 2 commands, should i ? They remove the iwl drivers from the system (they are not needed) because the ipw are now in use ?

---

### Post by lamborghiniwang on 2008-05-02
> **kikapu said:**
> Xmmm... in my case, yes. I have the Intel 4965AGN card. I didn't do the last 2 commands, should i ? They remove the iwl drivers from the system (they are not needed) because the ipw are now in use ?

  They just remove and then reload the iwl4965 module. I guess you could simply reboot if you don't want to apply the last 2 commands. 
  btw, although this does bring the LED on, it doesn't flash when there is any wifi activity, but at least the LED would automatically turn on/off when you switch on/off the wireless. :guitar:

---

### Post by kikapu on 2008-05-02
> **lamborghiniwang said:**
> They just remove and then reload the iwl4965 module. I guess you could simply reboot if you don't want to apply the last 2 commands. 
  btw, although this does bring the LED on, it doesn't flash when there is any wifi activity, but at least the LED would automatically turn on/off when you switch on/off the wireless. :guitar:

Ah, ok. I already have rebooted many times from that time so i guess these 2 aren't needed. You are correct, it doesn't flash but the fact that is on and now can see the change (on/off) when you press the key combination (Fn-F5 in my laptop) is a very welcome addition.

A strange point: Before getting the drivers from ubuntu backport, i remember that when returned from Suspend, my WiFi worked right away. Now (i did it only once so i cannot be sure) WiFi was not working and i had to re-connect to enable it.
Does it happen to other too ??

---

### Post by reggie_mac on 2008-05-02
Im at the same point on a TravelMate 5720, but from looking around the may be a solution at here :

[http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1209](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1209)

But i've only being doing the Ubuntu thing for a week now, and my bash skills are still weak, when the read me says stuff about compiling kernals i tend to walk away. May help you get it sorted though, if it works let me know and i'll try to figure it out.

---

### Post by tommyhakinen on 2008-05-02
I am using Intel PROSet/Wireless 2200BG. It is working on XP. So I am sure it's not broken. Since it works when I press it. Just do not have the light indicator.

---

### Post by tommyhakinen on 2008-05-03
I have tried this:

[QOUTE]
sudo apt-get install linux-backports-modules-2.6.24-16-generic
sudo rmmod ipw2200
sudo modprobe ipw2200
[/QUOTE]

I also tried this:

> 
 modprobe ipw2200 led=1


They are both not working. Any solution?

---

### Post by reggie_mac on 2008-05-04
Try here [http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

looks like these are the drivers your after.

---

