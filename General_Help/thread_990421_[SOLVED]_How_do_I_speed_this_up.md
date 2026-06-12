---
title: "[SOLVED] How do I speed this up?"
date: 2008-11-22
forum: General Help
---

### Post by Zagoofeek on 2008-11-22
I am new to Ubuntu and I have the most recent one. How do I speed up my Ubuntu? The only large thing I have added to my Ubuntu is World of Warcraft (up to wotlk) and wine. Also I am having sound problems with my WoW. If anyone has any suggestions of how to fix both of these problems. I greatly appreciate it. Thanks in advance.

---

### Post by dexter on 2008-11-22
What kind of hardware are you running and why whould you like to speed it up? Is it that slow?

---

### Post by Zagoofeek on 2008-11-27
I checked my free space and I don't know why I'm using so much memory. I have Ubuntu 8.10, the most recent wine, WoW (wotlk included), gnome,  and firefox. My computer is going really slow to load anything. I don't know what to do to speed it up. I am going to just provide a ton of information. I need to speed this pc up, I can't take it but I realy enjoy Linux (other than that it is slowing down for me).
I'm a noob to Linux and I need some help. :confused:


             total       used       free     shared    buffers     cached
Mem:        895072     862788      32284          0      79272     234336
-/+ buffers/cache:     549180     345892
Swap:      2618552       5236    2613316

---------------------------------------
top - 10:31:20 up 41 min,  3 users,  load average: 0.06, 0.10, 0.17
Tasks: 133 total,   2 running, 131 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.0%us,  0.7%sy,  0.0%ni, 97.2%id,  0.2%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    895072k total,   864492k used,    30580k free,    78988k buffers
Swap:  2618552k total,     5236k used,  2613316k free,   229656k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6462 user   20   0  548m 153m  26m S    3 17.5   3:09.27 firefox            
 5655 root      20   0  166m  53m  12m S    2  6.1   1:39.78 Xorg               
 6816 user    20   0  239m  26m  11m R    1  3.1   0:04.40 gnome-terminal     
 6323 user    20   0  270m  36m  14m S    1  4.2   0:32.60 compiz.real        
    1 root      20   0  5240 2020  616 S    0  0.2   0:57.03 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.08 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.20 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.04 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   49 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0      
   50 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1      

-------------------------------------------
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            305086324  22689700 266899124   8% /
tmpfs                   447536         0    447536   0% /lib/init/rw
varrun                  447536       208    447328   1% /var/run
varlock                 447536         0    447536   0% /var/lock
udev                    447536      2772    444764   1% /dev
tmpfs                   447536       260    447276   1% /dev/shm
lrm                     447536      2380    445156   1% /lib/modules/2.6.27-8-generic/volatile
--------------------------------------------
2.6.27-8-generic #1 SMP Thu Nov 6 17:38:14 UTC 2008 x86_64 GNU/Linux
--------------------------------------------
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid

---

### Post by sdennie on 2008-11-27
What specifically is slow?  Your info looks normal to me.  WoW will run slower under wine than under Windows.  Also, WoW uses a lot of memory and so will blow your caches.  That means that after you exit wine, applications may start a bit slower than they did before you played WoW.

Edit:
Just noticed you are using compiz.  That will *greatly* slow down WoW.  Before starting WoW, hit Alt-F2 and type, "metacity --replace".  After closing WoW, hit Alt-F2 and type, "compiz --replace".

---

### Post by Zagoofeek on 2008-11-28
I removed Compiz off of my computer. It sped my computer up a lot. Thank you.

---

### Post by Zagoofeek on 2008-11-28
Not sure if you might have a solution for my other WoW problem. My sound doesn't work at all. I have tried changing to ALSA and then OSS, I tried checking the driver emulation. Here is what is in my Config.wtf. Thanks for any help. 

SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "58"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET doodadAnim "0"
SET lodDist "100.000000"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "397"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET realmList "us.logon.worldofwarcraft.com"
SET soundMaxHardwareChannels "12"
SET locale "enUS"
SET readTerminationWithoutNotice "-1"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "2"
SET videoOptionsVersion "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET spellEffectLevel "4"
SET installType "Retail"
SET expansionMovie "0"
SET portal "us"
SET Gamma "1.000000"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET realmName "Bleeding Hollow"
SET gameTip "51"
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"
SET checkAddonVersion "0"
SET mouseSpeed "0.5"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET VoiceActivationSensitivity "0.39999997615814"
SET uiScale "0.89999997615814"
SET useUiScale "1"
SET baseMip "1"
SET environmentDetail "0.75"
SET weatherDensity "0"
SET Sound_NumChannels "64"
SET Sound_EnableSoundWhenGameIsInBG "1"
SET accountName "asheenwalsh"
SET lastCharacterIndex "2"

---

### Post by Zagoofeek on 2008-11-28
Now I just need to fix my sound with WoW. Any suggestions?

---

### Post by robertyou on 2008-11-28
Basically, wine simulates windows environment on your linux machine to run WoW and that is going to cost your pc some performance trade-off.

or you might as well check System -> Administration -> System Monitor to see if any process is eating up cpu usage

---

### Post by bapoumba on 2008-11-28
Threads merged.

---

### Post by nxe on 2008-12-01
> **Zagoofeek said:**
> Now I just need to fix my sound with WoW. Any suggestions?

i fixed my sound by running the following command in the terminal before running wow: 

> killall pulseaudio

---

