---
title: "GTX970 with Realtek driver,no sound... fresh install"
date: 2016-03-24
forum: Hardware
---

### Post by tonyoh2 on 2016-03-24
Hi,

I am a new user of ubuntu. :)

However life is hard... I spent 7 hours in order to fix the lack of sound but without any success.
Could anyone please advice what I should do ?

I think I have to disable one of the audio device (preferably the nvidia ? from GTX 970) and possibly the HDMI ?
Please see picture attached.

[[IMG]http://s10.postimg.org/rjulcbp51/multipledrivernosound.jpg[/IMG]]("http://postimg.org/image/rjulcbp51/")

Best Regards,

---

### Post by Drone4four on 2016-03-24
First of all, welcome to the community, my friend.  

So you're have difficulty with sound, eh?  The first thing to try would be alsamixer. Enter 'alsamixer' in your terminal and increase the volume for each bar.  You might have to install alsamixer.  Although given that you know enough to try 'aplay -l', I suppose you may have already tried all this, just didn't mention it in your original post.

> I think I have to disable one of the audio device (preferably the nvidia ? from GTX 970) and possibly the HDMI ?
I'm running a slowly aging GTX 560 Ti.  I can very easily toggle between HDMI (my GPU) and Analog Output (mobo) from Gnome's All Settings menu which you can find by clicking the top right corner of your desktop, navigating down the the wrench and screw driver icon and then under 'Hardware', click, 'Sound.'  You should have something which looks like what i've attached.  From there you can choose to enable and disable what ever audio devices were auto detected by Ubuntu.  You can also try adjusting the volume from this Sound menu.

---

### Post by tonyoh2 on 2016-03-25
Thank you very much :)

Unfortunately I do not have the sound icon in "Hardware", please see picture.
[URL="http://postimg.org/image/mjxxeix59/"][IMG]http://s14.postimg.org/mjxxeix59/Settings_002.jpg[/IMG]

[[img]http://s28.postimg.org/tuslsy0eh/tonyoh_tonyoh_Buntu_003.jpg[/img]](http://postimg.org/image/tuslsy0eh/)
[/URL]

---

### Post by tonyoh2 on 2016-03-25
Okay... I connected 1990s speakers and it worked just fine.

Problem seems to be related to Creative T10 Inspire.
Could you please advise me why I don't have the sound icon in Hardware ?

---

### Post by Drone4four on 2016-03-25
> Could you please advise me why I don't have the sound icon in Hardware?
I'm running Gnome 3.14.  You look like you're running Xfce.  Amiright?  Xfce should still have an option for sound hardware I just have no idea why its not there.  I wish I could provide better advice.  Suggesting that you try Gnome isn't very helpful. =/

---

### Post by tonyoh2 on 2016-03-27
Thank you I use gnome now. (Still helpful) ;)

---

