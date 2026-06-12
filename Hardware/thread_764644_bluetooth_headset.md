---
title: "bluetooth headset"
date: 2008-04-24
forum: Hardware
---

### Post by Corey on 2008-04-24
I have an LG HBS-200 stereo bluetooth headset. I want to pair it with my hardy machine so I can use it to listen to music/skype calls etc. I had to install bluetooth-alsa and gnome-bluetooth and now it finally shows up when I scan for devices. However when I click connect I get an error:

Couldn't display "obex://[00:0D:3C:BA:73:65]/".

Not too helpful. What do I need to do to make this happen?!

Thanks,
Corey

---

### Post by cakalle on 2008-04-29
Hello 
I have the same problem and I use SonyEricson bluetooth headset hbh-ds200. I have tried to look for answers in other forums but with no luck, might be that I am a total newb concerning linux and ubuntu that's why I can't find anything relevant to my problem.
So please somebody help me/us 
/kalle

---

### Post by oiper on 2008-05-01
I'm fairly certain that you can ignore that obex error. From what I understand, it's an error saying that it can't browse your device, which since it's a headset, doesn't matter.

On the other hand, getting any further with a headset in Hardy, seems not too possible at this moment. I've yet to get mine working fully.

---

### Post by damis648 on 2008-05-01
This is easy to fix. Just right click the bluez icon and select "Preferences". Go to the "services" tab and check the "audio" service. Make sure that is selected, then click "add" at the bottom. Select your device and let is connect. Thats all :)

---

### Post by vladi11 on 2008-05-16
> **damis648 said:**
> This is easy to fix. Just right click the bluez icon and select "Preferences". Go to the "services" tab and check the "audio" service. Make sure that is selected, then click "add" at the bottom. Select your device and let is connect. Thats all :)

It doesn't work.
I was unable to connect the headset (LG HBS-200) to any media player / skype etc. :(

---

### Post by balagosa on 2008-05-16
hmmm....had this problem but it was syncing with my Sony Ericsson phone though.

did you try installing "obex-ftp-server" from synaptic??

---

### Post by hihihi on 2008-05-24
hi,
obex files are meant for communication between pc and moile phone, to access its directories and such.
if you want your headset to work you have to create a new sound-device,
check out this link, might help you:
[http://ubuntuforums.org/showthread.php?t=786640](http://ubuntuforums.org/showthread.php?t=786640)

---

