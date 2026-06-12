---
title: "How do I change the default system sound card ?"
date: 2006-03-16
forum: Hardware &amp; Laptops
---

### Post by Stinger on 2006-03-16
Hi all !
I'm quite happy with my current Breezy setup , but there is one thing that really gets on my nerves. :mad: 
Changing the default system sound card.
My box has two sound cards , one onboard and one PCI soundcard , Breezy detects both but chooses the onboard sound card (even if I disable it in BIOS) to be the default system sound card.:-# 
But I want my PCI sound card to be the default system sound card.:cool: 

Does anybody know how to change it ?

I found this guide [http://doc.gwos.org/index.php/Multisounds/]("http://doc.gwos.org/index.php/Multisounds/")
but it doesn't work for me , it just leaves me with only the onboard sound card working. :-? 

The only way I can change sound card seem to be as **user** in 
System > Settings > Sound.
But thats not what I want.

---

### Post by JustRandomName on 2006-03-16
Hi,

You can set the default sound card by running this in a terminal:
```
gnome-sound-properties
```

And selecting your sound card.

This however does not always work (ALSA ignores it for example).

The best method I found is to follow this guide [http://www.ubuntuforums.org/showthread.php?t=44753](http://www.ubuntuforums.org/showthread.php?t=44753) :

When you have finished open the /etc/asound.conf file and search for this bit:
```

pcm.snd_card {
     type hw
     card 0
}

```

And change "card 0" to "card 1"

Hope this helps

---

### Post by Stinger on 2006-03-16
Thanks for the tips JustRadomName.:) 

I have already set the card using```
gnome-sound-properties
```
But this doesn't work for games like Frozen-Bubble or Solarwolf , sound from app's like these games still uses the output from the onboard sound card.

I tried the solution from the thread you linked to , but it seems to be written for hoary Hedgehog , it's corrected for Breezy on the last two pages (11,12).

I didn't work for me , I tried  "card 1" for PCI , it just leaves me with only the onboard sound card working again.:-? 

It would be nice if there was som kinda sound card setup during installation or a sound card control tool.

---

### Post by Stinger on 2006-03-17
I found it !

The answer lies on the Ubuntu users maling list on this thread (Page 2)
[ Ubuntu and Multimedia (audio, in particular)]("http://www.ubuntuforums.org/showthread.php?t=115540&page=2&highlight=%2Fproc%2Fasound")

> crimsun@fungus.sh.nu
wrote:

In a Terminal:

```
echo "options [COLOR="Red"]snd-ali5451[/COLOR] index=-2" | sudo tee -a /etc/modprobe.d/alsa-base
```

Afterward it's probably easiest to reboot, but you could use (instead):

```
sudo invoke-rc.d alsa force-reload
```

Now [COLOR="Red"]snd-ali5451[/COLOR] needs to be replaced with the sound module for your onboard sound card , the one that you'll like to move from "card 0" to "card 1" .

Note !!
If you have been experimenting with different /etc/asound.conf setups , like I have , you'll have to remove the /etc/asound.conf file and most likely the .asoundrc file in your home directory.
Basicly restoring the original Ubuntu sound setup.

---

