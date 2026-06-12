---
title: "HP DV7 with Beats Audio"
date: 2010-10-25
forum: Hardware
---

### Post by BadPenguin86 on 2010-10-25
I have an HP DV7 with Beats audio. Ubuntu can use the crappy laptop speaker, but not the good beats speakers. help?

---

### Post by Racecar56 on 2010-10-25
> **BadPenguin86 said:**
> I have an HP DV7 with Beats audio. Ubuntu can use the crappy laptop speaker, but not the good beats speakers. help?
Assuming those plug into the laptop's headphone jack, Ubuntu apparently doesn't support using the headphone jack on your laptop. Maybe you should post the output of this command:

```
lspci|grep Audio
```

Do the main speakers mute when you plug in those speakers? If not then Ubuntu isn't catching the fact that you plugged those in.

---

### Post by BadPenguin86 on 2010-10-25
I should have explained better.. There are two sets of speakers in the laptop, the beats audio, and regular speakers. Ubuntu can use the regular speakers, but not the good beats speakers. Headphone jack works fine. Here is the output just to be complete:

[INDENT]justin@jpubuntu:~$ lspci|grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
02:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series] (rev ff)
[/INDENT]

---

### Post by Racecar56 on 2010-10-26
> **BadPenguin86 said:**
> I should have explained better.. There are two sets of speakers in the laptop, the beats audio, and regular speakers. Ubuntu can use the regular speakers, but not the good beats speakers. Headphone jack works fine. Here is the output just to be complete:[INDENT]justin@jpubuntu:~$ lspci|grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
02:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series] (rev ff)
[/INDENT]
Not sure about that then. :(
[SIZE=1][COLOR=White]offtopic: yay ATI
F
[SIZE=2][COLOR=Black]Edit:[/COLOR][/SIZE][SIZE=2][COLOR=Black] Did some s[/COLOR][/SIZE][SIZE=2][COLOR=Black]earching, no avail.[/COLOR][/SIZE]
[/COLOR][/SIZE]

---

### Post by igorbb on 2010-11-12
I'm also in the same situation.

Any news ?

---

### Post by lidex on 2010-11-12
Start here. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by igorbb on 2010-11-27
[http://www.alsa-project.org/db/?f=9f556618f3688ed22fb507f15097a9bf82e1cd77](http://www.alsa-project.org/db/?f=9f556618f3688ed22fb507f15097a9bf82e1cd77)

---

### Post by lidex on 2010-11-27
> **igorbb said:**
> [http://www.alsa-project.org/db/?f=9f556618f3688ed22fb507f15097a9bf82e1cd77](http://www.alsa-project.org/db/?f=9f556618f3688ed22fb507f15097a9bf82e1cd77)

Try this for me please. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
options snd-hda-intel model=hp-dv5 enable_msi=1
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by stephenjbarr on 2011-01-03
Any progress on getting the subwoofer to work?

---

### Post by Colonel_Ingus on 2011-01-20
Pavilion dv7 here, got beats, haven't ever heard it work. I blasted win7 out of it as soon as I got it out of the box.

Any idea how to get beats audio to work?

---

### Post by Colonel_Ingus on 2011-01-20
Pavilion dv7 here, got beats, haven't ever heard it work. I blasted win7 out of it as soon as I got it out of the box.

Any idea how to get beats audio to work?

---

### Post by Colonel_Ingus on 2011-01-20
Pavilion dv7 here, got beats, haven't ever heard it work. I blasted win7 out of it as soon as I got it out of the box.

Any idea how to get beats audio to work?

---

### Post by Colonel_Ingus on 2011-01-20
Pavilion dv7 here, got beats, haven't ever heard it work. I blasted win7 out of it as soon as I got it out of the box.

Any idea how to get beats audio to work?

---

### Post by BadPenguin86 on 2011-01-25
None of those methods worked. Still using only the fallback (tiny) speakers.

---

### Post by SebSmith on 2011-01-30
did this work?

same problem here.

---

### Post by igorbb on 2011-02-08
No ..
Nothing Works so far.

---

### Post by Colonel_Ingus on 2011-02-24
Still needing to know how to get this thing to work...

---

### Post by SebSmith on 2011-02-25
> **lidex said:**
> Start here. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

Your ALSA information is located at [http://www.alsa-project.org/db/?f=cf5ee9a0cca73a4bc4869e3bcb9d8ed90f7b9d0f](http://www.alsa-project.org/db/?f=cf5ee9a0cca73a4bc4869e3bcb9d8ed90f7b9d0f)

---

### Post by Yellow Pasque on 2011-02-26
> **SebSmith said:**
> Your ALSA information is located at [http://www.alsa-project.org/db/?f=cf5ee9a0cca73a4bc4869e3bcb9d8ed90f7b9d0f](http://www.alsa-project.org/db/?f=cf5ee9a0cca73a4bc4869e3bcb9d8ed90f7b9d0f)
Your ALSA install is borked (no kernel module/driver loaded). You might want to try the ALSA upgrade script (or the daily Natty/11.04 LiveCD) to see if using a more recent ALSA helps.

---

### Post by SebSmith on 2011-02-26
> **Temüjin said:**
> Your ALSA install is borked (no kernel module/driver loaded). You might want to try the ALSA upgrade script (or the daily Natty/11.04 LiveCD) to see if using a more recent ALSA helps.


how do i do this?

---

### Post by Yellow Pasque on 2011-02-26
[http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

---

### Post by SebSmith on 2011-02-26
> **Temüjin said:**
> [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

no avail. script works fine, sound card still undetected. any other ideas? and i really appreciate this

---

### Post by magatsu on 2011-04-08
same here, i have a DV7 4180us, and the sound is awfull, we really need Beats Audio in ubuntu ;__;

---

### Post by whiteskate on 2011-04-21
Hello, 

I searched everywhere to find out how to get the sub to work and i finally found a HP forum.   


Just add this line to the end of the conf file,
      options snd-hda-intel model=ref
 
In this file :
      (sudo gedit /etc/modprobe.d/alsa-base.conf)

And restart your computer 



Link to where I found out how to do this

[http://h30434.www3.hp.com/t5/Notebook-Operating-systems-and/quot-Beats-Audio-quot-Linux-HP-Envy-17/td-p/520175](http://h30434.www3.hp.com/t5/Notebook-Operating-systems-and/quot-Beats-Audio-quot-Linux-HP-Envy-17/td-p/520175)



I also updated my Alsa drivers to v1.0.23
   I used the attached file to update my alsa drivers


I am New to the linux/ubuntu world, I will try and help with what i can but i am simply using what others have already done.

---

### Post by Faz1 on 2011-05-29
Works like a charm!
Thanks **whiteskate**!!! :)

Quality first post! =D>
I can finally enjoy my new HP!!!  :guitar:

---

### Post by NexusZA on 2011-05-31
> **whiteskate said:**
> Hello, 

I searched everywhere to find out how to get the sub to work and i finally found a HP forum.   


Just add this line to the end of the conf file,
      options snd-hda-intel model=ref
 
In this file :
      (sudo gedit /etc/modprobe.d/alsa-base.conf)

And restart your computer 



Link to where I found out how to do this

[http://h30434.www3.hp.com/t5/Notebook-Operating-systems-and/quot-Beats-Audio-quot-Linux-HP-Envy-17/td-p/520175](http://h30434.www3.hp.com/t5/Notebook-Operating-systems-and/quot-Beats-Audio-quot-Linux-HP-Envy-17/td-p/520175)



I also updated my Alsa drivers to v1.0.23
   I used the attached file to update my alsa drivers


I am New to the linux/ubuntu world, I will try and help with what i can but i am simply using what others have already done.

Adding that line actually stopped my sound from working entirely.

---

### Post by lawrencesilva on 2011-08-24
hi guys im using a dv7-6135dx and got the two main speakers working (right out of the box), 

but still wanting to have the other two front speakers and the subwoofer to work.

ive tried adding this:

options snd-hda-intel model=ref

via: /etc/modprobe.d/alsa-base.conf

rebooted. and noticed that sound output was REVERSED. now the two main speakers aren't working but the two small front speakers and subwoofer are working.

sigh... the only problem now is to make them work together all at the same time. :(

help. :confused:

---

### Post by lidex on 2011-08-24
> **lawrencesilva said:**
> hi guys im using a dv7-6135dx and got the two main speakers working (right out of the box), 

but still wanting to have the other two front speakers and the subwoofer to work.

ive tried adding this:

options snd-hda-intel model=ref

via: /etc/modprobe.d/alsa-base.conf

rebooted. and noticed that sound output was REVERSED. now the two main speakers aren't working but the two small front speakers and subwoofer are working.

sigh... the only problem now is to make them work together all at the same time. :(

help. :confused:

What is your amixer output:
```
amixer
```
And what profile is selected in sound preferences?

---

### Post by lawrencesilva on 2011-08-24
dv7:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 46 [72%] [-13.50dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 0 [0%] [-48.00dB] [on]
  Front Right: Playback 0 [0%] [-48.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front Mic Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In'
  Item0: 'Mic In'
Simple mixer control 'Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 3 [100%] [0.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Digital',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 60 [50%] [0.00dB]
  Front Right: Capture 60 [50%] [0.00dB]
Simple mixer control 'Internal Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]

profile: analog stereo duplex

thanks for the reply. :)

---

### Post by lidex on 2011-08-25
I'm not sure how the outputs are attained. Maybe you can ask one of the others who got it working if they used a surround profile.
Have you tried raising this level:
```
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 0 [0%] [-48.00dB] [on]
  Front Right: Playback 0 [0%] [-48.00dB] [on]
```

---

### Post by sharat90 on 2011-09-11
here's what worked for me.

goto sound preferences > output

and in Connector choose Analog Speakers. now you should get output from all four speakers.

but when you connect headphones output continues from the front speakers (subs). in that case choose analog output as the connector.

hope this helps..

---

### Post by lawrencesilva on 2011-09-15
man. you're correct! now all of my laptop's 4+1 speakers are working! only problem now is you need to switch it back to the other setting for you to use a headphone and turn off the external speakers.

guys any idea how to deal with this issue? thanks y'all

---

### Post by Evandar on 2011-10-09
> **lawrencesilva said:**
> man. you're correct! now all of my laptop's 4+1 speakers are working! only problem now is you need to switch it back to the other setting for you to use a headphone and turn off the external speakers.

guys any idea how to deal with this issue? thanks y'all

I am a bit late, so you might have found it, but to do that, you just change your output to Analogue Headphones instead of Analogue Output in the "Output" Tab on your Sound Preferences.

On the subject of this thread (hoping that it's not dead yet), while the HP forums solution works, the speakers give a distorted output when the volume is cranked up - it sounds like someone has added a killswitch and a fuzz effect on top of the output - on my dv7 4050ea. I really can't remember what Windows 7 sounded like, but I would certainly remember it if it sounded like THAT. Seeing as I know a few things about sound mixing, I can tell that the computer is playing the wrong frequencies out of the wrong speakers - for example, playing high frequencies loudly on the subwoofer. Anyone know what I have to edit to make the right frequencies route to the right speakers? Should I be asking this in sound?

btw, I'm using Natty.

---

