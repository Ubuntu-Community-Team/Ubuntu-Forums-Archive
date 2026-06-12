---
title: "Headphones no longer work after jaunty upgrade(Sony Vaio)"
date: 2009-04-27
forum: Hardware
---

### Post by linuxgr on 2009-04-27
Hi all,

many of you have experienced this problem before - headphones not working or not muting the speakers in many laptops. The workaround so far was to find the sound card's codec and add some lines to /etc/modprobe.d/alsa-base

Yesterday I upgraded to 9.04 and the problem is back again!

I noticed the alsa-base file was now moved to alsa-base.conf
The lines I added that worked so far were

options snd-hda-intel model=vaio index=0
options snd-hda-intel model=3stack probe_mask=1

(YES, BOTH LINES AT THE SAME TIME. I worked A LOT to get there and somehow using both these lines was the only way to get my system working perfectly! If I used only one, it did not work)

Now that I upgraded does not work anymore. Tried to remove both lines, then one of them, then the other but no luck!!!

Please if you have any suggestions I really need to hear them....

After every upgrade I always get a problem as a gift.... :-(

---

### Post by gcvisel on 2009-04-27
> **linuxgr said:**
> Hi all,

many of you have experienced this problem before - headphones not working or not muting the speakers in many laptops. The workaround so far was to find the sound card's codec and add some lines to /etc/modprobe.d/alsa-base

Yesterday I upgraded to 9.04 and the problem is back again!

I noticed the alsa-base file was now moved to alsa-base.conf
The lines I added that worked so far were

options snd-hda-intel model=vaio index=0
options snd-hda-intel model=3stack probe_mask=1

(YES, BOTH LINES AT THE SAME TIME. I worked A LOT to get there and somehow using both these lines was the only way to get my system working perfectly! If I used only one, it did not work)

Now that I upgraded does not work anymore. Tried to remove both lines, then one of them, then the other but no luck!!!

Please if you have any suggestions I really need to hear them....

After every upgrade I always get a problem as a gift.... :-(

   Try typing "alsamixer" in a terminal window.  Then turn on/off what you need there.  Tab to see other settings.

---

### Post by linuxgr on 2009-04-27
Thanks for the reply, but unfortunately all I see there now since the upgrade is PCM and Master. The rest of the controls that used to be there are now gone......

---

### Post by linuxgr on 2009-04-28
I also found a file where I had stored the output of:
cat /proc/asound/card0/codec#* | grep Codec

I used to receive:
Codec: SigmaTel CXD9872AKD 
Codec: Conexant ID 2c06 
Codec: Realtek ALC262

But now, with the same command I receive only the first, Sigmatel.


I do not know if this is relevant.

The whole laptop sound situation IS SO FREAKIN ANNOYING!!!!!

I have installed ubuntu on over 10 laptops and every time the same sh*t! 

Half an hour to install, three hours to find a workaround for the audio....And my case is the worst of all!

---

### Post by dwolf on 2009-04-28
I have a Sony Vaio AR520. I did an upgrade to Jaunty as well, and had the same problem you do with the headphone jack. I found this thread: [http://ubuntuforums.org/showthread.php?t=1087407&highlight=sony+vaio+ar]("http://ubuntuforums.org/showthread.php?t=1087407&highlight=sony+vaio+ar")


I added the following lines to my alsa-base.conf (from the thread):

options snd-hda-intel model=vaio enable=1 index=0 position_fix=1

options snd-hda-intel model=vaio probe_mask=1

options snd-hda-intel model=vaio


Hope this helps. It worked for me. :)

---

### Post by linuxgr on 2009-04-28
dwolf,

YOU ARE THE MAN!!!!!!

It works great now! Only problems I have is with the microphone and skype, but this is the least of my problems!


THANKS!!!!

---

### Post by linuxgr on 2009-04-28
Apparently, one line is enough:

options snd-hda-intel model=vaio enable=1 index=0 position_fix=1 probe_mask=1


Are you experiencing problems with the microphone? Along my voice I get a sound like someone is frying onions. lol.

Back to ibex again, there was an extra capture level called "Digital". With the new configuration, it is there no more. Whenever I got that weird sound, all I had to do was to lower the "Digital" and all was ok.

I'll try more, but if anyone has ideas they are welcome.

---

### Post by linuxgr on 2009-04-28
ok, it seems that playing with the "index" value makes things a little better. If I find more, I will post here.

Thanks

---

### Post by dwolf on 2009-05-21
Great that it's working for you now. :guitar:

Thanks for letting me know that one line is necessary - still learning. :)

I haven't tried the mic yet.

---

### Post by johny_ on 2009-05-27
Thank you so much for this hint dwolf. It solved me a big problem indeed.

I don't know pretty anything About alsa internals, but wonder about that lines

> options snd-hda-intel model=vaio enable=1 index=0 position_fix=1

options snd-hda-intel model=vaio probe_mask=1



Why is it necessary to make the switching go?

This one 

>  options snd-hda-intel model=vaio

makes me understand it activates some kind of special configuration for the module, to make it understand it's dealing with a Vaio, right?

If anyone of you know how to figure out this, just for learning how to deal with Alsa...

Cheers

---

### Post by the_fury on 2009-06-24
> **dwolf said:**
> I have a Sony Vaio AR520. I did an upgrade to Jaunty as well, and had the same problem you do with the headphone jack. I found this thread: [http://ubuntuforums.org/showthread.php?t=1087407&highlight=sony+vaio+ar]("http://ubuntuforums.org/showthread.php?t=1087407&highlight=sony+vaio+ar")


I added the following lines to my alsa-base.conf (from the thread):

options snd-hda-intel model=vaio enable=1 index=0 position_fix=1

options snd-hda-intel model=vaio probe_mask=1

options snd-hda-intel model=vaio


Hope this helps. It worked for me. :)


Confirmed and working on a Sony Vaio VGN-FZ240E ... thank so much dwolf

---

### Post by nothingspecial on 2009-08-03
Thankyou, this has been doing my head in.

:guitar:

---

### Post by whomajigi on 2009-12-06
This sounds like my problem after my 9.10 upgrade.

Unfortunately, I'm a complete n00b when it comes to Linux. Is there any way someone could explain what I should be doing to fix this in a step by step kind of way? I'd be endlessly appreciative. 

(I've managed to fix all of my other upgrade issues except this one and my monitor brightness adjusting!)

---

### Post by linuxgr on 2009-12-07
whomajigi,

this is an old thread, and it applies to ubuntu 9.04.

I have not had the time to upgrade to 9.10, I am not sure it will work but you can always try.
Here it is:

1)open a terminal(for gnome: applications->accessories->terminal)
2)type:

```
sudo gedit /etc/modprobe.d/alsa-base
```

3)enter your password and a file will open. Go to the very end and add a new line:
```
options snd-hda-intel model=vaio enable=1 index=0 position_fix=1 probe_mask=1
```

4)restart.

Let us know if it works for 9.10. If not, you repeat steps 1 and 2 and erase the line you added and then wait for the rest of us to start talking about it again 

:-)

---

### Post by whomajigi on 2009-12-07
Oops, somehow I missed that this was for 9.04! 

Hrm. No luck. Thanks for trying to help though. The file that opened was completely empty, what are the odds that that is part of the problem?

---

### Post by linuxgr on 2009-12-07
oops!!!! sorry!


I forgot alsa-base changed to alsa-base.conf!

for step 2, type:

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```


That should do it...

---

### Post by whomajigi on 2009-12-07
Thanks for the update! Unfortunately, it did no good. It might be my imagination but my headphones appear to be making a little more static-ey noise than last time. 

Ah well. I'm on a netbook. Once I have the opportunity, I think I'm just going to go back to 9.04. This version has way too many glitches that don't seem to be getting addressed. Thanks for all of your help though! :)

---

### Post by linuxgr on 2009-12-08
I just finished updating to 9.10. I usually have problems in every upgrade, this time though not so much. As for the headphones, they seem to work out of the box! Amazing...

You said you had a netbook? Then maybe these settings do not apply to you. You need to find out your audio codec and then add options related to your codec.

There is a howto somwhere here on the forum, it is very explanatory.

cheers

---

