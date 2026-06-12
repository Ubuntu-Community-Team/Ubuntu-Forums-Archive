---
title: "IBM T500 Intel Core 2 Duo processor T9400 (2.53 GHz)"
date: 2016-02-14
forum: Hardware
---

### Post by dave157 on 2016-02-14
I have kubuntu 14.04 installed and I have been looking at power management to help with my battery power draining to fast meaning it drains in about 3 hours. Seems there is nothing except this.

[https://help.ubuntu.com/community/PowerManagement/ReducedPower](https://help.ubuntu.com/community/PowerManagement/ReducedPower)

I am decided to use powertop to test but, as am new to this kind of configuration and this is my first laptop with Ubuntu I need some explaining on what to change for this processor type. What sure what to enable an what not to. 

what is installed 
powertop
pm-utils

I enable the powertop by "sudo pm-powersave true" do I need any other packages installed? Once I enble it it does not seem to be doing anything as far as I can tell. 

Thanks
Dave

---

### Post by kurt18947 on 2016-02-14
Are you aware of TLP? I'm not sure how it compares to powertop.

[http://www.unixmen.com/how-to-improve-laptop-battery-life-and-usage-in-linux-using-tlp/](http://www.unixmen.com/how-to-improve-laptop-battery-life-and-usage-in-linux-using-tlp/)

or

[http://www.unixmen.com/laptop-mode-tools-extend-laptop-battery-life/](http://www.unixmen.com/laptop-mode-tools-extend-laptop-battery-life/)

The biggest battery saver on a Thinkpad X201 w/ SSD is dimming the display as much as practical.

---

### Post by dave157 on 2016-02-14
I read about TLP linrunner but never tried it hmm. Seems easier to use than powertop. Should I have removed thermald? I did because of powertop.

---

### Post by kurt18947 on 2016-02-15
> **dave157 said:**
> I read about TLP linrunner but never tried it hmm. Seems easier to use than powertop. Should I have removed thermald? I did because of powertop.

I don't really know. I get the impression the above linked are all-in-one so would personally remove everything I recalled adding previously so as to avoid potential conflict. That is based on gut feeling and experience rather than knowledge though so I may be wrong.

---

### Post by mörgæs on 2016-02-15
> **kurt18947 said:**
> 
The biggest battery saver on a Thinkpad X201 w/ SSD is dimming the display as much as practical.

Yes, and installing the lightest possible desktop environment will also save battery. The eye-candy of Kubuntu drains power.

---

### Post by dave157 on 2016-02-15
I have no luck with other desktop interfaces I tested mate which I liked but it had artifacts with the mouse pointer. if I clicked on a file that file icon or image would stick to the pointer and the only way to remove it as to logout out and login that was the oddest thing to see. If Ubuntu did not make the desktop so static meaning I can not move the panel where I want it etc in Ubuntu 14.04 I would have used that. But is gnome [ or is it gnome] more or less a power on a battery?

---

### Post by weatherman2 on 2016-02-15
I use Gnome Flashback (with Metacity) in Ubuntu 14.04 to get the best performance on older machines.  (This gives you a Mate-like interface.)  Although I can't say for sure that it would improve battery life, my intuition is that it should.  I'd also make sure to install any Additional Driver for the graphics card.

Things like Powertop should I believe no longer be needed by modern distros to save power.  Power savings should largely be built into the OS now.

I have found that some hardware simply doesn't work well with Linux, though.  My usual test, if Windows is available on the machine, is to check the power draw at idle with a "watt meter" in Windows and then compare it to Linux.  In a few cases, even after some driver tweaking in Linux, I could not get the power draw even close to what I got in Windows.  But the same distros work great on other machines without any tweaking: I get the same power draw in Windows that I get in Linux.  (If the laptop is drawing 50% more power in Linux than it is in Windows, your battery isn't going to last nearly as long, obviously.)

---

### Post by dave157 on 2016-02-16
If I used TLP how if needed would I edit the config file. I think is would be this
sudo edit filename 

what if anything am I missing?

---

### Post by mörgæs on 2016-02-19
> **dave157 said:**
> I have no luck with other desktop interfaces I tested mate which I liked but it had artifacts with the mouse pointer.

Did you try a live boot of Lubuntu 15.10?

---

