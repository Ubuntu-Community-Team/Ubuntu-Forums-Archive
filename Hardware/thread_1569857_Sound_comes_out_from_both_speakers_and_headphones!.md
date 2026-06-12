---
title: "Sound comes out from both speakers and headphones! Please help :("
date: 2010-09-07
forum: Hardware
---

### Post by 3rlend on 2010-09-07
[FONT=Arial][/FONT][FONT=Garamond]Hei. I have a problem with Linux Ubuntu. When I plug in my headphones, the sound comes out from both the internal speakers and the headphones!
Please help me!
[/FONT]

---

### Post by ottosykora on 2010-09-07
did you try other headphones?
This is more a hardware problem then ubuntu .
There is a simple switch inside the socket where you insert your headphones and this should switch off the speaker. But if the connector does not fit properly, the everything is possible.

---

### Post by 3rlend on 2010-09-07
> **ottosykora said:**
> did you try other headphones?
This is more a hardware problem then ubuntu .
There is a simple switch inside the socket where you insert your headphones and this should switch off the speaker. But if the connector does not fit properly, the everything is possible.

I have tried other headphones, and it works in Windows 7, which I also have on this computer...

---

### Post by ottosykora on 2010-09-07
what computer ist it? 
Have not met so far anything where this is done by some kind of software pure. The interlock is simple mechanical device, even by inserting some wooden stick into the socket, the speker should go off, I used to have even an alarm clock years ago, simply have let the toothpick have been pulled out of the socket by an ordinary mechanical clock and so the sound started form the speakers. 
It can be well a cold solder joint on the main board or similar causing this.
Can you switch off the speakers by some suitably sized wooden stick, someting like rest of a tooth pick or so?

---

### Post by 3rlend on 2010-09-07
> **ottosykora said:**
> what computer ist it? 
Have not met so far anything where this is done by some kind of software pure. The interlock is simple mechanical device, even by inserting some wooden stick into the socket, the speker should go off, I used to have even an alarm clock years ago, simply have let the toothpick have been pulled out of the socket by an ordinary mechanical clock and so the sound started form the speakers. 
It can be well a cold solder joint on the main board or similar causing this.
Can you switch off the speakers by some suitably sized wooden stick, someting like rest of a tooth pick or so?


I have Asus X52J.
I can't switch the speaker off by putting a tooth pick in the input...

---

### Post by AlexZaim on 2010-09-07
It's an kernel issue. I had it too...
Either upgrade to the latest available in the repos, or search for "best-intel ppa"(guido iodice) and add it to your repos + install the latest kernel.

---

### Post by 3rlend on 2011-04-13
> **AlexZaim said:**
> It's an kernel issue. I had it too...
Either upgrade to the latest available in the repos, or search for "best-intel ppa"(guido iodice) and add it to your repos + install the latest kernel.

(I am sorry I respond so late)
I am new to this... how do you do that?

---

### Post by Yellow Pasque on 2011-04-13
Try:
```
echo "options snd-hda-intel model=asus" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```

If that doesn't work, edit the alsa-base.conf and change 'asus' to 'hp-laptop'
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

---

### Post by 3rlend on 2011-04-16
> **Temüjin said:**
> Try:
```
echo "options snd-hda-intel model=asus" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```If that doesn't work, edit the alsa-base.conf and change 'asus' to 'hp-laptop'
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

None of those worked :S

On the first:

```

erlend@erlend-laptop:~$ echo "options snd-hda-intel model=asus" | sudo tee -a /etc/modprobe.d/alsa-base.conf
[sudo] password for erlend: 
Sorry, try again.
[sudo] password for erlend: 
options snd-hda-intel model=asus
```

---

