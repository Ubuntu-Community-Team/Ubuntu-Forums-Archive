---
title: "System Sounds don't work anymore??!!"
date: 2006-09-15
forum: Hardware &amp; Laptops
---

### Post by GoodPanos on 2006-09-15
Recently I got a Logitech 250 USB headset and I thought I try it with Ubuntu.  To my surprise it worked! =D> 

After I shut my notebook and openned it up again without the headset the system sounds did not work any more; :confused: you know the intro music when you log in.  I went to Preferences\Sounds and clicked on the play button next to the Login sound and nothing.  Then I went to Device Manager and clicked on Ubuntu Device Database.  When I ran the sound test there was none.  I openned up an MP3 and I could here the song. ](*,) 

My notebook is a Dell Inspiron 6000 with a SIGMATEL STAC 975X AC97 sound card.  My Ubuntu installation uses the Intel ICH6 sound driver and all along it has been working fine with this driver until I plugged the Logitech headset.

The same headset did not work in Kubuntu.

Any ideas of what's going on?

---

### Post by shat on 2006-09-15
Yeah, I had this same exact problem.

USB headsets create .conf files in your home directory with device information.  My solution was to just delete these files, however, I'm sure there is a more elegant way to do it.  Essentially, alsa makes the .conf files, then when the headset isn't plugged in, looks for the device, and doesn't find it, and reverts to oss.  That's why some music will work (w/ alsa), and other things dont.

Edit:  I think there were 2, and I think one was called something like .asoundrc

---

