---
title: "problem with sound card"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by mulligan on 2009-08-30
i run 8.04 and i cannot get the sound to work. i have looked at some old posts and found that alsa will help. i have downloaded all of the alsa that show in synaptic. it still does not work. any suggestions.

---

### Post by tgeer43 on 2009-08-30
It's likely to just be a configuration issue but you don't give any information beyond "i cannot get the sound to work."

Have you opened up the volume control applet to make sure that nothing is muted or turned way down?

Have you check the sound configuration in System->Preferences->Sound? It even has 'Test' buttons so you can see if any changes you make have the desired effect.

There's an excellent sticky thread in the Multimedia & Video forum for troubleshooting sound problems. It's located here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

All of the above should give you a good starting point at least.
If you still can't resolve your issue then post back here but please give us a little information to go on and tell us what you've tried already so we don't try to reinvent the wheel.

tgeer

---

### Post by mulligan on 2009-08-31
> **tgeer43 said:**
> It's likely to just be a configuration issue but you don't give any information beyond "i cannot get the sound to work."

Have you opened up the volume control applet to make sure that nothing is muted or turned way down?

Have you check the sound configuration in System->Preferences->Sound? It even has 'Test' buttons so you can see if any changes you make have the desired effect.

There's an excellent sticky thread in the Multimedia & Video forum for troubleshooting sound problems. It's located here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

All of the above should give you a good starting point at least.
If you still can't resolve your issue then post back here but please give us a little information to go on and tell us what you've tried already so we don't try to reinvent the wheel.

tgeer

hi i have been following the tutorial in the link and got to the part where i was reinstalling part of the kernel. then i got this response.

morgan@morgan-desktop:~$ sudo apt-get install linux-sound-base alsa-base alsa-utils
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
morgan@morgan-desktop:~$ 

any ideas?

---

### Post by tgeer43 on 2009-08-31
I would do what it's telling you:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```I mean, you've come this far already, haven't you?
I can't very well recreate the problem here so I say just go for it. If you continue to have problems then post back here and we'll take it one thing at a time.

tgeer

p.s. Although it's not stated, you need to run dpkg with sudo powers so the correct command will be:
```
sudo dpkg --configure -a
```

---

### Post by mulligan on 2009-08-31
> **tgeer43 said:**
> I would do what it's telling you:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```I mean, you've come this far already, haven't you?
I can't very well recreate the problem here so I say just go for it. If you continue to have problems then post back here and we'll take it one thing at a time.

tgeer

p.s. Although it's not stated, you need to run dpkg with sudo powers so the correct command will be:
```
sudo dpkg --configure -a
```

i did what you said and it said it worked i rebooted as it said and then this was displayed.

"error 
the panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet"
do you want to delete the applet from your configuration."

i also did the aplay -l and got this.

morgan@morgan-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI_1 [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
morgan@morgan-desktop:~$ 

do you have any further advice.

i will have a look at the later documentation on that thread to see if that will help.

thank you for your help so far.

---

### Post by tgeer43 on 2009-08-31
If dpkg configured correctly then you need to resume where you left off after getting the error message. I believe you were installing some alsa related packages at the time.

Did you let the system remove the Fast User Switching applet? If so, try adding it back to the panel. If not, try removing it then adding it back. You only need to do this if you actually use that applet. This is unrelated to your sound problem.

Let me know how things go.

tgeer

---

### Post by mulligan on 2009-08-31
> **tgeer43 said:**
> If dpkg configured correctly then you need to resume where you left off after getting the error message. I believe you were installing some alsa related packages at the time.

Did you let the system remove the Fast User Switching applet? If so, try adding it back to the panel. If not, try removing it then adding it back. You only need to do this if you actually use that applet. This is unrelated to your sound problem.

Let me know how things go.

tgeer

i removed the Fast User Switch applet. i followed the instructions below and i am up to general help step 4 on the link. i will reboot and see if it works.

---

### Post by mulligan on 2009-08-31
> **mulligan said:**
> i removed the Fast User Switch applet. i followed the instructions below and i am up to general help step 4 on the link. i will reboot and see if it works.

i went through the instructions on this link too. it did not work.

[http://ubuntuforums.org/showthread.php?t=1167232&highlight=xonar](http://ubuntuforums.org/showthread.php?t=1167232&highlight=xonar)

---

### Post by tgeer43 on 2009-08-31
I guess I should have asked you which sound card you have. It would have saved both of us a lot of time.

The ASUS Xonar DX is well known to be very problematic under Ubuntu. A few folks have gotten it working under 8.04 32-bit but that's about it.

I'm afraid that's about the extent of what I can do for you. Better folks than I have tried and failed. :(

tgeer

---

### Post by mulligan on 2009-08-31
> **tgeer43 said:**
> I guess I should have asked you which sound card you have. It would have saved both of us a lot of time.

The ASUS Xonar DX is well known to be very problematic under Ubuntu. A few folks have gotten it working under 8.04 32-bit but that's about it.

I'm afraid that's about the extent of what I can do for you. Better folks than I have tried and failed. :(

tgeer

yeah i suspected as much when i researched it but i thought it was worth a go. do you think it is worth updating to 9 or is that problematic too. also although i am new to ubuntu i am good with computers so if there was a way i would have done it. 

also i write computer software. i recently wrote a program that works out interest calculations etc. i noticed there is nothing like it in the ubuntu add remove. i was wondering if the people here would like a version of it for distribution. i am not a programmer by trade but i learned how to do it.

do you know what i would have to do to suggest it to someone.

thanks for your help.

---

### Post by tgeer43 on 2009-08-31
Re: upgrading - Generally speaking, upgrading is not problematic and often times (but not always) can resolve issues that you had with your previous release as the hardware and software compatibility continues to get better and better. You never mentioned which version you are currently running so be aware that you can only upgrade to 9.04 from 8.10. If you are running an even older version then you would have to upgrade to each successive release until you reach 9.04. In that case a fresh install would probably be a better option.

Re: your application - There is a highly structured process for submitting an app for inclusion in Ubuntu which I am not very familiar with. To start learning about it begin here:

[http://www.ubuntu.com/community/processes/newdev](http://www.ubuntu.com/community/processes/newdev)

For obvious reasons the developers are very selective about the packages that are included with a standard Ubuntu installation. A more realistic goal may be trying to get your application included in an official repository so users can add it to their installation if they so choose.

Best of luck,

tgeer

---

