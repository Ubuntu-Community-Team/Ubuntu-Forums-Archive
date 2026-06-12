---
title: "Missing: USB mic!"
date: 2015-08-13
forum: Hardware
---

### Post by Zestie Bumwhig on 2015-08-13
Has anyone seen my new USB mic? Because ALSA certainly hasn't.

Actually, it WAS being seen, and now it's not.

The beginning seemed like a common problem: Jack recognized my Blue  Snowball USB microphone when I first plugged it in; after that, while it  showed up in Jack's options (using qjackctl), I couldn't get sound from  it. If I ran Pure Data with ALSA (instead of Jack), I could use the  mic.

I eventually got it to work with Jack, following these instructions: [http://www.penguinproducer.com/Blog/...ces-with-jack/]("http://www.penguinproducer.com/Blog/2011/11/using-multiple-devices-with-jack/") ... essentially, using alsa_in to point out the mic, and then I made the connections in Jack's Connections tab.

BUT then my computer crashed! (Not because of audio - there's a bad  battery connection, and that happens sometimes when it gets jostled). It  crashed while I was still playing (successfully) with PD/Jack/Snowball,  the first time.

I fear that some .config file was written wrong/not-written because of  the "improper" closing. Now, I can't get the computer to see this sucker  anywhere.

Running lsusb, it seems like it's not seen. My USB ports still work -  thumb drives are recognized. Also, the LED power light on the mic comes  on.

ONE OTHER THING! In my attempts to solve this problem, I deleted the  relevant portion of /var/lib/alsa/asound.state (as suggested here: [http://ubuntuforums.org/showthread.php?t=2153270](http://ubuntuforums.org/showthread.php?t=2153270)  ) I don't think this relates - I did that BEFORE my crash, and got it  to work. Post-crash, I've also re-installed all things ALSA-related, in  the hope that it would fix itself - so, I believe a new asound.state has  been written anyway.

Any takers? I think I probably just need to alter some config file... but I've no idea which, or with what.

Thanks!

by the way - running LXDE 12.04.05 on a 2006 Vaio laptop. I'm not technically running Ubuntu Studio, but that's only because my lappy can't handle it.

---

### Post by CharlesA on 2015-08-19
Going to give this a bump. Hope you are able to find the answer to your problem.

---

