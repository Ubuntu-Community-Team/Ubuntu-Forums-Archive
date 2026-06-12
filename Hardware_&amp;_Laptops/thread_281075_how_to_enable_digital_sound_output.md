---
title: "how to enable digital sound output"
date: 2006-10-20
forum: Hardware &amp; Laptops
---

### Post by misterbeetz on 2006-10-20
Hey everyone.  Does anyone know to enable digital output of sound in ubuntu.  I get sound through headphones when i plug them into the analog jack.  Nothing however is coming through my digital speakers which are connected to the spdif jack.

For reference, im using the onboard sound on my a7n8x-e deluxe.  I believe the sound is soundstorm.  This mobo uses the nforce2 chipset.

-misterbeetz

---

### Post by burito on 2006-11-04
Actually, you have a realtek AC97 chipset

And I'm yet to get it outputting through the digital outputs...

---

### Post by burito on 2006-11-04
Update: Go into System->Preferences->Sound in Gnome, select "NVidia nForce2 IEC958" as your decault output for everything... voila!

I don't know if it outputs through optical, but I'm hearing output through coax as we speak.

You'll probably want to go into the volume control and turn up a bunch of volume settings, unmuting where appropriate.. I've got them all on, so I can't tell you which one to use, my guess is you want the ones concerning IEC958... good luck

---

### Post by burito on 2006-11-04
just forget about your digital out.. its much easier...

ALSA ppl think that an API should not hide the hardware details from the program. So you will need to tell EVERY program that uses ALSA, that you actually want it to output to IEC958, which is peachy as about 2% of alsa programs are capable of understanding that request.

About the only way you will get relatively pain free IEC958 support, is to write to the ALSA developers, asking them to get their act together.

---

### Post by jocko on 2006-11-04
Actually [that mobo]("http://www.asus.com/products4.aspx?modelmenu=1&model=217&l1=3&l2=13&l3=56") have soundstorm. That means you could follow my [guide to get nvidias soundstorm drivers working]("http://www.ubuntuforums.org/showthread.php?t=253725").
If you don't want nvidias drivers (which support hardware mixing and dolby digital encoding), you could check the settings in alsa-mixer and try which channels to unmute to get digital output through ac'97 (which in my experience have **very** poor sound quality and can not output sound from several sources).

---

### Post by burito on 2006-11-04
oh silly me.
I've seen a few nforce2's all of which with the realtek chip, and naively thought they all were like that

anyway after much googling I've managed to piece together a config file for alsa that will output everything to digital and eliminate multiple program problems (with dmix), but no 5.1 :-(

perhaps I may have to use the nvidia drivers :-( - update: nvidia's not offering them on their site.. so I figure folks out there may want my config file...
create /etc/asound.conf and fill it with this...
[FONT=System]pcm.ossmix {
        type dmix
        ipc_key 1024
        ipc_key_add_uid false
        ipc_perm 0660
        slave {
                pcm "hw:0,2"
                rate 48000
                channels 6
        }
}

pcm.!default {
        type plug
        slave.pcm "ossmix"
}

pcm.dsp "ossmix"
pcm.dsp1 "ossmix"[/FONT]

---

### Post by jocko on 2006-11-04
nvidia still have their latest (one year old) drivers in their [driver archive]("http://www.nvidia.com/object/linux_nforce_1.0-0310.html").

---

