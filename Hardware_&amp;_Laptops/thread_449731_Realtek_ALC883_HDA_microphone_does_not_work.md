---
title: "Realtek ALC883 HDA microphone does not work"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by Silent_Hunter on 2007-05-20
I have a Gigabyte 965P-DS3 motherboard with a integrated audio chip Realtek ALC883 HDA. My sound partialyl working in Ubuntu 7.04 32bit desktop edition. Sound will play but depending on the application it is sometimes choppy. **My microphone will not work at all. **I have tried every single type of configuration possible from Sound Preferences with no luck to fix mic issue.  I have posted a few weeks back to the kernel team.  Here is the link, [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/112695](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/112695)

I also noticed a discrepancy with lspci.  My Realteak ALC883 shows up as, 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

Here is my dmesg and lspci output:
[http://librarian.launchpad.net/7572474/dmesg.txt](http://librarian.launchpad.net/7572474/dmesg.txt)
[http://librarian.launchpad.net/7572477/lspic.txt](http://librarian.launchpad.net/7572477/lspic.txt)

---

### Post by pedromoraes on 2007-05-20
Same situation here. it won't work with alsa, I can use it with oss which is very annoying. Tried about everything , I think it's definitely a driver issue

---

### Post by go_beep_yourself on 2007-10-15
bump!!! im having the same problem.

---

### Post by brucealdridge on 2007-10-23
same problem....

yet to test this solution ...
[http://ubuntuforums.org/showpost.php?p=1357412&postcount=23](http://ubuntuforums.org/showpost.php?p=1357412&postcount=23)

make sure you change this line ... 
options snd-hda-intel model=ref 
 tooo 
options snd-hda-intel model=ALC883

or at least thats how i understand it ...
will try when i get home

-bruce

---

### Post by brucealdridge on 2007-10-24
it works :)

---

### Post by brucealdridge on 2007-10-25
Okay, i lied when i said it works...
it didn't ..... at least not in skype / voice recorder...
but i could hear myself "live" (ie directly through the speakers, not when recording though) ...
this fixed it for me  though.
[https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)

followed by some tweaking here...
[http://ubuntu-linux-dell-inspiron-9400.blogspot.com/2007/06/microphone-audio-capture-very-faint.html](http://ubuntu-linux-dell-inspiron-9400.blogspot.com/2007/06/microphone-audio-capture-very-faint.html)

---

### Post by willskills on 2008-02-04
I am using a Gigabyte P35 DS3R motherboard, and it required a small amount of tweaking to get my mic to work.

I did this; [https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture) - it was indeed the volume settings for the capture tab. This worked when plugged in to the rear ports of the mobo.

I also needed to check ¨input source¨ - and set this to Front Mic, as I am plugging my headset in to the front ports of my case.

I am now a very happy man, hope this helps someone :)

---

### Post by Cato2 on 2008-05-20
Thanks for mentioning the Gigabyte P35-DS3R, I have the same motherboard and got the microphone working as a result!

I find the volume of recording is rather low even when all sliders are at max - any ideas on that?  Perhaps it's my microphone, which is 600 ohm.

Also, does anyone know how to re-map the mixer's sliders to different sound card values?  I find that Center controls LFE, for example, rather than Center, and that Front controls overall volume not Front, and that PCM doesn't do anything.  This happens in alsa-mixer, gnome-volume-control, etc.

On the positive side, I do have sound working for almost everything including Firefox and Youtube, and with my Logitech 5.1 speakers it sounds great!

---

### Post by Cato2 on 2008-05-22
I've made some progress on this, using the ALC 889A on the Gigabyte P35-DS3R motherboard, but much of this will work with other models too.

If you see the sliders are different to what they should be, it's a sign that ALSA hasn't fully recognised your hardware.  

Here's what I did on Gutsy - quite easy, no recompiling ALSA needed!

I used [http://ubuntuforums.org/showthread.php?t=584755](http://ubuntuforums.org/showthread.php?t=584755) as a guide to install the Ubuntu Backports repository  modules, which include alsa 1.0.16 from Hardy (vs. 1.0.14 in Gutsy).  To install: 
[LIST]
[*]Add the backports repository using Synapitic or editing sources. list (google for Ubuntu backports)
[*]sudo aptitude install linux-backports-modules-2.6.22-14-generic linux-backports-modules-generic
[*]Disable backports again, so I don't use it by mistake for other packages
[/LIST]

Once the modules were installed, I configured them based on [http://www.sfr-fresh.com/linux/misc/alsa-driver-1.0.16.tar.gz:a/alsa-driver-1.0.16/alsa-kernel/Documentation/ALSA-Configuration.txt](http://www.sfr-fresh.com/linux/misc/alsa-driver-1.0.16.tar.gz:a/alsa-driver-1.0.16/alsa-kernel/Documentation/ALSA-Configuration.txt) (ALSA-Configuration.txt for 1.0.16) using the information under ALC885 model - this goes in /etc/modprobe.d/alsa-base, I just added ```
options snd-hda-intel model=6stack-dig
``` at the end (meaning 6 sound ports on the motherboard plus digital output).

Generally everything works quite well now, and I can get 5.1 channel sound with DVDs (7.1 would work but I have a 5.1 speaker setup).

---

