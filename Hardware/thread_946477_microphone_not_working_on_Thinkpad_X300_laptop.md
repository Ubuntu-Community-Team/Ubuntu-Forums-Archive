---
title: "microphone not working on Thinkpad X300 laptop"
date: 2008-10-13
forum: Hardware
---

### Post by gnychis on 2008-10-13
Hi all,

I have gotten everything working on the X300 from GPS to the webcam, but the one thing I have struggled with for weeks now is trying to get the microphone to work.  This would be great for skype.

After doing some googling, it seems as though other people have the same issue.  I think it stems from the fact that it is a digital microphone.

Has anyone been able to get it working?

Thanks!
George

---

### Post by dvstin on 2008-10-18
Hi,

I had sound fully working in 8.04 after installing alsa-driver-hg20080424.tar.bz2 and following the procedure of removing the stock alsa drivers, ./configure --with-cards=hda-intel, make, make install, ./snddevices, and reboot. The annoying part about this is that it had to be done after every kernel update.

With 8.10 on 2.6.27, this driver no longer compiles. Also, the default settings don't work for sound capture. In fact, there is really strange behavior where if I start recording in sound recorder and stop a couple seconds after, sound recorder has about 10 minutes of data. The recorded data is all silence.

Another problem with sound on 8.10/2.6.27 is that I only see one microphone in the mixer when the x300 actually has two: analog mic input jack and built in digital mic.

I would be happy to provide any more information or report a bug about this if it would help get sound working before the 8.10 release.

Dustin

I have reported bug #285621 with ubuntu [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/285621](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/285621)
and also bug #4192 with alsa-driver [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4192](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4192)

---

### Post by gnychis on 2008-10-20
Hi Doug!

Sorry for the long response toget back to you, but I'm traveling out of the country.

Thanks!  This did work for me.  I think a major trick to this also is the proper things enabled in the alsa settings.  Under the recording tab, capture and digital both need to be enabled.  Under Switches, internal MIC needs to be selected.

I think this would definitely be useful to push in as a fix.  After some googling, many people have this issue.

Thanks!
George

---

### Post by dvstin on 2008-10-20
I figured out that I can record only after doing pkill pulseaudio

I guess my issue is with pulseaudio and not alsa.

Is there any way to disable pulse audio in ubuntu 8.10? or to troubleshoot pulse audio and why it would stop my sound capture from working?

I reported issue [http://pulseaudio.org/ticket/392](http://pulseaudio.org/ticket/392)

---

### Post by dvstin on 2008-10-20
as stated in the bug, I fixed the problem by doing the following:

1. installed: padevchooser libao-pulse libsdl1.2debian-pulseaudio
2. changed /etc/libao.conf to: default_driver=pulse
3. selected Pulse Audio as my capture source in sound preferences.

---

### Post by catchagato on 2008-11-05
How do I change the /etc/libao.conf? When I try to change it to "pulse" it tells me I do not have the permissions necessary to save the file...

---

### Post by dvstin on 2008-11-10
gnychis:

To change /etc/libao.conf press alt-f2 and enter:

gksudo gedit /etc/libao.conf

---

### Post by dvstin on 2009-01-30
I would like to add that sound is working out of the box on the thinkpad x300 in jaunty 9.04 alpha 3. The only issue is that the digital mic is not selected as an input source, and the volume control software doesn't show the alsa channels, so I have to run alsamixer -c0 to see the controls for selecting an input method.

Thank you to the developers who got this working.

---

### Post by jlopezbr on 2009-10-24
I made this [http://grzen.blogspot.com/2009/05/configuring-thinkpad-x300-internal-mic.html](http://grzen.blogspot.com/2009/05/configuring-thinkpad-x300-internal-mic.html)
 and worked for me.

---

### Post by Bashar &quot; on 2009-10-30
i have the same issue on 9.10

and the steps above does not apply...

---

### Post by farchumbre on 2009-11-07
how do you configure internal mic in ubuntu 9.10?

---

### Post by farchumbre on 2009-12-29
Hi 
Did you find any solution for x300 using ubuntu karmic?
your solution worked for ubuntu 9.04 but not for ubuntu 9.10

---

### Post by grzen on 2010-02-14
Just upgraded my X300 to 9.10... Had to perform some experiments (as always with a new distro) to configure the internal mic, but eventually got it working... Here is the link to what worked for me:
[http://grzen.blogspot.com/2010/02/configuring-thinkpad-x300-internal-mic.html](http://grzen.blogspot.com/2010/02/configuring-thinkpad-x300-internal-mic.html)

More seriously, there's a bunch of bugs that will certainly apply here, namely 440251 or 434520, so a proper fix will probably make it into the distro, but pending their resolution, you may want to try the steps described above...

Of course, comments are welcome   : )
Cheers!

---

### Post by tareko on 2010-06-22
Sadly, the problem persists and appears unfixable with any of the things I've read in 10.04

tarek : )

---

### Post by nidelius on 2010-07-24
any news on how to get the internal microphone to work in 10.04?

---

### Post by juska on 2011-06-29
I am quite convinced that Canonical does not give a **** whether the internal mic works or not. The issue has been present with like at lest 6 versions in a row and nothing changes.

I tried days to make it work with 10.04 (and thinkpad x300) and eventually got too desperate, so I tried updating to 10.10. As you can guess, it did not pay off.

Dont even suggest updating to 11.04, I tried it once and it was a mistake..

I think I've read somewhere that mic works in 11.04. 10.04 should be an LTS, so the bug fix ought to be included there..?

I am quite frustrated.

---

