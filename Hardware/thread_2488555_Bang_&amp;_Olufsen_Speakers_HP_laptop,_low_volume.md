---
title: "Bang &amp; Olufsen Speakers HP laptop, low volume"
date: 2023-07-08
forum: Hardware
---

### Post by meetdilip on 2023-07-08
Hi, I have an HP Pavilion laptop which comes with Bang & Olufsen speakers. While the sound is fine on Windows 10, my dual boot Ubuntu 22.04 has a very low volume. Sometimes, I am forced to use Bluetooth speakers to actually hear some media or YouTube videos. 

Recently I did an AskUbuntu search and found a few topics on the same. There was a suggestion to use alsa-tools. I did install it and even tried a GUI for the same. Sadly, I couldn't figure out what to do with those options. 

Is it actually possible to fix the low volume issue ( that is the only problem ) using ALSA tools or other methods through some guidance here? Would be great if someone can help. Thanks.

PS : It is a two year old laptop and has Nvidia GeForce GTX 1650 graphics card and AMD Ryzen 5600H processor

---

### Post by Autodave on 2023-07-08
[https://ubuntuforums.org/showthread.php?t=2485707&highlight=low+volume](https://ubuntuforums.org/showthread.php?t=2485707&highlight=low+volume)

That thread worked for me.  If it works for you, then you need someone, with a higher pay scale than me, how to make that run whenever you boot the machine.

---

### Post by meetdilip on 2023-07-08
Thanks for the reply. My issue is not only with Firefox but VLC and other options as well. It is the same if I use Google Chrome. 

Is it safe to set the volume as 150% though? While VLC has that option, I was told never to go beyond 100% to keep the hardware safe. 

The closest answer I found on AskUbunt is this 

[https://askubuntu.com/questions/1052432/bang-olufsen-audio-issue-on-hp-laptops](https://askubuntu.com/questions/1052432/bang-olufsen-audio-issue-on-hp-laptops)

While I do not have the crackling sound issue, I have low volume problems. There is a script / command which says enables the Bass speaker. I am not sure whether it is the same for my model.

That is where I got the idea of using ALSA tools. Thanks.

Update:

I used alsamixer in Terminal. Volume is max ( 100% ) for my sound card.

---

### Post by meetdilip on 2023-07-10
The sound card model is Realtek ALC285.

---

### Post by SeijiSensei on 2023-07-10
Have you checked in the System Settings for sound? It may be that the master volume for the output is set too low.

---

### Post by meetdilip on 2023-07-10
Yes, I did check. Almost all options including settings, alsamixer, and pavucontrol. All of them are at 100%. 

Thanks. I was told it has to be a driver issue.

---

### Post by meetdilip on 2023-07-11
Created a bug report 

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/2026719](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/2026719)

I tried Fedora 36 live on Ventoy. The volume was better than what I had in 22.04.

---

