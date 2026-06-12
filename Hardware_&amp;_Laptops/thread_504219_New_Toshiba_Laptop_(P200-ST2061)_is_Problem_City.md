---
title: "New Toshiba Laptop (P200-ST2061) is Problem City"
date: 2007-07-18
forum: Hardware &amp; Laptops
---

### Post by tripinva on 2007-07-18
Wow!

I never would have imagined that a laptop could have so many different problems with Linux all at one shot, but, here I am.

I bought this new Toshiba P200-ST2061 as I am preparing to go off to college, and ever since I got it on Monday I've been having one issue after another with it.

[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteP200-ST2061](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteP200-ST2061)

That's the report I was preparing to file on it, but I had so many issues with it that I just listed stuff at the top.  Maybe someone out there can help me get this thing up.

Let's start from the top.

**_Video_**
Intel GMA X3100

This was a relatively easy problem to resolve.  I had to install some stuff from the command line, then tweak xorg.conf, and install some SDL things, and now I finally have this working.  Despite this, Compiz still does not work.  However, this is the least of my concerns.  (If anyone wants to take a shot at this, I can post more info on it)  I'm running a 2.6.22-8-generic kernel now, plus the newest Xorg and udev and some other select things from Gutsy.

**_Wireless_**
Intel 4965AGN

The easiest to resolve.  Found a nice step-by-step on here somewhere that quickly guided me through it.  2.6.22 kernel was a must-have here.

**_Sound_**
RealTek?  Intel?  I get conflicting data

While the sound does, in fact, work out of the box, it's not correct.  First and most importantly, when I plug in my headphones, no sound comes out of them and the speakers remain on.  Second, it would appear that the in-built microphone does not work.  Third, the volume dial on the front increments in huge steps, making it nearly useless for volume control.  Fourth, all I have listed in KMix is Master and PCM for outputs, and nothing for input.  This seems light.

I've tried the 3stack thing, I tried RealTek's drivers.  Gutsy Alpha's ALSA package left me with no sound at all.

**_[color=blue]DVD Burner - SOLVED[/color]_**
DVD Super Multi

Of all the things to not work, I wouldn't have expected this to be one of them.  I've tried a number of things, including rebuilding the init file and putting piix in the /etc/modules file.  Linux doesn't even appear to detect the drive, though I don't really know which command to use to confirm this.  This one is especially important as I'm trying to get a kvm image up and running.  I have XP installed from an ISO but that's about it.

**_Webcam_**
Chicony

This is of low priority at the moment, but some progress is made.  I eventually got it to display a picture with the uvcvideo driver and luvcviewer, but I'd like to use this cam with Ekiga or something similar, and cannot seem to find any program that has V4L2 support.  Any ideas?

**_Card Reader_**
Texas Instruments

Despite the new kernel, the new udev, and modprobe tifm_sd and others, I cannot get any SD cards I put in the slot to read.  According to forum posts, those are the three things needed to get this card reader working, but this is evidently not the case.  It shows up in dmesg, but never mounts.

**_KDE 3.5.6_**

Yeah, I know, this isn't hardware.  However, after running normal system updates, Alt+F1 no longer brings up the K Menu, and Alt+F2 no longer brings up the Run dialog box.  Any thoughts on this would be most appreciated.  I'm almost considering trying to install Gutsy's KDE packages to see if the issue is resolved.

Despite all the things wrong with it, all the things that DO work are a nice surprise.

**_*These things work!*_**

**_Media Buttons_**

The media buttons on the unit work with Amarok very well, and I was quite surprised to accidentally discover this while playing with xev.

**_ACPI_**

Does CPU scaling, detects battery life, dims the screen when on battery power; the whole thing is just wonderful!  I know my old system didn't have ACPI that worked as well, though it did toward the end of its four years.

**_Bluetooth_**

If I boot into Vista first and enable it, then it remains enabled through any warm reboots into Linux and is then fully usable.  I'm afraid to try to install the Omnibook driver to build in native support, as I don't want to lose the functioning ACPI.

**_Fingerprint Reader_**

Installed Thinkfinger package, worked fine.  Not good for much in KDE, but oh well.

I love the machine, but these driver problems are about to send me up the wall!

And finally, a little personal thing that may not be resolvable, but I'm somewhat of an addict to the shooter game "Sauerbraten," and my hope was that I could play it on this computer.  While it does try to run, I get this out of it without being able to play:

```
./sauerbraten_unix -w1680 -h1050
init: sdl
init: enet
init: video: mode
init: video: misc
init: console
init: gl
Renderer: Mesa GLX Indirect (Mesa project: www.mesa3d.org)
Driver: 1.4 (2.1 Mesa 7.0)
WARNING: No vertex_buffer_object extension! (geometry heavy maps will be SLOW)
Rendering using the OpenGL 1.5 assembly shader path.
COMPILE ERROR (VS:caustic) - (null)
!!ARBvp1.0
    OPTION ARB_position_invariant;
    ATTRIB opos = vertex.position;

        DP3 result.texcoord[0].x, opos, state.texgen.object.s;
        DP3 result.texcoord[0].y, opos, state.texgen.object.t;

    TEMP fogplane;
    MAD fogplane, state.matrix.modelview.row[2], program.env[8], program.env[9];
    DP4 result.fogcoord, -opos, fogplane;

        END
    xcooQ

    !!ARBfp1.0

    OPTION ARB_precision_hint_fastest;



        OPTION ARB_fog_linear;

    TEMP caustic, caustic2;
    TEX caustic, fragment.texcoord[0], texture[0], 2D;
    TEX caustic2, fragment.texcoord[0], texture[1], 2D;
    LRP result.color, program.env[0], caustic2, caustic;

        END
    lt  COMPILE ERROR (VS:caustic) - (null)&#65533;P&#375;P&#375;= fragment.texcoord[1];
        ATTRIB tc2 = fragment.texcoord[2];
        ATTRIB camts = fragment.texcoord[3];



    DP3 cam.w, camts, camts;
    RSQ cam.w, cam.w;
    MUL cam.xyz, cam.w, camts;



        TEX dudv, tc1, texture[2], 2D;
        MAD dudv.xy, dudv, 2, -1;


    TEMP reflect, refract;

    MAD temp, dudv, 0.4, projtc;
    TXP reflect, temp, texture[0], 2D;
    TXP refract, temp, texture[3], 2D;

    MAD temp, dudv, 0.025, tc2;
    TEX bump, temp, texture[1], 2D;
    MAD bump.xyz, bump, 2, -1;





    DP3_SAT invfresnel, cam, bump;
    MAD invfresnel, invfresnel, 0.5, 0.5;
    LRP result.color, invfresnel, refract, reflect;


        END
&#65533;         MAD Xv, 2, -1;


    TEMP reflect, refract;

    MAD temp, dudv, 0.025, tc2;
    TEX bump, temp, texture[1], 2D;
    MAD bumpxyz, bump, &#65533;0xy, dudv, 2,&#65533;P temp.w, projtc.w;
    MUL temp.xyz, projtc, temp.wwww;
    MAD temp.xy, dudv, 0.01, temp;

    TEX reflect, temp, texture[0],2D;
    TEX&#65533;@ARAM specfa           DP3_SAT he, he, bump;
            POW he, he.x, specfactor.w;

            MUL light, program.env[4], light.w;
           RC&#65533;Pgram.env[3],0[3];



    DP3_SAT invfresnel, cam, bump;
    MAD invfresnel, invfresnel, 0.5, 0.5;
    LRP temp, invfresnel, rfract, refl&#65533;`D:
    refleX temp, dudv, 0.4, projtc;
    TXP reflect, temp, texture[0], 2D;

    MAD temp, dudv, 0.025, tc2;
    TEX bump, temp, texture[1] 2D;
    MA&#65533;pecfactor = 98    DP3_SAT he, he, bump;
            POW he, he.x, specfactor.w;

            MUL light, program.env[4], light.w;
           RCP_SAT l&#65533;&#65533;v[3], progra`


    DP3_SAT invfresnel, cam, bump;
    MAD invfresnel, invfresnel, 0.5, 0.5;
    MUL temp, fragment.color, progam.env[5].&#65533;;:
    MAD co&#65533;ight, temp;
    MUL col.a, invfresnel, program.env[5].y;

    TEMP fog;
    SUB fog, state.fog.params.z, fragment.fogcoord.x
    MUL_SA&#9618;&#65533;g, col, {0, &#65533;k:
        END
    i%(&#65533;8`&#65533;p&#65533; &#65533;&#65533;X&#65533;&#9618;&#9618;k&#65533;@&#65533;`&#65533;`&#65533;`&#65533;P&#9618;k\h&#65533;&#65533;&#65533;&#65533;<&#65533;<&#65533;<&#65533;&#65533;&#65533;&#65533;k&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;)&#65533;&#65533;)&#65533;&#65533;)&#65533;&#65533;)&#65533;&#65533;)&#65533;&#65533;)&#65533;&#65533;)Y&#65533;Segmentation fault (core dumped)
```

Anything you need as far as outputs of commands, etc. I'll be glad to provide, because I'm really anxious to get this machine up and running.  When it's all said and done, I'll try and write a nice guide for it, as well!

Thanks in advance, and I hope there are people able to help me with this mountain of issues.

- Trip

---

### Post by tripinva on 2007-07-18
Okay, just to update, I stumbled upon a solution to the DVD Burner problem.  

sudo modprobe ide-generic

So that now resides in /etc/modules ready to be loaded on each bootup.  Found it in a thread about a Vaio with the same issue.

- Trip

---

### Post by fd9_ on 2007-07-18
Can you tell me where you find that step-by-step guide for the Intel 4965AGN? Are you using ndiswrapper? Thanks!

---

### Post by tripinva on 2007-07-18
> **fd9_ said:**
> Can you tell me where you find that step-by-step guide for the Intel 4965AGN? Are you using ndiswrapper? Thanks!
No NDISWrapper, but does use the Gutsy kernel.

[http://ubuntuforums.org/showthread.php?t=493095](http://ubuntuforums.org/showthread.php?t=493095)

- Trip

---

### Post by tripinva on 2007-07-19
> **tripinva said:**
> Okay, just to update, I stumbled upon a solution to the DVD Burner problem.  

sudo modprobe ide-generic

So that now resides in /etc/modules ready to be loaded on each bootup.  Found it in a thread about a Vaio with the same issue.

- Trip
Another update, this apparently did not fully resolve the issue.  I tried to open up K3B this morning, and it's complaining that DMA is not enabled, and attempting to enable it through the command line gives me:

```
sudo hdparm -d 1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)
```

That said, it does work.  I'm not complaining too much, though if performance is very slow on burning, then I may care more.  Reading a whole data DVD last night didn't seem slow, so I don't know yet.

- Trip

---

### Post by tripinva on 2007-07-19
Back with another update, and wondering if anyone has any ideas for me.

Apparently, research indicates that ALSA does not have a driver for the ICH8 at this time, meaning that I am out of luck as far as audio is concerned.  I'll have to live with what I have for the time being.

I managed to get Sauerbraten running today by disabling shaders on startup, which tells me that I still don't have the video drivers I need.  Whether they simply don't exist yet or I don't have them installed, does anyone know the procedure needed to get this going?  I imagine that straightening out this problem would also allow Compiz to run.

I'm also considering wiping and moving to the Gutsy Tribe 3 disk.  Any thoughts?

Thanks again in advance.  Please help if you can.

- Trip

---

### Post by tripinva on 2007-07-20
Got Sauerbraten running!

sudo dpkg-reconfigure -phigh xserver-xorg

Turns out that though the Intel driver was installed, it wasn't actually enabled.  So once I figured out how to do that, I restarted X and Sauerbraten (as well as videos) was running fine!

-Compiz still does not work, but that's no surprise.  Also, CD burning doesn't seem to be negatively impacted by the lack of DMA, so I'm not going to concern myself with that.

So now I still have to straighten out the sound driver, once that becomes available, as well as getting the webcam to work in applications other than the testing app, and it would be nice if the card reader worked as well.

- Trip

---

### Post by jacob01 on 2007-07-20
do finger print readers even work with linux

---

### Post by tripinva on 2007-07-20
> **jacob01 said:**
> do finger print readers even work with linux
All I had to do was install the ThinkFinger package.

- Trip

---

### Post by tripinva on 2007-07-20
I've finally dealt with the wiki page.

[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteP200-ST2061](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteP200-ST2061)

Any additional help on the sound and webcam and such would be appreciated.

- Trip

---

