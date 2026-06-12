---
title: "Ubuntu 12.10 x32 + NVIDIA drivers"
date: 2012-11-22
forum: Hardware
---

### Post by forums4me on 2012-11-22
[FONT=Liberation Mono, monospace][SIZE=2]After installing Ubuntu 12.10 x32 as a second OS alongside Windows 7 x64, everything worked fine... until my attempt to update my NVIDIA drivers.[/SIZE][/FONT]
  

  [FONT=Liberation Mono, monospace][SIZE=2]Note that everything worked fine, with no lag or resolution issues.[/SIZE][/FONT]
  [FONT=Liberation Mono, monospace][SIZE=2]I decided to update my drivers after checking Software Sources > Additional Drivers and saw that I had no proprietary drivers in use.[/SIZE][/FONT]
  [FONT=Liberation Mono, monospace][SIZE=2]Similarly, under System Settings > Details > Graphics I saw that my driver was labelled as “Unknown” (and “Experience” as “Standard”).[/SIZE][/FONT]
  

  [FONT=Liberation Mono, monospace][SIZE=2]After a quick search I found this: [http://techhamlet.com/2012/11/install-nvidia-drivers-in-ubuntu-12-10/](http://techhamlet.com/2012/11/install-nvidia-drivers-in-ubuntu-12-10/) and followed the steps.[/SIZE][/FONT]


 [FONT=Liberation Mono, monospace][SIZE=2]First, I entered the following three commands in the terminal:[/SIZE][/FONT]
> 
 [FONT=Liberation Mono, monospace][SIZE=2]sudo apt-get install linux-source
sudo apt-get install linux-headers-generic
sudo apt-get install nvidia-current-updates[/SIZE][/FONT] [FONT=Liberation Mono, monospace][SIZE=2]...I rebooted, logged-in and Unity didn't appear, just my wallpaper with the sole ability to use the right-click context menu.[/SIZE][/FONT]
 

 [FONT=Liberation Mono, monospace][SIZE=2]Here is what I did in order to solve my problem:[/SIZE][/FONT]
> 
 [FONT=Liberation Mono, monospace][SIZE=2]sudo apt-get purge nvidia-current
sudo apt-get purge nvidia-current-updates
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get dist-upgrade[/SIZE][/FONT] [FONT=Liberation Mono, monospace][SIZE=2]... I deliberately ignored the last suggested command (sudo apt-get install nvidia-current)[/SIZE][/FONT]
 

 [FONT=Liberation Mono, monospace][SIZE=2]It worked.[/SIZE][/FONT]
 

 [FONT=Liberation Mono, monospace][SIZE=2]Problem solved, cool, now could anyone tell me what happened?[/SIZE][/FONT]
 

 [FONT=Liberation Mono, monospace][SIZE=2]How come my driver is unknown yet works perfectly well?[/SIZE][/FONT]

---

### Post by forums4me on 2012-12-06
[FONT=Liberation Mono, monospace][SIZE=2][SIZE=2]Ok, after removing dconf to replace it with UnSettings, the above problem reoccurred.

This time, I couldn't solve the problem using the above steps.

If anyone could actually guide [SIZE=2]me towards an explanation of what *seems* to be an enormous [SIZE=2]Ubuntu/[SIZE=2]Nvidia driver[/SIZE] clusterfuck (or of my own doing)[SIZE=2] [/SIZE]other than [this video]("https://www.youtube.com/watch?v=iYWzMvlj2RQ")[SIZE=2]...[SIZE=2] [/SIZE]that'll be greatly [SIZE=2]appreciated.

[SIZE=2]Than[SIZE=2]k you[SIZE=2] :)[/SIZE][/SIZE][/SIZE]
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT]

---

### Post by sabrefresco on 2012-12-06
I own a Samsung NP700Z5C-S04US and all was well when I was using Windows 7 and 8. I had epic battery life and awesome GPU performance and then I planned to switch to Ubuntu because I always loved it. Unfortunately, NVIDIA Optimus is only supported on Windows at the moment and NVIDIA has no comment on supporting other OSes like Linux in the near future([or do they?]("http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY")).
 
So there is no support for NVIDIA GPUs which use the Optimus feature and [I believe in your case the Intel GPU was working but NVIDIA GPU was not although the NVIDIA GPU was not properly switched off]("http://en.wikipedia.org/wiki/Nvidia_Optimus#Unix_Support") (You will have high temps and poor battery life when running in this state). To fix this, you have to install [Bumblebee]("https://github.com/Bumblebee-Project/Bumblebee/wiki/FAQ"), which helps offloading the work and switching off your NVIDIA GPU when not required(using bbswitch).
 
My laptop has a GT640M which, as far as I understand, is not fully supported. Fortunately, it seems that the GT630M is supported since [its not really a Kepler GPU]("http://www.notebookcheck.net/NVIDIA-GeForce-GT-630M.63761.0.html"), so you might get be able to get Bumblebee to work.
 
Installation instructions are [here]("http://www.bumblebee-project.org/install.html#Ubuntu"). Check their [wiki]("https://github.com/Bumblebee-Project/Bumblebee/wiki") for more information and also things that are [working]("http://nouveau.freedesktop.org/wiki/FeatureMatrix"). 
 
I tried it on my Ubuntu 12.04 using Wubi and it did not work. But now I have Win8 and Wubi is broken so I cannot really retry or help you with any further instructions.

---

### Post by Axxon95 on 2012-12-07
The graphics driver showing up "Unknown" is because Ubuntu doesn't come by default with the mesa-utils package. Once you install it Ubuntu will correctly detect it.

```
sudo apt-get install mesa-utils
```
And a few other testers:
```

glxinfo | grep render
glxinfo | grep OpenGL
glxgears

```

A quick YouTube video I uploaded regarding this: [http://www.youtube.com/watch?v=oxD6S8P1P3A](http://www.youtube.com/watch?v=oxD6S8P1P3A)

Hope this helps!

---

### Post by forums4me on 2012-12-07
Thank you for your feedback guys :)

Interestingly, Linux Mint 14 recognised the Intel graphic card and "Intel (R) Ivybridge Mobile" can be found under Details > Driver.

So I guess I should get that following Axxon95's procedure under Ubuntu though I'm hesitating to re-load it.

Regardless, again, thank you for your help.

---

### Post by Axxon95 on 2012-12-08
> **forums4me said:**
> Thank you for your feedback guys :)

Interestingly, Linux Mint 14 recognised the Intel graphic card and "Intel (R) Ivybridge Mobile" can be found under Details > Driver.

So I guess I should get that following Axxon95's procedure under Ubuntu though I'm hesitating to re-load it.

Regardless, again, thank you for your help.


Linux Mint by default has mesa-utils.
And yes if the drivers are installed and you have that package it will show.

---

### Post by forums4me on 2012-12-08
Thank you for your time.

I'll give Ubuntu another shot.

I hope it'll work; I really like this OS.

---

### Post by forums4me on 2012-12-08
Yep, it does work, thank you.

---

### Post by Axxon95 on 2012-12-09
Glad I could help.

---

