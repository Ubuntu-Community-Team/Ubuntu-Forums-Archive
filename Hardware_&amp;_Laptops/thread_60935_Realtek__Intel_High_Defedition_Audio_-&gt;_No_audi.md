---
title: "Realtek / Intel High Defedition Audio -&gt; No audible sound (as in muted)"
date: 2005-08-29
forum: Hardware &amp; Laptops
---

### Post by Moralez on 2005-08-29
After using the [hda intel how to guide](https://wiki.ubuntu.com//HdaIntelSoundHowto) I was able to flwalesslsy install and configure my sound board (even removed the -with-cards=hda-intel to check that I was installing the right driver, alsaconfig deteced the right devide and I checked with modinfo, everithing is loaded)

Now I have two devices: HDA Intel (Alsa Mixer) and Realtek ALC800 (OSS Mixer)... I have tried activating everything, boosting all sound, changing from one device to another and there is simply no sound coming from the speakers and the headphones... I just don't understand...

It's a Asus AV6a laptop.

Can some1 help me? thanks in advance.

Edit: Installed the Realkted driver pack, worked like a charm... now to get the headphone jack working :-(

Tried boosting all sound to the max in alsamixer, unmuted everything... still dosen't work, mabye it's because I'm using a laptop... in Windows the speakers shut down as soon as jack in a mic (preety cool... if your using Windows....).

---

### Post by Septor on 2005-08-30
[QUOTE=Moralez]After using the [hda intel how to guide](https://wiki.ubuntu.com//HdaIntelSoundHowto) I was able to flwalesslsy install and configure my sound board (even removed the -with-cards=hda-intel to check that I was installing the right driver, alsaconfig deteced the right devide and I checked with modinfo, everithing is loaded)

Now I have two devices: HDA Intel (Alsa Mixer) and Realtek ALC800 (OSS Mixer)... I have tried activating everything, boosting all sound, changing from one device to another and there is simply no sound coming from the speakers and the headphones... I just don't understand...

It's a Asus AV6a laptop.

Can some1 help me? thanks in advance.

Edit: Installed the Realkted driver pack, worked like a charm... now to get the headphone jack working :-(

Tried boosting all sound to the max in alsamixer, unmuted everything... still dosen't work, mabye it's because I'm using a laptop... in Windows the speakers shut down as soon as jack in a mic (preety cool... if your using Windows....).[/QUOTE]

There should be a "Headphone" control in alsamixer.  If it is there, it should be a toggle switch (i.e. no volume control, only mute or unmute).  Unmuting might activate the front headphone jacks.  You might want to try some of the other mixer switches which can be adjusted by alsamixer as well.

---

### Post by BigMadWolf on 2005-09-08
[QUOTE=Moralez]After using the [hda intel how to guide](https://wiki.ubuntu.com//HdaIntelSoundHowto) I was able to flwalesslsy install and configure my sound board (even removed the -with-cards=hda-intel to check that I was installing the right driver, alsaconfig deteced the right devide and I checked with modinfo, everithing is loaded)

Now I have two devices: HDA Intel (Alsa Mixer) and Realtek ALC800 (OSS Mixer)... I have tried activating everything, boosting all sound, changing from one device to another and there is simply no sound coming from the speakers and the headphones... I just don't understand...

It's a Asus AV6a laptop.

Can some1 help me? thanks in advance.

Edit: Installed the Realkted driver pack, worked like a charm... now to get the headphone jack working :-(

Tried boosting all sound to the max in alsamixer, unmuted everything... still dosen't work, mabye it's because I'm using a laptop... in Windows the speakers shut down as soon as jack in a mic (preety cool... if your using Windows....).[/QUOTE]
 i have the same problem :(
speakers are working but the jack headphones aren't :(

---

### Post by kbuel on 2005-10-03
Hey, I have a Asus z71v and I have the same problem, I can't get any sound out of the headphones.

I was wondering if anyone had an update on this issue.

Thanks a lot!
-K

---

