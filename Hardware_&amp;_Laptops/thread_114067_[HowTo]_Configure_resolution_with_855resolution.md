---
title: "[HowTo] Configure resolution with 855resolution"
date: 2006-01-07
forum: Hardware &amp; Laptops
---

### Post by Derek Djons on 2006-01-07
This is a general guideline and example on how to use 855resolution for notebooks meeting it's hardware requirments and resolution changing problems.

_1. Downloading / installing 855resolution_
The easiest thing to do is download 855resolution using Synaptic Package Manager. Use 'search' to find the application quickly. If you can't find it make sure you have added Ubuntu (binary) universe / multiverse in you repository.

_2. How does 855resolution work_
855resolution works by a CLI. It still hasn't got a GUI. Mabye that's an idea to develop for upcoming 6.04?! :)

We will only use two options from 855resolution. The first is '-l'. This option will display 855resolution all possible resolutions according you vbios. The other option we will use is mode 'X Y' About this later more.

_3. Reading out your vbios._
Okay. Now the application is installed and we know what options we have to be using let's get to work.

Open a terminal or shell and use the following command:
*sudo 855resolution -l*

If your graphical chipset (vbios) is being recognized a list with resolutions and names will appears similar like this:
> Chipset: 855GM (id=0x35808086)
VBIOS type: 1
VBIOS Version: 29

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1400x1050, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1400x1050, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1400x1050, 32 bits/pixel
Mode 7c : 1024x600, 8 bits/pixel
Mode 7d : 1024x600, 16 bits/pixel
Mode 7e : 1024x600, 32 bits/pixel
djons@voyager:~$ 855resolution --help
855resolution version 0.4, by Alain Poirier

I've read on this forum that there are also have been some incidents in which 855resolution wouldn't recognize the vbios. In that case the only thing to do is hang on and wait til a new (version of this) application. 

_4. Double-checking your modes_
As you see in the example above here there are three sections. All resolutions which are working on 8 bit, 16 bit and 32 bit. Already at this stage you have to be sure what you want. Not that it is system-crucial though.

The most imporant thing which is system-crucial is the resolution. I know from specs and other general information about LCD panels that my notebook doesn't supports a resolution higher as 1400x1050 @ 60Hz. But in the list above, 855resolution displays a lot of resolution which won't work and can even knock you out of X. So from this point... **know what you are doing!**

_5. Choosing / Configuring your desktop mode_
We're almost there. Here's where the other application options comes in. I will use my own situation for example.

As I said before my maximum resolution is 1400x1050. From the list I decided to work with 5c. The reason for the choice was:
* My notebook support 32-bit color depth.
* The default resolution mentioned at 5c was really something my notebook can't handle. I used the next command to change the resolution of 5c and at the same time select 5c to be my screen resolution:
*sudo 855resolution 5c 1400 1050*

If correctly entered the application will confirm your settings and you will be done configuring 855resolution.

_6. Applying your new resolution_
Use ctrl+alt+backspace to restrart your X server and wait for the login screen to re-appear. While and after login in... enjoy!

The readme of 855resolution mentioned that with every reboot the resolution has to be re-entered again. But enabling the 'use this resolution as default' option overrides 855resolution making it last permanent.

---

### Post by danbert on 2006-09-14
I did exactly as you described in the post, and 855resolution gives a message that says:

Chipset: Unknown (0x25908086)
VBIOS type: 2
VBIOS Version: 3412

** Patch mode 5c to resolution 1680x1050 complete

Yet, when I go look at the availible resolutions again, the resolution was not set.  I have not been able to get the 1680x1050 to stick, and thus be able to use it.

As far as system info, I have the Intel 955 graphics chipset, and a screen that is capable of 1680x1050.

Any help would be greatly appreciated.  Thanks

---

### Post by ampop on 2006-09-15
I had the same problem:
```
ampop@acer-laptop:~$ sudo 855resolution -l
855resolution version 0.4, by Alain Poirier

Chipset: Unknown (id=0x27a08086)
Unknow VBIOS structure
ampop@acer-laptop:~$

```
Thank you

---

### Post by ampop on 2006-09-15
> **ampop said:**
> I had the same problem:
```
ampop@acer-laptop:~$ sudo 855resolution -l
855resolution version 0.4, by Alain Poirier

Chipset: Unknown (id=0x27a08086)
Unknow VBIOS structure
ampop@acer-laptop:~$

```
Thank you
I solved my issue with this post: [http://ubuntuforums.org/showthread.php?p=1501028#post1501028](http://ubuntuforums.org/showthread.php?p=1501028#post1501028)

---

### Post by Wolfeman on 2007-04-13
THANK YOU SO MUCH!  I used 915resolution but the steps were the same (1280x800 resolution too).  I couldn't get my resolution correct on my Dell 700m :)

---

