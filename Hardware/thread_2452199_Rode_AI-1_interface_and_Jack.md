---
title: "Rode AI-1 interface and Jack"
date: 2020-10-18
forum: Hardware
---

### Post by indifferen7 on 2020-10-18
Hi!
I have a question regarding the Rode AI-1 audio interface and if anyone has managed to get the headphone output working in Jack (i.e., [https://jackaudio.org/)?](https://jackaudio.org/)?) My goal is to record some music with Ardour in Ubuntu Studio 20.04 and for that I understand that I am better off with Jack up and running. When I connect AI-1 to the computer via a USB port, the QjackCtl gives me the option (under the "Settings..") to use the "hw:AI1" audio interface, which seems to be just what I want. But after selecting that interface and starting Jack via the GUI I get the following output: 

Sun Oct 18 19:16:15 2020: Starting jack server...

 Sun Oct 18 19:16:15 2020: JACK server starting in realtime mode with priority 10

 Sun Oct 18 19:16:15 2020: self-connect-mode is "Don't restrict self connect requests"

 Sun Oct 18 19:16:16 2020: Acquired audio card Audio1

 Sun Oct 18 19:16:16 2020: creating alsa driver ... hw:AI1|hw:AI1|1024|3|44100|0|0|nomon|swmeter|-|32bit

 Sun Oct 18 19:16:16 2020: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods

 Sun Oct 18 19:16:16 2020: ALSA: final selected sample format for capture: 24bit little-endian in 3bytes format

 Sun Oct 18 19:16:16 2020: ALSA: use 3 periods for capture

 Sun Oct 18 19:16:16 2020: ALSA: final selected sample format for playback: 24bit little-endian in 3bytes format
 Sun Oct 18 19:16:16 2020: ALSA: use 3 periods for playback
 Sun Oct 18 19:16:16 2020: ERROR: ALSA: could not start playback (Broken pipe)
 Sun Oct 18 19:16:16 2020: ERROR: Cannot start driver
 Sun Oct 18 19:16:16 2020: ERROR: JackServer::Start() failed with -1
 Sun Oct 18 19:16:16 2020: ERROR: Failed to start server
 Sun Oct 18 19:16:16 2020: Released audio card Audio1
 Sun Oct 18 19:16:17 2020: Saving settings to "/home/indifferent/.config/jack/conf.xml" ...
 [COLOR=#ff0000]19:16:22.102 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock

 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock

Now, if I switch to the "advanced" tab and select the AI-1 as "Input Device", I can actually use the audio interface to record audio in Ardour. But it seems impossible to get the same interface working as "Output device", i.e., to use the headphone jack as sound output. If I try that, I get a simlar error as above when starting Jack. Any ideas or clues would be super helpful.

Edit: The headphone output on the AI-1 works fine when listening to e.g. music, so it is functional, but it does not work as output device when attempting to start Jack via QjackCtl.


Best wishes,
Martin Moberg

---

### Post by indifferen7 on 2020-10-18
After some more hours digging I located the following post: [https://ubuntuforums.org/showthread.php?t=2116803](https://ubuntuforums.org/showthread.php?t=2116803). After trying out a bunch of different USB ports on my computer I found one that worked. So, lessons learned, while USB ports might look the same they may differ in functionality under the hood. So, case closed. :)

Best,
Martin

---

