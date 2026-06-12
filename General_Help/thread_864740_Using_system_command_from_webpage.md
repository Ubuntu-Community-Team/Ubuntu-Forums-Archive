---
title: "Using system command from webpage"
date: 2008-07-19
forum: General Help
---

### Post by xshagy on 2008-07-19
I'd like to play mp3's with a webpage.  I tried using the system command in the following code. I'm using ubuntu server and perl seems to be working.

```

#!/usr/bin/perl

print <<END;
Content-Type: text/html\n\n
<html>
<head></head>
<body>
END

system("mplayer 'song.mp3'");

print <<END;
</body>
</html>
END

```

If this file is run in terminal (perl file.pl) it plays the song and works fine but in a browser it displays the following

[html]
MPlayer 2:1.0~rc1-0ubuntu13.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+ (Family: 15, Model: 107, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Terminal type `unknown' is not defined.

Playing song.mp3.
Audio file file format detected.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 192.0 kbit/13.61% (ratio: 24000->176400)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
[AO SDL] Samplerate: 44100Hz Channels: Stereo Format s16le
Opening /dev/dvb/adapter0/audio0
AO: [null] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   0.0 (00.0) of 175.0 (02:55.0) ??,?%                                        
A:   0.0 (00.0) of 175.0 (02:55.0) ??,?%                                        
A:   0.1 (00.0) of 175.0 (02:55.0) ??,?%                                        
A:   0.1 (00.1) of 175.0 (02:55.0) ??,?%                                        
A:   0.2 (00.1) of 175.0 (02:55.0)  1.2%                                        
A:   0.2 (00.1) of 175.0 (02:55.0)  1.2%                                        
A:   0.2 (00.2) of 175.0 (02:55.0)  1.2%                                        
A:   0.3 (00.2) of 175.0 (02:55.0)  1.2%                                        

A:   0.3 (00.2) of 175.0 (02:55.0)  1.2%                                        
A:   0.3 (00.3) of 175.0 (02:55.0)  1.2%                                        
A:   0.4 (00.3) of 175.0 (02:55.0)  1.2%
[/html]

Seems like all the permissions are fine or it wouldn't display anything, right? I says "starting playback", so I'm assuming mplayer is running.  

Any ideas or things to try?  I'm stumped.

---

### Post by xshagy on 2008-07-20
What about using includes.....

<!--#exec cmd="mplayer 'song.mp3'" -->

or

<!--#include virtual="page.pl"-->

or

<!--#exec cmd="perl page.pl" -->

Can I do this?
I'm playing around with the apache conf file but it doesn't seem like it'll let me do this.

Any ideas?

---

### Post by mcduck on 2008-07-20
How about trying MPD (Music Player Daemon) with one of it's web-based clients?

Taht would mean installing MPD together with Apache (and I supposed at least PHP as well, so you probably want the whole LMP stack) and then adding the web client.

[Music Player Daemon]("http://www.musicpd.org/")
[Ampache]("http://www.ampache.org/")
[Pitchfork]("http://linux.softpedia.com/get/Multimedia/Audio/pitchfork-23134.shtml") (their own website seems to be down)

---

