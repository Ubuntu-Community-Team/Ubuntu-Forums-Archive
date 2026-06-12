---
title: "[HELP] Rear Speakers Not Working"
date: 2010-10-16
forum: Hardware
---

### Post by JustinHD on 2010-10-16
Hello,

I'm currently using Ubuntu 10.10.
I've searched around to fix this problem and although i've tried numerous solutions provided by users on multiple forums I ended up screwing my sound completely and had to reinstall ubuntu.

So the problem goes like this:

In my sound settings I enabled Analog Surround 5.1 but my Rear Speakers are not outputting any sound. Also the Front-Center and LFE channels are swapped around. (when I click TEST in LFE it sounds in center and viceversa)
In windows my RealTek ALC889 software utility has an option to swap Center/Sub output.

Any help would be appreciated.

Thanks.

EDIT: If I switch to 7.1 my rear speakers work but they work when I click test on the side speakers and they sound really slow (i think its because i need to turn up the volume in my alsa mixer, but i would like to leave this option as a last call if i don't find any fix for the 5.1 option)

---

### Post by JustinHD on 2010-10-16
Center/Sub fixed. Modified the PulseAudio channel mapping file and now the center speaker and sub-woofer work fine.

Now all that remains is to fix the rear speakers not making any noise.

Ultimately if there is no solution to this problem I will set my output to Analog Surround 7.1 and just modify the PulseAudio channel mapping file again to reflect the correct output.

Cheers,
Justin

---

### Post by JustinHD on 2010-10-17
Bump, anyone?

---

### Post by JustinHD on 2010-11-23
oh come on, nobody ?

---

### Post by SlugSlug on 2010-11-23
I find pulse rubbish for my 5.1,

I remove it and install alsa + gnome-alsamixer

---

### Post by JustinHD on 2010-11-24
I think i tried with alsa too...that didn't solve it :(

---

