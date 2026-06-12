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

### Post by JonahRowley on 2005-05-17
Add **snd_sb16** to **/etc/modules**.  The alsa startup scripts will now also save your mixer levels.

---

### Post by 4ebees on 2005-05-17
Thanks Jona.

Sorry about this. I had a net connection failure and reposted this, then reaslised that it had accepted my last post - which I thought had failed when my net connection went down.

See: [http://www.ubuntuforums.org/showthread.php?t=35147](http://www.ubuntuforums.org/showthread.php?t=35147)

---

