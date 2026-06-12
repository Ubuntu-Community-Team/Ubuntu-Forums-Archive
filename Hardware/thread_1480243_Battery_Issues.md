---
title: "Battery Issues"
date: 2010-05-11
forum: Hardware
---

### Post by danger pigeon on 2010-05-11
To start, I have a gateway mini LT2104u running the 10.04 UNR. I have a very strange problem though and it seems to be related to flash. I recently reinstalled ubuntu on my netbook to use the most recent version and ive been having problems with the battery ever since. The battery indicator generally shows less time left then there actually is, but that's only aesthetic because the battery lasts as long as it should. 

The real problem occurs when i try to play a flash video. The battery "discharges" and i get warned to connect to an external power source immediately to avoid losing work. If i ignore it, the computer will shut down after a minute or two on it own. The battery still has plenty of power because if i reboot into either ubuntu or windows 7 (i have a dual boot) it shows i have several hours left. But if i watch a flash video again same thing happens. I have no idea what could be causing this, and i couldnt even find a mention of a similar problem online. I could really use some help with this because if cant fix this im gonna have to remove ubuntu, something i really dont want to do. If it would be easier i can be contacted by instant messenger.

---

### Post by Maximus559 on 2010-05-11
I've just experienced the same problem with Flash video for the first time. However, I've been unable to duplicate the problem the way you say you can. I've set my Acer AO532h to suspend on low battery now, but I'm not sure if that will help in the event of another episode. You might try that. At least then you won't loose everything. I'm wondering if this problem wasn't the result of a recent update, as I've never seen it before.

---

### Post by danger pigeon on 2010-05-13
It might be from an update, but i don't think it was. I just did a fresh install of 10.04 last week and i'm pretty sure i haven't updated anything yet. It would be great to figure out because if i can't use flash on ubuntu it's hardly worth running it on a netbook.

---

### Post by Maximus559 on 2010-05-13
Well, I've tried several times to duplicate the problem, but have been unsuccessful. However, I am developing a sneaking suspicion that it had to do with something else that I was playing around with at the same time: screen dimming options in the power management control panel. Try unchecking the boxes for "reduce backlight brightness" and "dim display when idle" under the "on battery power" tab. My machine was giving me problems with these features, and I disabled them at about the same time I had the Flash battery episode. Let me know if this fixes it.

---

### Post by Maximus559 on 2010-05-18
Well, I've just had it happen a second time, and this time I was not viewing a Flash video. I was simply browsing the web, and I got a lower power notification. I clicked cancel, then went to look at my battery status. Sure enough, it showed up at 0% capacity. A few seconds later, my machine went to standby, the way I've told it to when battery is critically low. I immediately hit a key to bring it out of standby, and when the desktop came back, everything was back to normal. Firefox was right where I'd left it, and battery status was where it should have been. So, setting your machine to go to standby instead of turn off when battery runs out will turn this from a critical bug into a minor annoyance. Still, it would be nice if a fix could be found...

---

### Post by danger pigeon on 2010-05-21
Yeah, its still pretty annoying. I can reproduce this bug on command, it happens literally every time i watch a flash video. Not the end of the world, it just means i'll have to use windows more on the netbook.

---

### Post by Maximus559 on 2010-05-22
Too bad. Seems like a problem with power management. Here's to hoping they fix it in an update sometime soon.

---

### Post by Maximus559 on 2010-07-24
Update: I think I may have found a solution to this problem. While searching around Acer's support site yesterday, I realized that a good number of BIOS updates have been released since I bought my Aspire One sometime around January or February. I flashed the BIOS to the latest version, and so far so good. The update also seems to have fixed this warning message I used to get when booting up: "acer-wmi: Unable to detect available WMID devices." Now, to flash your BIOS: first, go to Acer's site and download the latest BIOS update (1.25 at the the time of this writing). Next, if you're dual booting with Windows, just run the Windows version of the update utility. If you're like me and are running UNR exclusively, it's a little more complicated. First, follow the instructions [here]("http://www.bay-wolf.com/usbmemstick.htm") to create a bootable DOS USB flash drive. Then copy the folder containing the DOS BIOS update utility to the flash drive. Next, simply boot from the flash drive and run the batch file to update your BIOS. Hope this helps.

---

