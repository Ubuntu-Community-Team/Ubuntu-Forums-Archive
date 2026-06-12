---
title: "low sound output"
date: 2009-08-31
forum: Hardware
---

### Post by calanor on 2009-08-31
i have onboard alc888 realtek audio chip and i am using ubuntu 9.04 ,
in windows through realtek settings when i choose headphones as the output device volume gets doubled 
but in ubuntu even after setting device as headphones i just get half that of windows 
how can i rectify this problem do i need any sort of drivers

---

### Post by calanor on 2009-09-02
anyone??

---

### Post by calanor on 2009-09-03
nobody??

---

### Post by Zoot7 on 2009-09-03
Why not try installing the Gnome Alsa Mixer and moving all the sliders to the max?
```
sudo apt-get install gnome-alsamixer
```

Failing that you could try upgrading Alsa to the latest version. This is what sorted the low volume on my laptop's speakers, I no longer have to turn it up to the max just so I can watch Movies/TV on it. 
I'd advise using this script listed here:
**[http://ubuntuforums.org/showthread.php?t=1046137]("http://ubuntuforums.org/showthread.php?t=1046137")**

---

### Post by calanor on 2009-09-04
the script exits with this error

Resolving ftp.alsa-project.org... failed: Name or service not known.
wget: unable to resolve host address `ftp.alsa-project.org'
rm: cannot remove `alsa*.tar.bz2': No such file or directory
mv: cannot stat `alsa-*': No such file or directory

-------------------------------------------------------------
-  Prepare for compilation and installation...
-------------------------------------------------------------

alsa-driver-1.0.20  not found

---

### Post by Zoot7 on 2009-09-04
Did you give the Gnome ALSA Mixer a try?

---

### Post by calanor on 2009-09-05
all the sliders were already maxed out and the script doesn't work even after modifying the version no
i have wriiten about it in the alsa thread that you directed me to
how did you make it work

---

### Post by DaveHi on 2009-09-05
Hi calanor

Had much the same problems since upgrading to 9.04.

Solved problem by following soundcheck's instructions on the thread that Zoot7 directed you to and installing Gnome Alsa Mixer, again as suggested by Zoot7.

Are you sure that you managed to download a uncorrupted version of soundcheck's script from [http://ubuntuforums.org/attachment.php?attachmentid=113163&d=1241945700](http://ubuntuforums.org/attachment.php?attachmentid=113163&d=1241945700) ?

Suggest that you reinstall Gnome Alsa Mixer, again dowmload soundcheck's script, run script as instructed and finally run Gnome Alsa Mixer, un-mute and max all channels. Please don't make my mistake by not maxing the 'side' channel!!!

Hopefully, like me you will then have sound.

Now if anyone can explain to me why my 'master' channel mutes and reduces volume each time I open preferences I would be a happy NOOB!

Good luck.

---

### Post by DaveHi on 2009-09-05
OK. my *intentional* mistake has been spotted!

Volume will stop muting if I point both the volume control and Gnome Alsa Mixer at the same device!

Doh! :redface:

---

