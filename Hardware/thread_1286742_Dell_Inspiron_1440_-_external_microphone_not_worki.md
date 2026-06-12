---
title: "Dell Inspiron 1440 - external microphone not working"
date: 2009-10-09
forum: Hardware
---

### Post by tomas.splatch on 2009-10-09
Hi there,
I recently installed Kubuntu 9.10 Beta on my brothers Dell Inspiron laptop. Everything works just perfect, except for microphone. There is no built-in microphone on the notebook, so we have to use external microphone when using Skype etc. However I can't get it working. I also installed Pulse audio packages and tried to play with PulseAudio Device Chooser, but it seems it doesn't detect the microphone. I checked AlsaMixer and I put all the devices to 100% volume, but didn't help.
Here is my amixer output:

```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono                                    
  Limits: Playback 0 - 64                                    
  Mono: Playback 34 [53%] [-22.50dB] [on]                    
Simple mixer control 'Headphone',0                           
  Capabilities: pvolume pswitch                              
  Playback channels: Front Left - Front Right                
  Limits: Playback 0 - 64                                    
  Mono:                                                      
  Front Left: Playback 64 [100%] [0.00dB] [on]               
  Front Right: Playback 64 [100%] [0.00dB] [on]              
Simple mixer control 'PCM',0                                 
  Capabilities: pvolume                                      
  Playback channels: Front Left - Front Right                
  Limits: Playback 0 - 255                                   
  Mono:                                                      
  Front Left: Playback 254 [100%] [0.20dB]                   
  Front Right: Playback 254 [100%] [0.20dB]                  
Simple mixer control 'Front Mic',0                           
  Capabilities: cvolume cswitch                              
  Capture channels: Front Left - Front Right                 
  Limits: Capture 0 - 31                                     
  Front Left: Capture 31 [100%] [12.00dB] [on]               
  Front Right: Capture 31 [100%] [12.00dB] [on]              
Simple mixer control 'Line In',0                             
  Capabilities: cvolume cswitch                              
  Capture channels: Front Left - Front Right                 
  Limits: Capture 0 - 31                                     
  Front Left: Capture 31 [100%] [12.00dB] [on]               
  Front Right: Capture 31 [100%] [12.00dB] [on]              
Simple mixer control 'Mic Jack Mode',0                       
  Capabilities: enum                                         
  Items: 'Mic In' 'Line In'                                  
  Item0: 'Mic In'                                            
Simple mixer control 'Mono Mux',0                            
  Capabilities: enum                                         
  Items: 'DAC0' 'DAC1' 'Mixer'                               
  Item0: 'DAC0'                                              
Simple mixer control 'Capture',0                             
  Capabilities: cvolume cswitch                              
  Capture channels: Front Left - Front Right                 
  Limits: Capture 0 - 15                                     
  Front Left: Capture 15 [100%] [22.50dB] [on]               
  Front Right: Capture 15 [100%] [22.50dB] [on]              
Simple mixer control 'Capture',1                             
  Capabilities: cvolume cswitch                              
  Capture channels: Front Left - Front Right                 
  Limits: Capture 0 - 15                                     
  Front Left: Capture 15 [100%] [22.50dB] [on]               
  Front Right: Capture 15 [100%] [22.50dB] [on]              
Simple mixer control 'Amp',0                                 
  Capabilities: cvolume                                      
  Capture channels: Front Left - Front Right                 
  Limits: Capture 0 - 3                                      
  Front Left: Capture 3 [100%] [30.00dB]                     
  Front Right: Capture 3 [100%] [30.00dB]                    
Simple mixer control 'DAC0',0                                
  Capabilities: cvolume cswitch                              
  Capture channels: Front Left - Front Right                 
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [12.00dB] [on]
  Front Right: Capture 31 [100%] [12.00dB] [on]
Simple mixer control 'DAC1',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [12.00dB] [on]
  Front Right: Capture 31 [100%] [12.00dB] [on]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 120 [100%] [30.00dB]
  Front Right: Capture 120 [100%] [30.00dB]
Simple mixer control 'Digital Input Source',0
  Capabilities: enum
  Items: 'Analog Inputs' 'Digital Mic 1' 'Digital Mic 2'
  Item0: 'Digital Mic 1'
Simple mixer control 'Digital Input Source',1
  Capabilities: enum
  Items: 'Analog Inputs' 'Digital Mic 1' 'Digital Mic 2'
  Item0: 'Analog Inputs'
Simple mixer control 'PC Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 3 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]

```

Any help would be appreciated.

---

### Post by pookito on 2009-10-11
That is really funny, because to me is happening the other way around.  I have ubuntu on xps m1530 and the external mic works flawlessly, what it does not work is when I connect the any mic which is supported because I have use it before on other distros, it does not work.

---

