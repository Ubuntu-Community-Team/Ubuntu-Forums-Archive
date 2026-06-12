---
title: "Gigaware 43-215 USB Headset"
date: 2008-11-30
forum: Hardware
---

### Post by tnanek on 2008-11-30
I'm having problems getting my USB Headset to work. When it is plugged in and I go to System -> Preferences -> Sound, it is set there and it tests fine, yet when I go to a website such as youtube, the sound comes out of my normal speakers, and not my headset. I would also like to get the microphone working, but thats not as vital (I don't have the option of doing Skype type conversations unless I have both features really, so there's no point to the microphone part of the item unless the headphones part of it functions.

I've tried playing with the Default Mixer Track Settings found at the same location as above, but no luck with any of that.

The product company and product number is Gigaware 43-215

---

### Post by i.t.guru on 2009-02-05
Well, I am not alone in this. I bought a lesser version of the same brand, which is a Radioshack Brand BTW and it worked but me being me, I had to have the bigger set for gaming and now have the same issue. Not on Ubuntu but thats neither here nor there. It's Linux either way with the same issue but I can't use them playing UT2004 and also, in my infinite wisdom, unplugged my speakers thinking it would auto correct and switch to the usb headphones for sound out put but no go there either.
I also played around with Alsa and PulseAudio preferences and still didly. I am using Mandriva 2009 PowerPack so it is apparently not an Ubuntu only issue so since I have put in a request with Mandriva, if I get a resolution, I will come share it with you.
Peace... ;)

---

### Post by TonyFordz on 2009-06-02
...

---

### Post by austinpsycho on 2009-07-04
its a little late; but if your tests worked in alsa mode, all you gotta do is go to terminal; type in ```
asoundconf list
```
find out what your headset is called *ps mine was called default* then type in ```
asoundconf set-default-card default
``` replacing default with whatever yours is called..  

if it only works in oss then delete your pulse audio package ```
sudo apt-get remove pulseaudio
``` restart and follow the steps above.. you're headset will be working before you know it

---

### Post by austinpsycho on 2009-07-04
hope that helps everyone... since i couldn't find a solution i had to play.. for hours.. . . . .  and hours... . . and.. hours!

---

### Post by TonyFordz on 2009-09-05
> **austinpsycho said:**
> its a little late; but if your tests worked in alsa mode, all you gotta do is go to terminal; type in ```
asoundconf list
```
find out what your headset is called *ps mine was called default* then type in ```
asoundconf set-default-card default
``` replacing default with whatever yours is called..  

if it only works in oss then delete your pulse audio package ```
sudo apt-get remove pulseaudio
``` restart and follow the steps above.. you're headset will be working before you know it

Thanks a lot man your awesome!!!

asoundconf list

========================================================
tonyfordz@tonyfordz-desktop:~$ asoundconf list
Names of available sound cards:
ICH5
default
tonyfordz@tonyfordz-desktop:~$
========================================================

ICH5 is my onboard sound for Motherboard P4P800E-Deluxe

I deleted the sound pack too which allowed things to work & I was about blasted away when my Ubuntu logged in lol! & THERE WAS SOUND! Now to get the flash working... I had a guide to this that worked once guess I will have to find it again lol.

Thanks again dude that is awesome!

---

### Post by TonyFordz on 2010-02-23
Wow now I am trying to use this same headset on Ubuntu 9.10 64-Bit but when I try to use the same information on terminal it tells me,

asoundconf: command not found

Perhaps I just need to buy the older type headsets to avoid this drama...

---

### Post by TonyFordz on 2010-02-24
Can someone please tell me how to reinstall the default sound... I did the following trying to make my headset work now I get no sound at all even on my speakers.

```

sudo apt-get remove pulseaudio

```

Above is the code I used & I need the code to use to reinstall them being I don't know jack about Linux commands.

------------

Think I just answered my own question not sure till I restart. But I just changed remove in the line to install

---

### Post by JedMeister on 2010-02-24
```
sudo apt-get install pulseaudio
```

Should do the trick!

---

### Post by TonyFordz on 2010-06-05
Hey I have the latest version of Ubuntu right now which is the 10.04 64-Bit version... I try to use the above commands to list my sound devices & get the following,

[IMG]http://i46.tinypic.com/10yla2r.png[/IMG]

Also when I go to my sound icon I can get the mic to register my voice but I get no sound back in my headset but the mic seams to work.

Any ideas?

---

### Post by nomad5 on 2010-06-13
I get the same message on 9.10;

asoundconf: command not found

I would really like to use my headset so I can use skype.

---

### Post by nomad5 on 2010-06-13
Ok, I got it working. I got the solution from tenchi39.

[http://wwww.ubuntuforums.org/showthread.php?p=9454837#post9454837](http://wwww.ubuntuforums.org/showthread.php?p=9454837#post9454837)

The only additional thing I did was I had to change the settings in sound preferences input and output to audio adapter analog.

---

### Post by TonyFordz on 2010-10-27
[IMG]http://i54.tinypic.com/126ai55.png[/IMG]

I know this is an older version, but honestly couldn't get any of them to work in the list. If someone that codes for Ubuntu could add support for this in the upcoming releases that would be awesome because I love this headset, and have 4 of them now. I also run a few forums on private sites & promote Ubuntu so any help is always appreciated!

I will be upgrading to 10.10 64-bit as soon as I figure out why 10.10 64-bit doesn't display my HD, I am wondering if its because it already has a 32-bit Ubuntu installed not a 64-Bit... Guess I will have to use Windows to repartition.

---

