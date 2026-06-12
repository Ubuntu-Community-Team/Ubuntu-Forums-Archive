---
title: "Sound in web browser"
date: 2012-01-18
forum: Hardware
---

### Post by Larjk on 2012-01-18
Hi, I use Kubuntu 11.10 32bits in a ASUS pro64jq.

My problem is that: 

I have a 5.1 headphones (ozone strato). I can listen music in Amarok, audacious, dragon... but I can't listen the videos or music with the web browser.

What i can do?

Thanks

---

### Post by madvinegar on 2012-01-18
Which web browser are you using?

Open up your web browser, go to i.e. youtube and start playing a video clip of a song.

Leave the browser open with the videoclip playing, and then go to system, preferences, sound and on the last tab (applications) you will probably see an alsa plug-in bar.
Check to see if it set to 0 or is muted.

If yes, unmute it and set it all the way up.


Otherwise, your web-browser may be missing the sound plugging.

I use chrome and never had any problems. You should try it.

---

### Post by Larjk on 2012-01-18
I have problems with any web browser.

[IMG]http://img842.imageshack.us/img842/3977/instantnea4j.png[/IMG]

The left plugin is for firefox and the right for chromium.

Thanks

---

### Post by madvinegar on 2012-01-18
Just to understand.


When you use your web-browser you have sound from your speakers but you do not have sound from your headphones?

Or no sound at all, even from your speakers?

---

### Post by Larjk on 2012-01-18
Yes, I have sound in my speakers and in standard headphones but I don't have sound in my 5.1 headphones.

Thanks

---

### Post by MoreOrLess on 2012-01-18
Can you take a screenshot of your Phonon/KDE sound setting ('Multimedia' in systemsettings)?

---

### Post by Larjk on 2012-01-18
OK, thanks. 

I resolved my problem. In phonom I put the headphones as the prefer device, in music, video... but in audio reproduction i don't put yet. 

When I select the headphones as default device in the general section audio reproduction I resolved the problem. 

[IMG]http://img860.imageshack.us/img860/7375/instantnea5.png[/IMG]

Thanks

---

### Post by MoreOrLess on 2012-01-18
You;re welcome. Please mark the thread solved.

---

