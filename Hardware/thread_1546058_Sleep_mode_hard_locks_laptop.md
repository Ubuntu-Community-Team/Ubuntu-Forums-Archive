---
title: "Sleep mode hard locks laptop"
date: 2010-08-04
forum: Hardware
---

### Post by X5-655 on 2010-08-04
And I mean it, I have to pull out the battery and AC adapter, just to get it to even POST again..  Then once it does get back into Linux, networking is disabled, re-enable, and wifi won't connect.  I have to press the wifi button twice on the keyboard just to get it working again.

What a pain!

What does it do when it sleeps?  Well, power light blinks like it should, but when I try to wake it up, the caps lock and numlock light just flash and thats it, LCD doesn't even power up, just stays with backlight off...

Compaq CQ61-313us...

This is the only hardware problem  I'm having with this laptop with Linux.

10.04 64-bit

---

### Post by X5-655 on 2010-08-04
I just tried to use uswsusp, and use s2ram, but i get this error:

```
brandon@brandon-laptop:~$ sudo s2ram
Machine is unknown.
This machine can be identified by:
    sys_vendor   = "Hewlett-Packard"
    sys_product  = "Presario CQ61 Notebook PC"
    sys_version  = "0392100000210D10000020000"
    bios_version = "F.15"
See http://suspend.sf.net/s2ram-support.html for details.

If you report a problem, please include the complete output above.
```

---

### Post by X5-655 on 2010-08-05
Just updated to the latest 39 kernel, still does it..

This makes using my laptop hard.

Hibernate works, but is slower than just booting from scratch, which don't seem right..

---

### Post by X5-655 on 2010-08-05
Please, this is VERY important.

It's not a deal breaker, but it's highly annoying, and forces me to do full shut downs instead of sleep..

---

### Post by X5-655 on 2010-08-06
So it's not just me:  [http://answers.yahoo.com/question/index?qid=20100310072014AAoTH5R](http://answers.yahoo.com/question/index?qid=20100310072014AAoTH5R)

Clearly other CQ61 laptops based on the same hardware have the SAME sleep mode problem.

---

### Post by X5-655 on 2010-08-11
The new ACPI-Support update, along with the other Ubuntu updates I got this morning, didn't help..  Still won't wake from sleep.

---

### Post by X5-655 on 2010-08-23
This is ridiculous.

BUMP!!

[https://wiki.ubuntu.com/HoaryPMResults](https://wiki.ubuntu.com/HoaryPMResults)

I see the same problem listed in here since Hoary..  This is just idiotic that it's not fixed.  For a laptop this is a HUGE problem!  Especially since Hibernate is SLOWER to resume than just a cold boot.

---

### Post by X5-655 on 2010-08-25
BUMP

Debian works fine in sleep mode and resumes fine, so this IS an Ubuntu issue..

---

### Post by X5-655 on 2010-09-02
8th bump.  This is very ridiculous that no one has an answer or any words of helpful wisdom..

When it goes into sleep mode, it won't come back, just fan revs and blank screen, no HD activity.  Hold down power button to turn off, turn back on, HP status code flashes 2, which means "BIOS Corruption".  Pull the battery, and all is fine again.  This ONLY happens in Ubuntu, and I verified with several HP DV laptops in a store today..

If no one helps, then I will dismiss Ubuntu as a joke..

---

### Post by X5-655 on 2010-09-02
Bump 9..

---

### Post by X5-655 on 2010-09-03
Bump 10..

[http://www.youtube.com/watch?v=pEsF72DPLSo](http://www.youtube.com/watch?v=pEsF72DPLSo)

Now I have video..

---

### Post by X5-655 on 2010-09-03
Bump 11..

---

### Post by X5-655 on 2010-09-05
Bump 12

At this point, it's true about Ubuntu guys:  "If I don't have a problem, I don't care about troubleshooting someone else."

You guys seriously suck.  12 bumps in and not a single freakin bit of help.

---

### Post by jamesa00789 on 2010-09-05
I feel you matey! I am still having several problems with my install.

- Suspend and hibernate do not work. Laptop just hangs.
- Sound is crackly (its really bad, i turned off the sounds).
- Reinstalled ALSA and now I have no sound.
- My headphone jack doesn't work.

There have been a range of updates lately, and none of which has been of any beneficial to me! grrr

---

### Post by X5-655 on 2010-09-05
> **jamesa00789 said:**
> I feel you matey! I am still having several problems with my install.

- Suspend and hibernate do not work. Laptop just hangs.
- Sound is crackly (its really bad, i turned off the sounds).
- Reinstalled ALSA and now I have no sound.
- My headphone jack doesn't work.

There have been a range of updates lately, and none of which has been of any beneficial to me! grrr

I used to have a headphone jack that didn't work, but this command fixed it:

```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
apt-get install linux-alsa-driver-modules-$(uname -r)
```

I'm guessing you tried that one, but worth a shot to help.  I like to help people if I can..

I just hope my sleep mode issue can get fixed.  I'm actually making a Fedora 13 disk right now, I might be switching over to that OS..

---

### Post by Veloteuton63 on 2010-09-08
> **X5-655 said:**
> And I mean it, I have to pull out the battery and AC adapter, just to get it to even POST again..  Then once it does get back into Linux, networking is disabled, re-enable, and wifi won't connect.  I have to press the wifi button twice on the keyboard just to get it working again.

What a pain!

What does it do when it sleeps?  Well, power light blinks like it should, but when I try to wake it up, the caps lock and numlock light just flash and thats it, LCD doesn't even power up, just stays with backlight off...

Compaq CQ61-313us...

This is the only hardware problem  I'm having with this laptop with Linux.

10.04 64-bit

Same here with a HP Pavillon DV6, except that it reboots after prolonged use of the power button. Afterwards it wants to check its HDs - in the process of which it hangs itself again ... So I have to restart and and skip the HD verif at the following boot, then it works.

This is not the only problem I have and I think that Ubuntu is beginning to live its last instances on this machine ...

---

