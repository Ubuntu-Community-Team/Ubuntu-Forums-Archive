---
title: "Hardy Heating Issues: what could it be related to?"
date: 2008-05-26
forum: Hardware
---

### Post by ferdinando_villa on 2008-05-26
Hi all,
After installing Hardy, i was having problems with video playback (video was often laggy and choppy). At first i thought it was an issue with Compiz or the configuration of my video card, so i disabled compiz, donwloaded and configured the newest ATI drivers, and well, it seemed to work, but after 20 minutes or so of video playback, problem returns.

But it wasn't until i've installed a temperature monitor on my gnome panel that I've realized what was going on - after 20 minutes of video playback, my laptop temperature would rise to 80 degrees celsius, and then everything turned slow and unresponsive, until i quit VLC and waited a couple of minutes... this happens regardless of my CPU frequency scaling, even if i reduced it to 800Mhz (i have 2.2Ghz). I hear the fans blowing when that happens, but not enough to stop the temperature from going up to 80 celsius.

Now, i am a newbie here and i have no clue what could be related to this problem - is it my video card configuration? 

If anyone has any suggestions, I would really, really appreciate it - it really sucks not to be able to watch any videos anymore on my computer!

Thank you all!

---

### Post by ferdinando_villa on 2008-05-26
And i've also just noticed... it happens when i play music for more than 20 minutes also. After 15 minutes playing MP3s in Amarok, temperature is now 75 and rising...

---

### Post by RSingh on 2008-05-26
well same here, it seems somehow the fans in my laptop seem to be going of the scale. I have never heard the fan in my  machine but after some minutes of video playback or music playback, the fan is going overdrive. Whats even strange is that somehow, the CPU usage graphs don't register any such sort of spike....


Any Ideas?????

---

### Post by ferdinando_villa on 2008-05-26
I've just realized something odd - all the files in my /proc/acpi/thermal_zone/THRM are empty! cooling_mode, trip_points, all of them do not contain anything, so I am afraid my cooling system is not configured correctly... does anyone know how do i set them?

---

### Post by RSingh on 2008-05-27
Just checked my acpi info. Everthing seems ok. It seems I was freaking out for nothing.

CPU Idles at 40 C on mine.

It seems my laptop's fan was running normally. The system in my laptop is that when the temperature goes above 60 C, the fan kicked in and cooled it below 40 C.

---

### Post by pbhill on 2008-06-01
> **ferdinando_villa said:**
> I've just realized something odd - all the files in my /proc/acpi/thermal_zone/THRM are empty! cooling_mode, trip_points, all of them do not contain anything, so I am afraid my cooling system is not configured correctly... does anyone know how do i set them?

I'm having similar fan/cooling trouble on my Acer 5670 running Gutsy. After reading this post, I checked my /proc/acpi/thermal_zone/THRM files, and they too are empty... is this the problem? Can anyone out there with more knowledge than I comment on this? Thanks in advance!

---

