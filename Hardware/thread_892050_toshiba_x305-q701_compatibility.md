---
title: "toshiba x305-q701 compatibility"
date: 2008-08-16
forum: Hardware
---

### Post by sexicanme on 2008-08-16
i love ubuntu i just bought this laptop :KS and i do not know if all the hardware is compatible w ubuntu studio edition. Ive done some research but my result was nil.

Please help!! as I am getting irate at microsux windblows vista.

---

### Post by saygin on 2008-10-22
Hi, 
I have bought the same laptop recently too. I have used ubuntu before for 2 years and I installed it on this machine. However, what I write here should not be an exact answer because I installed 8.10 beta and haven't tweaked any.
First, the touchpad doesn't work, but i have an external mouse plugged in usb and works like a charm. (by the way I tried fn+F9 but it seems that all fn functions and the graphical user interface in vista are made for vista, doesn't run on linux)

Second, the headphones are in but speakers on the laptop still gives sound. this may be done in pulseaudio mixer or something like that but i couldn't do anything to prevent this in alsa mixer.

I haven't try wireless connection yet but the wired one is working without any problems. also havrn't try bluetooth either.

after installing restricted driver for nvidia, compiz etc. works smooth.

it seems like the red buttons on the top of laptop are mostly usable thanks to gnome. the play/pause, stop, next track, prev track buttons are working, but the others are not. And yet I could't find a way to assign them any shortcut.

Before the end of writing, I should tell this again, It is tested in beta version of ubuntu 8.10. some issues may be solved in normal version. After some time with ubuntu, I may write some more. bye for now!

---

### Post by saygin on 2008-12-01
Here again,
I have ubuntu 8.10 stable and fully updated. I have to make some updates to the thread and some corrections.
-I installed nvidia 18.06 beta driver and it is now much better, especially with compiz on.
-Headphones issue has stoped since I have downloaded and compiled the newest alsa drivers package. Now it works as it should be.
-Still haven't tried bluetooth and wireless internet. So, nothing new.
-I could see that red shortcut buttons can be used in gnome but I couldn't do it yet in amarok. I'm not sure it is because of me or drivers.
-Touchpad still not usable. I use an external usb mouse.
-Haven't tried webcam yet.

I think thats all for now. I may update this thread as some changes appear.

---

### Post by sniper0269 on 2009-01-12
I have a the same laptop. I did a clean install of Ubuntu 8.10. My touchpad worked. So I would suggest checking your bios to see if it got turned off. My wireless works however it is using the ath9k driver. The driver seems slow. I am looking into that issue now. I didn't need to use the beta driver, I used the driver the ubuntu suggested when it tested my hardware. I havn't tried the webcam or the bluetooth yet. I will let you know how that works. I do know that I downloaded and compiled the newest alsa and it didn't do me any good as far as headsets when. I don't have the touch keys working yet either. I will keep you posted on what I get to work and how I did it.

---

### Post by sniper0269 on 2009-01-23
> **sniper0269 said:**
> I have a the same laptop. I did a clean install of Ubuntu 8.10. My touchpad worked. So I would suggest checking your bios to see if it got turned off. My wireless works however it is using the ath9k driver. The driver seems slow. I am looking into that issue now. I didn't need to use the beta driver, I used the driver the ubuntu suggested when it tested my hardware. I havn't tried the webcam or the bluetooth yet. I will let you know how that works. I do know that I downloaded and compiled the newest alsa and it didn't do me any good as far as headsets when. I don't have the touch keys working yet either. I will keep you posted on what I get to work and how I did it.

Ok, So I just installed Cheese. My webcam works just fine. Cheese is a linux answer to photo booth for apples. I still can't seem to get my hot keys to work. I am trying to play with that now. My headphone jack is playing sound it's just not disabling my main speakers.

---

### Post by Ryuki_NdranC on 2009-01-25
Well i got a similar laptop (Qosmio x305-q705) and since this is the only thread that seems to be talking about x305 im gonna post here ;)

Well when i installed "everything" worked out of the box(i'll elaborate on this later). I had to update my ubuntu before been able to install the nvidia propietary drivers.

So far i have found a couple things that doesn't work:

-The exterior butons (you know the red touch sensitive butons above the keyboard) apparently only the play, stop, fwr, bwr butons works thats to gnome. I haven't found any thread related to this (i dont even know how those butons are called... :()

-The headphones problem, this seems to be a little common with some ppl. When you plug in your headphones even though they work fine, the speakers won't mute and it will keep sounding at the same time with your speakers. So far i got a couple clues about how to fix this, but im no so sure about them, im really new to the linux world and since i cant find updated material especifically refering to my laptop model i still haven't done a thing. I saw something about installing ALSA drivers (updated ones) because the ones in the repos are outdated, but i found this a little bit confusing since apparently when the system updates (and this installation was outside the repos) sometimes this may cause bugs and complete removal of the updated drivers.

-Aparantly the bluetooh isn't working either. I haven't check this very well, but when i try to use gnomes default bluetooh tranferfile it seems not to be able to show my phone (it works under vista), so idk yet.

-My media card reader doesnt seem to be working either. I tried to plug in a SD memory and nothing happened (i thing ubuntu should auto mount it, but i could be wrong)


So far this is it. I haven't tested if the subwoofer works ok with ubuntu and i havent tested the webcam. To be honest this laptop seems wierd. Like for example if i press the " buton it will only show the " character after i press space of another character like it was some sort of accent. I also found that my compiz is performing rather... slow compared with the way windows games show. When i use stuff like transparent cube the cube moves at (what i think is) 15 fps or less. That seems to suck big time.

I wish i could fix this ishues because no matter how much i love ubuntu and i hate that ugly vista, if my video card/bluetooh/mediareader perfomes badly ill have to switch back.

I propose to make this thread (or maybe a new one) dedicated to our findings, since it seems rather hard to find something related with x305 and linux. Ill not give up yet, and if you think you could point me out to the howto you used to install the alsa drivers that would be great.

Thanks :)

---

### Post by Ryuki_NdranC on 2009-01-25
Ok i got an update on my Headphone Jack problem.

I upgraded to ALSA 1.0.19 with an script shown in this thread

and after testing i notice that

-my headphone jack now mutes my speakers correctly

-my external volume control stoped working (it shows the animation of volume up/down put it doesnt do anithing)

-my subwoofer is definetively not working and neather my secon par of speakers (the ones near the screen) it's only working the ones near the touchpad.

-My volume seems unbalanced... what i mean is if i manually use the mouse to go up my volume, when the bar is halfway it sounds wayyy too low compared with windows version... for example

- ====#========= + Almost cant hear a thing

- ========#===== + Really low sound although better

- ===========#== + All of the suden BANG! its starts to sound ok

- =============# + OK sound (im aware that this may be cause by the subwoofer and other set of speakers not working... but i dont think so)

Im really getting disapointed of this... I really hate vista with my soul... But im not gonna nerf my laptop just because of it.

I guess i feel kinda depressed by the poor info i can find related to this. With my old HP laptop was soooo much easy to install and fix all the problems. Idk if its because this model is unpopular with linux or just too new.

Plz anybody? thx

---

