---
title: "interlaced effect at 640x480 at 60hz on laptop display"
date: 2008-01-21
forum: Hardware &amp; Laptops
---

### Post by yodahome on 2008-01-21
Hi!

My problem is this: I run Ubuntu Gutsy on a somewhat dated laptop, display usually is 1024x768 at 60 hz on a ATI Radeon Mobility 9000 using the standard ATI driver. Works fine. However if I want to use a resolution at 640x480 (eg with ScummVM in fullscreen mode) I get an unhealthy interlaced effect which makes the screen unreadable (or unwatchable for that matter). I found that if I set the resolution to 640x480 and the refresh rate from 60 to 59 the screen looks good. So I edited the modes in my xorg.conf  and set 640x480@60 to 640x480@59. However, after restarting the effect still appears if the resolution switches and obviously the refresh rate still is 60hz.

What else can I do to set the refresh rate just for this specific resolution to 59?

---

### Post by Yellow Pasque on 2008-01-21
I wrote a little script for you (there's probably a more elegant way to do it, but I'm not very good at bash scripting): It creates a file with the modeline if it's 640x480, otherwise the file will be empty. It then checks to see if the file is empty or not, and sets the correct resolution if it's not empty. It then removes the file in preparation for the next boot.

You can place the code snippet in a script file that runs at startup, like /etc/init.d/gdm (assuming you're using regular Ubuntu and not Kubuntu or Xubuntu).
Put it at the the end before 'exit 0'

```
`xrandr -q | grep *+ | grep 640x480 > filename`
if [[ -s filename ]]
then
	`xrandr -r 59.0`
fi
`rm filename`
```

---

### Post by yodahome on 2008-01-22
> **Temüjin said:**
> I wrote a little script for you (there's probably a more elegant way to do it, but I'm not very good at bash scripting): It creates a file with the modeline if it's 640x480, otherwise the file will be empty. It then checks to see if the file is empty or not, and sets the correct resolution if it's not empty. It then removes the file in preparation for the next boot.

You can place the code snippet in a script file that runs at startup, like /etc/init.d/gdm (assuming you're using regular Ubuntu and not Kubuntu or Xubuntu).
Put it at the the end before 'exit 0'

```
`xrandr -q | grep *+ | grep 640x480 > filename`
if [[ -s filename ]]
then
	`xrandr -r 59.0`
fi
`rm filename`
```

Thanks, that's a great idea. However, as I understand the script, it would only work if the resolution presently is 640x480. If I put it in a start script it would not do anything, because at boot the resolution is 1024x768. When I then use some program that runs fullscreen at 640x480 it will still be at 60hz. So I probably would have to change your script so that it checks periodically in the background if the resolution changed or something like that. I'll be tinkering with that a bit.

---

### Post by Yellow Pasque on 2008-01-22
Ah, if you know when the resolution is going to change, just bind the *xrandr -r 59.0* command to a key instead of running a cron job.

---

