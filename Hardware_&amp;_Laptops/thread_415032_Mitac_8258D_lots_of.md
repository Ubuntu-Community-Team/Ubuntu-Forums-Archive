---
title: "Mitac 8258D lots of"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by sbanjac on 2007-04-20
Yesterday I installed festy and i was pleased with the setup, it took me where litle to configure my system (when comparing with edgy). But I still have some problems so if anybody knows the solution, i would be greatful for sharing it with me... here are my problems: 

1. I have an Mitac Notebook 8258D and it is using hda-intel soundcard with the chip rt ac 883. It has only 2 standard analog conectors - line in and microfon. It also has a digital conection, but i cannot use it because my amplifier is prety old. In windows i could transform these inputs in to outputs and that way have 3d sound. Then I could with varios tplugins for winamp make winamp reproduce mp3 on all 6 channels. I connect my amplifier to the line in and than i can listen music only on the good speakers (the notebookspeakers are garbage for listening to music). In festy ( i installeed it today, but i had the same problem with edgy for months) when i run alsamixer i cant change channel number from 2 to anything else, as it is locked (perhaps i dont know how). In the volume control i have already activated volume control for surround, center, LFE, side but nothing happens. I have tryed to test the sound with speaker-test -c 5 and it gives me the following:
speaker-test 1.0.13

Das Wiedergabegerät ist default
Stream parameters are 48000Hz, S16_LE, 5 channels
Using 16 octaves of pink noise
Samplingrate auf 48000Hz gesetzt (gefordert waren 48000Hz)
Buffer size range from 2048 to 16384
Period size range from 1024 to 1024
Using max buffer size 16384
Periods = 4
was set period_size = 1024
was set buffer_size = 16384
 0 - Vorne Links
 1 - Vorne Rechts
 2 - Hinten Links
 3 - Hinten Rechts
 4 - Center
Time per period = 14,609831

This plays the noise on the notebook speakers but nothing comes out of the stereo speakers.
I would like to be able to mute the fron speakers and enable only my surround speakers. This way i could listen to music with me highq stereo speakers. Is it posible to automaticaly make the stereo mp3s play on all channels? This could also enable me to listen music via headphones. My notebook is great but some dumbass forget to make an headphone conector. Instead i have an SPDIF which i cant use for any kind of headphones....

2. My special function keys don't work (except for volume control)
My notebook has a couple of special keys:
wireless control (on/off  FN + F1)
brightness control (8 levels FN + F6  -  FN+F7)
hibernate / sleep (FN + F12) <- this one i dont need
turning the lcd off (FN + F5) 
and there is a functin key that can change the display modes on the fly. Like a profile changer, but that is not important and probably hard to fix.

3. After i go to shutdown or hibernate or sleep... everything goes fine, but the notebook doesn't power down on it self. I have to press the poweron key for 4 secs and this can be irritateing at night when you are ready to crush...

4. The brightness applet doesnt work. If i could get this to work, than i wouldnt need the function key function.

Any help would be welcome (regarding any of the problems listed above). If you need any information, i will reply as soon as posible.

---

### Post by cime on 2007-11-02
Have you recived any answer?
I looked everywhere for solutions, but I still can't fix problem no. 3 - the laptop won't power off whatever you do. If anyone found a solutions please post it here.

---

### Post by LamM on 2007-11-04
Hi! i have the same laptop and i have de same problem...

---

### Post by cime on 2007-11-05
And noone know the solution :/

---

### Post by luksmann on 2008-01-12
I also have the same laptop - bought it in German under a different name (took me about 2 hours of internet search to find out that the real name of the laptop was Mitac 8258D)

I have the same problems as you guys...
Laptop not powering  off, hotkeys not working.

Running Gutsy now but the problems still remain...
Still nobody out there who's got any ideas?

Greets, luksmann

---

### Post by LamM on 2008-02-19
Refloting......

---

### Post by pedali on 2008-03-08
Hi all!
Nothing new... :(
I have a mitac 8258D too and the same problem.

Someone else want's to join our "Club"? :)

 
Peter

---

### Post by sagra on 2008-04-08
Hello everybody! :)

I have bad news :(
I also have the same laptop of course under a different name. It took me lots of research
to find out the original name and to trace the problem. Both the shutdown problem and the
Fn keys malfunction are related to the acpi support. The manual of the laptop says that it is
fully acpi compliant up to version 3a BUT that is not the case when it comes to linux.
Unfortunatelly Mr Bill Gates has worked very hard to make this acpi version incompatible with the
linux kernel. However I am sure that the problem can be solved somehow as I have observed that sometimes but very rarely the system works out of the box without any special configuration.
When I notice that the Fn keys about the screen and wireless work, then I know that the system
will shutdown, I try it and.. voila!

So lets become more in order to get the attention until someone with technical experience helps us out.
People you are so welcome to join the list! :)

---

### Post by LamM on 2008-04-21
Hi!! I compiled the windows acpi but not fixed the trouble :S:S:S

---

### Post by ezTol on 2008-04-22
Same laptop (in Germany: Nexoc Osiris E611), same problem. Tried to fix acpi (now 4 Warnings instead of 26), but no success. I can manage to get different outputs of "dmesg", but I never got suspend or keys for screenbrightness working. Suspend2disk and resume work with tuxonice, but this also doesn't power off, I have to press power button for 4 Seconds.
Too bad, that no distro (only parsix does) ships tuxonice as default.

---

### Post by sagra on 2008-05-14
suspend to disk also works in opensuse 10.2 but I haven't search about the mechanism it is used there.

---

### Post by LamM on 2008-05-21
ey guys!! in Mandriva sometimes work the keys

---

### Post by Ichido on 2008-05-28
I have a Dell insprion 1525n with a 'Dark' screen.
The Laptop's manual states:
"To adjust the screen's brightness,press the <Fn> key and the <Up Arrow> or <Down Arrow> and That FIXED my problem:)
Good Luck!

---

### Post by FreewheelinFrank on 2008-07-17
> **pedali said:**
> Hi all!
Nothing new... :(
I have a mitac 8258D too and the same problem.

Someone else want's to join our "Club"? :)

 
Peter

I'll join, for the record. I've just worked out that my UK Evesham Voyager C530 is actually a rebranded Mitac 8258D.

It almost never fully shuts down.

---

