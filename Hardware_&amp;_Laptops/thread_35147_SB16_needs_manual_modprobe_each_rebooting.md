---
title: "SB16 needs manual modprobe each rebooting"
date: 2005-05-17
forum: Hardware &amp; Laptops
---

### Post by 4ebees on 2005-05-17
Sorry for the long post, but I thought it best I explain as clearly as I can.

In short, each time I reboot, I have to modprobe my SB16 sound card. I'm trying to work out how to fix this.

I loaded Ubuntu 5.04, then installed KDE - what a whopper of an exercise that was!

I also installed the SB16 card I have and disabled the onboard sound card in the BIOS.

THEN

per

[http://www.ubuntuforums.org/showthread.php?t=31494&highlight=soundblaster](http://www.ubuntuforums.org/showthread.php?t=31494&highlight=soundblaster)

sudo modprobe snd_sb16

Then

alsamixer

and boosted the volume.

This gave me sound!!

Installed a kid-friendly collection of icons and a pink-cat Firefox theme (urm, okay, this is the point that I tell you this is for my daughter - why does she like PINK? - and is on an old Compaq)

So all works well, except... on reboot, I've no sound.

I then followed the suggestions at:

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Vibra16X.&chip=sb16&module=sb16#modp](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Vibra16X.&chip=sb16&module=sb16#modp)

and my install is brand new, with updates and with alsa-driver and alsa-utils up-to-date, so I shouldn't have to install the latest, as of posting, X.X.X.X.0.1 version (should I?) when I have those that were the latest the day before?

So I made a file called alsa, installed it as the suggested /etc/modutils/alsa

containing:

# ALSA portion
        alias char-major-116 snd
        alias snd-card-0 snd-sb16
    # module options should go here

        # OSS/Free portion
        alias char-major-14 soundcore
        alias sound-slot-0 snd-card-0
    
    # card #1
    alias sound-service-0-0 snd-mixer-oss
    alias sound-service-0-1 snd-seq-oss
    alias sound-service-0-3 snd-pcm-oss
    alias sound-service-0-8 snd-seq-oss
    alias sound-service-0-12 snd-pcm-oss

(just a question, where is says "# module options should go here", should there be anything there?)

Then ran

update-modules

and then... still doesn't work.

So

sudo modprobe snd_sb16

and

alsamixer

again

and again, sound... with XMMS and Realplayer, but not with Amarok...?

I can get sound (though not in Amarok), which is a huge improvement, but have to buggerise around after rebooting.

The Alsa site also suggest (I think this is correct) that I should modify the:

/etc/modules.conf

but the link describing how is broken.

Any assistance, advice, suggestions would be most appreciated.

Thanks,

---

### Post by dave9191 on 2005-05-17
You are going to want to add snd_sb16 to the /etc/modules file to have that loaded up for you each time. As for sound in KDE, you want to make sure that Arts sound server is running with the artsd command. That should provide sound from KDE apps like amoarK. Then you can configure other apps like XMMS and realplayer to use arts instead of ESD or whatever you have running on the system. Hope this helps :) 

Dave

---

### Post by 4ebees on 2005-05-18
To Dave9191 and Jonah, 

Much appreciated. Worked first time. (Actually, the second time - I entered the incorrect dialogue the first time :roll: )

---

### Post by dave9191 on 2005-05-18
Cool, glad it works now :)

---

### Post by macewan on 2005-05-18
[QUOTE=4ebees]Sorry for the long post, but I thought it best I explain as clearly as I can.

In short, each time I reboot, I have to modprobe my SB16 sound card. I'm trying to work out how to fix this.

I loaded Ubuntu 5.04, then installed KDE - what a whopper of an exercise that was!

I also installed the SB16 card I have and disabled the onboard sound card in the BIOS.

THEN

per

[http://www.ubuntuforums.org/showthread.php?t=31494&highlight=soundblaster](http://www.ubuntuforums.org/showthread.php?t=31494&highlight=soundblaster)

sudo modprobe snd_sb16

Then

alsamixer

and boosted the volume.

This gave me sound!!

Installed a kid-friendly collection of icons and a pink-cat Firefox theme (urm, okay, this is the point that I tell you this is for my daughter - why does she like PINK? - and is on an old Compaq)

So all works well, except... on reboot, I've no sound.

I then followed the suggestions at:

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Vibra16X.&chip=sb16&module=sb16#modp](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Vibra16X.&chip=sb16&module=sb16#modp)

and my install is brand new, with updates and with alsa-driver and alsa-utils up-to-date, so I shouldn't have to install the latest, as of posting, X.X.X.X.0.1 version (should I?) when I have those that were the latest the day before?

So I made a file called alsa, installed it as the suggested /etc/modutils/alsa

containing:

# ALSA portion
        alias char-major-116 snd
        alias snd-card-0 snd-sb16
    # module options should go here

        # OSS/Free portion
        alias char-major-14 soundcore
        alias sound-slot-0 snd-card-0
    
    # card #1
    alias sound-service-0-0 snd-mixer-oss
    alias sound-service-0-1 snd-seq-oss
    alias sound-service-0-3 snd-pcm-oss
    alias sound-service-0-8 snd-seq-oss
    alias sound-service-0-12 snd-pcm-oss

(just a question, where is says "# module options should go here", should there be anything there?)

Then ran

update-modules

and then... still doesn't work.

So

sudo modprobe snd_sb16

and

alsamixer

again

and again, sound... with XMMS and Realplayer, but not with Amarok...?

I can get sound (though not in Amarok), which is a huge improvement, but have to buggerise around after rebooting.

The Alsa site also suggest (I think this is correct) that I should modify the:

/etc/modules.conf

but the link describing how is broken.

Any assistance, advice, suggestions would be most appreciated.

Thanks,[/QUOTE]


obviously the color pink conflicts with Linux

uninstall anything with the color pink in it & stop rebooting your computer

---

### Post by 4ebees on 2005-05-18
[QUOTE=macewan]obviously the color pink conflicts with Linux

uninstall anything with the color pink in it & stop rebooting your computer[/QUOTE]




Actually the colour pink conflicts with me! We've tried to keep her away from such things, but as soon as you let them out in public...! What can a dad do?  ;-)

---

