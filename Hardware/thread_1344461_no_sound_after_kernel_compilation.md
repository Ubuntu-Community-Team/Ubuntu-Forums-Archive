---
title: "no sound after kernel compilation"
date: 2009-12-03
forum: Hardware
---

### Post by santiagorf on 2009-12-03
Hi,
I have customized a kernel for kubuntu, and when I run it with this kernel everything seems to work fine with the exception of the sound (which works fine with the generic kernel).

I have created this new kernel for kubuntu using the same .conf file I had already used to customize a kernel for archlinux. However, in archlinux I had sound, but in kubuntu I don't.

My sound card is 


[HTML]
aplay -l
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]

[/HTML]

In the .config file, one relevant configuration for the sound is 

[HTML]<M>   VIA 82C686A/B, 8233/8235 AC97 Controller   [/HTML]

With the following description

[HTML]CONFIG_SND_VIA82XX:                                                                                                                                                                     Say Y here to include support for the integrated AC97 sound device on motherboards with VIA chipsets. 
To compile this driver as a module, choose M here: the module will be called snd-via82xx.

Symbol: SND_VIA82XX [=m] 
Prompt: VIA 82C686A/B, 8233/8235 AC97 Controller
Defined at sound/pci/Kconfig:764
Depends on: SOUND && !M68K && SND && SND_PCI  Location:                                                                                                                                                                             
-> Device Drivers
   -> Sound card support (SOUND [=y])
      -> Advanced Linux Sound Architecture (SND [=y])
         -> PCI sound devices (SND_PCI [=y])

Selects: SND_MPU401_UART && SND_AC97_CODEC[/HTML]

Does anyone know what can I do?

Thanks

santiagorf

---

### Post by jocko on 2009-12-03
You probably should give some more information:

**1. Is the alsa module loaded?**
Check the output of:
```
lsmod | grep via82xx
```
It should show several lines containing "snd_via82xx". If it's not loaded, try to load it manually:
```
sudo modprobe snd_via82xx
```

**2. Do you get any error messages?**
Try to play a sound file from a terminal, and try some different outputs. If you have mplayer, try these commands (where [COLOR=Red]/path/to/some.mp3[/COLOR] is the full path and filename of an actual audio file on your computer):
```
mplayer -ao pulse [COLOR=Red]/path/to/some.mp3[/COLOR]
mplayer -ao alsa [COLOR=Red]/path/to/some.mp3[/COLOR]
mplayer -ao oss [COLOR=Red]/path/to/some.mp3[/COLOR]
```
alsa and oss should work, or at least give some output that may give clues to why it doesn't work. Not sure if kubuntu have pulse.

---

### Post by santiagorf on 2009-12-03
Hi Jocko,
From the customized kernel I get

```
lsmod | grep via82xx
snd_via82xx            20940  0
snd_ac97_codec         94708  1 snd_via82xx
snd_pcm                58108  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          8060  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6036  1 snd_via82xx

```

Nothing from:
```
sudo modprobe snd_via82xx
```


```
mplayer -ao pulse /home/sa/Desktop/test.mp3
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team    
mplayer: could not connect to socket                   
mplayer: No such file or directory                     
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/sa/Desktop/test.mp3.
Audio only file format detected.  
Clip info:                        
 Title: Bright Lights             
 Artist: Placebo                  
 Album: Battle for the Sun        
 Year: 2009                       
 Comment:                             
 Track: 6                             
 Genre: Rock                          
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3                     
AUDIO: 44100 Hz, 2 ch, s16le, 256.0 kbit/18.14% (ratio: 32000->176400)    
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)    
==========================================================================
[pulse] working around probably broken pause functionality,               
        see http://www.pulseaudio.org/ticket/440                          
socket(): Address family not supported by protocol                        
waitpid(): No child processes                                             
AO: [pulse] Init failed: Internal error                                   
Failed to initialize audio driver 'pulse'                                 
Could not open/initialize audio device -> no sound.                       
Audio: no sound                                                           
Video: no video                                                           


Exiting... (End of file)

```

```
mplayer -ao alsa /home/sa/Desktop/test.mp3
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team   
mplayer: could not connect to socket                  
mplayer: No such file or directory                    
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/sa/Desktop/test.mp3.
Audio only file format detected.  
Clip info:                        
 Title: Bright Lights             
 Artist: Placebo                  
 Album: Battle for the Sun        
 Year: 2009                       
 Comment:                             
 Track: 6                             
 Genre: Rock                          
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3                     
AUDIO: 44100 Hz, 2 ch, s16le, 256.0 kbit/18.14% (ratio: 32000->176400)    
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)    
==========================================================================
[AO_ALSA] alsa-lib: confmisc.c:768:(parse_card) cannot find card '0'      
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:392:(snd_func_concat) error evaluating strings                                                 
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory     
[AO_ALSA] alsa-lib: confmisc.c:1251:(snd_func_refer) error evaluating name
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
[AO_ALSA] alsa-lib: conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
[AO_ALSA] alsa-lib: pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
[AO_ALSA] Playback open error: No such file or directory
Failed to initialize audio driver 'alsa'
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video

Exiting... (End of file)

```




```
mplayer -ao oss /home/sa/Desktop/test.mp3
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/sa/Desktop/test.mp3.
Audio only file format detected.
Clip info:
 Title: Bright Lights
 Artist: Placebo
 Album: Battle for the Sun
 Year: 2009
 Comment:
 Track: 6
 Genre: Rock
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 256.0 kbit/18.14% (ratio: 32000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Permission denied
Failed to initialize audio driver 'oss'
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video
```

However, when I ran the last two lines as super user, i.e.
```

sudo mplayer -ao alsa /home/sa/Desktop/test.mp3
sudo mplayer -ao oss /home/sa/Desktop/test.mp3
```

I can play the mp3.


What is wrong?















> **jocko said:**
> You probably should give some more information:

**1. Is the alsa module loaded?**
Check the output of:
```
lsmod | grep via82xx
```
It should show several lines containing "snd_via82xx". If it's not loaded, try to load it manually:
```
sudo modprobe snd_via82xx
```

**2. Do you get any error messages?**
Try to play a sound file from a terminal, and try some different outputs. If you have mplayer, try these commands (where [COLOR=Red]/path/to/some.mp3[/COLOR] is the full path and filename of an actual audio file on your computer):
```
mplayer -ao pulse [COLOR=Red]/path/to/some.mp3[/COLOR]
mplayer -ao alsa [COLOR=Red]/path/to/some.mp3[/COLOR]
mplayer -ao oss [COLOR=Red]/path/to/some.mp3[/COLOR]
```
alsa and oss should work, or at least give some output that may give clues to why it doesn't work. Not sure if kubuntu have pulse.

---

### Post by jocko on 2009-12-03
> **santiagorf said:**
> However, when I ran the last two lines as super user, i.e.
```

sudo mplayer -ao alsa /home/sa/Desktop/test.mp3
sudo mplayer -ao oss /home/sa/Desktop/test.mp3
```I can play the mp3.
Not sure if this will help, but try adding your user to the audio group:
```
sudo adduser $USER audio
```
Then log out and log back in and try again.

---

### Post by santiagorf on 2009-12-03
It works, thank you!!
I wonder what does it have to do my user permission with the kernel.


> **santiagorf said:**
> Hi Jocko,
From the customized kernel I get

```
lsmod | grep via82xx
snd_via82xx            20940  0
snd_ac97_codec         94708  1 snd_via82xx
snd_pcm                58108  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          8060  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6036  1 snd_via82xx

```

Nothing from:
```
sudo modprobe snd_via82xx
```


```
mplayer -ao pulse /home/sa/Desktop/test.mp3
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team    
mplayer: could not connect to socket                   
mplayer: No such file or directory                     
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/sa/Desktop/test.mp3.
Audio only file format detected.  
Clip info:                        
 Title: Bright Lights             
 Artist: Placebo                  
 Album: Battle for the Sun        
 Year: 2009                       
 Comment:                             
 Track: 6                             
 Genre: Rock                          
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3                     
AUDIO: 44100 Hz, 2 ch, s16le, 256.0 kbit/18.14% (ratio: 32000->176400)    
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)    
==========================================================================
[pulse] working around probably broken pause functionality,               
        see http://www.pulseaudio.org/ticket/440                          
socket(): Address family not supported by protocol                        
waitpid(): No child processes                                             
AO: [pulse] Init failed: Internal error                                   
Failed to initialize audio driver 'pulse'                                 
Could not open/initialize audio device -> no sound.                       
Audio: no sound                                                           
Video: no video                                                           


Exiting... (End of file)

```

```
mplayer -ao alsa /home/sa/Desktop/test.mp3
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team   
mplayer: could not connect to socket                  
mplayer: No such file or directory                    
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/sa/Desktop/test.mp3.
Audio only file format detected.  
Clip info:                        
 Title: Bright Lights             
 Artist: Placebo                  
 Album: Battle for the Sun        
 Year: 2009                       
 Comment:                             
 Track: 6                             
 Genre: Rock                          
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3                     
AUDIO: 44100 Hz, 2 ch, s16le, 256.0 kbit/18.14% (ratio: 32000->176400)    
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)    
==========================================================================
[AO_ALSA] alsa-lib: confmisc.c:768:(parse_card) cannot find card '0'      
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:392:(snd_func_concat) error evaluating strings                                                 
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory     
[AO_ALSA] alsa-lib: confmisc.c:1251:(snd_func_refer) error evaluating name
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
[AO_ALSA] alsa-lib: conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
[AO_ALSA] alsa-lib: pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
[AO_ALSA] Playback open error: No such file or directory
Failed to initialize audio driver 'alsa'
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video

Exiting... (End of file)

```




```
mplayer -ao oss /home/sa/Desktop/test.mp3
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/sa/Desktop/test.mp3.
Audio only file format detected.
Clip info:
 Title: Bright Lights
 Artist: Placebo
 Album: Battle for the Sun
 Year: 2009
 Comment:
 Track: 6
 Genre: Rock
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 256.0 kbit/18.14% (ratio: 32000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Permission denied
Failed to initialize audio driver 'oss'
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video
```

However, when I ran the last two lines as super user, i.e.
```

sudo mplayer -ao alsa /home/sa/Desktop/test.mp3
sudo mplayer -ao oss /home/sa/Desktop/test.mp3
```

I can play the mp3.


What is wrong?

---

