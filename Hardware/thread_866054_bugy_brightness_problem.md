---
title: "bugy brightness problem"
date: 2008-07-21
forum: Hardware
---

### Post by oguzy on 2008-07-21
My current problem is really annoying. I have problems with adjusting the brightness. Indeed i am able to adjust it using the nvidia-settings and the nvidia_video_brightness_up.sh and nvidia_brightness_down.sh. So i changed the events/video_brightnessup and events/video_brightnessdown as if the scripts will be called. 

If you check the nvidia_video* files you will see they are just calling a script called dimmer with either --inc or --dec parameter. 

So i have a general dimmer.sh script under /usr/bin which is executed eveytime i press my brightness hot keys. Till now everything is ok. It works and my brightness increases or decreases. But the on screen display of the brightness never changes. When i check the /var/log/acpid i saw it executes both nvidia_video_brightnessup.sh and video_brightnessup.sh concurently which shouldnt be happened. So i added some debug parts to the scripts and here is the output of when i press the brightness up hotkeys,

[Mon Jul 21 17:27:09 2008] received event "video DD03 00000086 00000000"
[Mon Jul 21 17:27:09 2008] notifying client 5710[0:0]
[Mon Jul 21 17:27:09 2008] notifying client 5549[111:123]
[Mon Jul 21 17:27:09 2008] notifying client 5710[0:0]
[Mon Jul 21 17:27:09 2008] executing action "/etc/acpi/nvidia_video_brightnessup.sh"
[Mon Jul 21 17:27:09 2008] BEGIN HANDLER MESSAGES
running nvidia
before nvidia runs: 30
running nvidia
before nvidia runs: 30
nvidia ended
after nvidia finished: 30
[Mon Jul 21 17:27:09 2008] END HANDLER MESSAGES
[Mon Jul 21 17:27:09 2008] action exited with status 0
[Mon Jul 21 17:27:09 2008] executing action "/etc/acpi/video_brightnessup.sh"
[Mon Jul 21 17:27:09 2008] BEGIN HANDLER MESSAGES
running video-up
currentlevel: 30
video-up finished
lastlevel: 40
[Mon Jul 21 17:27:09 2008] END HANDLER MESSAGES
[Mon Jul 21 17:27:09 2008] action exited with status 0
[Mon Jul 21 17:27:09 2008] completed event "video DD03 00000086 00000000"


i see the calling of nvidia_video_brightnessup.sh double. 
I dont know why. This is one question i want to find.

Second when i run press the brightness up hot keys again i see the same output but i should see 40 and 50 instead. So it seems whenever i press hotkeys the proc values are resetting. 

I dont know the anser of this thing too. 
 
And last, why is this video_brightnessup.sh called although it is not mentioned in the events file:

And i want to see my brightness bar increase and decrease. 

So how can i fix all these? Because i am tired of dealing with this bugy gnome-power-manager things. Any body who can help me?

/etc/acpi/events/video_brightnessup [http://pastebin.com/f2c4b939d](http://pastebin.com/f2c4b939d)
/etc/acpi/nvidia_video_brightnessup.sh [http://pastebin.com/f7ea8428b](http://pastebin.com/f7ea8428b)
/usr/bin/dimmer.sh [http://pastebin.com/f7a29517e](http://pastebin.com/f7a29517e)
/etc/acpi/video_brightnessdown.sh [http://pastebin.com/f33c3c339](http://pastebin.com/f33c3c339)

---

