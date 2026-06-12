---
title: "Nokia 5200 USB connection"
date: 2008-12-10
forum: Hardware
---

### Post by canoemoose on 2008-12-10
Hi all,
I have a Nokia 5200.  I use it as my mp3 player as well as my phone, so I need to connect it to my laptop to put the music on it.

When I connect the USB lead, the phone gives me 3 options for connecting the phone:-
1) Nokia mode.  If I use this, the phone is recognised as a modem.  This is correct.
2) Printing and Media.  This is supposed to make the phone emulate an mp3 payer so it shows up in media players as a portable device.  This makes the phone show up as a camera under Ubuntu, which is what it did in Windows.
3) Data Storage.  This should make the phone act as a flash drive.  This is how I put music on my phone in Windows, but when I select this mode in Ubuntu nothing happens - nothing is shown in the log files either (/var/log/syslog)

If I try to use Printing and Media mode to connect to my phone, I can view files but receive errors if I try to copy files onto or off the phone.  When I find my USB lead again I'll post some screenshots.

I'm using kernel 2.6.27-9-generic.

Thanks for any help.

---

### Post by pistacoppu on 2009-02-22
i can copy files from my 3500c but not on it (it is the same as 5200) with the Printinting and Media mode.
If i use the phone ad a data storage it happens nothing to me too.

---

### Post by amias on 2009-02-24
I gave up trying to write to the phone directly , for music playing i have a 1gb micro sd in my phone , i just take this out (you can hotplug) and plug it in to my laptops sdcard socket with an adapter.


I've managed to download my phone numbers from it via gnokii in both bluetooth and usb modes but cannot get text messages off it.

---

### Post by amias on 2009-02-24
oh i forgot to say , for it to work with gnokii via usb you need to put the phone into nokia mode when you plugin the usb.

---

### Post by canoemoose on 2009-02-25
Yes, I can copy files off the phone in camera mode.  In nokia mode mine gets automagically recognised as a modem, so I'll have to try gnokii now and see what happens.  If I had a card reader, that'd be the obvious solution as my MicroSD card came with a converter.

---

### Post by pistacoppu on 2009-03-23
the problem is that if u remove your sd to use it in a card reader, u lost all your setting that are taken from the sd, like themes, tones etc... it is a stupid thing but ...
By the way, as i can read from various forums only s40 (5200, 3500c ...) have that kind of probles, s60 (like n70, n73 ...) does not.

---

### Post by OrganizedFellow on 2009-03-29
I have Nokia N73. Mine works just fine.

On the phone, set this setting:
Tool > Data Cable
Mine has 5 choices: 
* Ask on connection
* Media player
* PC Suite
* Mass Storage
* PictBridge

I have mine set on Mass Storage, and when I connect the phone to the computer via the USB cable, it picks it up automatically.

---

### Post by kylea on 2009-05-17
Do this - it came from here:

[http://ubuntuforums.org/showthread.php?t=1049778](http://ubuntuforums.org/showthread.php?t=1049778)


"Hi
well, I couldn't get it working as MTP device (exactly MTP), but the changes I applied are as following:

cd /usr/share/hal/fdi/information/10freedesktop

(I did this)

sudo gedit 10-usb-music-players.fdi

find a comment like <!-- Nokia N82 --> (which ends with </match>)

Add these lines:
<!-- Nokia 5800 -->
<match key="@storage.originating_device:usb.product_id" int="0x156">
<merge key="storage.model" type="string">5800</merge>
<addset key="portable_audio_player.access_method.protocols " type="strlist">storage</addset>
<append key="portable_audio_player.output_formats" type="strlist">audio/mpeg</append>
<append key="portable_audio_player.output_formats" type="strlist">audio/aac</append>
<append key="portable_audio_player.output_formats" type="strlist">audio/x-wav</append>
<append key="portable_audio_player.audio_folders" type="strlist">Music/</append>
</match>

If you have your music in "Sound" folder, put it in the last line.

sudo reboot / restart d-bus"


The 5800 will show up in Rhythmbox

---

### Post by canoemoose on 2009-05-17
The phone now works if set to "Data storage" mode.  This was due to a kernel bug, fixed with the release of Jaunty.

EDIT: Isn't there supposed to be "Mark thread solved" under the "Thread Tools" menu?

---

