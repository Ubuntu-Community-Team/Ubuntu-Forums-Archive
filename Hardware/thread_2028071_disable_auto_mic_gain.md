---
title: "disable auto mic gain?"
date: 2012-07-17
forum: Hardware
---

### Post by adelattre on 2012-07-17
I'm trying to use a Logitech H530 usb headset on my Thinkpad Edge13 running ubuntu 12.04 64 bit, and the automatic mic gain keeps pushing the mic volume to 100% [so, the volume is WAY too loud and picks up lots of background noise etc], even as I've turned it down in alsamixer and pulseaudio. I've searched, but been unable to find anything about how to disable the auto mic gain or otherwise fix this problem. 
sound card is:
andre@andre-ThinkPad-Edge:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

Any advice would be appreciated.
Thanks.

---

### Post by adelattre on 2012-07-19
bump

---

### Post by jmfal on 2012-07-19
Welcome to Ubuntu

Try installing pulse audio volume control:
```
 sudo apt-get install pavucontrol   
```

And to open
```
 pavucontrol
```

This should give you an option for your mic.

---

### Post by adelattre on 2012-07-19
> **jmfal said:**
> Welcome to Ubuntu

Try installing pulse audio volume control:
```
 sudo apt-get install pavucontrol   
```

And to open
```
 pavucontrol
```

This should give you an option for your mic.
Thanks for your reply.  What I meant by having tried to adjust the mic gain in 'pulseaudio' in my original post is just what you've suggested - pulse audio control.  It does indeed give me an option to regulate the mic level, but after I've done that, it automatically pushes the level back up to 100% [not immediately, but over about 20-30 seconds].  That is why I'm looking for some way to disable the auto mic gain feature.
Any advice on doing that would be greatly appeciated

---

### Post by jmfal on 2012-07-19
Open alsamixer
press F5
look for mic boost
and turn off (press m or M)
Leave alsamixer open
check if problem solved
if so
Press esc key
at command prompt enter
```
 sudo alsactl store
```
This will save alsamixer settings

---

### Post by jmfal on 2012-07-20
Take a look at this, go down to screenshots
[http://askubuntu.com/questions/131812/logitech-usb-headset-not-working-on-12-04](http://askubuntu.com/questions/131812/logitech-usb-headset-not-working-on-12-04)

---

### Post by adelattre on 2012-07-20
> **jmfal said:**
> Open alsamixer
press F5
look for mic boost
and turn off (press m or M)
Leave alsamixer open
check if problem solved
if so
Press esc key
at command prompt enter
```
 sudo alsactl store
```
This will save alsamixer settings
thanks for your continued effort to help me solve this.
Although I feel that I've seen a 'mic boost' option in alsamixer before, there is not one there now.  The tabs in alsamixer are:
Master
<Headphone>
Speaker
PCM
S/PDIF
Beep
Capture
Auto-Mut
Internal
<Internal>

so, I'm not sure if that is a problem, or one of the above is the functional equivalent of 'mic boost'.

---

### Post by adelattre on 2012-07-20
> **jmfal said:**
> Take a look at this, go down to screenshots
[http://askubuntu.com/questions/131812/logitech-usb-headset-not-working-on-12-04](http://askubuntu.com/questions/131812/logitech-usb-headset-not-working-on-12-04)
The screen shots that I see are of Pulseaudio Volume Control, and I've used that and can lower the headset mic input volume, but then as I've described it pushes itself back up to 100% - I can watch it happening with the PVC panel still open.

I have tried changing the level and then using the 'sudo alsactl store', but it still pushes the volume back up to 100% over a 20-30 second period [eg not all at once but gradually].

---

### Post by jmfal on 2012-07-20
Are you using skype or a similar app?

In the alsamixer press F5 and use right arrow key , sometimes there are controls farther to the right off screen. 
turn capture down a little bit.

---

### Post by adelattre on 2012-07-20
> **jmfal said:**
> Are you using skype or a similar app?

In the alsamixer press F5 and use right arrow key , sometimes there are controls farther to the right off screen. 
turn capture down a little bit.
I'm making calls via gchat/googleplus.
those are all of the options, even far to the right, off of the screen, when I press f5.
There is the option to press f6, which lets me select the sound card, and there is an option for my headset "Logitech USB Headset", and if I press that I get 3 tabs:  Speaker, <mic>, mic
the middle tab "<mic> is muted, and the "mic" tab controls the mic volume, and again I can set it low, but it automatically pushes it gradually back up to 100% again.

also, changing the level for "capture" doesn't change the level of mic input volume [back in the f5 menu]

---

### Post by jmfal on 2012-07-20
Ok  you'll have to experiment till we find a fix.
select the head set in alsamixer and set the mic controls to about 75
and use the 'sudo alsactl store" see if that helps
If not::
run this in a terminal
```
    aplay -l
```
and 
```
 lspci | grep  -i audio    
```

and post the output between the ]CODE][CODE] brackets using # above.

---

### Post by adelattre on 2012-07-20
to be clear:  when you say "select the headset in alsamixer", I'm assuming that you mean select f6 and then select the usb headset and then modify the mic level in those settings, THEN do "sudo alsactl store".
Doing that doesn't keep the mic input level from inching right back up as soon as I make a call.

out put from "aplay -l":

andre@andre-ThinkPad-Edge:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

out put from "lspci | grep -i audio"

andre@andre-ThinkPad-Edge:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

---

### Post by jmfal on 2012-07-20
Lets try this
Run this in a terminal, it will open the alsabase.conf file

```
gksudo gedit /etc/modprobe.d/alsa-base.conf    
```
Press enter
enter password, press enter
scroll to end of file
enter this line
```
  options snd-hda-intel model=auto      
```
Click save button
close file
In window click "etc" and save (must save to etc folder)
restart
test headset

---

### Post by adelattre on 2012-07-20
the last line of alsa-base.conf is already VERY similar to that.  It is:

options snd-hda-intel model=auto enable=yes

So, should I deleted "enable=yes" or add another line that is "options snd-hda-intel model=auto", or ?

---

### Post by jmfal on 2012-07-20
Sorry for taking so long to reply,yes leave the line as it is
Open sound settings and select capture and see if there are mic settings 
same with pavucontrol click on headset and check in drop dowm box for options

---

### Post by adelattre on 2012-07-21
> **jmfal said:**
> Sorry for taking so long to reply,yes leave the line as it is
Open sound settings and select capture and see if there are mic settings 
same with pavucontrol click on headset and check in drop dowm box for options
np.  I appreciate your help.
Perhaps I'm not understandingf your request, but I can see and use controls for the mic volume in the regular sound settings AND pulseaudio control [as well as alsamixer].  Changing any of those settings DOES change the input level, but then the auto mic gain feature kicks in and gradually raises the input volume back up to 100%.

---

### Post by jmfal on 2012-07-21
Hi
I don't know what to tell you
Every thing I've read says that you headset should work out of the box.
Plus all fixes that I found are outdated, so they probably won't work.
I'll keep on looking, so be patient

You can try the logitech website and see if you can find a driver for ubuntu or get on a chat and maybe they can recommend something.

---

### Post by strid3r on 2013-06-05
This is a problem with Google Voice not playing nice with the audio. 

Fix:

```
echo "audio-flags=1" >> ~/.config/google-googletalkplugin/
```


source: [http://joshmckibbin.com/stuff/stop-google-voice-from-auto-adjusting-the-mic-volume/](http://joshmckibbin.com/stuff/stop-google-voice-from-auto-adjusting-the-mic-volume/)

---

### Post by rolfp on 2013-07-14
> **strid3r said:**
> This is a problem with Google Voice not playing nice with the audio. 

Fix:

```
echo "audio-flags=1" >> ~/.config/google-googletalkplugin/
```


source: [http://joshmckibbin.com/stuff/stop-google-voice-from-auto-adjusting-the-mic-volume/](http://joshmckibbin.com/stuff/stop-google-voice-from-auto-adjusting-the-mic-volume/)

~/.config/google-googletalkplugin/ is a directory, dutifully reported by bash.  This should go in a file, afaik.  Has anyone else tried this?  Is there a valid file name to use?

In that directory, I have log files along with googletalkplugin_port and googletalkplugin_ws_port, the contents of which are &#65533;&#65533;137Oqo1Cjvygd/6p and "&#65533;yLnrw/XRlI+Qdn5/ respectively.  

Thanks.

---

### Post by SorryGoFish on 2013-12-04
> **rolfp said:**
> ~/.config/google-googletalkplugin/ is a directory, dutifully reported by bash.  This should go in a file, afaik.  Has anyone else tried this?  Is there a valid file name to use?

In that directory, I have log files along with googletalkplugin_port and googletalkplugin_ws_port, the contents of which are &#65533;&#65533;137Oqo1Cjvygd/6p and "&#65533;yLnrw/XRlI+Qdn5/ respectively.  

Thanks.

It looks like it should go in `~/.config/google-googletalkplugin/options` though I don't know if it will work.

---

