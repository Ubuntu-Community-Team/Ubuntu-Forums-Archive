---
title: "After upgrade 904 to 910 - no Sound"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by webrp on 2009-11-11
Hi,

After an upgrade I lost sound from my Ubuntu. No sound on start up, no sound on videos, no sound anywhere.
I went intomenu on system-preferences-Sounds and it seems that no hardware is currenlty installed, but not sure 

What should I do?

---

### Post by RedSingularity on 2009-11-11
Have pulseaudio installed?  Pulseaudio Device Chooser?

---

### Post by RedSingularity on 2009-11-11
Oh and before anything else type this in terminal and check your sound levels.

gnome-volume-control

---

### Post by webrp on 2009-11-11
Hi,

-Have pulseaudio installed?  Pulseaudio Device Chooser? 
Sorry, dont know that. 

-Oh and before anything else type this in terminal and check your sound levels. gnome-volume-control     
Thats ok, sound levels are enabled and high, and columns theyrself are turned on. I have nothing in the "hawdware" tab wich dont know if its normal. And by the way my soundcard is onboard

This was working ok before upgrade, 

More tips?

---

### Post by RedSingularity on 2009-11-11
Ok to install pulse volume control do this

sudo apt-get install pavucontrol

Then look in Sound and Video section and select pulseaudio volume control.  Make sure everything is up and nothing is muted.

---

### Post by michaelzap on 2009-11-11
If you have a proprietary modem driver listed in System -> Hardware Drivers try removing it. That immediately made my sound card appear in the Sound panel. Before that all I saw was "Dummy Output".

---

### Post by webrp on 2009-11-11
So I did the command...
sudo apt-get install pavucontrol 
and then went to applications>sound&video>pulseaudio nothing is mutted, everythings enabled. Just like other similar menu I have on bottom right corner with a sound icon. So what was this coomand for, installing a second sound software?

Still no sound.

---

### Post by RedSingularity on 2009-11-11
That was just the control panel for the pulseaudio sound server.  Your settings are correct it sounds.

See if pulseaudio is installed "sudo apt-get install pulseaudio"

---

### Post by webrp on 2009-11-11
I runned that command, its already instaled, yes.
thanks for trying to help me, but no way...

What could have happen in upgrading procces? why did the upgrade caused my sound go off?

---

### Post by RedSingularity on 2009-11-11
Maybe your card was not supported in the new kernel.  One more thing though. 

Run "sudo apt-get autoremove --purge pulseaudio"

Then reboot and see what happens.  

PS:  Check in system>prefs>sound yet?  There is a sound test there.

---

### Post by webrp on 2009-11-11
I did that command and reboot. Still no sound and speaker volume icon is gone too.
I reinstalled pulseaudio in synaptic.

More tips?

---

### Post by michaelzap on 2009-11-11
> **webrp said:**
> More tips?

Did you try [my suggestion]("http://ubuntuforums.org/showpost.php?p=8297911&postcount=6")?

There are some other good tips [here]("http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html").

---

### Post by webrp on 2009-11-11
sorry michaelzap,
Yes I did check that. My system>administratio>hwdrivers is empty

---

### Post by TonyLB on 2009-11-18
I've had exactly the same sort of problem but I can go one better:evil:      Totem and iPlayer have no volume, but Xine and vlc both do, along with amarok.

I also removed the nvidia driver to see if that was the problem.  It wasn't, and to make metters worse now I can't reinstal/activate the nvidia driver.

I still haven't managed to sort either of these issues out.

Much more and I'll reinstall 9.04  :mad:

Tony

---

### Post by webrp on 2009-11-18
linux+drivers=hell

---

### Post by TonyLB on 2009-11-18
True.

I removed pulseaudio and most things seemed to work, as I said above.  Put it back again and it all stopped.  Now I've purged it again and only totem and iPlayer fail on the sound.  Still won't reinstall the nvidia driver though.

Tony

---

### Post by Henzor on 2009-11-18
I got some problems with my sound to after upgrading from 9.04 to 9.10.
Can't get sound in audioprograms such as Amarok and Kaffeine. 
I get this message when I start up Amarok and Kaffeine (translated from norwegian): 
**Phonon: KDE's multimedialibary**
Soundplaying unit C-Media CMI8738 (model 55) (C-Media PCI DAC/ACD) doesn't work. Go back to default.

---

### Post by AlanR8 on 2009-11-18
> linux+drivers=hell

Really?

Not in my experience.

Upgrading from a previous version (IMHO PLEASE NOTE) is NOT the way forward. Backup and fresh install. 

Saves so many problems........

Posted from my Sony Vaio (Propriety hardware), connected to the web via Blue tooth and 3.5G courtesy of my Nokia Navigator mobile phone. Driver issues....don't think so!!:p

---

