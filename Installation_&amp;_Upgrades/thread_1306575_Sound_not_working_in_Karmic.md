---
title: "Sound not working in Karmic"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Tanvir on 2009-10-30
Hello Everyone, I have a Dell Inspiron 1501 laptop. I just upgraded from 9.04 to 9.10. Everything is working except the sound. 

I used to not have any problem with sound in Ubuntu. Could any one please help me?

Thanks

---

### Post by fenzik on 2009-10-31
While upgrading I got the same problem, I'm having Dell Vostro 1500 and here is the sound card

```

fenzik@fenzik:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: SigmaTel STAC9205
Codec: Conexant ID 2c06

```

---

### Post by malayalees on 2009-11-10
Mine neither. Running HP Pavilion dv6733tx (2yrs old)

```

$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC268
Codec: Motorola Si3054

```

---

### Post by terryzhouke on 2009-11-19
I have the same problem. any promotion else?

---

### Post by devgujar on 2009-11-19
Mine no prblem...
My laptop is Dell Inspiron 1525.

---

### Post by josephe on 2009-11-19
Same problem with my Inspiron 1520

Anyone got a solution  please?

---

### Post by fenzik on 2009-11-19
> **josephe said:**
> Same problem with my Inspiron 1520

Anyone got a solution  please?


josephe : My speaker volume was low and I couldn't identify from Kmixer. Then I make it work by increasing the volume by adjusting the volume level in **alsamixer** from command line.

---

### Post by josephe on 2009-11-20
Hi there
 
Thanks, I'll give that a try

---

### Post by Paul Vega on 2009-11-20
Kia Ora
It sounds like (no pun intended) like my similar problem. Installed Karmic 9.01 and no sound. I found a thread on a launchpad.com board that discussed Bog #409518 in Coherence. So I went to Synaptic and installed Python Coherence and all associated files. I also discovered my Hardware settings in Sound Preferences were wrong so I changed to Analogue Stereo Duplex and now i have sound. I don't know if both changes were needed as late last night I thought that I had altered my Sound Preferences to no avail. Hope this may help...

---

