---
title: "Auzentech X-Plosion No Sound.."
date: 2009-09-07
forum: Hardware
---

### Post by shashank_re on 2009-09-07
I have Ubuntu 9.04 installed everything is fine except the sound :(
I use Auzentech X-plosion Sound card and Speakers are connected to it using  TOSLINK Optical Cable.Here is the output of lspci:
> 
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 13)
05:03.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
05:04.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

And in the 'Sound Preferences', i have set everything to Auto Detect...

Another thing, how do i get my WinTV PVR 150 TV Tuner work in Ubuntu..?


Regards,
Shashank

---

### Post by shashank_re on 2009-09-07
Somebody please help...

---

### Post by shashank_re on 2009-09-18
Nobody can help..?
This is something which i did not expect from the Ubuntu community :(

---

### Post by the_internet on 2010-01-03
Four months later...

I got it. 

Auzentech X-plosion running digital passthrough on optical.  I can't tell you exactly HOW I did it, I just futzed with stuff 'til it worked,

I got a lot of good info at the ALSA wiki, 

[http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut)

Anyways, I'm a total n00b at this stuff, so I'll just tell you what I installed and how my system is set up.

My install found the card but it was silent...So I set the sound preferences under hardware to digital stereo output + analog stereo input. I made no other changes there.

I installed two different Alsa mixer GUIs using the Ubuntu Software center in apps. I twiddled a little there and when I rebooted I had stereo sound through optical.  No clue why, really. The only things of note I can remember was moving the "line" slider up and that there's a list of buttons and the top "in" and bottom out are the only things checked.

I then started reading the Alsa digital wiki I linked above and following the instructions there... I downloaded a multichannel wav file from a link listed there 
[http://www.sr.se/sida/default.aspx?ProgramId=2446](http://www.sr.se/sida/default.aspx?ProgramId=2446)
 and it played multichannel, both using aplay in the terminal window and with default movie player and mplayer. Notably, VLC did NOT play it 5.1... got the front three channels and missed the rest. Movies with known DTS/AC3 still played stereo in all players though.  

I read a little more on the wiki and Xine sounded like the easiest player to get the passthrough working on so I downloaded xine-ui from one of those "sudo apt get" sorta commands in the terminal window. There's probably an easier way but Synaptic had like 50 different xine-related things and it just confused me. I finally found a link here;

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Xine-UI_Multimedia_Player](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Xine-UI_Multimedia_Player)

the command was" sudo apt-get install xine-ui "

After I installed it, set the configuration level to "master of the known universe" (a blatant lie) in the gui tab and then went to the audio tab and set audio driver to "alsa" and speaker type to "Pass Through".  Have fun with that- the dropdown windows for options are buggy as hell. It'd freeze solid if I used the scroll wheel. It works if you use the arrow keys and press enter though.

BAM! glorious 5.1, showing up as DD or DTS properly on my reciever.

Seems like an alright player thus far. 

I'm sure there's better ways to go about this but this got it working for me. I apologize this isn't more technical but I barely know my way around in Ubuntu. Spend some time at the ALSA wiki- it was really the best help I got.  And AVOID trying to install the OSS4 driver instead of the ALSA one unless you're a guru 'cause that completely messed me up.  I ended up reinstalling 9.10 from scratch after that debacle. 

WWW

---

