---
title: "NVIDIA: Movie playback leading to higher and higher CPU usage"
date: 2013-02-11
forum: Hardware
---

### Post by mupi_foerster on 2013-02-11
**Problem description:**

I use a four year old laptop as a media center to playback movies on my TV Screen. It shows fine at the beginning, but after about 20 or 30 minutes the movie starts to stutter more and more. 
I usually use the standard movie player (totem) or VLC for playback. Both show the same symptoms. When I check with top, the movie starts with VLC or totem showing around 25% CPU usage, after 20 Minutes it suddenly surges to 80%, then later to around 120% (using the second CPU), and the stuttering begins. Killing the movie player and restarting the movie does not help. I have to reboot to get again the normal performance.

As the movie plays all right for about 20 minutes, I think the hardware is generally powerful enough to do the job. I read a few threads about similar problems (but there, Xorg eats the CPU) for example here: [http://www.dedoimedo.com/computers/ubuntu-pangolin-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-pangolin-nvidia.html)  , but those vblank etc. settings did not solve the problem.

Two things I have in mind that could cause this, but I'm not wise enough to narrow them down:
- thermal problem, leading to reduced speed at the graphic card, in turn increasing CPU load
- Software problem, in analogy to a memory leak a "CPU-leak" ?

**Software:**

[LIST]
[*]Ubuntu Precise 64 bit
[*]NVIDIA post-release updates driver (I changed to that one to see if it helps, but did not change anything)
[*]VLC or totem for movie playback
[*]using Xinerama to extend to both screens - I could not get the external screen working via HDMI without Xinerama.
[/LIST]
[B]

Hardware:[/B]
Lenovo N500 with NVIDIA GeForce 9300M GS , using an external SAMSUNG TV via HDMI

Any help, infos, input or tests I could do are appreciated

---

### Post by Dedoimedo on 2013-02-12
When the stuttering begins, anything interesting in /var/log/messages or dmesg? Did you consider polling memory/cpu/disk usage every 30 sec to see what gives? Can you monitor the card temp when playing?

Dedoimedo

---

### Post by SeijiSensei on 2013-02-12
Are the players configured to use "VDPAU?"  

You can try installing smplayer from the repositories and go to Options > Preferences > Video and choose "vdpau" as the output driver.  Does that help?

---

### Post by mupi_foerster on 2013-02-12
Thanks Dedoimedo, I will try that - just, I'm not a real linux crack.
 I know how to use top or sysmon to check on CPU and Memory consumption. Disk usage I did not consider important, but is a good hint.
I have no clue however how I could monitor the card temperature - any idea of the command necessary to get to that info?

---

### Post by mupi_foerster on 2013-02-12
Thanks also, [SeijiSensei]("http://ubuntuforums.org/member.php?u=698195") 

I will try to download it and test, but I hope it is not too big, as internet where I live is not exactly speedy. I will come back with more info then.

---

### Post by Dedoimedo on 2013-02-13
This should work:
nvidia-settings -q gpucoretemp

Dedoimedo

---

### Post by mupi_foerster on 2013-02-14
I watched a movie yesterday and managed now to analyze in more depth:
During the movie playback:

[LIST]
[*]CPU load starts at around 25 % for totem, the rest of programs together <10%
[*]GPU temperature starts at about 70 C and rises till about 90 C in 10 minutes, were it stabilizes
[*] I do not know if it stabilizes because of thermal equilibrium or because it starts to offload work to the CPU
[*]CPU load increases at this point to around 80%,  movie still runs fine
[*]but then after around 20 minutes, CPU-load goes through the roof: I saw totem at 110% and pulseaudio at 80%. Of course the movie is not enjoyable anymore at this point and the machine is very sluggish.
[*]dmesg (see attachment) shows throttling back of CPU because of overheat condition
[*]I put a pack of frozen peas :D under the laptop which reduced CPU-load of totem to a (still high) 80% and thus was able to watch the movie till the end.
[/LIST]


**Conclusion**: It looks like this is not a software problem after all. I guess the CPU cycles needed to playback the movie do not change at all, just the CPU gets throttled more and more.


Now I will have to check the cooling of my laptop... where I live, humidity is often as low as 5%, and I guess this makes it harder to transport heat by air. I will see if there is any dust accumulated inside.

Any comments to my dmesg? There are a few things I don't understand there: hpet increased? Where can I find that machine error log?

And one last thing: Is there a command that shows CPU temperature similar to the one above for the GPU?


Thanks for all the answers

---

### Post by typhoon_tip on 2013-02-14
If it's a laptop, that temperature is off the roof !! You definitely need to clean the fan and heat sink. It is usually shared by video card and CPU, so the temperature are basically the same after they reach such level (maybe CPU core is even higher !). I guess that CPU goes to 120+ % because frequency is scaled down by the BIOS to avoid frying it, which is a good thing...

---

### Post by papibe on 2013-02-14
Hi mupi_foerster.

In order to use video hardware acceleration on VLC, you need to install this library:
```
sudo apt-get install vdpau-va-driver
```
And then enable hardware acceleration on the settings.

Could you post the result of this command?
```
vainfo
```
(install it if you don't have it already).

Regards.

---

### Post by mupi_foerster on 2013-02-16
I cleaned the fan, but there was not much dust... of course, most technical specs say humidity should be somewhere between 10% and 90%, so I fear I can't blame the manufacturer. I put some duplo-bricks from my kids underneath now, hope they help to get more air into the system.

Thanks for the further remarks, I installed the vdpau -driver, but can't find any settings for it to enable hardware acceleration. What is the command needed?

vainfo returns this:

```

libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/nvidia_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems VDPAU backend for VA-API - 0.7.3
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :    VAEntrypointVLD
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileVC1Simple              :    VAEntrypointVLD
      VAProfileVC1Main                :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD


```

---

### Post by papibe on 2013-02-16
That looks good. VAAPI is installed and available.

To enable GPU acceleration on VLC, open it and then go to:
```
Tools -> Preferences -> Input and Codecs -> Use GPU acceleration
```
Let us know how it goes.
Regards.

---

### Post by mupi_foerster on 2013-02-16
Thanks papibe,
I at first thought you referred to a setting configuring the vdpau-driver, but later reread and understood you meant a VLC-setting.
I ticked that setting and it seems to be as it should, no stuttering etc., so that is great! Thanks a lot for all the help.

One last question before I mark this as solved, can I also enable hardware acceleration for the standard movie player? I prefer its UI, VLC always annoys me with a clumsy full screen behavior.

---

### Post by papibe on 2013-02-16
Since vainfo is showing all is good, and the 'Movie Player' supports VAAPI, you should be able to play HD videos on it now.

Regards.

---

