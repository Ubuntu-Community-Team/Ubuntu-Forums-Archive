---
title: "Tricky display/graphics crash with Acer 5720Z"
date: 2010-02-11
forum: Hardware
---

### Post by recyclist on 2010-02-11
Hello, trying again, perhaps in a more appropriate forum category. I am not much of an expert on linux, been using ubuntu for less than a year and limited prior experience with linux. (Had a brush with linux/unit while at the university, more or less before the WWW happened, typing e-mails and sending jpegs using uuencode in vt220 terminals, other than that I never learned much beyond simple file system commands.) )I will try to summarize my experience with my Acer 5720Z laptop up until the current messed-up situation, hoping somebody will have suggestions as to how I might rescue this computer. Here goes:

 Summer of 2009: Installed Ubuntu 9.04 on the Acer 5720Z. Everything worked right away. Installed java and flash plugins for Firefox. Accepted all updates from the update manager. Used the computer daily with a stability and dependability I have never experienced with Windows.
Been very very happy.

Some three weeks ago I wanted to see what could be done to improve video performance and found the thread "HOWTO: Jaunty Intel Graphics Performance Guide", elsewhere on this forum. I ended up following the instructions for "optimal" configuration, including the 2.6.30.9. kernel install. After this I have been very happy with improved video performance and continued to enjoy a stable, fast system.

Until...

Last Sunday. On the second power-up that day, the laptop's display alternated between all white or all black, absolutely nothing else - as if only the fluorescent backlight was working. Ubuntu completed startup and jingle was heard. Screen all white. At first I thought it might be a bad connector at the LCD or some such thing. A visiting friend thought it might be the "white screen of death". I was mystified and worried. I found out that I would get normal video output at the VGA connector to an external monitor, so if anything, the system still had normal video output *there*. Something relating to the internal lcd screen was positively wrong. I prepared to inspect the LCD assembly and shut down the computer one more time before removing the frame/cover of the LCD screen. Now the real trouble began. In order to check if the Acer's display worked (electronically) I'd have to switch back to the internal display with the Fn+F5 (toggles internal/external display on this computer) but now this simply did not work. Video only available at the VGA connector, from the moment of depressing the power-up button onwards, and also impossible to dim using function keys. Before I got a chance to look into THIS situation (which I wrongly expected to persist), there was another shutdown before reassembing the LCD screen. On the next power-up things got even WORSE: halfway into the boot process, the screen (now only the external Acer AL1914 display) went black and all HD activity stopped. Ubuntu startup now did not complete at all.

 After a while I managed to start ubuntu again (still only with the external monitor) by editing xorg.conf using pico and specifying Driver "VESA". By now I was not expecting any easy fix of anything, so I made backups of all my valuable data on the HD.

Meanwhile I had established that "live" sessions from the 9.04 or 9.10 CDs had to be started in safe graphics mode or else would lose video and not complete loading. 

 Obviously something had gone very wrong with graphics drivers or some such thing, but I'd have to look for help, and was growing very frustrated.

 I kept on reading here and there and trying to find reports of similar problems, but nothing quite like it mentioned anywhere.

 Having made the necessary data backup, I thought I might as well try installing Ubuntu 9.10. When I first tried this I did not specify "safe graphics mode", but installation now failed to complete, stalling with a black screen. (or waiting for keyboard/mouse user input while video is gone, no idea which) I therefore proceeded to install ubuntu 9.10 in safe graphics mode. Which worked. When completed, I was greeted with a warning saying that my hard disk drive has errors, and turned out to have many bad sectors. Aaaargh!!! 

 At this point I may not have relevant logs from the last days of ubuntu 9.04 on this computer, but to summarize:

-Internal display first worked perfectly, and Fn+F5 would toggle internal/external   display as it should - the normal situation.

-Next the computer seemed to have lost control of the internal display except the backlight, but ubuntu still finished loading and started up.

-Next I was able to connect an external display and switch to external display using Fn+F5. (But I was never able to switch back!) Ubuntu still started.

-Next there was video to the external display halfway into the ubuntu startup when screen turned black and everyhting froze. Startup would not complete.

-Ubuntu startup completed again with Driver set to "VESA" in xorg.conf.

-New install of 9.10 (deleting previous 9.04 install etc,) resulted in same old loss of video minutes into the process unless safe graphics mode was selected (F4 in CD menu).

-Ubuntu 9.10 installed in safe graphics mode works only with video output to external display.

-Computer has 282 reallocated sectors on the hard drive and I get a warning on startup. I have no idea how long the hard drive has been developing bad sectors.

So....

 Could the BIOS be damaged somehow - if so, why does this even happen? (I had it happen in Windows once in the late 90s because of a virus called CIH, but apart from viruses??)
 I notice that keys F5 and F6 do not work normally for editing the BIOS settings, not even when I use an external USB keyboard. Changing settings using arrow keys, as well as F10 and the other F-keys seem to work normally.

Again, F4 and F5 are also needed to  switch between internal/extrernal display. However, F5 and F6 DO work in the live CD boot menu! 

 I have done BIOS flashing before, but never to restore a computer running linux. And certainly never on a laptop that's forgot it's got a built in lcd screen. But I am running out of ideas. The hard drive should obviously be replaced. Other than that, the Acer 5720Z is not that old and has been working flawlessly with ubuntu.

 Oh, well...I really , REALLY hope that somebody will at least respond with a friendly comment or some suggestions or questions. I have a spare computer of course, but not a better laptop than the troubled Acer.

Optimistically,

Thomas

Ski, Norway

---

### Post by recyclist on 2010-02-14
Just back in to call off my call for help, more or less... After today's efforts - flashing mainboard BIOS as well as VGA BIOS and still no lcd display detected - and a phone conversation with a hardware wiz friend, with all the events, circumstances and efforts discussed (basically all conceivable software based approaches I could think of)  - we came to the conclusion that there most likely is a bad connection between the VGA adapter (graphics card) and the LCD assembly. I have ordered a replacement LCD cable which will be installed with no small amount of anticipation...

Thomas

---

