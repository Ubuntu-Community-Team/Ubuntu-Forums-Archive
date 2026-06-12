---
title: "Sound Stopped Working. Ubuntu 9.04"
date: 2009-04-24
forum: Hardware
---

### Post by Pan-Chan on 2009-04-24
I'm running an IBM Thinkpad T40, just freshly installed ubuntu 9.04. The problem i have is sound not working for multiple programs. I can hear the login sound, however, sound doesn't work well after that. I don't get sound in audacious, pidgin, or firefox. however, if i change audacious's sound output to OSS, audacious plays sound. when i go into system->preferences->sound i do not get sound when testing. Only if i change the device to OSS, it will play sound, but i have to stop the song playing in audacious, else i get the error 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

such the same, sound works in pidgin, provided audacious is not playing a song. even with audacious off, firefox does not play sound when watching a youtube video.

sound was working perfectly without any problem in 8.10, and was even working in 9.04, however has suddenly stopped for some reason.

any ideas on how to fix this, maybe re-installing sound somehow?

sound device is listed under lspci as:
Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

i'm not sure why it stopped, and have tried rebooting to no avail.
have also checked the volume control applet to ensure none are muted or down.
same in firefox, pidgin, and audacious.

---

### Post by Pan-Chan on 2009-04-24
as a side request, pertaining to sound, is there a way to have a logout sound?
i've set up a sound to play under the sounds applet system->preferences->sound, sound tab, desktop->logout, and set a custom sound. this sound does work, but i have never gotten it to play upon logout. doesn't play if you simply logout, or select to shutdown. is there something obvious i'm missing? i setup the login ready, successful, and failed sounds in the login window manager. those work fine, there was no option for logout, though.

---

### Post by Eezyville on 2009-05-03
I am having the exact same problem so any help will be appreciated.:(

---

### Post by Eezyville on 2009-05-06
I found a temporary solution.

I was google searching when I came across this post:

[HTML]http://ubuntuforums.org/showthread.php?t=1052754[/HTML]

So I typed this command in the terminal and my sound started to work.

```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

But I had to do it every time so I just put that piece of code up there in to my sessions manager so it starts when I log in. But there has to be a better fix. This works though.

---

### Post by Earth Infinite on 2009-05-27
I'm very new to Ubuntu, and I am having the same problems. The login sound will work at times, but the audio is completely gone otherwise.

---

### Post by iluii on 2009-06-06
Interesting, I upgraded to Xubuntu 9.04 back in April on my IBM x41and the sound would work for about 10 seconds and the cut out suddenly.I also noticed sounding was booting completely muted but after bringing up all volumes the sound cut off again.After googling for hours I couldn't find anything so I was forced to reinstall 8.10 which sux cause I could finlly use lassoing on my desktop on 9.04! Im gonna try Eezyville's fix as soon as I have some free time to mess around but if anyone has a more permanent solution that would be awesome.

---

### Post by wwuster on 2009-06-07
I don't know if this is related, but audacious just doesn't work anymore. All other players work fine, but starting about 10 days ago audacious now just produces a white noise sound and the graphical interface doesn't display on the gnome desktop. I'm running 9.04. I've tried uninstalling and reinstalling audacious, but it makes no difference. The only way to stop it from running is do do a 'killall audacious' from the command line.

Does anyone know why it doesn't work anymore?

William

---

### Post by firebone on 2009-06-13
I have the same issue. Every now and then my sound drops. I can hear the login sound just fine but after that it just dies.

My soundmeter shows that there is sound playing but I can't hear anything.

---

### Post by cesarsalles on 2009-06-16
I was haveing the same problem when I found this page. Went to Applications >> Sound and Video >> Gnome Alsa Mixer - and found PCM button all the way down; just slide it up and the sound came back.:D

---

### Post by Adyhr on 2009-08-24
Have had the same issue but got it fixed. Here what I did:

1. use pachage manager and uninstall ALL ALSA packages. This will break your gnome and, if installed, your KDE.
2. Restart. You will have to start in recovery mode.
3. log into console. You actually need to have your computer connected through CAT5. Wireless most likely will not work. (let me know if it would work for you though. I could not get it going)
4. run apt-get install gnome (and if desired apt-get install kde)
5. reboot again.

That was all what I did. Sound is now working again.
Good luck

---

### Post by rahul.goyal018 on 2009-09-05
hello.

          I am facing a problem regarding sound in ubuntu 9.04.actually it was working fine till last time when i booted it.it gives a  murmuring sound while i log into it.there is absolutely no problem regarding sound in my other OS .But in ubuntu at the moment i do not get even the startup sound nor any other sound.also when  i play any movie or song it still gives a murmuring sound .

I have Got a HP 6703TX notebook.Please help..!!
i am a beginner to ubuntu.



rahul goyal

---

### Post by theZoid on 2009-09-12
> **cesarsalles said:**
> I was haveing the same problem when I found this page. Went to Applications >> Sound and Video >> Gnome Alsa Mixer - and found PCM button all the way down; just slide it up and the sound came back.:D

That wasn't the problem with me....I have the same symptoms described in this thread....anyone else other than reinstalling gnome?

---

### Post by caspertk on 2009-09-13
after researching i found that the following code worked in the terminal
```

killall pulseaudio
alsamixer -Dhw

```Good luck :D

---

### Post by Exore on 2009-09-16
> **Adyhr said:**
> Have had the same issue but got it fixed. Here what I did:

1. use pachage manager and uninstall ALL ALSA packages. This will break your gnome and, if installed, your KDE.
2. Restart. You will have to start in recovery mode.
3. log into console. You actually need to have your computer connected through CAT5. Wireless most likely will not work. (let me know if it would work for you though. I could not get it going)
4. run apt-get install gnome (and if desired apt-get install kde)
5. reboot again.

That was all what I did. Sound is now working again.
Good luck

It was a dirty way, but it worked fine for me! 
Thank you!

---

### Post by theZoid on 2009-09-16
> **Exore said:**
> It was a dirty way, but it worked fine for me! 
Thank you!

I got mine working again by removing the login wav sound, changing the settings around and back to where they should be, reboot and all is well.  The login wav sound was locking up the sound system somehow I think.

---

