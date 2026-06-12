---
title: "1060ti reporting incorrect screen size?"
date: 2020-06-16
forum: Hardware
---

### Post by camilovietnam on 2020-06-16
Hello Ubuntu forums. I'm having a small problem with my ubuntu system.

GPI: Nvidia 1060ti
Monitor: Samsung B1930 and Hugon 24"
Ubuntu: 18

and sometimes after I turn on the computer, the resolution of the screens is a bit off. I use two screens, and both of them will appear to have a very high resolution, or be misaligned and the desktop showing partially off the screen.

I was checking DPI issues, and I read somewhere about ```
xrandr | grep -w connected
``` command, and when I ran it, these were the results:

```
DVI-D-0 connected 1280x960+0+0 (normal left inverted right x axis y axis) 880mm x 500mm
HDMI-0 connected primary 1920x1080+1280+0 (normal left inverted right x axis y axis) 160mm x 90mm
```


If I am not mistaken, this is reporting that my screens are 80cmx50cm and 16cmx9cm. To me, this is clearly wrong, my screens are 19 inches and 24 inches respectively.
 I'm trying to figure out why the resolution is changing, where could I start? I checked the installed drivers with `ubuntudrivers autoinstall` and i already have the recommended driver.

Any suggestions as to where could I start resolving this issue? Thank you very much.

---

### Post by Yellow Pasque on 2020-06-17
Try the latest driver: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=bionic](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=bionic)

---

### Post by camilovietnam on 2020-06-17
It didn't change anything. I installed driver 440.82 but still the screen was giving me the wrong size.

I plugged the two monitors off the card, plugged them back in, and now the size seems correct, but one of them is still off to the left. This is the result of xrandr | grep -w connected:

```
DVI-D-0 connected primary 1360x768+0+0 (normal left inverted right x axis y axis) 410mm x 230mm
HDMI-0 connected 1920x1080+1360+0 (normal left inverted right x axis y axis) 160mm x 90mm
```

I'm not sure if these dimension (160mm x 90mm) are correct, if these are supposed to be screen width and height they are definitely not correct.

Here's a picture of the monitor with the offset: 
[IMG]https://youdieifyou.work/files/bpcvuiyfqk.jpeg[/IMG]

What could be causing this? I tried changing resolutions or positioning with arandr, but it didn't solve the offsetting.

---

### Post by camilovietnam on 2020-06-17
It appears to be fixed now, at least until it happens again.

The optimal resolution for this monitor is supposed to be 1360x768, but using this resolution will move the picture offside. With resolution 1280x720 the screen is centered correctly. Perhaps there is a way to offset the picture manually using xrandr, so I can use the optimal resolution? Could this be a GPU issue?

---

### Post by Autodave on 2020-06-17
There should be a button on your monitor to center the screen that little bit.  Usually it has a name like "self adjust" or something similar.

I do not think that it is a GPU problem.  Possibly a cable problem.  I would try finding the self adjust or self centering button first.

How is the monitor connected?  What cabling and any adapters?

---

### Post by Yellow Pasque on 2020-06-17
> **Autodave said:**
> There should be a button on your monitor to center the screen that little bit.  Usually it has a name like "self adjust" or something similar.

That is for analog/VGA signals.

---

### Post by Autodave on 2020-06-18
Really?  You maybe right, but this BenQ monitor has that button and it is hooked up via HDMI and I used the button when it was first hooked up to get the screen that last 1/8" centered.

---

### Post by Yellow Pasque on 2020-06-18
> **Autodave said:**
> Really?  You maybe right, but this BenQ monitor has that button and it is hooked up via HDMI and I used the button when it was first hooked up to get the screen that last 1/8" centered.

Heh, I might be wrong too. What you describe is new to me. I have a BenQ BL2411PT from a few years ago. When you use a digital connection (DVI, DP), the positioning and auto-adjust are grayed out.
I wonder if the button you are describing has something to do with underscan/overscan? So I can educate myself - What model monitor is it?

---

### Post by Autodave on 2020-06-18
You don't need to educate yourself......you are fine.  I just looked for it and cannot find it.

Very disappointed in myself......I have been wrong 3 times this year already.

Sorry for the confusion!

---

### Post by camilovietnam on 2020-06-21
The first monitor, a Samsung SyncMaster b1930, is connected via an VGA cable, but I am using an active DVI to VGA converter because the 1060ti does not have a VGA output. 
The second monitor, a Hugon 24", is connected through an HDMI cable. 

Worth mentioning perhaps that I had to change the HDMI cable on the Hugon a few weeks, I think I remember the monitor would just not get any signal through the cable. Oh, and also sometimes the monitors just turn off. It's not the screen saver because I would be working actively with both screens and then suddenly one of them would just go black, but all you have to do is turn it back on. Perhaps all these symptoms might help narrow down the problem. 

Both of them experience issues , this is why I was considering that this could be a GPU problem. I just came to work this morning and found that the resolutions were again messed up, and at 1024x768 the text on the small monitor is illegibly small, when it should be the opposite, a resolution like that should give me really big icons and font size. This problem started happening only a few weeks ago. 

I will now disconnect the monitors, turn off the computer, turn it back on and reconnect them again to see if that again fixes the issue for now.

PS: Yes, connecting and reconnecting the monitors fixed the issue. It would be interesting if this was a cable problem, because that would mean both cables for both monitors started malfunctioning at the same time. I think today in the evening I will reinstall all nvidia drivers and reinstall again, see what that does

PS2: The Samsung monitor is kinda broken and it won't do anything when I press the Menu button. Sometimes it works, sometimes it doesn't. The Hugon has a Reset option but it does nothing to fix the resolution issues.

---

### Post by Yellow Pasque on 2020-06-22
> The first monitor, a Samsung SyncMaster b1930, is connected via an VGA cable

Why? Does it not have any digital inputs? I would try to get rid of that adapter.

---

### Post by camilovietnam on 2020-07-05
No, this monitor only has a VGA input, that's why I needed the adapter. 

Last Friday I turned on the PC, the resolution was all messed up, but I didn't feel like disconnecting the monitors so I just worked like that, struggling to read the small text on some programs (NixNote, FileZilla) while others scaled the text perfectly (Slack, Chrome, Brave-Browser).

Monday morning I turn on the PC, the resolution is all okay. I'm puzzled.

---

### Post by camilovietnam on 2020-07-13
Bump for any possible solutions, changing DPI, or changing GPU, etc

This is a screenshot of my 20-inch monitor, impossible to read the small text. Wonder if this is a dpi problem?

[ATTACH=CONFIG]286460[/ATTACH]

---

