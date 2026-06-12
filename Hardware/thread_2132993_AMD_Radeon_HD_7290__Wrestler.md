---
title: "AMD Radeon HD 7290 : Wrestler"
date: 2013-04-06
forum: Hardware
---

### Post by raring on 2013-04-06
Hello Peeps,

I have a relatively new Acer Aspire One 725, it contains the AMD graphics integrated chip as below..

```
tux@akira:~$ lspci -v | grep VGA
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 7290] (prog-if 00 [VGA controller])

```

Unfortunately I can't seem to find a compatible driver that unlocks the power of this device, I know it's quite beefy (comparitively speaking) as
running Steam a la Team Fortress 2 is possible (under Windows 7), though with 12.10 / 13.04 beta it's unbearable and unplayable.

Any ideas / suggestions? The latest Catalyst driver on 22nd of March didn't even recognise their own card :/

---

### Post by Yellow Pasque on 2013-04-06
> **raring said:**
> The latest Catalyst driver on 22nd of March didn't even recognise their own card
Do you mean that it didn't work or are you referring to the annoying "unsupported hardware" watermark that sometimes occurs with newer cards/drivers?

---

### Post by raring on 2013-04-08
Didn't detect / support card, the install cancels. I wouldn't mind if it had the watermark as I read ways people can remove that.

---

### Post by raring on 2013-04-10
[http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-3LINBetaDriver.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-3LINBetaDriver.aspx)

Anyone try this one out recently? 10th of April..

---

### Post by raring on 2013-04-10
So I tried out the new driver and alls well so far.. pictures in imgur link..

[http://imgur.com/a/aw3dt](http://imgur.com/a/aw3dt)

I'm re-downloading Team Fortress 2 now on Steam to check out the performance.. will update post in respect of results / findings.

Note : if you see in the last photo, a warning comes up when starting Steam client, I haven't looked any further into it until I actually start TF2 but it references to go here -> [https://support.steampowered.com/kb_article.php?ref=9938-EYZB-7457](https://support.steampowered.com/kb_article.php?ref=9938-EYZB-7457)

UPDATE : so I get an error when trying to start Team Fortress 2 -> [http://i.imgur.com/oCCfaaU.png](http://i.imgur.com/oCCfaaU.png)  so I tried ..

> tux@akira:~/Downloads$ LIBGL_DEBUG=verbose glxinfo
name of display: :0
libGL: screen 0 does not appear to be DRI2 capable
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/swrast_dri.so
libGL error: failed to load driver: swrast


So I decided to install the driver again, overwriting the first one..
and hey presto, it worked !

but just to resolve my curiousity I ran LIBGL_DEBUG=verbose glxinfo again

> tux@akira:~$ LIBGL_DEBUG=verbose glxinfo
name of display: :0
libGL: AtiGetClientDriverName: 12.10.5 fglrx (screen 0)
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/fglrx_dri.so
ukiDynamicMajor: found major device number 251
ukiDynamicMajor: found major device number 251
ukiOpenByBusid: Searching for BusID PCI:0:1:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 6, (OK)
ukiOpenByBusid: ukiOpenMinor returns 6
ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: ATI
server glx version string: 1.4



etc..

So in conclusion the best / easier way is to run

> sudo apt-get install mesa-utils:i386 ia32-libs 

and *then* install the latest AMD driver (with fingers crossed)

Of course you'll have to rerun the watermark script if you did what i did originally.

Team Fortress 2 runs ok, considering the netbook that it is I just turn the settings all the way down :)

-------------------------------------------

To remove AMD 'Testing use only' watermark, try the solution below..

"Running this script worked for me on Ubuntu 12.10/13.04 64bit:

> #!/bin/sh
DRIVER=/usr/lib/xorg/modules/drivers/fglrx_drv.so
for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6}'); do
 sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done

One way to accomplish this:

    Open a terminal
    Type 'nano'
    Paste the above code in to the editor
    Control-x, Y to save
    Enter a filename (I used 'logo.sh') and enter to return to the command line
    chmod a+x logo.sh to make the script executable
    sudo ./logo.sh
    sudo reboot

No more logo after reboot for me"

--------------------------------------

I came across this program *after* I did a manual install..

It appears to be an automatic process which grabs the latest beta. might be worth checking out..

[http://sourceforge.net/projects/uaci/](http://sourceforge.net/projects/uaci/) and their website : [http://www.thefanclub.co.za/how-to/ubuntu-amd-catalyst-install](http://www.thefanclub.co.za/how-to/ubuntu-amd-catalyst-install) 

Apparently this tool 'uaci' automatically removes the watermark for you as well, I contacted them about the 10th April update, 
hopefully it won't take them long to incorporate that into their tool.

thx

---

### Post by ppjdee on 2013-04-11
> **raring said:**
> 
--------------------------------------

I came across this program *after* I did a manual install..

It appears to be an automatic process which grabs the latest beta. might be worth checking out..

[http://sourceforge.net/projects/uaci/](http://sourceforge.net/projects/uaci/) and their website : [http://www.thefanclub.co.za/how-to/ubuntu-amd-catalyst-install](http://www.thefanclub.co.za/how-to/ubuntu-amd-catalyst-install) 

Apparently this tool 'uaci' automatically removes the watermark for you as well, I contacted them about the 10th April update, 
hopefully it won't take them long to incorporate that into their tool.

thx

It sounds neat. I just did a fresh install of 13.04, so I'm going to give this a try.

---

