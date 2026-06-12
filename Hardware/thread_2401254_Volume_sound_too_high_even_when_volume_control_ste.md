---
title: "Volume sound too high even when volume control step its at minimum"
date: 2018-09-15
forum: Hardware
---

### Post by CarlosHP2000 on 2018-09-15
Hi Everybody!,

 I recently installed Lubuntu 18.04 on an HP dv5234us laptop. The only issue I am having is when I moved the volume control slider, it seems its no graduating the audio output and is too high even when I set at almost minimum. I think could be an issue with the sound drivers, I see is Intel NM/10/ICH7 and it is using the snd_hda_intel kernel module.

I am attaching a screenshot of the volume control position (at this position the audio is too high), and the sound drivers description.

Could you advise is this is something fixable, or any configuration I am missing.

I will really appreciate your help.

Best Regards,

Carlos.

---

### Post by Adam_GUI on 2018-09-15
What does Alsamixer look like when you run it in terminal?

---

### Post by CarlosHP2000 on 2018-09-15
Hi!, this is an screenshot of the Alsa Mixer and additional information the utility shows, thanks in advance,

Carlos.

[ATTACH=CONFIG]281079[/ATTACH]

---

### Post by CarlosHP2000 on 2018-09-15
Hi I apologize, this is the correct screenshot, with the Alsamixer running from terminal.

Carlos.

[ATTACH=CONFIG]281080[/ATTACH]

---

### Post by Adam_GUI on 2018-09-15
Huh...  Weird that it reports the card as Pulseaudio.  
Can you click where it says "Card" and change the audio device?

I'm sorry if that seems an odd question.  There's a disconnect between what I see in terminal and what your terminal has output.

Here's the type of screen I see:
[ATTACH=CONFIG]281081[/ATTACH]

---

### Post by Adam_GUI on 2018-09-15
> **CarlosHP2000 said:**
> Hi I apologize, this is the correct screenshot, with the Alsamixer running from terminal.

Carlos.

[ATTACH=CONFIG]281080[/ATTACH]

Oh, wow.  For that your card should be mute to whisper.

I know you had pulseaudio controls nigh on mute.  
I just wanted to be sure Alsamixer wasn't fluked and maxed out or something.

Do you see anything that looks funny when you use your right arrow key to scroll right?

---

### Post by ajgreeny on 2018-09-15
What happens if you reduce the PCM level?
One of my machines several years ago was terribly distorted if I set the PCM level to 100 as you show, but when running at somewhere between 60 and 70 all was fine.
On that system the volume control in the panel did not change to PCM level, only the master was affected.

---

### Post by CarlosHP2000 on 2018-09-16
Hi,

 I have been testing the right arrows while in Alsamixer and I think the behave ok. I can interact with the bottom menu in the Alsamixer. I even expanded a little more the screen to see other options that were hide when I sent the initial screenshots. I also selected the sound card to confirm it is using the sound card, still I don't see the volume control adjust the volume correctly. I goes from a lower sound to a maximum at this position that you see in the image (The control doesn't have to reach the full length of graduation to the right)

This how it looks:
[ATTACH=CONFIG]281086[/ATTACH][ATTACH=CONFIG]281087[/ATTACH][ATTACH=CONFIG]281088[/ATTACH]

---

### Post by CarlosHP2000 on 2018-09-16
Hi,

 I tested reducing  the PCM parameters, it decreases or increases the sound level , but still the mismatch with the volume control continues. I used the values you suggested. It seems that a volume step value its soo high that the minimum step on the volume control when moving to the right causes to reach the maximum sound.

---

