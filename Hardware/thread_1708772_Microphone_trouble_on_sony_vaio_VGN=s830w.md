---
title: "Microphone trouble on sony vaio VGN=s830/w"
date: 2011-03-17
forum: Hardware
---

### Post by rollyah on 2011-03-17
Hello,
i recently installed the latest ubuntu on my laptop.
everything works perfect as it should. though microphone is causing a bit of trouble.
i had installed the latest release of skype and i found out i cannot use my MIC.
trying to troubleshoot i went to sound and audio, and tried recording thugh that didn't work either.
i went into preference where i made sure the MIC isnt muted.
there's in the dropdown list three choices: mic1 mic2 line
tried them all with no luck.
i've googled for the past 1 day for a number of solutions
where i installed pvhdchooser and then used pulse -V all through terminal.

nothing is working with me! or maybe am simply  doing it wrong.

NB: it's worth to mention that if i record, theres a white noise being recorded. and sometimes if the hdd or fan gives a higher sound, the level of input that shows in the audio preferences changes a bit.

---

### Post by ptptaylor on 2011-03-17
When you record and make a noise yourself is that picked up? Eg speaking. Because sometimes you can get electrical interference causing those noises from the cpu or hdd.
Does the input level in sound preferences change when you make a noise? 
What profile are you on in the sound preferences application within the hardware tab?

---

### Post by rollyah on 2011-03-17
hey, thanks for helping out.

to answer your questions:

1. no not at all, nothing's picked up.

2. not sure if understood the profile though it used to be analog stereo output. i've previously set it to analog stereo duplex.


> **ptptaylor said:**
> When you record and make a noise yourself is that picked up? Eg speaking. Because sometimes you can get electrical interference causing those noises from the cpu or hdd.
Does the input level in sound preferences change when you make a noise? 
What profile are you on in the sound preferences application within the hardware tab?

---

### Post by rollyah on 2011-03-25
any advice?

> **ptptaylor said:**
> When you record and make a noise yourself is that picked up? Eg speaking. Because sometimes you can get electrical interference causing those noises from the cpu or hdd.
Does the input level in sound preferences change when you make a noise? 
What profile are you on in the sound preferences application within the hardware tab?

---

### Post by lidex on 2011-04-03
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

