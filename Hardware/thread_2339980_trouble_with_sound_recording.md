---
title: "trouble with sound recording"
date: 2016-10-14
forum: Hardware
---

### Post by Lloydb39 on 2016-10-14
[COLOR=#000000]I use a Logitech webcam for audio and video recording, and using Skype. The video seems to still be working and the sound output is fine, but for some reason it won't record sound. Pulse Audio says it is unplugged but I don't think it is. Webcam is hooked up to USB port as always. Can someone advise how to trouble shoot?  I moved this from another forum where I think I had it misposted.[/COLOR]

---

### Post by RobGoss on 2016-10-15
What version of Ubuntu are you using? If you're using **16.04,** there should be a sound icon at the top of your desktop, **click **on the **sound icon,** then choose the **sounds settings, **from there see if your sound device is listed

---

### Post by Lloydb39 on 2016-10-16
It lists a 081a microphone under "input". Speaking makes the sound indicator (at 100 %) light up, but only two bars. Pulse Audio shows the same. It is set at "built in analog stereo" for input and has the choices front microphone, rear microphone and line in, in addition to the 081a, but says all are unplugged. I tried Audacity and it would not record anything. I haven't tried some of the remedies suggested for removing and reinstalling or messing with Alsa, because the output and video are working and I didn't want to screw that up too.

---

### Post by RobGoss on 2016-10-16
Hello, Just wanted to make sure what version of Ubuntu are you using? 

You can try changing the USB port for starters in some cases it's been known that some may not function as expected it's a good place to start

Let's start with the sound settings, open up your sound settings by clicking on the little sound** icon **at the top **right hand **corner of your desktop. Click on** Input - **tab make sure your input devices is listed and also not muted, if it's plugged in and working correctly it should be listed, now close the sound settings and move on to the next step

When using Audacity you need to make sure your device is set as **default **in order for the sound to be recorded each system maybe different there are a few things to consider

**First:** Open up **Audicity, **at the top left side of **AUD **you will see a few options listed for the drop menu's right below play buttons, place your **cursor **over the **second **drop down menu it should say **Recording device, **click on the menu and make sure the device you're using to record with is listed from that drop down menu. 

**Second: **Now move your cursor over to the** fourth** menu it should say  **Playback device,** I have mine set to default it should allow your device to record after that you can run a few test to see if it is recording correctly.

**NOTE: **If all else fails open up your terminal and run this command: it will open up the **Alsamixer **for sound control

```
alsamixer
```

Make sure all the volumes are in the** red** so your sounds can be heard, use the arrows on your keyboard to navagate each one I've noticed many times for some reasons they are lowered to the lowest level not sure how.


With Audicity you sometimes have to make sure the right devices are added once that's done you should be good to go

Hope this helps

---

### Post by Lloydb39 on 2016-10-17
I am using 16.04. The problem began after I upgraded. Well, followed your instructions. In Alsamixer I found master and front mic too low. Bumped them up to red and I'm now able to record on Audacity and the Skype test call plays back my recording, so I think I'm fixed. Thank you very much.

---

### Post by RobGoss on 2016-10-17
Glad  I could help if your sound is effected in the future keep the Alsamixer in mind

If your issue is resolved you can mark this thread as solved, use the **Thread tool **at the top of this post

---

