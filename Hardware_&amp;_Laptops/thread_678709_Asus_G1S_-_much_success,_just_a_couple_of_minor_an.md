---
title: "Asus G1S - much success, just a couple of minor annoyances"
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by AndyC_772 on 2008-01-26
Just bought my G1S this week - it's a great machine and very well supported 'out of the box'. With a little tweaking I even have a clock on my OLED display, and the email LED comes on when I get a message :) Even the wireless card (Intel 4965AGN) worked straight away.

But, there's a few things that aren't quite 100% that would be nice to fix:

- it doesn't connect automatically to my wireless network at start-up. I'm using Wicd because I need a static IP address which Network Manager can't yet do. My network's SSID is hidden, and I have to click the Wicd tray icon, select 'hidden network', enter the SSID and then all is well. It's the same on my wife's PC (Acer / Atheros / ndiswrapper), but my old laptop (Dell / Broadcom / ndiswrapper) did always connect OK.

- the wireless LED doesn't work

- even though I've set the display brightness to 80%, occasionally it goes back up to 100% on its own and I have to set it back again. I've heard mention of this under Windows too and it was to do with an Nvidia tool called Smartdimmer. Although I do have a package called smartdimmer installed, trying to make it do anything via the command line throws up an error 'init_nvclock() failed!', so I don't think it's even compatible with my driver or hardware. I'm using the nvidia-glx-new driver, and the card is (obviously) the 8600 GT.

- the camera LED is on all the time. I find it creepy! And how do I actually USE the camera anyway?

- somehow Windows (XP) seems more responsive, and the fan seems to run faster. Is there a power management dialogue I've missed somewhere?

I'm sure I'll spot other little gremlins in due course, but so far it seems like a really nice piece of kit. If anyone could help me straighten out the last few wrinkles that would be great :)

Andy.

---

### Post by HoMie_G on 2008-01-27
Hey,

Well to fix your camera and read see more about UBUNTU and the G1s. check this out:

[http://ubuntuforums.org/showthread.php?t=473396&highlight=asus+g1s](http://ubuntuforums.org/showthread.php?t=473396&highlight=asus+g1s)

(there is a shell, just run it and the camera should work) I do not know why your camera LED is on all the time, that is weird, never happened to me :S

I think UBUNTU is more responsive... windows and computers dont mix.

regardless, i find that the fan runs faster on UBUNTU, if you are working the computer hard you will notice the fan going faster.

BTW  How did you get the clock working ? and what email client do you use to get the email led working? (i use evolution, is there a plug in for it?)  The link i gave you gives you the option of turning off the OLED or putting images, i really want my clock !!

Thanks,
HoMIe_G

---

### Post by AndyC_772 on 2008-01-27
I use Thunderbird for email, and the LED plugin is called Thunderled.

If anything I think the fan runs less of the time. CPU frequency monitor shows my CPU running at 800MHz most of the time, though it does speed up to 2.2GHz under load. Oddly, transcoding video using ffmpeg doesn't run the CPU at full speed, which I need to look into at some point.

I know there are different cameras used in the G1S, maybe mine's a different model?

To get the clock working, google "asus oled ubuntu" - there's a little utility called asusoled.

---

### Post by HoMie_G on 2008-01-28
Thanks man, got the time working!!

 i already have evolution set up, im not gnna move cause of the LED light.

Did you try running the camera script? 
Peace,
HoMie_G

---

