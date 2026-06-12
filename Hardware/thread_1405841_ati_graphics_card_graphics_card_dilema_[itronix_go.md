---
title: "ati graphics card graphics card dilema [itronix gobook ix260+]"
date: 2010-02-13
forum: Hardware
---

### Post by Gigastorm123 on 2010-02-13
hello, i recently purchased an itronix gobook ix260+ [high spec ruggedized military laptop] off ebay that came preloaded with windows xp, and i more quickly than should've deleted the hard drive with dban out of contempt for windows, so i put my ubuntu disc in, semed fine at first but then the screen got all graphics garbled and patches of black on the screen and would then becone unresponsive regardless what i did. so i put fedora on there, it worked partialy well but still had many graphical flaws in the test part of it. i then installed it and turned it back on, same reaction as with ubuntu, deformed pixeles and black screen. i then wiped the hard drive again and started over, i tryed ubuntu 9.10 thinking it was a hardware issue and maybe id have etter suport with a new distro, still same reaction. so i too it to the guy at geeksquad. he fiddeled around and explained a few things and said it was the graphics card chipset, [ATI radeon rv250 (mobility fireGL 9000)]. he installed ubuntu in text mode, it installed, but upon boot up it had the same graphical glitching and unusability, he hen went into single user mode and did some commands and found out what exactly the card was, and then did something else to try and get the thing working, but he came to a splash screen and it froze. the store was then closed and he said i could bring it back but told me to muck around with it first.


so here i am with an installed linux operating system and no way to veiw my computer, so i ask you now the question...

is there a driver for this specific chipset for my specific rugged notebook, and if so, may i also have some directions on how to install in single user mode where i cannot use any graphical interface?

please answer, i really need a working laptop, and id prefer not to shell out 30 bucks to have something done that i want to do on my own but just dont know how.

so thankyou in advance,

-Giga-

---

### Post by waynefoutz on 2010-02-13
[http://support.amd.com/us/kbarticles/Pages/737-28041SupportforATIMobility.aspx]("http://support.amd.com/us/kbarticles/Pages/737-28041SupportforATIMobility.aspx")

That's what I get when I go to AMD's site to look for the proprietary linux driver for the Mobility FireGl. If the open source drivers aren't working, I'm afraid you are most likely stuck with Microsoft on that machine.  ATI's linux support really sucks. My stupid ATI card works, but it's crippled, so I have to keep a dual boot of Windows if I want to do any gaming.

I did a bit of reading, it seems that the touchscreen is a problem.

---

### Post by Gigastorm123 on 2010-02-13
yeah i read quite a bit before hand and saw other people sucsessfuly install ubuntu on this laptop, but i didnt read any stories like this on google, i wonder if the graphics card could be swapped...

i just hope the guy at geek squad might be able to do something, but perhaps not if theres no driver suport ~bleh~

---

### Post by Gigastorm123 on 2010-02-13
nope, no swapable graphics card, anyone else with any links, or someone's succsess story with my model?

---

### Post by Gigastorm123 on 2010-02-19
alright, i did a bit of research, and there is an opensource x.org driver for my computer, and the default flgrx driver for the video card in my laptop is not supported. i know its relatively easy to install the open-source driver through synaptics package manager, but again i have no working video/graphics card, so i cant even access that, all i have is a computer that the best it can do is go into a maintenance shell mode when i press escape at boot.

i guess I'm wondering i its possible to:

1. connect to the internet in maintenance mode..

and

2. download/install the appropriate driver through maintenance mode

if anyone knows how to do this [if its a possible option] could they please post some command lines on how to do this?

also i think this would happen with any PC that had an unsupported driver in ubuntu that needed installing [glitchy/black screen and whatnot] so if anyone who has a similar situation with another computer model, could they please tell me their story? whether it was solved or not

thank you very much

Giga

---

### Post by Gigastorm123 on 2010-02-19
here is some info on the open source driver for my model i found btw:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

i just don't know how to get it on my PC in maintenance mode

---

### Post by gabriel.bato on 2010-05-13
hello, 
I have the same laptop, and for the moment I use vesa mode, I am not a gamer, so it's ok for me, but If you really need the accel driver I could have a look...

my "basic" /etc/X11/xorg.conf 
(you should be able to edit it with nano in console mode (CTRL+ALT+F1) )

```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection


```

---

