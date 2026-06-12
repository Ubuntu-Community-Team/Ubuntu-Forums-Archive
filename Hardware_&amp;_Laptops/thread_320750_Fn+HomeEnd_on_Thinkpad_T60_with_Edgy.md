---
title: "Fn+Home/End on Thinkpad T60 with Edgy"
date: 2006-12-17
forum: Hardware &amp; Laptops
---

### Post by jasonxh on 2006-12-17
Fn+Home is the combination for brightness up on T60. It's working actually, but it doesn't generate a proper event, thus no OSD available either with hotkey-setup or tpb. However ibm_acpi recognizes it and ```
cat /proc/acpi/ibm/brightness
``` reports properly.

On the other hand, Fn+End (brightness down) generates an acpi event and triggers OSD both with hotkey-setup and tpb, but ibm_acpi module doesn't seem to recognize it! The above code gives the old value. hotkey-setup seems to depend on ibm_acpi, so it simply displays an OSD with a progress bar that doesn't change. But tpb displays fine with Fn+End.

In short, both combinations are working (they should be working without any driver), but the OS is not properly informed.

Any T60 users notice this problem?

---

### Post by iamhimay on 2006-12-31
Hi,
I'm another almost perfectly content t60 owner, running amd64 edgy.
I haven't gotten into it yet, but I am getting xserver crashes when I hit the the fn-home combo to adjust brightness. The gui controls in kpowersave and the gnome power interface control the brightness fine, but it would be nice to have the hotkeys working. I'll definitely investigate more soon. Only had this thing just over a week. It crashes X even from the login screen. I should probably be glad it's so predictable; that actually encourages me that it's fixable. 

Himay

---

### Post by PseudoRandom on 2006-12-31
I use tpb for the OSD on my T60, and it does behave oddly. If I hold down Fn-End, the brightness (and the meter) drop as expected, but if I continue to hold down Fn and switch from End to Home, the brightness goes back up, but the meter stays down. And if I release Fn, then Fn-Home lets me raise the brightness, but there's no OSD at all.

And BTW, I installed tpb because the much nicer OSD that worked out of the box with kubunty Edgy just disappeared one day.

---

### Post by mgrusin on 2007-01-01
> **iamhimay said:**
> Hi,
I'm another almost perfectly content t60 owner, running amd64 edgy.
amd64?  Don't the T60s all have intel processors?  Could this be the reason for your crashing?

---

### Post by riven0 on 2007-01-01
Well, I've got the Thinkpad R60 and hitting Fn+End works just fine, but if I hit Fn+Home it'll completely blank out the screen. The thing is, Ubuntu will be running fine, and there's no crash, but the screen won't come back on and I'm forced to do CTRL + ALT + Del to restart. 

Haven't looked into the problem, though, so I don't know what could be causing it.

---

### Post by iamhimay on 2007-01-05
Hello Thinkpadders,

There is a problem with the acpi video driver which affects the fn/home ibm keystroke. I am getting around this issue by not loading the module for it. Just edit /etc/modprobe.d/blacklist to add the line 'blacklist video'. Now I can adjust brightness up and down and no x crashes. Good luck,

---

### Post by drasch on 2007-01-05
What happens for me when pressing Fn+Home is that it toggles the Video Out just like Fn+F7 should.

---

### Post by jasonxh on 2007-01-05
Thanks himay. It works for me. But what's the use of this video module?

---

### Post by iamhimay on 2007-01-06
ibm_acpi takes care of the video specifically on these ibm/lenovo  machines. The video module is part of the general acpi system in the kernel. The fn/home acting like fn/f7 (toggle external monitor) is an issue on machines with newer bios.

---

### Post by Lowfront on 2007-01-12
> **iamhimay said:**
> Hello Thinkpadders,

There is a problem with the acpi video driver which affects the fn/home ibm keystroke. I am getting around this issue by not loading the module for it. Just edit /etc/modprobe.d/blacklist to add the line 'blacklist video'. Now I can adjust brightness up and down and no x crashes. Good luck,

where do I add this line?  this should work on my x60 right considering I have the same problem?

---

### Post by Lowfront on 2007-01-21
?

---

### Post by Paulo Wageck on 2007-04-11
blacklist video

is the way to go
worked here
thanks

---

### Post by VortexICS on 2007-04-29
blacklist video works on my X60s but the progress bar of the brightness OSD is stuck at 50% even though I can change the brightness.

---

### Post by chrono325 on 2007-04-30
The "blacklist video" trick worked for me as well, and the keys now work brilliantly.

The only thing that does not work is that when I change the brightness controls using Fn+Home/End, the Gnome applet does not notice the changes. Pressing one of the keys makes the brightness level indicator pop up, but the bar does not change at all. Clicking on the panel applet allows me to adjust the brightness just fine and does update the slider.

Here is a screenshot of what it looks like to change the brightness with the keyboard:

[IMG]http://farm1.static.flickr.com/219/478661199_a6bff411e1.jpg?v=0[/IMG]

This is no huge issue, but it would be nice to have the bar update along with the brightness.

---

### Post by Eddie Hung on 2007-07-18
> **chrono325 said:**
> The only thing that does not work is that when I change the brightness controls using Fn+Home/End, the Gnome applet does not notice the changes. Pressing one of the keys makes the brightness level indicator pop up, but the bar does not change at all. Clicking on the panel applet allows me to adjust the brightness just fine and does update the slider.

This is no huge issue, but it would be nice to have the bar update along with the brightness.

I have this exact issue with an IBM X41 (not tablet)... have we made any progress?

Is this bug reported on launchpad? I didn't know where inside launchpad I should start looking...

Eddie

---

### Post by AnythingBut on 2007-07-22
I just noticed this thread.  I think my solution in [http://ubuntuforums.org/showthread.php?p=3064312](http://ubuntuforums.org/showthread.php?p=3064312) might apply.

---

### Post by tewe on 2007-08-24
i've similar problem.
/Thinkpad R60e Gutsy/
The brightness buttons work, but if i press fn+End (or Fn+home) the brightnes goes to minimum (or maximum) dont stop.

echo "down" /proc/acpi/ibm/brightness and
echo "up" /proc/acpi/ibm/brightness work well.

---

### Post by Eddie Hung on 2007-08-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/81407](https://bugs.launchpad.net/bugs/81407) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				It seems that GPM has regressed to an even worse state since I last posted, but it has been reported on launchpad.

Eddie

---

### Post by wayneschutz on 2007-10-09
Just fyi, I have a T60 (1953-dau) that was behaving strangely.  When I used FN+Home/End to adjust the brightness, the screen would go dark and I had to press the key combo three times before I'd get video back.  Also, the OSD always showed maximum brightness, regardless of the actual brightness.  The brightness slider in the gnome pwr mgmt applet worked fine.

The OSD fix posted by AnythingBut worked fine for fixing the OSD issue and adding "blacklist video" to the blacklist file and then a reboot fixed the FN+Home/End issue.  Hope this helps someone else. -w

---

### Post by the.ant on 2007-10-18
With my t60 and Feisty buttons worked fine without OSD, in Gutsy they don't react at all, which is kinda annoying. Any ideas?

---

