---
title: "how to use nvidia GT 750M with 14.10"
date: 2015-01-01
forum: Hardware
---

### Post by Allen McBride on 2015-01-01
I've just installed Ubuntu on a new laptop, and I've been searching for information about using (potentially with automatic graphics switching) my nvidia geforce gt 750m card with Ubuntu 14.10. I have the impression that a lot has changed this year in terms of nvidia drivers and what they support, so I'm confused about which advice is up to date.

*[EDIT regarding below questions: I was able to get CUDA working, thanks to some advice I read somewhere to install nvidia-modprobe. So I can definitely use my GPU now. But if anyone cares to point me in the right direction regarding how Optimus, 14.10, Bumblebee, and the latest NVIDIA drivers relate to each other, I'd still appreciate it.]*

I switched to the propriety driver in Software & Updates -> Additional Drivers (ver. 331.133) and rebooted, and nothing seemed to go obviously wrong. But when I run "inxi -Gxx", I get:

Graphics:  Card-1: Intel Haswell-ULT Integrated Graphics Controller bus-ID: 00:02.0 chip-ID: 8086:0a16
           Card-2: NVIDIA GK107M [GeForce GT 750M] bus-ID: 04:00.0 chip-ID: 10de:0fe4
           Display Server: X.Org 1.16.0 drivers: intel (unloaded: fbdev,vesa) FAILED: nouveau
           Resolution: 1920x1080@60.0hz
           GLX Renderer: Mesa DRI Intel Haswell Mobile
           GLX Version: 1.4 (3.0 Mesa 10.3.0) Direct Rendering: No

...and from what I've read, this output might indicate that I don't have the card/drivers set up correctly. But I'm not sure whether:

   1) There is no such thing as automatic graphics switching for nvidia cards in Ubuntu yet, and therefore I need to install Bumblebee to actually use my card, or
   2) The late-2014 nvidia graphics drivers support Optimus, and (therefore?) I don't need Bumblebee, but something else isn't set up right (or maybe it is and I just don't know what I'm looking for).

Any advice for me? Feel free to just point me to some correct, up-to-date thing that I need to read (even Wikipedia's pages on this stuff look possibly dated.) My next step will be to try to get CUDA up and running (I'm a novice with GPGPU stuff but I'm trying to learn).

If it helps, I'm using a Dell Inspiron 17 7000-7737.

---

### Post by Allen McBride on 2015-01-02
I finally figured it out, mostly.  The answer seems to be that one no longer needs Bumblebee, because nvidia-settings can switch which card is in use. I didn't know about nvidia-settings.

---

### Post by introsiut on 2015-01-03
Hi Aleen, I am new to Ubuntu on MacBooks as well.

So the automatic switching between both cards works without any issues for you? Is there a way to force to use only Intel GPU?

---

### Post by Allen McBride on 2015-01-04
Hi introsiut! No, I don't think automatic switching is working for me, but I'm not sure. I think only manual switching is working. I switch between the two by running nvidia-settings, which launches a GUI where there's an option for switching under "PRIME profiles". Unfortunately, I have to log out and back in again to make it work (which is what the program prompts me to do). So yes, forcing only one GPU or the other seems to work fine and to be the only thing I can do. I'm still confused about whether this means that Optimus is supported or not, or what the deal is in general with automatic graphics switching. Also, I should clarify that I'm using a Dell Inspiron 7737 now, not a MacBook. (Coincidentially, I actually made the switch to Dell and Ubuntu because my MacBook Pro started kernel-panicking every time it tried to do an automatic switch to the dedicated GPU.) Good luck with your new Ubuntu install!

---

### Post by Bashing-om on 2015-01-04
Guys;

The better support for hybrid Intel/Nvidia is recognized as nvidia-prime.

purge all drivers and install nvidia-prime from the repository.

There is also a PPA that "might" give better results:
[http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html) <- quickly switch between Intel and Nvidia graphics cards.

My bit
[INDENT][INDENT][INDENT]to try and help
[/INDENT][/INDENT][/INDENT]

---

### Post by Allen McBride on 2015-01-12
Hi Bashing-om,

Sorry I didn't notice your post when you made it, but thank you. I poked around, and nvidia-prime seems to have been installed automatically along with nvidia-331 when I selected the nvidia proprietary driver in Software & Updates -> Additional Drivers.

---

### Post by subhranath on 2015-06-07
> **Allen McBride said:**
> I finally figured it out, mostly.  The answer seems to be that one no longer needs Bumblebee, because nvidia-settings can switch which card is in use. I didn't know about nvidia-settings.

I tried the new nvidia binary drivers from xedgers ppa but I don't see the gpu switcher or selector at nvidia-settings. Do we need to configure anything else to get to that section?

---

### Post by amias2 on 2015-10-25
i have a dell 7737 with the nvidia 750m , it works perfectly with nvidia-updates-346 on ubuntu 15.04 with nvidia-prime.
It just handles enabling and disabling as you need it, no need to tell it.
I haven't managed to get cuda working with it but steam works really well even at 4k resoutions via the hdmi.

---

### Post by amias2 on 2015-11-06
fwiw here is the inxi -Gxx output from a system where prime is working great (dell 7737) on 15.04

amias@rome:~$ inxi -Gxx
Graphics:  Card-1: Intel Haswell-ULT Integrated Graphics Controller
           bus-ID: 00:02.0 chip-ID: 8086:0a16
           Card-2: NVIDIA GK107M [GeForce GT 750M]
           bus-ID: 04:00.0 chip-ID: 10de:0fe4
           Display Server: X.Org 1.17.1 drivers: (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.0hz
           GLX Renderer: Mesa DRI Intel Haswell Mobile
           GLX Version: 3.0 Mesa 10.5.9 Direct Rendering: Yes

---

