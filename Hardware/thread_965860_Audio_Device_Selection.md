---
title: "Audio Device Selection"
date: 2008-10-31
forum: Hardware
---

### Post by michaelfeb16 on 2008-10-31
This is my third run ubuntu in three years, and I am getting close to putting Vista back on. The first time it was an inability to select resolutions easily, the second time it was wireless, and this time it is audio.

While I am happy that the first two problems have been taken care of, I can't get over this third one. I want to love ubuntu. I really do. I love everything else open source....but it seems that is only because I have for years run it on windows which seems capable of using, you know, computer hardware.

Anyway, to the specifics..
I am currently running 8.10 on a laptop and a desktop. Both had their standard audio (creative card for the desktop and internal for the laptop) work at install.

Now, when I plug in a USB headset (any model really, I have used four so far) in either, I get spotty performance at best. Some applications automatically use it, some use it if I go to system->preferences->sound, some work if Bob Smith three states away is in a good mood, and others never work at all.

I've been through dozens of "guides" to fixing this and none have done anything. So I come here for help...
Is there a way to beat this OS into doing something so-simple-windows-can-do-it, and if so where is it?

More important to me is...what excuse could there possibly be for this being such a hassle? Why can I not go into Sound select a device, and set as default across all applications?

---

### Post by kostkon on 2008-11-01
> **michaelfeb16 said:**
> This is my third run ubuntu in three years, and I am getting close to putting Vista back on. The first time it was an inability to select resolutions easily, the second time it was wireless, and this time it is audio.

While I am happy that the first two problems have been taken care of, I can't get over this third one. I want to love ubuntu. I really do. I love everything else open source....but it seems that is only because I have for years run it on windows which seems capable of using, you know, computer hardware.

Anyway, to the specifics..
I am currently running 8.10 on a laptop and a desktop. Both had their standard audio (creative card for the desktop and internal for the laptop) work at install.

Now, when I plug in a USB headset (any model really, I have used four so far) in either, I get spotty performance at best. Some applications automatically use it, some use it if I go to system->preferences->sound, some work if Bob Smith three states away is in a good mood, and others never work at all.

I've been through dozens of "guides" to fixing this and none have done anything. So I come here for help...
Is there a way to beat this OS into doing something so-simple-windows-can-do-it, and if so where is it?

More important to me is...what excuse could there possibly be for this being such a hassle? Why can I not go into Sound select a device, and set as default across all applications?
Since most of the sound in *Ubuntu* is now controlled by *PulseAudio* (I am saying mostly, since some apps don't work with it yet) then you could try to control which device an application uses to  output its sound through it.

Thus, you will need to install the *PulseAudio Device Chooser* utility (the package is called *padevchooser*).

After you run it (it will create a menu item in *Applications -> Sound & Video*) you will see its icon appearing in your taskbar. Left-click on it and select *Volume Control*. In the *Output Devices* tab you should see your soundcard(s) and your headset(s). You can right click on the one you want to set as the default and enable the *Default* option. This will make it the default device to be used by your applications.

That's one problem solved.

Now, you can easily select which device your applications use output their sound individually. This is very handy, since you may want some apps to use your headset and some your soundcard (i.e. speakers) or another headset, etc.

This can be done easily. For example, if you run *Totem*, select the *PulseAudio Volume Control*, as above, and in the first tab (*Playback*) right click on its stream and you should be able to see all your devices in the list that appears. Thus, you can now, for example, send its sound from your one headset to the other, or from your soundcard (i.e. speakers) to your headset. *PulseAudio* will remember your selections the next time you run this same application (in our example, *Totem*).

Thus, you can have a great flexibility of controlling the devices that your applications use to output their sound. You can even output a sound to two or more devices at the same time...

Also, you get individual volumes per application.

You can make the *PulseAudio Device Chooser* to start automatically when you login from its preferences (left-click on its icon, select *Preferences*).

For this to work, you will have to set your Sound Playbacks in *System -> Preferences -> Sound* to *Autodetect*.

Hope that helps you...

If you have any questions regarding the above I wrote don't hesitate to ask here...

---

### Post by michaelfeb16 on 2008-11-05
*Thank you!*

You have answered my questions in a simple manner without being condescending. You are my hero. hahah



Seriously, my problems are fixed. I already had PulseAudio Applet installed, but I had not been able to find it. I never looked for it there because, by my intuition, it should be expected to be in preferences or administration. (I still don't know why it isn't..?)

Once more, thank you!

---

### Post by arkhitekton on 2008-12-07
Hi Kostkon,

This was a very useful post.  Thank you.  :KS

I've been trying to get a Creative Sound Blaster Audigy 2 ZS Notebook pcmcia card working with Ubuntu 8.04 Hardy Heron on a Dell Inspiron 9100.  I've been searching for solutions for some time.  I found your post, installed the PulseAudio Device Chooser and everything works!  I can map different applications to the internal Intel device or Audigy or both. I am now able to get 2-channel audio out of the headphone socket via 3.5mm jack plug and 2-channel audio out via the optical fiber socket as well.

Why these applications are not part of the default installation is beyond me?  Your post, or certainly its information should be made more promenent as there does not seem to be much information on the default sound/audio arrangements in the various releases of Ubuntu - or not that I could find.

Thanks, again.

Arkhitekton

---

### Post by atish on 2009-02-15
> **kostkon said:**
> 

After you run it (it will create a menu item in *Applications -> Sound & Video*) you will see its icon appearing in your taskbar. Left-click on it and select *Volume Control*.

Hello...I still have a problem. 
In my PulseAudioDeviceChooser.....Volume Control, Manager, Volume Meter, Configure Local Sound Server appear as disabled. I can not click on them.

So how to proceed ?

Thanks,
- Atish .

---

### Post by cliff01 on 2009-02-18
Thanks for taking the time to post this info. I had no idea. I'll try this when I get home tonight and let you know.

---

### Post by chris319 on 2010-02-07
> This can be done easily. For example, if you run *Totem*, select the *PulseAudio Volume Control*, as above, and in the first tab (*Playback*) right click on its stream and you should be able to see all your devices in the list that appears. Thus, you can now, for example, send its sound from your one headset to the other, or from your soundcard (i.e. speakers) to your headset. *PulseAudio* will remember your selections the next time you run this same application (in our example, *Totem*).First it should be pointed out that PulseAudio works by stream, not by device as with other OSs. You don't select a specific device as the default for all audio operations. Second, it should be mentioned that a stream has to be *running*, otherwise there is nothing to allow device selection. Third, there is now a button to the right of the stream name which lets you select the device.

---

### Post by CosmicEnergy on 2011-03-14
Finally this fixed my no playback problem on 10.10! Thanks a bunch!

---

### Post by jcottier on 2011-05-13
I just tried this with a plug in USB headset. But it locked up the PC solid after it was unplugged. I tried it again after a forced power down (not even Ctrl+Sysreq+etc would function). It did exactly the same thing. Always works fine without PulseAudio Device Chooser, except that I have to manually select audio input for the headset. I will report this as a (very nasty) bug.

---

### Post by jcottier on 2011-05-13
Apparently this package has bugs going back 3 years, and no new versions since Hardy Heron.

---

