---
title: "Microphone not working on Vaio laptop"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by Askrates on 2008-01-25
Hi all, 

After getting a new vaio laptop, the first thing to do was shred vista and install ubuntu :) 

I got sound working by adding "options snd-hda-intel model=sony-assamd" to /etc/modprobe.d/alsa-base. However, the microphone doesnt work. I have set it to max in alphamixer and made sure it isnt muted.

The soundcard is a HDA INTEL - Realtek ALC262
The laptop is a vaio tz50b

I hope some kind sould can help!

---

### Post by dali101 on 2008-01-26
Same problem here! On my Vaio FZ21m I'm unable to get the built-in micrphone working... I also tried it with Skype.

I'm running Gutsy and when I start the alsamixer with "-V All" option to view the output and input channels I have the Master and PCM outputs which can also be adjusted, then I have the Mic Jack (with a red CAPTUR L R) which isn't adjustable, then I have Capture and Digital, both adjustable and not muted, and then I have Internal... actually nothing there. I tried to mute and unmute different channels, tried all the possible setups but it doesn't seem to work.

The card is HDA Intel and the chip is SigmaTel STAC9872AK .

Any help regarding this issue is greatly appreciated.

---

### Post by Wim Verhaegen on 2008-01-29
Hello,when I first installed ubuntu on my sony vaio vgn fz 21m I only had sound via the build in speakers.
The audio jack didn't work (I didn't test the mic, sorry)
so i searched the ubuntu forums.
what seemed to do the trick with my 7.10 was to go to the software sources under administration,
go to the update tab and to check the gutsy backports. update your repository list then run in a terminal:
sudo apt-get install linux-backports-modules-generic
(generic would be the normal case but it could also be i386 if you have been messing a bit around in your synaptic.)
linux spits some output and when it's done I used the following command:
sudo gedit /etc/modprobe.d/alsa-base
now a gedit file should open.
be carefull now. you are editing a file which only root has access to.
just add at the end of this file in a new line

options snd-hda-intel model=vaio

now reboot and cross your fingers

For the record this is just a cp from someone elses post :)

---

### Post by dali101 on 2008-01-30
You can't help but to love the Ubuntu community!!! I am so glad that I finally found a good windows replacement.

And Wim, you are a genius! Thank you very much... it worked!

I also had to add this line to /etc/modporbe.d/alsa-base, additionally to what you suggested:

options snd-hda-intel model=3stack

Then I had to restart and set the volume in the mixer to maximum in the Recording tab and also had to uncheck the "Let Skype adjust de mixer" option in Skype, because the volume was far too low.

Now everything works fine and I have a fully functional Ubuntu Vaio...

---

### Post by jorgecarrillo150990 on 2008-03-02
Thank you, your advice really worked.
Now my laptop is fully using the powah of ubuntu

---

### Post by duvis on 2008-05-07
hi everybody I am new to UBUNTU and I just find it great fun! 

Had the same problem with VAIO PCG-602M OS UBUNTU 8.04 when using SKYPE no outgoing sound. 

I have fixed the problem as follows:

open volume control
edit preferences
select all of them and close
in Recording tab unclick no microphone and raise volume
in Switches click Internal Mic 

hope this helps!:)

---

### Post by nuskak on 2008-05-09
> **dali101 said:**
> You can't help but to love the Ubuntu community!!! I am so glad that I finally found a good windows replacement.

And Wim, you are a genius! Thank you very much... it worked!

I also had to add this line to /etc/modporbe.d/alsa-base, additionally to what you suggested:

options snd-hda-intel model=3stack

Then I had to restart and set the volume in the mixer to maximum in the Recording tab and also had to uncheck the "Let Skype adjust de mixer" option in Skype, because the volume was far too low.

Now everything works fine and I have a fully functional Ubuntu Vaio...

WOW!! now I can use the headphones but the microphone doesn't works yet.

And The mic also runs correctly.

what I've done with the mic is to go on Aplications/Sound and Video/Recording sound and then you select the input: I've choosen internal MIC and also runs with capture.
In sound properties, in the Switch option , I've not activate de Mic Jack option.
Thank's a lot!!

---

