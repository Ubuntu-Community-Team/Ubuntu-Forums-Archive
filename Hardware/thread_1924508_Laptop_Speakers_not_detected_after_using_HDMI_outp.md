---
title: "Laptop Speakers not detected after using HDMI output"
date: 2012-02-12
forum: Hardware
---

### Post by screaminj3sus on 2012-02-12
I've been having a strange issue. My sound usually works fine, but I noticed After plugging in my laptop via hdmi to my tv and using hdmi sound an annoying issue occurs.

After unplugging the HDMI cable I cannot get my laptop speakers to work again. If I go to sound settings > output it still says Intel HDMI output. So then I went to the hardware tab to change it from HDMI to analog stereo. After doing that it still does not work, and the output tab changes to "Dummy output, stereo". The only way I've been able to fix it was rebooting, which let me select my output normally.

I've also had a similar issue happen with my USB headset's output. A few times, seemingly a random occurance it would suddenly stop detecting my USB device. It would show at all in the hardware our output tab until rebooting.

Anyone else run into issues like this?

My laptop is an asus u52f, driver is snd-hda-intel, sound card is "00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)"

At first I assumed its some kind of issue with the intel sound driver, but a similar issue occasionally happens randomly to my usb headset, and the usb functions as sort of its own sound card with a different driver afaik.

---

### Post by patmalcolm91 on 2012-05-06
I'm also having the same issue with my sound in 12.04. My card is the Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) with the snd-hda-intel driver.

For me, though, rebooting didn't help. I also noticed that my headphone jack still works, it's only the speakers on the laptop that have stopped working.

---

### Post by patmalcolm91 on 2012-05-06
I think I may have solved the issue. Upon examining /etc/modprobe.d/alsa-base.conf, I noticed that it no longer had the following line.

options snd-hda-intel model=auto

I re-added this line, saved, rebooted, and everything seems to be working now.

---

### Post by sammiev on 2012-05-06
When switching I had to go into system settings ---> sound and make the changes there. Not sure if I had to do that in 11.10 or not as I have been using 12.04 since per-alpha.

---

### Post by pjhoyer on 2012-05-10
Hei I'm had the same issue on asus nj61/ati hd 5730  with 12.04 after gluing in the missing line as you mentioned and restart ....perfect.
thank you so much

---

### Post by arthurzennig on 2012-06-08
Hey guys, 
If those solutions above did not worked as planned - like it just happened to me - don't panic! 
This is no fancy solution, but it works fine:

> It seemed that none solution from posts were working for me.
After everything fails, any solution is good, right?
So i did this ( and worked ):
- I plugged back my notebook to the HDMI connection from my turned on tv;
At this moment, i arranged to make the display to show on the tv ( like  everytime when i want to watch a movie from the pc in my tv );

- Then, i played a music.
- The sound came from the tv;
- Opened the [I]sound settings;
[/I]- Changed configurations so that the music came from the notebook again;
- unplugged the HDMI cable from the notebook;

**And now i am hearing musics back from my notebook again!** 

footnote: this is no fancy solution and i wish i had one, but it worked  right. Now every time when i watch a movie from the notebook through the  tv, i will re-adjust the sound configuration to playback from the  notebook before i unplug the HDMI cable from it.Hoped it helped someone.

The link to the post:
[http://ubuntuforums.org/showthread.php?t=1851870](http://ubuntuforums.org/showthread.php?t=1851870)

---

