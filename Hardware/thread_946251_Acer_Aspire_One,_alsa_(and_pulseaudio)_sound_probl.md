---
title: "Acer Aspire One, alsa (and pulseaudio?) sound problem"
date: 2008-10-13
forum: Hardware
---

### Post by aykito on 2008-10-13
I have a Acer Aspire One 150L laptop, and I have installed the Ubuntu-eee distribution, which makes almost everything run out of the box.

One of the things not working is the sound. 
Despite the alsa drivers should support the hardware, I can't make all work (microphone, speakers, earphones...) and keep it working after suspend.
There is a lot of information in forums to making it work but so far for some reason every method is failing.
As described in [https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne")
After rebuilding ALSA, and editing the file **/etc/modprobe.d/alsa-base**, the only configuration option with sound working is:
```
options snd-hda-intel model=acer
```
The behaviour is anyway funny. Running in the console
```
aplay -Dplughw:0,0 -fcd /usr/share/sounds/question.wav
```
works only sometimes. Running the command twice in a row makes it work the second time. And reproducing a video the sound is working only after a couple of seconds. The impression is that there is some king of buffer and only when it is full, the sound starts.
Unfortunately the internal microphone is not working, neither after configuring the properties with **alsamixer**.
The options
```
options snd-hda-intel model=auto
options snd-hda-intel model=basic
```
Do not even make sound work...

I have reinstalled the newest version of the alsa drivers (1.018rc3), both with the script found in [http://ubuntuforums.org/showpost.php?p=5792918&postcount=104]("http://ubuntuforums.org/showpost.php?p=5792918&postcount=104"), and also directly with the options
```
./configure --with-cards=hda-intel --with-sequencer=yes&&make&&make install
```
At some moment after installing sound and micro did work (I don't remember which which 'options snd-hda-intel model=XXX') but not after suspend.
I was doing some tries more with the '**options snd-hda-intel model=XXX**' (also without that line) to fix the suspend issue but now I'm not even able to reproduce the state of micro and sound working before suspend!.

What I find very strange is that right after login (my system is configured to do it automatically), the login sound IS WORKING. But right after I can't hear anything anymore.
But if it is a problem in the drivers, the sound should **never** work!
To make the sound work I have to write
```
sudo alsa force-reload
```
And the, independently of the 'options snd-hda-intel model=XXX' everything is working perfectly (micro, speakers, aux output...).
I have compared the list of processes before and after the '**alsa force-reload**' and the only difference is that right after two processes are missing:
>  5801 ?        00:00:01 pulseaudio
 5804 ?        00:00:00 gconf-helper
Both are PulseAudio modules. It could be that Pulse Audio is blocking the sound, but killing and restarting pulse audio with:
```
pulseaudio -k
pulseaudio -D
```
Does not fix anything if the sound is not working, and does not break the sound if it is working before.
By the way, when starting PulseAudio ('**pulseaudio -D**') I can read the output:
> W: core-util.c: setpriority(): Permission denied

I have been checking the system logs and I have found problems with both alsa and pulseaudio:
In kern.log
> Oct 13 07:56:32 david-aa1 kernel: [  372.348188] alsactl[7608]: segfault at 00000000 eip b7cef283 esp bf89050c error 4
(several times)
In messages
> Oct 13 07:51:24 david-aa1 pulseaudio[5860]: core-util.c: setpriority(): Permission denied

Is it a problem with the alsa drivers? But then I couldn't hear the login sound!
Is it a problem with the alsa configuration? But then 'alsa force-reload' should not repair it!
Is PulseAudio messing up the sound? But then killing and restarting should repair it.
Is there some other component loaded after the login sound which breaks the sound?

I have no clue, I don't know what's different in my system because some people make it work with the alsa drivers 1.018rc3.
Did someone solve this problem before?

---

### Post by dsm iv tr on 2008-10-26
Same problem here on my AAO 150.

Solutions are welcome, I've tried pretty much the same stuff.

---

### Post by teaker1s on 2008-10-26
yes had same problem,if it helps I found intrepid and acer as model option worked on a150 with intrepid alsa. Also intrepid with atheros worked with restricted driver.

Lastly it was me who commented on hardrive click of death on aspireone doc's-be interested to see your experiences.

---

