---
title: "Radeon R7 M265 Graphics Card Driver"
date: 2020-03-27
forum: Hardware
---

### Post by grenic on 2020-03-27
Hi guys,

I am struggling to install graphics card drivers for my laptop running Ubuntu (Linux 5.3.0-42-generic x86_64).

Please can someone help.

---

### Post by grenic on 2020-03-27
When I run this command:- lspci -vnn | grep VGA -A 12

The following is output:

00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Haswell-ULT Integrated Graphics Controller [1025:0775]
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at c0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 4000 [size=64]
	[virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915


00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 09)
	Subsystem: Acer Incorporated [ALI] Haswell-ULT HD Audio Controller [1025:0775]

---

### Post by kurt18947 on 2020-03-27
What is your display doing or not doing? I'm not an expert but I don't know that you need to install anything, it looks like the appropriate driver is already installed. As I said, I'm not an expert so could be wrong.

---

### Post by grenic on 2020-03-28
I am trying to play Dota 2 & CS GO on Steam. My fps is approximately 25 fps when it should be somewhere near 115? I cannot confirm that I have actually installed the drivers for the graphics card for the laptop - I was wondering if someone might be able to help me confirm by perhaps being able to walk me through a diagnostic to check what I have installed and what I need? Any assistance would be very much appreciated during this COVID-19 time we find ourselves in.

---

### Post by Yellow Pasque on 2020-03-28
> **grenic said:**
> I was wondering if someone might be able to help me confirm by perhaps being able to walk me through a diagnostic to check what I have installed and what I need? 

Everything should be installed out of the box. To verify:
```
glxinfo -B        #This command should show Intel as the OpenGL renderer
DRI_PRIME=1 glxinfo -B        #This command should show AMD as the OpenGL renderer
```

So when you want to run something on the AMD GPU, you need to run the command with DRI_PRIME, as in the command above.

---

### Post by Yellow Pasque on 2020-03-28
Oh, to do DRI_PRIME automatically for Steam, you can right-click on a game and add right click on the game and add this to the launch options:
```
DRI_PRIME=1 %command%
```

---

### Post by grenic on 2020-03-28
Adding {DRI_PRIME=1 glxinfo -B} to the launch option of the game definitely doesn't help. Unless I've done something wrong. Is that the only command I should have added in the advanced launch option properties?

Thank you for your help thus far.

---

### Post by Yellow Pasque on 2020-03-28
No, glxinfo is only a diagnostic command. You were supposed to look at the output and verify the result (or copy/paste here if not sure).
You were literally supposed to put this in the launcher:
```
DRI_PRIME=1 %command%
```

Try again.

---

### Post by grenic on 2020-03-29
Putting: [COLOR=#000000][FONT=&quot]DRI_PRIME=1 %command% - into the launcher outputs the below.[/FONT][/COLOR]

bash: fg: %command%: no such job

---

### Post by him610 on 2020-03-29
RE: Post #7
> glxinfo -B
should be
```

glxinfo -b
```

---

### Post by Yellow Pasque on 2020-03-29
> **him610 said:**
> re: Post #7
should be
```

glxinfo -b
```

noooooooooooooooooo

---

### Post by grenic on 2020-03-29
greg@greg-Aspire-V5-561G:~$ DRI_PRIME=1 glxinfo -b

67

---

### Post by grenic on 2020-03-29
Why?

---

### Post by Yellow Pasque on 2020-03-30
Sorry, but I have nothing else to suggest. I don't use Steam on Linux, so maybe my Google-fu has failed me in this case. The bottom line is that you need to use "DRI_PRIME=1" to launch things on the AMD GPU and the command is "glxinfo -B". (Yes, it's a capital B and I'm not sure what the heck him610 is talking about.)

---

### Post by him610 on 2020-03-31
> Yes, it's a capital B and I'm not sure what the heck him610 is talking about.
From the terminal, ```
man glxinfo
``` shows
```

glxinfo(1)                           General Commands Manual                           glxinfo(1)

NAME
       glxinfo - show information about the GLX implementation

SYNOPSIS
       glxinfo [options]

DESCRIPTION
       The  glxinfo program shows information about the OpenGL and GLX implementations running on
       a given X display.

       The information includes details about the server- and client-side GLX implementation, the
       OpenGL and GLU implementations as well as a list of available GLX visuals.

OPTIONS
       -v      Print visuals info in verbose form.

       -t      Print verbose table.

       -display display
               Specify the X display to interrogate.

       -h      Print usage information.

       -i      Force an indirect rendering context.

       -b      Find the "best" visual and print its number.

       -l      Print interesting OpenGL limits.

AUTHOR
       glxinfo was written by Brian Paul <brian.paul@tungstengraphics.com>.

       This  manual page was written by Thierry Reding <thierry@gilfi.de>, for the Debian project
       (but may be used by others).

                                            2006-11-29                                 glxinfo(1)

```
There is no uppercase '**-B**' listed.

---

### Post by Yellow Pasque on 2020-03-31
Well, then the manpage is out of date:
```
$ glxinfo -h
Usage: glxinfo [-v] [-t] [-h] [-b] [-l] [-s] [-i] [-display <dname>]
	-display <dname>: Print GLX visuals on specified server.
	-i: Force an indirect rendering context.
	-B: brief output, print only the basics.
	-v: Print visuals info in verbose form.
	-t: Print verbose visual information table.
	-h: This information.
	-b: Find the 'best' visual and print its number.
	-l: Print interesting OpenGL limits.
	-s: Print a single extension per line.
```

---

### Post by him610 on 2020-03-31
@Yellow Pasque
Thanks for the update. One can learn something from the forum everyday.

---

### Post by grenic on 2020-04-03
I am still left puzzled as to if I need to install drivers for my laptop running Ubuntu. The reason I query this is because I can recall when I was running Windows 10 OS I had at least 110 FPS in CS GO and Dota 2! Now I'm only receiving approximately 20% of that!

Do I need to install any additional graphics card drivers for my machine, if so, please can you assist me with a step-by-step guide to do so.

---

### Post by Yellow Pasque on 2020-04-03
> **grenic said:**
> I am still left puzzled as to if I need to install drivers for my laptop running Ubuntu.

Probably not. Again, please give the output of these two commands to verify you have 3D acceleration working correctly:
```
glxinfo -B
DRI_PRIME=1 glxinfo -B
```

> The reason I query this is because I can recall when I was running Windows 10 OS I had at least 110 FPS in CS GO and Dota 2! Now I'm only receiving approximately 20% of that!

Is that running with DRI_PRIME or not? Even if so, you would not be the first person I've seen complaining about poor performance with Intel/AMD hybrid graphics on Linux.

---

### Post by QIII on 2020-04-03
This is a laptop with hybrid Intel/AMD graphics, is it not?

In that case, you will have to determine if your BIOS/EFI will allow you to select the preferred GPU.

Generally, there is nothing to do to install the AMD driver.  If AMDGPU is supported for the GPU, that module is loaded.  If it is not, Radeon is loaded.

Let's first see if either of those is loaded.

Please post the results of the following, which will list the loaded modules and filter for amdgpu and radeon respectively:

```
lsmod | grep amdgpu
```

and

```
lsmod | grep radeon
```

---

