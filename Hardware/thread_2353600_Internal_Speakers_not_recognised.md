---
title: "Internal Speakers not recognised"
date: 2017-02-23
forum: Hardware
---

### Post by angel mike on 2017-02-23
On my Compaq Pressario PC there is no sound from the speakers and they are no recognized in the Setting-Sound page.

---

### Post by Frogs Hair on 2017-02-23
What audio card/chip is in use and have you checked for additional drivers yet. The following command should display the sound card info. ```
lspci 
```

---

### Post by angel mike on 2017-02-27
Thanks Frogs Hair for replying - sorry about delay.#
I have a built tin sound card - HDA Intel HDA NVidia and the Linux compatible is ALSA Driver Version k4.4.0-63-generic. 
Can I install this via the terminal - the Software Centre does not show up anything.
Also do I need to delete the existing driver snd hda intel ?

---

### Post by Frogs Hair on 2017-02-28
Does this driver show up in additional drivers ?

---

### Post by angel mike on 2017-02-28
Not showing up in Additional Drivers.
I obtained the Sound Card Driver using the command 'cat /proc/asound/version ' after first finding the installed card driver by command 'grep snd/proc/asound/modules' which gave snd_hda_intel

---

### Post by Frogs Hair on 2017-03-03
You might want to view the link.
 [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by angel mike on 2017-03-04
Thanks for response Frogs Hair will follow up and hopefully mark this as solved ! Mike

---

### Post by angel mike on 2017-03-04
The link page says its out of date and the follow up links seem to be about de-bugging issues and ALSA development. I think I know what the problem is--the existing driver 'snd_hda_intel' needs to be replaced by the Linux compatible 'ALSA Driver Version k4.4.0-63-generic. Surely there must be away of doing that using the Terminal .

---

### Post by him610 on 2017-03-04
angel mike, I think some more information needs to be displayed. 
Please show results of ```
inxi -A
```

---

### Post by angel mike on 2017-03-05
OK him610 - I loaded the program and output is 
```

sudo inxi -A
Audio:     Card NVIDIA High Definition Audio Controller driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.4.0-64-generic

```
which is the info given previously.
Now what ?
 Thanks for replying and hope you can see a simple way forward. I have search quite a few sites but the info is confusing and complicated. Regards Mike

---

