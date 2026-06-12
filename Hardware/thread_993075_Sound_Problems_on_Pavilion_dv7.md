---
title: "Sound Problems on Pavilion dv7"
date: 2008-11-25
forum: Hardware
---

### Post by jlochhead on 2008-11-25
Hi,

I recently bought a new HP Pavilion dv7 and decided to install Ubuntu 8.10 on it. Everything seems to be working fine except for the sound.

Initially, the welcome sound was repeating many times on the login screen. Then, when I was fully logged in and trying to play some music in totem/rythmbox an error message was appearing.

From googling the problem I found that updating to the latest version of alsa might help. During the "make install" part of the installation there was something said about the alsa volume being set to zero by default.

Anyway, after installing the alsa driver and restarting my system the welcome screen was not playing any sound at all and the media players were no longer displaying an error message. Totem now acts normally except no sound comes out and rythmbox goes non-responsive.

I did some more googling and a command that took me into alsa mixer, the volume appeared to be on so I have no idea what the previously mentioned warning was on about. 

I also tried VLC to see if the problems were just on the totem/rythm; it didn't work either.

According to lspci I have :

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

Pretty much exhausted all the useful threads that I can find now. Has anyone got any ideas?

Please post if you need any additional info from my ubuntu install.

P.S. I am new to Linux. Oh and sorry about the waffle.

Thanks in advance,

James

---

### Post by ohingst on 2008-11-25
Hi James,

I just registered to tell you that you need to add the following line in /etc/modprobe.d/alsa-base (right at the bottom).

options snd-hda-intel enable_msi=1

I have a HP DV7 1020ea and this worked.

---

### Post by jlochhead on 2008-11-26
Great, this worked perfectly after I did a clean install, changed the file and rebooted.

Thank you.

---

### Post by neira on 2008-12-09
hi,
i have a HP pavilion dv7 1195eg notebook, and linux is running on it.
Everything runs fine, but i dont have a sound :/.
I have sound on start up, but when its starts its not working.
thanks in advance
Neira

---

### Post by jlochhead on 2008-12-13
You are better off starting a new topic on the subject if the above fix does not work, you will get a better response.

However, in case you mean you don't understand how to try the above fix, here it is in more user friendly steps:

1) Press Alt+F2, type in gnome-terminal and press enter.
2) In the terminal: type sudo gedit /etc/modprobe.d/alsa-base
3) In gedit: Scroll to the bottom of the file and add the new line:
    options snd-hda-intel enable_msi=1
4) Save the file and close gedit (you can now also stop the terminal).
5) Reboot the computer.

If the sound is working then there you go, otherwise I suggest you remove the line by adapting the steps above.

Note: I this may not work if you have been fiddling with alsa before you try it, It might be worth doing a clean install and then trying it. This was the case for me.

Good luck.

P.S. I have been distro hopping recently and I believe this method may work for other distros with sound problems on the dv7 1020ea.

---

### Post by ericmc783 on 2008-12-14
Greetings,

i have a HP DV7-1025nr, and I just wanted to say that the fix presented in this thread worked for me.

It was actually more hassle getting the sound to work in XP than it was in Ubuntu. Just goes to show, that when you give it time, there is very little that the ubuntu community can't tackle.

-------------------------

Also, I thought it may help if I shared the settings I'm using for the audio on my HP.

In System | Preferences | Sound:

Sound Events - Sound Playback: Autodetect

Music and Movies - Sound Playback: Autodetect

Audio Conferencing - Sound Playback: Autodetect

Sound Capture: HDA Intel STAC92xx Analog (ALSA)

Default Mixer Tracks - Device: HDA Intel (Alsa Mixer).
(Select "Front" as the track to control with the keyboard).

After setting this, right-click on the speaker icon (usually at the top-left of the screen), and select "Open Volume Control". Click the Preferences button and Check ALL of the choices given to you. Click CLOSE, and now in the volume control, you should see a new tab that says switches. Go to that tab. Check "IEC958 Default PCM", and leave the other 3 options UNCHECKED. Using the Default PCM switch instad of the regular ICH958 seems to be the trick to getting audio working correctly. 

After doing this, go back to the playback tab. Set the PCM volume to at least 50% (you may want to go higher). Set the master volume to 100&, and the Front to 50%. You should now be able to hear sound properly. you can test this with the sound effects in system | preferences | sound. The volume buttons on your keyboard will adjust the audio for the front speakers, which seems to work better than using the Master, at least in my case. You can try using Master or PCM instead if you want.

Keep in mind that editing the alsa-base file (as decribed earlier in this thread) and rebooting should be done before editing any of these settings.

---

### Post by faind on 2009-02-17
> **jlochhead said:**
> 

1) Press Alt+F2, type in gnome-terminal and press enter.
2) In the terminal: type sudo gedit /etc/modprobe.d/alsa-base
3) In gedit: Scroll to the bottom of the file and add the new line:
    options snd-hda-intel enable_msi=1
4) Save the file and close gedit (you can now also stop the terminal).
5) Reboot the computer.


confirmed, it works for me :D thanks:KS

---

### Post by jaminux on 2009-03-04
... quite a while later ...

I am still using the command that Ohingst originally gave me.

A quicker way to do it would be:

1) Open a terminal.

2) Type sudo -i, press enter and enter your password. Follow this mini-guide exactly after doing this. Using sudo like this can be dangerous and cause harm to your system if you do not know what you're doing.

Note: Tried to do this without using the -i paramater all in one command with echo. Didn't work. Any ideas why?

3) Type echo "options snd-hda-intel enable_msi=1" >> /etc/modprobe.d/alsa-base and then press enter.

4) Type exit and restart the computer.

---

### Post by joce_psych on 2009-03-13
Bonjour
I bought myself a Hp Pavillon d7 today, I had the weird startup problem on the onset of Ubuntu 10,  the following command worked for me... What a great community!! Keep up the good work!

1) Press Alt+F2, type in gnome-terminal and press enter.
2) In the terminal: type sudo gedit /etc/modprobe.d/alsa-base
3) In gedit: Scroll to the bottom of the file and add the new line:
options snd-hda-intel enable_msi=1
4) Save the file and close gedit (you can now also stop the terminal).
5) Reboot the computer.

cheers
Joce

---

### Post by James_Lochhead on 2009-03-27
**Intro**

Hello everyone. I use this thread quite a lot (re-install quite a bit) and I thought I would update it with info on doing this in Jaunty.

In Jaunty the name of the file has been changed, so here are the Jaunty commands as well as the Intrepid/Hardy ones:

**For Jaunty:**

1) 

Open Applications > Accessories > Terminal.

2) 

Type:
```
sudo -i
``` 
Then press enter and enter your password.

3) 

Type: 
```
echo "options snd-hda-intel enable_msi=1" >> /etc/modprobe.d/alsa-base.conf
``` 
Then press enter.

4) 

Type: 
```
exit
``` 
Then press enter, close the window and restart the computer.

**Note: It is important that you type exit or close the window. You must not leave root terminals lying around.**

*Summary for advanced users:*
```

sudo -i
echo "options snd-hda-intel enable_msi=1" >> /etc/modprobe.d/alsa-base.conf
exit

```

**For Intrepid & Hardy:**

1) 

Open Applications > Accessories > Terminal.

2) 

Type:
```
sudo -i
``` 
Then press enter and enter your password.

3) 

Type: 
```
echo "options snd-hda-intel enable_msi=1" >> /etc/modprobe.d/alsa-base
``` 
Then press enter.

4) 

Type: 
```
exit
``` 
Then press enter, close the window and restart the computer.

**Note: It is important that you type exit or close the window. You must not leave root terminals lying around.**

*Summary for advanced users:*
```

sudo -i
echo "options snd-hda-intel enable_msi=1" >> /etc/modprobe.d/alsa-base
exit

```

---

### Post by ericmc783 on 2009-07-03
UPDATE:

Using 9.04, The sound does work on my dv7t, but it only comes out of the left speaker. 

However, when using headphones or external speakers, sound works correctly.

The steps I took were upgrading the alsa-driver to the latest version (1.0.20) and adding the options snd-hda-intel enable_msi=1 line as described above. I have never been able to get sound to come out of the right side, or sub-woofer.

Ironically, it acted the exact same way in Windows XP (laptop shipped with Vista).

I should also mention that there are random times where I can get no sound at all, an the only solution is to reboot.

---

### Post by joshjh on 2009-08-13
I had ubuntu 8 and now just downloaded 9. Both i had/have no sound. I tried the fix posted earlier btu when i type sudo gedit /etc/modprobe.d/alsa-base it opens a blank document am i missing something?

---

### Post by michaeljbergin on 2009-08-16
> **joshjh said:**
> I had ubuntu 8 and now just downloaded 9. Both i had/have no sound. I tried the fix posted earlier btu when i type sudo gedit /etc/modprobe.d/alsa-base it opens a blank document am i missing something?

The file name is now /etc/modprobe.d/alsa-base.conf, don't forget the .conf.

---

### Post by Daniel Libonati on 2011-06-14
Hey fellas, i tried enable_msi=1 but I couldn't get my subwoofer to work. I have a DV7t-4100.

Instead of that I just added:

options snd-hda-intel model=ref

and now I have the subwoofer working, though it sounds louder than what it does on Windows, you'll have to keep your PCM volume lowered. Just give it a try.

---

### Post by rmerren on 2011-07-28
I have an HP Pavilion dv7-4073nr.  I have found that out-of-the-box (meaning after installing Ubuntu and without changing any settings), the sound system works fine EXCEPT for the subwoofer.  I was able to get that working by adding the following line to  /etc/modprobe.d/alsa-base.conf:
```
options snd-hda-intel model=ref
```Based on other forum answers and bug reports I had previously tried all of the following without success:
```
options snd-hda-intel model=dell-m4-2
options snd-hda-intel enable_msi=1
options snd-hda-intel model=hp-dv5
```The above alsa-base.conf change works perfectly except for one annoying flaw: when I plug the headphones in, the subwoofer does not shut off.

To resolve this, I use the alsa mixer.  (You can install it from the reps as gnome-alsamixer.)  When I plug the headphones in, I have to open alsa mixer and turn the volume down on the "Front", which keeps the woofer volume down.  If I adjust the volume with the dropdown on the panel, the woofer comes back on, so with headphones plugged in I have to use alsa mixer to adjust the volume.

Without headphones plugged in, the system works exactly as expected--the volume knobs work and the sound (including the woofer) pounds out quite nicely.  With headphones plugged in, I have to use the alsa mixer.

If anyone has a suggestion for ensuring that the subwoofer is tied to the rest of the speakers so that it shuts off and volumes properly, I would love to hear it and test it out!

For the record, when I do a ```
lspci | grep Audio
``` I get the following:
```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
```

---

