---
title: "Possible 8.10 Ibex Screen Resolution Fix?"
date: 2008-11-05
forum: General Help
---

### Post by Nylo on 2008-11-05
Has anyone tried this to correct their screen resolution issue?  It looks good but I'm a bit cautious these days.

[http://ubuntuforums.org/showpost.php?p=6086662&postcount=8](http://ubuntuforums.org/showpost.php?p=6086662&postcount=8)

---

### Post by phidia on 2008-11-05
What video card are you having problems with Nylo? I think the guide that bscbrit posted should work since the xorg in intrepid is the same as hardy's.

But if you want to provide more specifics on what you're seeing and your hardware I'm sure someone will try to help.

---

### Post by Nylo on 2008-11-05
> **phidia said:**
> What video card are you having problems with Nylo? I think the guide that bscbrit posted should work since the xorg in intrepid is the same as hardy's.

But if you want to provide more specifics on what you're seeing and your hardware I'm sure someone will try to help.

My card is Intel(R) 82815 in a Vaio R505JL/C.

There is no other choice other than 800x600 and 640x480 in Ibex screen resolution settings.  No drivers are reported.

#####################
       description: VGA compatible controller 
       product: 82815 Chipset Graphics Controller (CGC) 
       vendor: Intel Corporation 
       physical id: 2 
       bus info: pci@0000:00:02.0 
       version: 11 
       width: 32 bits 
       clock: 66MHz 
       capabilities: bus_master cap_list 
       configuration: latency=0 
######################

########################
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
###############################

Any help would be appreciated.

Sony Vaio (laptop) PCG-R505JL/C
10.4" screen, 60 re-fresh
Intel(R) 82815 graphics controller

---

### Post by Amerinidiot1231 on 2008-11-05
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1152x864"
    EndSubSection
EndSection
```

I would suggest trying to change the xorg.conf screen section to this, this is how I have fixed the issue in both hardy and ibex.  Simply change the mode to your desired screen resolution.

If it does not work and you get a blank screen, go into grub boot options and choose the recovery mode, and then the 'fix xorg server,' or the option is something in that range, and it will bring back the default configuration.

---

### Post by Nylo on 2008-11-06
> **Amerinidiot1231 said:**
> ```
Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1152x864"
    EndSubSection
EndSection
```

I would suggest trying to change the xorg.conf screen section to this, this is how I have fixed the issue in both hardy and ibex.  Simply change the mode to your desired screen resolution.

If it does not work and you get a blank screen, go into grub boot options and choose the recovery mode, and then the 'fix xorg server,' or the option is something in that range, and it will bring back the default configuration.

All this did was black out my screen.  Had to restore.

Any other ideas?

---

### Post by Amerinidiot1231 on 2008-11-06
do you have an nvidia graphics card?

---

### Post by wgrant on 2008-11-07
> **phidia said:**
> I think the guide that bscbrit posted should work since the xorg in intrepid is the same as hardy's.

Intrepid's xserver is very different from Hardy's. However, installing displayconfig-gtk from Hardy shouldn't cause too many more problems than it did originally in Hardy, but it's still not a good idea.

---

### Post by wgrant on 2008-11-07
Have you tried [the X resolution fixing documentation](https://wiki.ubuntu.com/X/Config/Resolution)?

---

### Post by Nylo on 2008-11-07
> **Amerinidiot1231 said:**
> do you have an nvidia graphics card?

Nope.  I have an Intel(r) 82815 card.

---

### Post by Nylo on 2008-11-11
> **wgrant said:**
> Have you tried [the X resolution fixing documentation](https://wiki.ubuntu.com/X/Config/Resolution)?

I went your link but I cant seem to get 1024x768 working.  

Below are my "xrandr" results as well as my tail of the tape.

#####################
**Lspci**

       description: VGA compatible controller 
       product: 82815 Chipset Graphics Controller (CGC) 
       vendor: Intel Corporation 
       physical id: 2 
       bus info: pci@0000:00:02.0 
       version: 11 
       width: 32 bits 
       clock: 66MHz 
       capabilities: bus_master cap_list 
       configuration: latency=0 
######################
**xrandr **

Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600 
default connected 800x600+0+0 0mm x 0mm 
   800x600        60.0*    56.0   
   640x480        60.0  
########################

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
###############################

Any help would be appreciated.

Sony Vaio (laptop) PCG-R505JL/C
10.4" screen, 60 re-fresh

---

### Post by denvergeek on 2008-11-20
Nylo,

I've been messing with the same issue on 8.10 for a week, finally fixed it.  I have a Sony Vaio PCG-R505JL, same display chipset.

On my install, it seems that the driver was not guessed correctly (should be "intel").  Even if you set this driver by hand, xorg still can't guess the resolution correctly.  

(edit) Also can't guess "HorizSync" and "VertRefresh" options correctly, which is why you get the black border in the first place.

Here's my working xorg.conf, which gives me a good 1024x768 display, without the cursed "black border":

```

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "intel"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync 31.5-48.5
        VertRefresh 40-70
        Option "dpms"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth 16
        Option "Accel"
        SubSection "Display"
                Depth 16
                Modes "1024x768"
        EndSubSection
        SubSection "Display"
                Depth 24
                Modes "1024x768"
        EndSubSection
EndSection

```

Let me know if this works!

--Jake

---

### Post by mgolden on 2008-12-02
This works for me on my (very old) Sony Vaio PCG-FC370P.  Thanks!

---

### Post by craig.o on 2008-12-02
> **denvergeek said:**
> 
Let me know if this works!

--Jake

Jake;

From one GWOH* to another, thank you! I've a Sony VAIO R505-JLK and the X (mis-) configurations were maddening.  Your xorg.conf snippet worked the charm on my Ubuntu 8.04 derivative (gOS v3.0).

much appreciated,
-Craig

*[Geek with Older Hardware]

---

### Post by lufc on 2009-01-04
> **denvergeek said:**
> Nylo,

I've been messing with the same issue on 8.10 for a week, finally fixed it.  I have a Sony Vaio PCG-R505JL, same display chipset.

On my install, it seems that the driver was not guessed correctly (should be "intel").  Even if you set this driver by hand, xorg still can't guess the resolution correctly.  

(edit) Also can't guess "HorizSync" and "VertRefresh" options correctly, which is why you get the black border in the first place.

Here's my working xorg.conf, which gives me a good 1024x768 display, without the cursed "black border":

Let me know if this works!

--Jake


Hi Mate,

This works great for me with a Sony Vaio PCG-R600HEK . I'm using Xubuntu 8.04.1 on the Alternate Install. Took me many, many hours of messing around till I found this thread. Many thanks.

---

### Post by jell on 2009-01-17
Jake,

Many thanks for this.  I have an old Vaio SRX51P (Pentium III 800 MHz, 256Mb, 82515 graphics, 1024x768) and was tearing my hair out trying to get th graphics sorted.  

Your code worked a treat :-)

Thanks Again.

Jell

---

### Post by yaaarrrgg on 2009-01-28
@denvergeek: thanks... this worked perfectly!  I installed xubuntu (intrepid ibex) on an old sony vaio PCG-983L.  Works great. :)

---

### Post by clarks on 2009-01-31
Thank you denvergeek.  I just found this and have been pulling my hair out with a Vaio FX340.  My resolution is now what it is supposed to be.

---

### Post by briandavids on 2009-02-08
Awesome! I have an old Sony VAIO PCG-FX370 that I just loaded Ubuntu 8.10 on. The solution above resolved the issue perfectly. Thanks!

---

### Post by dooglo on 2009-02-26
Hi, I'mnew to all this and was wondering how do I go about doing this?  I have same problem.  Where do I enter this?

Thanks.

---

### Post by dooglo on 2009-02-26
Forget it.  I figured it out.  It works GREAT!!  Thank you.

---

### Post by cenze on 2009-06-22
Just wanted to add my thanks! 
This fixed the xubuntu 8.10 display on my PCG-R505TE.

---

### Post by yotam on 2009-11-27
denvergeek, thank you!
It worked for me, just now with Ubuntu 9.10.
-- yotam

---

