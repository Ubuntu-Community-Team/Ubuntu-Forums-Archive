---
title: "Logitech USB headset not working"
date: 2008-11-01
forum: General Help
---

### Post by aliov_85 on 2008-11-01
Hello

I can't get my logitech heaset work under Intrepid Ibex.

>  /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf9ef4000 irq 22
 1 [Headset        ]: USB-Audio - Logitech USB Headset
                      Logitech Logitech USB Headset at usb-0000:00:1d.3-2, full speed

nazanin@alilaptop:~$ cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 1- 0]: digital audio playback
  5: [ 1- 0]: digital audio capture
  6: [ 1]   : control
  7: [ 0- 2]: digital audio capture
  8: [ 0- 1]: digital audio playback
  9: [ 0- 1]: digital audio capture
 10: [ 0- 0]: digital audio playback
 11: [ 0- 0]: digital audio capture
 12: [ 0]   : control





Thanks in advance for any advice

---

### Post by aliov_85 on 2008-11-01
Also under System-Preferences-Sound, when I want to "test" "Logitech USB headset" I get the following error:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback

---

### Post by jnnnnn on 2008-11-18
(please ignore this post - see below)


[http://linuxowns.wordpress.com/2008/07/08/how-i-got-my-usb-headset-to-work/](http://linuxowns.wordpress.com/2008/07/08/how-i-got-my-usb-headset-to-work/)

Note: The below instructions are somewhat technical; they provide additional information to the link above.  The above link has very clear instructions.


Basically comes down to 

sudo apt-get remove pulseaudio --purge

Unfortunately this also removes the ubuntu-desktop package so you might have problems later with distribution upgrades... but you can always add that package (and pulseaudio) back in for the upgrade.

Skype works for me as well (I had to change "Sound Devices | Sound Out " to "Logitech USB Headset (hw:Headset,0)").

You may have to run asoundconf-gtk (install it using Synaptic if you haven't got it) and choose Headset.  Rebooting may also be necessary.  You can use this to switch between usb headset output and your normal soundcard.

Flash works too.

---

### Post by kostkon on 2008-11-18
> **jnnnnn said:**
> [http://linuxowns.wordpress.com/2008/07/08/how-i-got-my-usb-headset-to-work/](http://linuxowns.wordpress.com/2008/07/08/how-i-got-my-usb-headset-to-work/)

Note: The below instructions are somewhat technical; they provide additional information to the link above.  The above link has very clear instructions.


Basically comes down to 

sudo apt-get remove pulseaudio --purge

Unfortunately this also removes the ubuntu-desktop package so you might have problems later with distribution upgrades... but you can always add that package (and pulseaudio) back in for the upgrade.

Skype works for me as well (I had to change "Sound Devices | Sound Out " to "Logitech USB Headset (hw:Headset,0)").

You may have to run asoundconf-gtk (install it using Synaptic if you haven't got it) and choose Headset.  Rebooting may also be necessary.  You can use this to switch between usb headset output and your normal soundcard.

Flash works too.
I don't think that's a good solution.


*aliov_85* you should install the *PulseAudio Device Chooser* (the package is called *padevchooser*). It will add a menu entry in *Applications &#8594; Sound & Video*.

Run it and it will put its icon in your taskbar. Left-click on it and select *Open Volume Control*. From there you will be able to select which audio device an application will use to output its sound.

For example, if you run *Totem*, then you will see its stream in the *Playback* tab. Right-click on it and select *Move Stream...* In the list that will appear you will see all of your audio devices (in your case your soundcard and your USB headset). You can then select the one you want to send the application's sound to.

Also, in the *Output Devices* tab you can set which device you want to be the default in your system. In this tab you should see your soundcard and headset listed. If, for example, you want to set your headset as the default device, then right-click on it and enable the *Default* option.

You can make *PulseAudio Device Chooser* to start every time you login from its preferences (i.e. left-click on its icon and select *Preferences*).

For the above to work, you should set all of your outputs in *System &#8594; Preferences &#8594; Sound* to *Autodetect*.

Hope that helps.

If you need some more help about this, don't hesitate to ask here.

---

### Post by jnnnnn on 2008-11-18
Thanks kostkon, that is a better solution.

I almost got there but I didn't realize how to set the default device. 

To get skype to use the Logitech headset set skype's sound devices options to sound in: headset (plughw), sound out and ringing to 'pulse'.

---

### Post by Eckman on 2008-11-25
I dont even see my Logitech USB headset as an option. THeres nothing there.
I listed out asound and there wasnt anything in the list.

---

### Post by djdarrin91 on 2008-11-25
Have you tried to edit /etc/modprobe.d/alsa-base and change the line



options snd-usb-audio index=-2

to



options snd-usb-audio index=0   ?

---

### Post by Eckman on 2008-11-25
Yep that worked. Thankyou.

---

### Post by JamesGarry on 2008-11-25
The follwing link has very clear instructions.
[http://linuxowns.wordpress.com/2008/07/08/how-i-got-my-usb-headset-to-work/](http://linuxowns.wordpress.com/2008/07/08/how-i-got-my-usb-headset-to-work/)

---

### Post by djdarrin91 on 2008-11-25
You are very welcome my friend:)

---

### Post by doyouhas on 2008-11-25
I had this exact problem with my sound card and my Logitech headset. They really need to add support to detect and change those settings automatically upon install, because for 98% of people sound is a necessity.

---

