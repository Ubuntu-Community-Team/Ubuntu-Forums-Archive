---
title: "No volume control GStreamer plugins and/or devices found."
date: 2008-07-10
forum: Hardware
---

### Post by mr.pirate on 2008-07-10
Alright, after trying to install totem with the xine backend i went over to my sound control and found this error message

No volume control GStreamer plugins and/or devices found.

So i tried uninstalling the totem program to no avail

Then i checked to see if my audio card was being detected

root@localhost:/home/slick# lspci | grep Audio
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

So i dont really know what to do now, all of the necessary gstreamer plugins are installed

root@localhost:/home/slick# aptitude search gstreamer0.10-plugins
i   gstreamer0.10-plugins-bad                                                                        - GStreamer plugins from the "bad" set                                                                       
p   gstreamer0.10-plugins-bad-dbg                                                                    - GStreamer plugins from the "bad" set                                                                       
p   gstreamer0.10-plugins-bad-doc                                                                    - GStreamer documentation for plugins from the "bad" set                                                     
i   gstreamer0.10-plugins-bad-multiverse                                                             - GStreamer plugins from the "bad" set (Multiverse Variant)                                                  
p   gstreamer0.10-plugins-bad-multiverse-dbg                                                         - GStreamer plugins from the "bad" set (Multiverse Variant)                                                  
i   gstreamer0.10-plugins-base                                                                       - GStreamer plugins from the "base" set                                                                      
i   gstreamer0.10-plugins-base-apps                                                                  - GStreamer helper programs from the "base" set                                                              
p   gstreamer0.10-plugins-base-dbg                                                                   - GStreamer plugins from the "base" set                                                                      
p   gstreamer0.10-plugins-base-doc                                                                   - GStreamer documentation for plugins from the "base" set                                                    
i   gstreamer0.10-plugins-farsight                                                                   - plugins for Gstreamer for Audio/Video conferencing                                                         
i   gstreamer0.10-plugins-good                                                                       - GStreamer plugins from the "good" set                                                                      
p   gstreamer0.10-plugins-good-dbg                                                                   - GStreamer plugins from the "good" set                                                                      
p   gstreamer0.10-plugins-good-doc                                                                   - GStreamer documentation for plugins from the "good" set                                                    
i   gstreamer0.10-plugins-ugly                                                                       - GStreamer plugins from the "ugly" set                                                                      
p   gstreamer0.10-plugins-ugly-dbg                                                                   - GStreamer plugins from the "ugly" set                                                                      
p   gstreamer0.10-plugins-ugly-doc                                                                   - GStreamer documentation for plugins from the "ugly" set                                                    
i   gstreamer0.10-plugins-ugly-multiverse                                                            - GStreamer plugins from the "ugly" set (Multiverse Variant)                                                 
p   gstreamer0.10-plugins-ugly-multiverse-dbg                                                        - GStreamer plugins from the "ugly" set (Multiverse Variant)

---

### Post by Isaacthulhu on 2008-07-10
I have the same error message, only I have just barely begun to learn all of the sorted idiosyncrasies of Ubuntu (Terminal, et all).  I haven't got the first clue what caused this error message or how return my sound functionality to it's previously operational state.

I have tried also several solutions I found online ( I can only hope I didn't cause more of a problem than existed already) by entering things in terminal....without any productive outcome.

In short I am very &#8220;Green&#8221;, without sound and totally confused about what to do to fix it, short of backing up everything and clean installing.

I learn fast though and any help anyone would like to give me would not be wasted effort.

I am on an old Dell Latitude, running Ubuntu 8.04

Please help.:neutral:

---

### Post by mr.pirate on 2008-07-10
1). Checking for /dev/snd, some people couldnt find theirs.
```

slick@localhost:~$ ls -l /dev/ | grep snd
drwxr-xr-x 2 root   root           180 2008-07-10 00:50 snd
lrwxrwxrwx 1 root   root            24 2008-07-10 00:50 sndstat -> /proc/asound/oss/sndstat

```

2). Trying alsamixer from the terminal, maybe i'll get some output
```

slick@localhost:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory

```

3). Checking to see what the error was in alsamixer
```

slick@localhost:~$ strace -eopen alsamixer
open("/etc/ld.so.cache", O_RDONLY)      = 3
open("/lib/libncurses.so.5", O_RDONLY)  = 3
open("/usr/lib/libasound.so.2", O_RDONLY) = 3
open("/lib/libm.so.6", O_RDONLY)        = 3
open("/lib/libdl.so.2", O_RDONLY)       = 3
open("/lib/libpthread.so.0", O_RDONLY)  = 3
open("/lib/libc.so.6", O_RDONLY)        = 3
open("/lib/librt.so.1", O_RDONLY)       = 3
open("/usr/share/alsa/alsa.conf", O_RDONLY) = 3
open("/dev/snd/controlC0", O_RDONLY)    = -1 EACCES (Permission denied)
open("/dev/aloadC0", O_RDONLY)          = -1 ENOENT (No such file or directory)

alsamixer: function snd_ctl_open failed for default: No such file or directory
Process 17212 detached

```

4). All of my drivers containing snd
```

slick@localhost:~$ lsmod | grep snd
snd_rtctimer            5344  1 
snd_hda_intel         440792  0 
snd_pcm_oss            48032  0 
snd_mixer_oss          20352  1 snd_pcm_oss
snd_pcm                93320  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12680  1 snd_hda_intel
snd_seq_dummy           5764  0 
snd_seq_oss            39424  0 
snd_seq_midi           10688  0 
snd_rawmidi            30240  1 snd_seq_midi
snd_seq_midi_event     10240  2 snd_seq_oss,snd_seq_midi
snd_seq                64256  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              28424  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71880  13 snd_rtctimer,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              11040  1 snd

```

My hypothesis:

1). Some people with this problem could not find their /dev/snd/ directory which would
cause a bit of a problem. I seem to have my directory so that is ok but other posts
said that the OSS drives may be causing an issue.

2). Permission denied sounds like it will **** something up so i logged in as root and
sound is fine, but why did it stop working on my user? well for some reason i have seen
that very thing happen with my nm-applet network manager. There may be something that has
bad permissions set up?

---

### Post by mr.pirate on 2008-07-10
```

chmod 666 /dev/snd/*

```

FIXED IT!

---

### Post by Isaacthulhu on 2008-07-11
I wish I understood the above.
I could try and just to cut and paste the commands I see however though this may or may not work for me, it will certainly not equip me to better troubleshoot or contribute my understanding in the future.
If someone can find the patience to explain this, I'll be thankful.

I tried  "chmod 666 /dev/snd/*" in terminal and it says "chmod: cannot access `/dev/snd/': No such file or directory".

---

### Post by Isaacthulhu on 2008-07-12
for the love of all that is Ubuntu will someone please help me.

---

