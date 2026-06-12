---
title: "How to set ubuntu server text mode to ol' 80x25"
date: 2014-05-22
forum: Hardware
---

### Post by Foxy_Land on 2014-05-22
First of all; greetings all. I am new in this forum (and in ubuntu as well), and hope that I can learn more about ubuntu here as well (if I can) share and help other members.

Now about my problem; here's the scenario. I want to use ubuntu server + dosemu as an OS replacement for MS-DOS 6.2 running my point-of-sales application. It now run on MS-DOS 6.2. I could successfully run the apps on *some* machine now. Upon installing ubuntu, those old machine automatically run as 80x25 text mode. The problem with other (newer) machine is that ubuntu force the resolution to high resolution (132x50?). My apps need only 80x25 text mode (comply with old MODE CO80 on MS-DOS). I tried to change some configuration on /etc/default/grub with no luck (e.g. appending vga=3840, appending vga=785, adding GRUB_GFXMODE=640x480, etc.).  Honestly, I forgot what I add until I had to re-install ubuntu all over again. That's when I stumble across this forum and decide to ask to you guys.

So the question is: how to set ubuntu server to use text mode 80x25? Looking forward to hearing from you.

Thanks in advance,

Foxy

---

### Post by papibe on 2014-05-22
Hi  Foxy_Land. Welcome to the forum ):P

Take a look at this tutorial: [Change TTY Resolution]("https://help.ubuntu.com/community/ChangeTTYResolution"), specially the instructions under 'FOR 9.10 KARMIC KOALA AND LATER'.

Hope it helps. Let us know how it goes, and if you need more directions.
Regards.

---

### Post by Foxy_Land on 2014-05-22
hi papibe, thanks for you quick respond.

I read the link and tried it on my test machine (acer AOA150bb netbook running ubuntu-server 12.04.4). I put GRUB_GFXPAYLOAD_LINUX=640x480, run sudo update-grub, and reboot. Yet, still no luck. I tried to enable GRUB_TERMINAL=console -- still with the same result. Netbook (which use VGA adaptor) should support 640x480, right? At least it runs with appropriate 80x25 text mode in MS-DOS 6.2.

For better explanation, following is the content of my /etc/default/grub
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXPAYLOAD_LINUX=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

Is there any setting I miss?

Regards,
Foxy

---

### Post by papibe on 2014-05-22
Sorry to hear that.

What resolutions are shown when you run vbeinfo on the grub's command line?

Regards.

---

### Post by Foxy_Land on 2014-05-22
There an asterisk in front of 0x115 800 x 600 x 32 (3200). This means I run 800 x 600, right?

---

### Post by papibe on 2014-05-22
Yes. Try that, although I'm guessing the asterisks means it is the current resolution.

Let us know how it goes.
Regards.

---

### Post by Foxy_Land on 2014-05-25
@papibe: still no luck. What I did was:
```

GRUB_GFXPAYLOAD_LINUX=800x600

```

Yet still, the console resolution wouldn't go to 80x25.
I consider my self a newbie in linux, and this really frustrating. How hard it is to set console resolution to old 80x25 row? Why should linux console depends on grub (which, afaik, is like a boot manager).

Can anybody help me with this?

Thanks in advance.

Foxy

---

### Post by papibe on 2014-05-25
Try this setting these parameters instead:
```
GRUB_GFXMODE=640x480
GRUB_GFXPAYLOAD_LINUX=keep
```
Then update grub, and reboot.

If that don't work, we could try with the legacy method by modifying the parameter 'GRUB_CMDLINE_LINUX_DEFAULT', so it looks like this:
```
"GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vga=792"
```
Again, update grub and reboot.

Let us know how that works.
Regards.

---

### Post by Foxy_Land on 2014-05-25
Thanks for your patience. Unfortunately, it didn't work. I still get console with 37 rows x some columns (didn't count the chars). I tried different parameter with vga=.... . Got it from [http://pierre.baudu.in/other/grub.vga.modes.html](http://pierre.baudu.in/other/grub.vga.modes.html) - yet, still, no luck (I didn't forgot to put sudo update-grub each time I made change with /etc/default/grub). The system persist on displaying 37 rows instead of 25.

Maybe some other way around exists? Or is this the only way? Please bear with me.... :(

Oh, one more thing; forgot to mention: the netbook I use as a testing machine also dual boot with linux mint 16. I installed the ubuntu 12.04 LTS first, then the mint afterwards. Would this be a problem? Maybe there is/are other setting(s) that I missed?

TIA,
Foxy

---

### Post by steeldriver on 2014-05-25
I seem to remember that when I was messing with this, the mode needs to be specified EXACTLY as shown by the grub vbeinfo command - in particular, if there is a depth parameter like 800 x 600 x **32** then the corresponding GRUB_GFXMODE also needs to be 800x600**x32** to get it to work. But I may be misremembering.

---

### Post by Foxy_Land on 2014-05-26
hi steeldriver: thank you for joining in. I have just tried what you suggested. I use 640x480x16. No luck. Still the same resolution on the ubuntu console.

Looking forward to hearing more from you (or anyone) about this matter

TIA

---

### Post by papibe on 2014-05-26
Could you run this command and post back its results?
```
lspci -nnk | grep -iA2 vga
```
What kind of computer is this? If it is a desktop, do you have another monitor?
Regards.

---

### Post by Foxy_Land on 2014-05-28
@papibe: thanks for your reply and sorry for a late follow up.

This is not a desktop computer. It is an old netbook; Acer AOA150BB running on first generation of Atom Processor with 120GB hard disk and 512MB DRAM. I use this as a test machine because I had the same resolution problem with several desktop computer on my client.

Following is the result of lspci line as you suggested:
```

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller [8086:27ae] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:015b]
	Kernel driver in use: i915

```

I hope this would help you or anybody to help me on make this machine running on 80x25 text mode. 
Looking forward to hearing more suggestion :)

TIA,
foxy

---

### Post by papibe on 2014-05-28
Thanks.

At this time we are left with some edgier options. Let's try this project: [915resolutiion]("http://915resolution.mango-lang.org/").

Please follow this instructions:

Download the project package:
```
wget http://915resolution.mango-lang.org/915resolution-0.5.3.tar.gz
```
Then uncompress it:
```
tar xvf 915resolution-0.5.3.tar.gz
```
Then move the just created directory:
```
cd 915resolution-0.5.3
```
finally run the main program:
```
sudo ./915resolution -l
```
Then post back what is the output of that.

Let us know how it goes.
Regards,

---

### Post by Foxy_Land on 2014-05-28
Thanks for detail instructions. It run well until I executed the main program. Following is the result:
```

Intel chipset detected.  However, 915resolution was unable to determine the chipset type.
Chipset Id: 27ac8086
Please report this problem to stomljen@yahoo.com

```

I'm on the edge of giving up now :( . I mean, this is only one machine. I have 10 clients running my POS application under DOS 6.2. Each client has up to 20 Point-of-sale running everyday. There is no specific machine in use. Some are new machines utilize Intel Pentium G2030, some others are old Dual Core or even Pentium 4s. Well, even Pentium 4 is a blast for DOS application ;). I was hoping to change MS-DOS to ubuntu server + dosemu, but I stumble on this resolution problem. 

Of course the best solution is to re-write the apps in java. But, I still find a way around that :)
Any idea? 

Foxy

---

### Post by papibe on 2014-05-28
Let's try fbset,

Install it:
```
sudo apt-get install fbset
```
Then run these commands and post back the results:
```
fbset -i

fbset -s
```
You may even try to set the resolution:
```
fbset -xres 800 -yres 600
```
or
```
fbset -xres 640 -yres 480
```
or set a virtual 640x480 resolution inside a 800x600 screen:
```
fbset -xres 800 -yres 600 -vxres 640 -vyres 480
```
Let us know if that makes any difference.
Regards.

---

### Post by Foxy_Land on 2014-05-29
hi papibe:

The result of fbset -i is:
```



mode "1024x600"
    geometry 1024 600 1024 600 32
    timings 0 0 0 0 0 0 0
    accel true
    rgba 8/16,8/8,8/0,0/0
endmode


Frame buffer device information:
    Name        : inteldrmfb
    Address     : 0x20020000
    Size        : 2457600
    Type        : PACKED PIXELS
    Visual      : TRUECOLOR
    XPanStep    : 1
    YPanStep    : 1
    YWrapStep   : 0
    LineLength  : 4096
    Accelerator : No

```

and the result of fbset -s:
```



mode "1024x600"
    geometry 1024 600 1024 600 32
    timings 0 0 0 0 0 0 0
    accel true
    rgba 8/16,8/8,8/0,0/0
endmode

```

I tried [COLOR=#000000][FONT=Ubuntu Mono]fbset -xres 1024 -yres 600 -vxres 640 -vyres 480[/FONT][/COLOR] and the screen was like being cut halfway down. The text size is still the same, but only occupied the top part of the screen. When I put [FONT=courier new]clear[/FONT], the system would only clear the top part and left the bottom part with text.

Anyway, this just cross my mind: what about using xterm (xwindow based; thus graphic based) instead of trying to 'force' the text resolution to 80 x 25? I reckon having 80 x 25 text in graphics (xterm) should be easier (and not too hardware-dependent) than force linux to use 80x25 text resolution. What do you think about this? If this would be the easier path, I would try to go that way. Well, although that would put me on different problem; how to install xterm in ubuntu server :D

Looking forward to hearing more from you.

Regards,
Foxy

---

### Post by Foxy_Land on 2014-05-29
I am completely baffled. In a confusion, I searched a lot and found this [http://knoppix.net/forum/showthread.php?30429-tty-80x25-not-available](http://knoppix.net/forum/showthread.php?30429-tty-80x25-not-available) . It is knoppix actually. I am really is newbie in linux --- and ubuntu is my first choice (actually it was sudo apt-get install that hooked me ;) ). Anyway, back to the topic, I hope gurus here can show me how to [COLOR=#333333]nomodeset as kernel parameter in ubuntu server 12.04. I have no clue.

TIA,
Foxy[/COLOR]

---

### Post by mcduck on 2014-05-29
> Oh, one more thing; forgot to mention: the netbook I use as a testing machine also dual boot with linux mint 16. I installed the ubuntu 12.04 LTS first, then the mint afterwards. Would this be a problem? Maybe there is/are other setting(s) that I missed?

I suppose both Papibe and steeldriver missed this as it was edited to your message afterwards...

Anyway, if you installed Mint after Ubuntu, make sure you are really making the Grub config edits on the correct place. If Mint was installed afterwards, and you allowed it to install Grub, the Grub boot line changes must be done on Mint's config files instead.

Edit: Also, this might help if you are not sure about which distribution is in control of Grub: [https://help.ubuntu.com/community/Boot-Info]("https://help.ubuntu.com/community/Boot-Info")

---

### Post by Foxy_Land on 2014-05-29
gosh... mcduck, you're a bit late :D -- or, maybe not. I've just format my netbook and as I'm writing this post, I am in the process of downloading slackware (I read [http://ubuntuforums.org/showthread.php?t=260746](http://ubuntuforums.org/showthread.php?t=260746) and thought that maybe other old distro would suit old requirement ;) ). Anyway, because you say so, I am going to give ubuntu another try. So, while waiting for the download to finish (gonna take a while with our slow-home-connection), I'm going to install ubuntu server again. I will surely let you guys know how it is going.

Thanks again guys ;)

Foxy

---

### Post by Foxy_Land on 2014-06-01
First of all, sorry for a late follow up.

Next, I tried all the suggestion in this thread on completely clean machine (format the hard disk, reinstall ubuntu server 12.04.4 from scratch) --- and the ubuntu server is the only operating system on the disk. Yet, still no luck. The resolution persist on a small 30-something rows. I couldn't set it to 80x25.

The solution (well, it's not actually *solved*, but it is solved for me :) ) : I installed slackware 14.1. It uses lilo instead of grub. I put vga = 3840 on /etc/lilo.conf, and it immediately run on 80x25 text resolution as I wanted in the first place. Now I'm learning how to use SlackBuilds as it seems that there's no way to immediately have the binaries installed without recompile in slackware (the reason why I chose ubuntu --- please guys, CMIIW).

So I consider the case is close for now. Thank you for all of your suggestions --- especially to papibe whose been very patience. :) . 

Regards,

Foxy

---

### Post by sudodus on 2014-06-01
What happens in Ubuntu if you

```
# Uncomment to disable graphical terminal (grub-pc only)
[COLOR=#ff0000]#[/COLOR]GRUB_TERMINAL=console

```
to

```
# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

```

in the file **/etc/default/grub**
and run

```
sudo update-grub
```

---

### Post by Foxy_Land on 2014-06-01
hi sudodus: Thanks for your reply. Yup. Done that. Tried to combine that with GRUB_GFX... (with various combination) but no effect whatsoever. I guess I'll just go with slackware. Though this slack give this newbie another caveat: I couldn't compile dosemu, because I didn't install gcc. I downloaded gcc, but I couldn't install it. I downloaded slapt-get only to found that I have to [FONT=courier new]make[/FONT] it first. Hmm... didn't I downloaded slapt-get to install gcc? Man, I do miss sudo apt-get install ....

(btw, I am reinstalling slackware now. I'll make sure to install the compiler ;) )

Foxy

---

### Post by sudodus on 2014-06-01
> Thanks for your patience. Unfortunately, it didn't work. I still get  console with 37 rows x some columns (didn't count the chars). I tried  different parameter with vga=.... . Got it from [http://pierre.baudu.in/other/grub.vga.modes.html](http://pierre.baudu.in/other/grub.vga.modes.html)  - yet, still, no luck (I didn't forgot to put sudo update-grub each  time I made change with /etc/default/grub). The system persist on  displaying 37 rows instead of 25.

Maybe some other way around exists? Or is this the only way? Please bear with me.... :sad:

Oh, one more thing; forgot to mention: the netbook I use as a testing  machine also dual boot with linux mint 16. I installed the ubuntu 12.04  LTS first, then the mint afterwards. Would this be a problem? Maybe  there is/are other setting(s) that I missed?

TIA,
Foxy


Why is it so important to have 80x25 characters instead of 37 rows? Will the text be too small and hard to read? I often prefer higher resolution than the standard one, because there can be more information on the screen.

What happens when you boot into ***recovery mode***? For me it usually means there will be a 80x25 text screen during boot (I think because of the boot option **nomodeset**).

---

### Post by Foxy_Land on 2014-06-01
sudodus:
[quote="sudodus"]
[COLOR=#000000]Why is it so important to have 80x25 characters instead of 37 rows? Will the text be too small and hard to read? I often prefer higher resolution than the standard one, because there can be more information on the screen.
[/COLOR][/quote]

I believe you miss my first post ;) [http://ubuntuforums.org/showthread.php?t=2225544](http://ubuntuforums.org/showthread.php?t=2225544) . 

My legacy POS application was written with Microsoft Foxpro 2.6 for DOS, and like any other DOS apps, it runs on 80x25 :)

Foxy

---

### Post by sudodus on 2014-06-01
I see. You really need 80x25 for that application.

Did you try with the boot option nomodeset or recovery mode?

---

### Post by sudodus on 2014-06-01
Another alternative might be to run a very light windows manager (not a full desktop environment) and a terminal window, that you can set easily with the geometry option to 80x25, for example

```
xterm -geometry 80x25 -fa default -fs 13 &
```

-fa default -fs 13 renders a nice font and size for me, you might prefer the default font or some other size.

You can select between jwm, fluxbox, openbox, ... These windows managers are all much lighter than a full desktop environment.

---

### Post by Foxy_Land on 2014-06-02
@sudodus: I have my netbook running slackware; on 80x25 resolution. But, really, slackware is not my cup of tea (e.g. where is /etc/network/interfaces ?). So, I (again) installed ubuntu on my virtualbox. After installing, I uncomment the line with  GRUB_TERMINAL and GRUB_GFXMODE. Did the sudo update-grub, and it works perfectly; beautiful 80 x 25 resolution as I wanted to be.

Honestly I don't know what's wrong with the netbook. The same configuration, yet it still goes to 30 rows. Anyway, my conclusion is this is hardware-dependent. Hence, I am going to try your suggestion to use light x window. I searched the net a bit, and found that ratpoison might be the first candidate that suits my need. Hmm... and now ubuntu gives back "Can't open display" when I try to run ratpoison. Gotta search the net first -- meanwhile, any idea?

Btw, I'm installing ubuntu server edition (thus, no x window). Would this mean I have to sudo apt-get something else as well? Isn't that would be added automatically by the system (as it knows what depend-on-what).

Regards,
Foxy

---

### Post by sudodus on 2014-06-02
It depends what comes with the installation of ratpoison. Maybe you need the package ***xinit*** and run startx to run your window manager. I have not used ratpoison, but I have used jwm, fluxbox and openbox. They are all pretty light-weight if you don't add a lot of eye-candy (only a simple background and the tools you need, like xterm).

Edit: See this link for the RAM using when idling

[https://help.ubuntu.com/community/9w/RAM_%26_disk_usage](https://help.ubuntu.com/community/9w/RAM_%26_disk_usage)

---

### Post by Foxy_Land on 2015-03-28
Hi all, it's been almost a year since I got this problem. I ended up postponed the project because slackware was (and still is) too 'alien' for me. Anyway, a month ago I had the same problem. I searched the net (and stumble upon this thread as well), but now, I finally found the answer. All I have to do is simply disable the framebuffer and -- voila! -- the resolution goes back to nice-old-80-columns-times-25-rows :) .

So, I think it's my responsibility to put the solution here. I hope someone would get the benefit from this thread.

Here is what I put on /etc/default/grub:
```

CMDLINE_LINUX_DEFAULT="vga=normal nofb nomodeset video=vesafb:off i915.modeset=0"

```

The other entry on grub is left unchanged. After I made the changes, I update the grub (sudo update-grub) and that's it. It works on various computer. I set 20 PCs and it just works.

Thank you all for reading :).

foxy_land

---

### Post by sudodus on 2015-03-28
Thank you for sharing :KS

---

