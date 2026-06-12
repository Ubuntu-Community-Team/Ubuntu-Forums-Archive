---
title: "Help Needd! HP TX2500 no sound after upgrade to Ubuntu8.10"
date: 2008-11-07
forum: Hardware
---

### Post by karrou on 2008-11-07
Hi all,

My leptop tx2500z lost sound when I upgradet my ubuntu system from 8.04 to 8.10. The sound was working good when I added a line in to /etc/modprobe.d/alsa-base:
    options snd-hda-intel index=0 model=toshiba position_fix=1

When system boots to the login window, I heard big noise and it was gone after Desktop showed up. And then the OS totally kept silent. I can see the 
Volume Icon and also the sound card info. 

Can anybody help me? Thank you very much.

---

### Post by TheYeti on 2008-11-07
I am having the same problemux. (A sickened former Vista user)
after updating to 8.10. I didn't attempt the alsa-base edit yet, as I am new to Linux.

If anyone has a solution, it would be greatly appreciated to give detailed steps for novices like me.

---

### Post by gali98 on 2008-11-07
Okay first just to make sure, upload your /etc/modprobe.d/alsa-bsse file for me to check....
That line should work.
You can also try the line:
options snd-hda-intel index=0 model=acer

Kory

---

### Post by gali98 on 2008-11-07
Just now saw the other post...

Okay, sound will not work without editing the alsa-base file.

to do this simply:

1. Press Alt+F2     this will open up a dialog.
2. in the box, type ```
gksu gedit /etc/modprobe.d/alsa-base
```
3. Scroll to the very bottom and add either one of these lines:
options snd-hda-intel index=0 model=toshiba position_fix=1
or
options snd-hda-intel index=0 model=acer
(you can only have one of these lines at a time, and the line needs to be on a line by itself)
4.Now simply save this and restart.
5. If sound does still not work, when you log in there should be a volume applet in the top-right corner of the screen. right click and select "Open Volume Control".
6. I do not have your model of laptop, so You will have to play with the knobs, but it is pretty easy. Basically if a knob is muted or pulled down far, try maxing it out and see if you get sound.
Kory

---

### Post by karrou on 2008-11-09
Thanks folks. I did added this line on my new 8.10 OS just like what I did on 8.04. The problem is in this new OS I only can hear big noise when I login.

In my Volume Control I saw three options:
HDA ATI SB (Alsa mixer)
Realtek ALC268 (OSS Mixer)
Capture:ALSA PCM on front:0 (ALCC268 Analog) via DMA .....

The wired thing is that I installed a WinXP OS in my virtualbox and it has sound!

I upload my alsa-base file below and hope some one would give me some advises.

---

### Post by toobaz on 2008-11-10
> **gali98 said:**
> Just now saw the other post...
3. Scroll to the very bottom and add either one of these lines:
options snd-hda-intel index=0 model=toshiba position_fix=1
or
options snd-hda-intel index=0 model=acer
(you can only have one of these lines at a time, and the line needs to be on a line by itself)


Does your sound work fine after that?

I mean: I did it and I do have sound, but if I plug in my headphones, I still hear music from the speakers...

Pietro

P.S: I know this has been reported in other posts, I only want to understand if you did find a fix for it

---

### Post by gali98 on 2008-11-10
I am beginning to think it may be a problem with updating instead of installing a new os....  Some users say it works fine, while others are having the same error as you. Did you upgrade or reinstall?
Kory

---

### Post by karrou on 2008-11-11
I totally re-installed the new OS.

---

### Post by gali98 on 2008-11-11
So does it work (with adding the line..)?
Kory

---

### Post by toobaz on 2008-11-11
> **gali98 said:**
> I am beginning to think it may be a problem with updating instead of installing a new os....  Some users say it works fine, while others are having the same error as you. Did you upgrade or reinstall?
Kory

If by "you" you mean "me": I reinstalled.

Pietro

---

### Post by gali98 on 2008-11-12
No lol...
I meant karrou.. But yours works, right?
Kory

---

### Post by toobaz on 2008-11-12
> **gali98 said:**
> No lol...
I meant karrou.. But yours works, right?
Kory

It almost does, but if I plug the headphones I still hear music (also) from the speakers!

---

### Post by gali98 on 2008-11-13
I suggest emailing the alsa devel mailing list with your system info. I did that, and though I'm not sure I did anything, Sound was fixed a lot in Intrepid... Maybe it will do the same in Jaunty... You can only try and hope..
Kory

---

### Post by karrou on 2008-11-13
Hi Kory,

I had this problem after I completely reinstalled OS from 8.04 to 8.10, but not just upgraded it. The method you told me works well in 8.04 but when I format and reinstalled the 8.10, the sound has problem. So I am thinking maybe it is because of other setting effects the sound setting. Have you checked my alsa-base.txt file? Did you find any an-normal?  Thanks.

Karrou

---

### Post by gali98 on 2008-11-14
I just checked it again, and can find nothing wrong with it. I guess your only hope is to bug the devs... Try the alsa site and launchpad. With any luck, you can get support soon... Sorry,
Kory

---

