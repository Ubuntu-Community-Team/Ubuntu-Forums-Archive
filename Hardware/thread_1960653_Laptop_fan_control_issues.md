---
title: "Laptop fan control issues"
date: 2012-04-17
forum: Hardware
---

### Post by afbrian13 on 2012-04-17
Hi all this is my first post and first experience with Ubuntu. Yes I've read, and searched, and searched and read some more but need a little clarification. Maybe ist because i'm learning the new language.

I'm running 11.10 on a Toshiba laptop, AMD duel core.

It seems like my fans never come on and it will over heat (and thanks to toshiba shutdown)
here is the walk through I found:
[http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)

I'm getting hung up on ID'ing my chip set and then editing the start/stop points for the temps.

sudo gedit /etc/sensors.conf
pulls up a blank window. what should be here and is there a different way to find this info?

its says add fanX_div4 (X= fan number) to the line with my chip set, but i don't show and info to add to.

Any help would be great so I don't overheat this thing. Hopefully I was detailed enough to show that I've been searching and working though this.

Thank you!!!

Brian

---

### Post by Mark Phelps on 2012-04-18
Try opening a terminal and running "sudo sensors-detect" -- and seeing what it finds.  If it finds no sensors, you're not going to be able to monitor or control your fans.

---

### Post by afbrian13 on 2012-04-18
when i run sensor detect the final summary tells me:

driver 'k10temp' (autoloaded):
*chip 'amd family 10h thermal sensors' (confidence: 9)

no modules to load.

I see that as I have sensors, but i don't know what to do with this info.

I found where i should run pwmconfig, but it doesn't work. According to the tutorial i found if it gives me the error message usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
than you need to apply this fix. If not, proceed to the next step.

So i go to the next step to edit the pwmconfig on line 68. swap a couple lines to switch the if then statements. however, i can't find the correct line. i can read all couple thousand lines of code i'm sure.

Am i on the right track? I'll keep hacking at it, I just want to make sure i'm headed the right direction.

Thank you!

Brian

---

