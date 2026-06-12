---
title: "nVidia 5200 screen flicker"
date: 2010-02-01
forum: Hardware
---

### Post by max-power2717 on 2010-02-01
Hello Forum :)

I recently changed the graphics card in my Pentium 4 system running Ubuntu 8.04. The old card was ATI, and the new card is an AGP card with the nVidia 5200 GPU. I followed some [SIZE=2][COLOR=DeepSkyBlue]**[instructions]("http://ubuntuhowtos.com/howtos/replace_ati_with_nvidia")**[/COLOR][/SIZE] about how to install the nvidia drivers and I got everything working satisfactorially.

That was about 4-5 days ago, and a day later I noticed an issue that bugs me, and which I can't explain. The problem continues to crop up, so I want to get on top of it. Every now and then my screen will go blank (black) for approximately 1-2 seconds and returns to the desktop with everything looking fine. It's something like a flicker. When this happens, my LCD screen (BENQ 2000W) reports the port the signal is coming in on (DVI).

As I said, I have no idea what the cause for this is, and i've had difficulty in searching for solutions. I'm guessing that the nVidia drivers could be causing the flicker (maybe I don't have the best settings). Something else that occurs to me is that I also installed the game Sauerbraten the same day I installed the nVidia drivers. The game plays very well, and the flicker didn't start until the next day, but those are the only two things I can think of that might have lead to this. 

I can't seem to generate these flickers, they occur randomly (as far as I can tell). This has only been going on a few days, but it's most annoying. I'd like to figure out the problem. Has anyone experienced anything like this? Or, do you have a suggestion what might be the cause of the flicker?

I can provide xorg.conf, or any other files which might be important on request. Look forward to any suggestions. 

Thanks.

---

### Post by mudguts on 2010-02-01
are you running any special themes just out of curiosity?
I have a similar issue that happens on 9.04 when I run a custom theme BUT if I switch back to the basics then it disappears..

could also be compiz... you try turning it off?

---

### Post by PhilGil on 2010-02-01
I'm using an Nvidia FX5500 video card (similar to your card).  I was never able to get a DVI connection to function without flashing/flickering.  The problem was worse with desktop effects enabled.  I finally gave up and switched back to a VGA connection and all is well.

---

### Post by max-power2717 on 2010-02-02
Thanks for the pointers guys.

I will try them all of the proposals but it might take some time to rule any soln due to the nature of the problem so far. Also, I'd have to do some reading about what this "compiz" is, haven't heard of it before. Will keep the thread updated if I learn anything.

About themes... what constitutes a "special" theme? Since installation, I've only changed the background in gnome a few times as far as I can remember. I once tried out some of the enhanced graphics effects for windows, but I found those elastic windows very disconcerting, so I changed the settings back very quickly. 

Thanks again.

---

