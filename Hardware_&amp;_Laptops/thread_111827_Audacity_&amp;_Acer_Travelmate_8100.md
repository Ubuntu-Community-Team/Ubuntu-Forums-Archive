---
title: "Audacity &amp; Acer Travelmate 8100"
date: 2006-01-03
forum: Hardware &amp; Laptops
---

### Post by strandlooper on 2006-01-03
My Notebook TM 8100 gives me again some hassle.
I installed audacity without problem and playing files is not a problem but recording doesn't work. 

Audacity recording with XP is o.k. Also on my Breezy Desktop PC recording works fine.

The difference what I have seen is that the tool bar which allows selecting the input devices (line-in, Mic.....) remains blank. No selection is possible. The second  concern is that in Preferences, I/O selection shows /dev/DSP and the device is not changeable. According to the Device Manager the alsa device is defined as /dev/snd/control....
Aaudacity-src-1.3.0b.tar.gz which can handle alsa system is not installable. Config command "./configure --with-portaudio=v19 --without-portmixer" worked fine but "make" gives me

export/ExportMultiple.o: In function `DoExport':
export/ExportMultiple.cpp:332: undefined re ference to `ExportOGG(AudacityProject*, bool, wxString, bool, double, double)'
collect2: ld returned 1 exit status
make[1]: *** [../audacity] Error 1
make[1]: Leaving directory `/home/fus5a/audacity1.3.0/audacity-src-1.3.0b-beta/src'
make: *** [audacity] Error 2

Any help would be appreciated to fix installation problem above.
If you guys could check how your audacity works on Acer please tell me.

---

