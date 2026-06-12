---
title: "No audio in speakers, headphones and microphone"
date: 2016-08-12
forum: Hardware
---

### Post by zangetsu94 on 2016-08-12
I've just installed the last LTS Kubuntu version (16.04), in dualboot with Windows10. Before to ask your help in this post I've tried even other versions or Ubuntu Distributions (live or not), but with everyone I have the same problem that makes unusable in the long run my PC: all audio systems (speakers, headphones and microphone) don't work!
But there's more, my problem can be divided into two; when I boot my PC what can happen is this:
[LIST]
[*]**1[SUP]st[/SUP] case:** Microphone doesn't work. Speakers work very fine, but when I connect the headphones the audio continues to be play from the speakers because the PC doesn't detect the headphones. If I switch (with Phonon) the output to the headphones then the sound came from them.
[*]**2[SUP]nd [/SUP]case: **Everything doesn't work,  but I see (with Phonon or alsamixer) that if I put the headphones they are detected despite they no play any sounds. What I see with alsamixer without headphones plugged in is this: [http://i63.tinypic.com/bev7gi.png](http://i63.tinypic.com/bev7gi.png)
[/LIST]

These are my PC features: 
[LIST]
[*]Brand and model: Asus F555UJ-DM059T
[*]GPU: nVidia GeForce-920M
[/LIST]

I've already followed some guides (like [this]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")) and threads and I tried to add some recommended line in: ```
sudo gedit /etc/modprobe.d/alsa-base.conf
``` actually without success...

I post something that often I saw asked:[B]1[SUP]st[/SUP] case:
[/B]```
[INDENT]~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC256 Analog [ALC256 Analog]
Subdevices: 1/1[/INDENT]
[INDENT]  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0  [/INDENT]

```[INDENT]
```
~$ lspci -nn | grep -i audio                                                                                                                                                
00:1f.3 Audio device [0403]: Intel Corporation Sunrise Point-LP HD Audio [8086:9d70] (rev 21)
```


```
~$ amixer                                                                                                                                                                   
Simple mixer control 'Master',0                                                                                                                                                              
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined                                                                                                                                
  Playback channels: Mono                                                                                                                                                                    
  Limits: Playback 0 - 87                                                                                                                                                                    
  Mono: Playback 61 [70%] [-19.50dB] [on]                                                                                                                                                    
Simple mixer control 'Headphone',0                                                                                                                                                           
  Capabilities: pvolume pswitch                                                                                                                                                              
  Playback channels: Front Left - Front Right                                                                                                                                                
  Limits: Playback 0 - 87                                                                                                                                                                    
  Mono:                                                                                                                                                                                      
  Front Left: Playback 0 [0%] [-65.25dB] [off]                                                                                                                                               
  Front Right: Playback 0 [0%] [-65.25dB] [off]                                                                                                                                              
Simple mixer control 'Speaker',0                                                                                                                                                             
  Capabilities: pvolume pswitch                                                                                                                                                              
  Playback channels: Front Left - Front Right                                                                                                                                                
  Limits: Playback 0 - 87                                                                                                                                                                    
  Mono:                                                                                                                                                                                      
  Front Left: Playback 87 [100%] [0.00dB] [on]                                                                                                                                               
  Front Right: Playback 87 [100%] [0.00dB] [on]                                                                                                                                              
Simple mixer control 'PCM',0                                                                                                                                                                 
  Capabilities: pvolume                                                                                                                                                                      
  Playback channels: Front Left - Front Right                                                                                                                                                
  Limits: Playback 0 - 255                                                                                                                                                                   
  Mono:                                                                                                                                                                                      
  Front Left: Playback 255 [100%] [0.00dB]                                                                                                                                                   
  Front Right: Playback 255 [100%] [0.00dB]                                                                                                                                                  
Simple mixer control 'IEC958',0                                                                                                                                                              
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',2
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'

```[/INDENT]


[LIST]
[*][B]2[SUP]nd [/SUP]case:
[/B]```
[FONT=monospace][COLOR=#000000]~$ aplay -l                  [/COLOR]
**** List of PLAYBACK Hardware Devices ****                                                                                                                                                   
card 0: PCH [HDA Intel PCH], device 0: ALC256 Analog [ALC256 Analog]                                                                                                                          
 Subdevices: 1/1                                                                                                                                                                             
 Subdevice #0: subdevice #0                                                                                                                                                                  
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]                                                                                                                                        
 Subdevices: 1/1                                                                                                                                                                             
 Subdevice #0: subdevice #0                                                                                                                                                                  
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]                                                                                                                                        
 Subdevices: 1/1                                                                                                                                                                             
 Subdevice #0: subdevice #0                                                                                                                                                                  
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]                                                                                                                                        
 Subdevices: 1/1                                                                                                                                                                             
 Subdevice #0: subdevice #0

[/FONT]
```

```
 [FONT=monospace][COLOR=#000000]~$ lspci -nn | grep -i audio[/COLOR]
00:1f.3 [COLOR=#FF5454]**Audio**[/COLOR][COLOR=#000000] device [0403]: Intel Corporation Sunrise Point-LP HD [/COLOR][COLOR=#FF5454]**Audio**[/COLOR][COLOR=#000000] [8086:9d70] (rev 21)[/COLOR]

[/FONT]
```

```
[FONT=monospace][COLOR=#000000]~$ amixer[/COLOR]
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 87
  Mono: Playback 61 [70%] [-19.50dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 0 [0%] [-65.25dB] [off]
  Front Right: Playback 0 [0%] [-65.25dB] [off]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]                                                                                                                                                   
Simple mixer control 'IEC958',0                                                                                                                                                               
  Capabilities: pswitch pswitch-joined                                                                                                                                                        
  Playback channels: Mono                                                                                                                                                                     
  Mono: Playback [off]                                                                                                                                                                        
Simple mixer control 'IEC958',1                                                                                                                                                               
  Capabilities: pswitch pswitch-joined                                                                                                                                                        
  Playback channels: Mono                                                                                                                                                                     
  Mono: Playback [on]                                                                                                                                                                         
Simple mixer control 'IEC958',2                                                                                                                                                               
  Capabilities: pswitch pswitch-joined                                                                                                                                                        
  Playback channels: Mono                                                                                                                                                                     
  Mono: Playback [on]                                                                                                                                                                         
Simple mixer control 'Auto-Mute Mode',0                                                                                                                                                       
  Capabilities: enum                                                                                                                                                                          
  Items: 'Disabled' 'Enabled'                                                                                                                                                                 
  Item0: 'Enabled'            
[/FONT]
```
[/LIST]

Please, help me :)



[SIZE=3][COLOR=#ff0000]**Update:**[/COLOR][/SIZE]
I came back to 14.04...

---

### Post by mook765 on 2016-08-17
You used this command
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
The programm gedit is not installed in Kubuntu by default.In Kubuntu you may use
```
gksudo kate /etc/modprobe.d/alsa-base.conf
```
When you want to use GUI-based applications as root it is recommended to use "gksudo" instead off "sudo".
If you use a GUI-based application with "sudo" and you change preferences during use, the configuration-file will change ownership to root,
this causes problems when you want to run the same application as normal user.
I know that this will not solve your problem, I just want to give you this hint about the correct use off "sudo" and "gksudo".
This will help you to avoid problems in th future.
Regards...

---

### Post by zangetsu94 on 2016-08-17
> **mook765 said:**
> 
When you want to use GUI-based applications as root it is recommended to use "gksudo" instead off "sudo".
If you use a GUI-based application with "sudo" and you change preferences during use, the configuration-file will change ownership to root,
this causes problems when you want to run the same application as normal user.
I know that this will not solve your problem, I just want to give you this hint about the correct use off "sudo" and "gksudo".
This will help you to avoid problems in th future.
Regards...

Thank you for the advice man ):P

---

### Post by howefield on 2016-08-20
Closed at request of the OP.

---

