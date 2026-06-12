---
title: "using a windows driver"
date: 2008-06-14
forum: Hardware
---

### Post by adamgram on 2008-06-14
I'm trying to figure out how to use my laptop with Ubuntu 8.4 to control the effects processor for my guitar.  It works through a USB connections. It comes with windows software, that runs fine through WINE, but the driver is another issue.

There is a setupinf.exe file that tells me to plug it in, wait for the windows 'found new hardware' wizard to appear and go from there, of course, with Ubuntu this doesn't happen.  I searched the forums and found out about ndisgtk to use windows wireless drivers, but this doesn't work.  I installed the .inf using ndisgtk but it says 'hardware not connected' and the software does not recognize that the processor is connected.  

Anyone who wants to share their knowledge on any of these issues with me would receive my great appreciation.

---

### Post by ellis rowell on 2008-06-14
It sounds similar to the problem I have with a Sony VN Voice Recorder. The Windows software wouldn't work under Wine. My work around was to plug a cable with a 3.5mm jack at each end, into the earphone socket on the VR and into the Mic socket on the computer. You then have to play the recording back on the VR and have "Sound Recorder" recording the transient audio signal. Thus recording in real-time, it's a pain when you have already recorded it once. Still, it's the only way around it as far as I can see.

---

### Post by adamgram on 2008-06-14
hmm... that wouldn't work for me, this is control software... it changes the setting of the processor using a MIDI signal so you can use the more intuitive GUI on the computer.  For all intents and purposes, though, it's a USB device with a windows driver.  What I can't figure out is how to use WINE to run the driver manually, since the setup .exe file doesn't actually set up the driver, it just lists instructions on how to do it in windows.

---

