---
title: "[SOLVED] Sound Card Problems"
date: 2007-06-29
forum: Hardware &amp; Laptops
---

### Post by senken12 on 2007-06-29
Before I upgraded from Edgy to Feisty, my soundcard used to work perfectly fine but now it just... doesn't! :o

I'm not sure what card it is but the laptop is a Toshiba Satellite Pro A100

---

### Post by matheuu on 2007-06-29
Hey mate,
I'ave a Toshiba Satellite A200. I got no sound too!
We might be able to fix your sound.
Firstly open a terminal and type      alsamixer 
and copy the whole screen into the post.

---

### Post by senken12 on 2007-06-30
It doesn't look quite right on here... But:

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.13 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA ATI SB                                                             &#9474;
&#9474; Chip: Generic 11c1 Si3054                                                    &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: PCM                                                                    &#9474;
&#9474;                                                                              &#9474;
&#9474;                &#9484;&#9472;&#9472;&#9488;                                                          &#9474;
&#9474;                &#9474;  &#9474;                                                          &#9474;
&#9474;                &#9474;&#9618;&#9618;&#9474;                                                          &#9474;
&#9474;                &#9474;&#9618;&#9618;&#9474;                                                          &#9474;
&#9474;                &#9474;&#9618;&#9618;&#9474;                                                          &#9474;
&#9474;                &#9474;&#9618;&#9618;&#9474;                                                          &#9474;
&#9474;                &#9474;&#9618;&#9618;&#9474;                                                          &#9474;
&#9474;                &#9474;&#9618;&#9618;&#9474;                                                          &#9474;
&#9474;                &#9474;&#9618;&#9618;&#9474;                                                          &#9474;
&#9474;                &#9474;&#9618;&#9618;&#9474;                                                          &#9474;
&#9474;                &#9474;&#9618;&#9618;&#9474;                                                          &#9474;
&#9474;                &#9474;&#9618;&#9618;&#9474;                                                          &#9474;
&#9474;                &#9492;&#9472;&#9472;&#9496;                 &#9484;&#9472;&#9472;&#9488;                 &#9484;&#9472;&#9472;&#9488;                &#9474;
&#9474;                                     &#9474;MM&#9474;                 &#9474;OO&#9474;                &#9474;
&#9474;                                     &#9492;&#9472;&#9472;&#9496;                 &#9492;&#9472;&#9472;&#9496;                &#9474;
&#9474;               84<>84                                                         &#9474;
&#9474;             <  PCM   >            Caller I             Off-hook              &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
May be able to see it better here: [http://img135.imageshack.us/my.php?image=screenshot32nf3.png](http://img135.imageshack.us/my.php?image=screenshot32nf3.png)

---

### Post by senken12 on 2007-06-30
Bumpy

---

### Post by HuXu on 2007-06-30
Hey i have a Toshiba Satellite P105 and im having the same problem.  I have researched and found that its the Intel HD Audio chipset that i have and i would like to follow these directions

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+HD-audio+and+modem.&chip=ICH6%2C+ICH6M%2C+ICH7%2C+ESB2&module=hda-intel](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+HD-audio+and+modem.&chip=ICH6%2C+ICH6M%2C+ICH7%2C+ESB2&module=hda-intel)

but its not clear as to what driver i need to be installing or what lib.
It sounds like to me in your Alsa mixer you just have to unmute it.  use the arrows and make it to where it has 00 underneth and no MM by pressing . or ,

this is what my screen shot looks like

[http://s16.photobucket.com/albums/b28/blueexplore/?action=view&current=myalsamixer.png](http://s16.photobucket.com/albums/b28/blueexplore/?action=view&current=myalsamixer.png)

---

### Post by lisati on 2007-06-30
Sorting out sound on Toshiba systems seems to be a common problem. What worked for me on my A100 laptop, after a creating a dual-boot machine (Windoze XP home & Ubuntu 7.04) was to use the update manager to load all the recommended updates, rebooting, and then tweaking the volume knob. This might not suit everyone , and if you're on dial-up it might take a while - good luck!

---

### Post by senken12 on 2007-06-30
thanks - Ill try both and get back to ya :)
well... When my CD player shuts up so I can hear it! :P

---

### Post by senken12 on 2007-06-30
Thanks HuXu but it didn't work :(

---

### Post by senken12 on 2007-06-30
> **lisati said:**
> Sorting out sound on Toshiba systems seems to be a common problem. What worked for me on my A100 laptop, after a creating a dual-boot machine (Windoze XP home & Ubuntu 7.04) was to use the update manager to load all the recommended updates, rebooting, and then tweaking the volume knob. This might not suit everyone , and if you're on dial-up it might take a while - good luck!

Thanks very much
Works perfectly now! :D

---

