---
title: "Battery life with Hardy"
date: 2008-04-27
forum: Hardware
---

### Post by kikapu on 2008-04-27
Hi,

my T61 was giving me more than 3 hours of battery life when running on Vista Business with WiFi on.
In Ubuntu 8.04 i can see that i can hardly get 2 hours and 30 minutes...:confused:

I already have laptop-mode-tools installed (came installed), do i need to make something more to achieve better battery life or that's it ?

---

### Post by PsychedelicReaction on 2008-04-27
i'm very concerned too about my battery, about 2 hours less on ubuntu than vista with a nine cell battery. the only thing i can tell you is to install powertop and visit [http://www.lesswatts.org/](http://www.lesswatts.org/)

---

### Post by acron1 on 2008-04-27
I am also interested in this. Powertop shows 14.2-17.3 watts during normal use (web surfing and office use Wi-Fi on) which is good for ~4 hours for my setup.

---

### Post by maphilli14 on 2008-04-27
> **acron1 said:**
> I am also interested in this. Powertop shows 14.2-17.3 watts during normal use (web surfing and office use Wi-Fi on) which is good for ~4 hours for my setup.

I've managed to squeeze a bit more from my T60p by installing kpowersave and setting the CPU freq policy to powersave.  You may need to change some bios settings to allow user settings on that.  Oh, BTW, much cooler now too!  :)

Mike

---

### Post by kikapu on 2008-04-27
But, as i read, laptop-mode-tools whould take care of this stuff (reducing processor speed when on battery etc etc), don't they ??

---

### Post by acron1 on 2008-04-27
> **maphilli14 said:**
> I've managed to squeeze a bit more from my T60p by installing kpowersave and setting the CPU freq policy to powersave.  You may need to change some bios settings to allow user settings on that.  Oh, BTW, much cooler now too!  :)

Mike

That sounds good but which settings in the bios did you change?
BTW what is your watt ratting and which CPU/GPU do you have?
Thanks

---

### Post by kikapu on 2008-04-27
> **maphilli14 said:**
> I've managed to squeeze a bit more from my T60p by installing kpowersave and setting the CPU freq policy to powersave.  You may need to change some bios settings to allow user settings on that.  Oh, BTW, much cooler now too!  :)

Mike

Hmmm...i run kpowersave now. On "powersave" mode, at what exactly speed the processor is running ? And can we adjust the setting that when we are on A/C then the processor runs fuul speed and when on battery at "powersave" mode ? Is this feasible ?

---

### Post by CREEPING DEATH on 2008-04-27
Wow, the Latitude C610 I had lasted nearly twice as long on 6.06 that W2K!  I would get 2-2.5 hours on W2K and 5-6 hours on Dapper.  I guess things have changed!

CD

---

### Post by maphilli14 on 2008-04-28
> **kikapu said:**
> Hmmm...i run kpowersave now. On "powersave" mode, at what exactly speed the processor is running ? And can we adjust the setting that when we are on A/C then the processor runs fuul speed and when on battery at "powersave" mode ? Is this feasible ?

In the BIOS there are settings for power.  Under settings, power I believe.  Verify that all settings are set as automatic or user mode.  If they specify a particular mode, then you cannot manipulate them in linux.
I use "CPU Frequency Scaling Monitor 2.22.1" that is added via the panel in a gnome desktop.  Monitoring both of my Intel Centrino duo core's I see that in power saving mode, I can get 1.0GHz of the max 2.17GHz.  Stick it there via the powersaving mode in kpowersave, but don't use dynamic as that can scale the cpu back to max and kill the battery.

Granted I don't get the 4-5 hours 'advertised' under WinXP on this config, but I'm trying not to use MS :p, but in Hardy, I can get ~2-2.5 hours on a single battery charge pretty easily.

Mike

---

### Post by lamborghiniwang on 2008-04-30
I am also seeing shorter battery life under Hardy than Windows XP on my 14" Thinkpad T61p with a 6-cell battery. I get about 3-3.5hrs under Windows, but only 2hrs 15minutes in Hardy.
  I've enabled the laptop-mode, made some powersaving changes under powertop's suggestion, but still Windows beats Hardy on battery life by almost an hour.

---

### Post by kikapu on 2008-04-30
> **lamborghiniwang said:**
> I am also seeing shorter battery life under Hardy than Windows XP on my 14" Thinkpad T61p with a 6-cell battery. I get about 3-3.5hrs under Windows, but only 2hrs 15minutes in Hardy.
  I've enabled the laptop-mode, made some powersaving changes under powertop's suggestion, but still Windows beats Hardy on battery life by almost an hour.

Hi, i installed kpower tool and  thus beeing able to switch the processor to a very lower state when on battery. I have yet to measure it but i can see that both cores runs at 800 MHz when on thos mode. SO i believe i will have better times.

What is the "laptop-mode" that you refer ? Is is a setting that i can also adjust ?

---

### Post by lamborghiniwang on 2008-05-01
> **kikapu said:**
> Hi, i installed kpower tool and  thus beeing able to switch the processor to a very lower state when on battery. I have yet to measure it but i can see that both cores runs at 800 MHz when on thos mode. SO i believe i will have better times.

What is the "laptop-mode" that you refer ? Is is a setting that i can also adjust ?

To enable laptop-mode, all you have to do is type the command "laptop_mode" in terminal.
I am using the "CPU frequency scaling monitor" applet to control the CPU frequency when on battery, and I think it does the same job as kpower tool (I can set CPU to run at 800Mhz fixed with this applet), but the battery life is still not as good as it is under Windows XP. I'll try kpower to see if it helps.

---

### Post by Steve- on 2008-05-01
I have a Dell Inspiron 1501 laptop, running an AMD Turion 64 X2 TL50.

My old setup:
[LIST]
[*]Ubuntu 7.10 (upgraded from 7.04)
[*]i386 version
[*]60GB hard drive
[*]Up to **5 hours** battery life
[/LIST]

My new setup:
[LIST]
[*]Ubuntu 8.04 (fresh install)
[*]amd64 version
[*]160GB hard drive
[*]**2 hours** of battery life
[/LIST]

Everything else on the chassis is the same.

Which of the three things have dented my battery life so much? Clearly I need a reinstall of something, but do I need to go back to my old HDD? 2 hours is simply useless, it mas aswell be a desktop.

I have *laptop-mode-tools* installed.

Thanks


Edit: Other changes that might, but probably aren't relevant, are my partition structure. Rather than a single 30-40GB parition for my install before, I now have:
4 GB for swap
40 ext3 for /
40 ext3 for /home
Could having too much swap space kill my battery? I have 2 gigs of RAM.

---

### Post by kikapu on 2008-05-01
> **Steve- said:**
> I have a Dell Inspiron 1501 laptop, running an AMD Turion 64 X2 TL50.

My old setup:
[LIST]
[*]Ubuntu 7.10 (upgraded from 7.04)
[*]i386 version
[*]60GB hard drive
[*]Up to **5 hours** battery life
[/LIST]

My new setup:
[LIST]
[*]Ubuntu 8.04 (fresh install)
[*]amd64 version
[*]160GB hard drive
[*]**2 hours** of battery life
[/LIST]

Everything else on the chassis is the same.

Which of the three things have dented my battery life so much? Clearly I need a reinstall of something, but do I need to go back to my old HDD? 2 hours is simply useless, it mas aswell be a desktop.

I have *laptop-mode-tools* installed.

Thanks


Edit: Other changes that might, but probably aren't relevant, are my partition structure. Rather than a single 30-40GB parition for my install before, I now have:
4 GB for swap
40 ext3 for /
40 ext3 for /home
Could having too much swap space kill my battery? I have 2 gigs of RAM.

You are not the only one on this...I had 3-3.5 hours on Vista and now on Ubuntu (8.04) less than 2.5.
I also have laptop-mode-tools installed (by Ubuntu installation) and i also think that with this battery life, no serious work can be done away from AC

---

