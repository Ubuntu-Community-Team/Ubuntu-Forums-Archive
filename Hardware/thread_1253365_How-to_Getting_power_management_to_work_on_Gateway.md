---
title: "How-to: Getting power management to work on Gateway LT31"
date: 2009-08-30
forum: Hardware
---

### Post by Prikolchik on 2009-08-30
**Introduction:**
Power management/CPU scaling does not work out of the box on Ubuntu 9.04 (as of Aug 30, 2009). Luckily for us, [Krists Krilovs]("http://www.pow.za.net/about.html") has figured out how to enable power management on Gateway LT31xx. See [here]("http://www.pow.za.net/index.html") and [here]("http://forum.notebookreview.com/showpost.php?p=5238903&postcount=217") for update. He provided patches for 
I have taken 2nd version of his patch (2nd link) and compiled a Ubuntu kernel based on [Ubuntu 2.6.30.5 linux sources]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30.5/"). (applied patches, all settings default).
This custom kernel can be easily installed on Gateway LT31xx (it may also work on other netbooks with AMD Athlon™ 64 L110 processor), which in turn enables Power management and CPU scaling features. 
The P-states for the CPU are 1200MHz@0.9V, 1100MHz@0.85V, 1000MHz@0.8V, 900MHz@0.75V, 800MHz@0.7V

[SIZE=5][COLOR=Red]Please note: USE AT YOUR OWN RISK! DO NOT PROCEED IF YOU DON'T HAVE YOUR DATA BACKED-UP.[/COLOR][/SIZE]

[SIZE=4]**How-to: Getting power management to work on Gateway LT31:**[/SIZE]
[SIZE=3]Step 1. Download pre-compiled kernel for Ubuntu 9.04:[/SIZE]

**_32-bit version:_**
[linux-image-2.6.30.5-acpifx.1_i386.deb Part 1]("http://rapidshare.com/files/272831089/linux-image-2.6.30.5-acpifx.1_i386.part1.rar")
[linux-image-2.6.30.5-acpifx.1_i386.deb Part 2]("http://rapidshare.com/files/272831518/linux-image-2.6.30.5-acpifx.1_i386.part2.rar")
[linux-headers-2.6.30.5-acpifx.1_i386.deb]("http://rapidshare.com/files/272707654/linux-headers-2.6.30.5-acpifx.1_2.6.30.5-acpifx.1-10.00.Custom_i386.deb")

**_64-bit:_**
[linux-image-2.6.30.5-acpifx.1_amd64.deb Part 1]("http://rapidshare.com/files/273524189/linux-image-2.6.30.5-acpifx.1_amd64.part1.rar")
[linux-image-2.6.30.5-acpifx.1_amd64.deb Part 2]("http://rapidshare.com/files/273523560/linux-image-2.6.30.5-acpifx.1_amd64.part2.rar")
[linux-headers-2.6.30.5-acpifx.1_amd64.deb]("http://rapidshare.com/files/273524344/linux-headers-2.6.30.5-acpifx.1_2.6.30.5-acpifx.1-10.00.Custom_amd64.deb")

[SIZE=3]Step 2. Unpacking *.rar files.[/SIZE]
If you don't have [FONT=Courier New]unrar[/FONT] installed, install it by typing in terminal:
```
sudo apt-get install unrar
```Once installation finishes, [FONT=Courier New]cd[/FONT] to the directory where you saved the *.rar files and type:
```
unrar x linux-image-*part1.rar ~/Desktop
```where [FONT=Courier New]~/Desktop[/FONT] is the directory where to place extracted files.

[SIZE=3]Step 3. Before installing the kernel.[/SIZE]
First of all, make sure you keep a working copy of the kernel (this is default, just don't delete the kernel you are using) in case new one will fail to work.
You may also optionally set a longer delay in GRUB menu by typing in terminal:
```
sudo gedit /boot/grub/menu.lst
```Find:
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3
```and change [FONT=Courier New]timeout[/FONT] value from 3 to 8 or larger if you need. Save and close.

[SIZE=3]Step 4. Installing the custom kernel.[/SIZE]
There are two ways you can go. First is GUI and second is command line.
1. GUI method. Navigate to the folder where you saved linux-header...deb file and double click on it. Click on "Install". Do same with linux-image...deb file that you extracted from *.rar files.
2. Command-line method. [FONT=Courier New]cd[/FONT] to where you saved *.deb files and type:
```
sudo dpkg -i linux-headers*.deb
sudo dpkg -i linux-image*.deb
```Wait until the process finishes. It may take a little while. :popcorn:

[SIZE=3]Step 5. Booting off new kernel.[/SIZE]
You may now restart your laptop and it should automatically boot from the new kernel.
Once laptop has finished loading open up the terminal and type:
```
uname -r
```If you see [FONT=Courier New]2.6.30.5-acpifx.1[/FONT] that means you are running on the new kernel. Congratulations! :) You can add "CPU Frequency scaling monitor" to your panel (Right click on panel -> Choose "Add to Panel" -> find "CPU Frequency..." -> select it and either drag and drop it on panel or click "Add"), so that you can manage with what speed/power settings your CPU is running.

And if you see something different, such as [FONT=Courier New]2.6.28-15-generic[/FONT] it means you are still running on your old kernel. Try restarting laptop and pressing ESC upon boot to get into GRUB menu and selecting line [FONT=Courier New]Ubuntu 9.04, kernel 2.6.30.5-acpifx.1[/FONT].

[SIZE=3]Step 6 (optional). If laptop fails to boot after kernel install.[/SIZE]
If after installing the new kernel your laptop fails to boot, you can enter GRUB menu by pressing ESC at boot and selecting to boot off a known working kernel (something that doesnt have "acpifx" or "recovery" in the name). Please report the error messages you get along with BIOS version.

[SIZE=3]Step 7 (optional). Uninstalling custom kernel.[/SIZE]
If this kernel does not work for you or you choose to remove it you can do it by typing in terminal:
```
sudo dpkg -r linux-image-2.6.30.5-acpifx.1
sudo dpkg -r linux-headers-2.6.30.5-acpifx.1
```Both 32-bit and 64-bit versions of my kernel were tested, and have fixed power management problems on my LT3110h (BIOS v1.1303).


If you have any further questions or would like to report the results, please feel free to comment!

---

### Post by Prikolchik on 2009-08-30
I would also like to mention that I have managed to successfully undervolt the AMD L110 processor in Ubuntu 9.04 by using program called [cpupowerd]("http://ubuntuforums.org/showthread.php?t=852415"). (you have to be running the custom kernel above before you can undervolt). So far I've tested 800@0.6875V and 1200@0.75V. The latter gives a very significant temperature drop. I will be writing LT31 Ubuntu undervolting guide soon.

---

### Post by Footer on 2009-08-30
Greetings and thanks for your guide.  I'm patiently waiting for the 64-bit version.  :)  I have the LT31 with BIOS v1.3201 (just picked it up on Wed. 8/26/09).  I'm running the 2.6.28-15-generic kernel at the moment and Kubuntu 9.04.  I'll let you know my results with the 64-bit after you get it up here.

One question I have is where you reference "CPU Frequency scaling monitor", those instructions appear to be for Ubuntu (Gnome), I'll find it in KDE (hopefully), but I'm wondering if you have to manually adjust the speed/power settings or does it happen automagically?  I'm hoping the latter as manually having to adjust these settings sort of defeats the purpose...?

Again, THANKS!

---

### Post by Prikolchik on 2009-08-30
64-bit version of the kernel has been uploaded.

> **Footer said:**
> One question I have is where you reference "CPU Frequency scaling monitor", those instructions appear to be for Ubuntu (Gnome), I'll find it in KDE (hopefully), but I'm wondering if you have to manually adjust the speed/power settings or does it happen automagically?  I'm hoping the latter as manually having to adjust these settings sort of defeats the purpose...?
Haha, no you don't HAVE to adjust CPU speed manually. It all happens automatically, but if you want manual control it is in CPU Frequency scaling monitor. 

I'm actually not sure that this kernel will work with any Ubuntu flavours (Kubuntu/Xubuntu, etc). I recall reading somewhere that you need to compile separately for those. I'm not 100% sure though. You can give it a try and see if it works on Kubuntu. And if it doesnt, I may look into compiling this custom kernel for all the other flavours.

---

### Post by Footer on 2009-08-31
Just got the 64-bit files downloaded.  300MB for kernel files...?  Any reason why they're so huge?  Aren't kernel files usually around 10-15MB?

I'll get to this tonight hopefully and respond here with my results (64-bit Kubuntu 9.04 on the LT31).

Thanks!

---

### Post by Footer on 2009-08-31
WHOOHOO!!!  The kernel compiled on Kubuntu 9.04 64-bit:

```

footer@netbook-pc:~$ uname -r
2.6.30.5-acpifx.1

```

One minor tweak to your instructions, Step 4, #2. the command line method.  If you do dpkg in the same directory as where your downloaded and unrar'd the files, then you should NOT do:

```
sudo dpkg -i linux-image*
```

but rather:

```
sudo dpkg -i linux-image*.deb
```

so it doesn't try to process the .rar files.  No harm done either way but it gives errors when trying to process the .rar files.

Now I guess we'll see if it actually extends the battery life!

One more thing I'd like to make happen automatically is the wi-fi connection.  I have to tweak after every reboot (go into the network settings and just open) after which it seems to work fine.  No idea what's up with that.

Thanks!

---

### Post by Prikolchik on 2009-08-31
> **Footer said:**
> Just got the 64-bit files downloaded.  300MB for kernel files...?  Any reason why they're so huge?  Aren't kernel files usually around 10-15MB?
It is not just kernel. It also includes all the drivers, modules, etc. You could double click on .deb file, go over to "Included files" and see what the package includes. Or in terminal type [FONT="Courier New"]dpkg -c linux-image*.deb | more[/FONT]
Nevertheless, it is a good question, but I'm afraid I don't know the answer.

> **Footer said:**
> One minor tweak to your instructions...

```
sudo dpkg -i linux-image*.deb
```
...
One more thing I'd like to make happen automatically is the wi-fi connection.  I have to tweak after every reboot (go into the network settings and just open) after which it seems to work fine.  No idea what's up with that.
I'm very glad it worked for you. I hope you'll enjoy it as much as I did :)
Oops, you are right about the tweak. My bad.
I'm afraid I'm not the right person to ask about the WiFi. As far as I know, the drives for LT31 wireless card were written by Madwifi/ath5k team (I can't remember which). Perhaps you should file a bug report/contact them? You could find out which driver it is exactly by typing [FONT="Courier New"]lspci -k[/FONT] and look for [FONT="Courier New"]Network controller[/FONT]. You will have driver and module names there.

I've actually returned my LT3110h back to the store today. I bought Acer Aspire 1410-8837 netbook instead. For $50 more I get more cpu/vid/ram/hdd/batt + everything works out of the box (except LAN). Let's just hope next week's flyer won't bring me back to the store returning this and getting some other newer model :)

---

### Post by skipstone on 2009-09-01
I have the Gateway netbook and mostly happy with it.
I ended up on Koala alpha 1 in July - installed 9.04 from my USB drive
but wireless did not work so I dist-upgraded and wireless worked.
Power management is not working. I have read Koala does not support
DSDT changes .. so what is the plan for Koala power management and
when do I "update" from alpha-1? Or, do I need to figure out how to
move back to Jaunty and do the DSDT update?
thanks!

---

### Post by Prikolchik on 2009-09-01
> **skipstone said:**
> I have the Gateway netbook and mostly happy with it.
I ended up on Koala alpha 1 in July - installed 9.04 from my USB drive but wireless did not work so I dist-upgraded and wireless worked.
Power management is not working. I have read Koala does not support DSDT changes .. so what is the plan for Koala power management and when do I "update" from alpha-1? Or, do I need to figure out how to move back to Jaunty and do the DSDT update?
thanks!
The easiest for you would probably be to reinstall Ubuntu 9.04 and install the linux-backports ```
sudo apt-get install linux-backports-modules-jaunty
```, which should enable your WiFi. Then you can simply download and install the kernel above. This will leave you with working power management and WiFi.

---

### Post by Footer on 2009-09-01
> **Prikolchik said:**
> 
I've actually returned my LT3110h back to the store today. I bought Acer Aspire 1410-8837 netbook instead. For $50 more I get more cpu/vid/ram/hdd/batt + everything works out of the box (except LAN). Let's just hope next week's flyer won't bring me back to the store returning this and getting some other newer model :)


Thanks again for your how to and info.  Sorry to hear your LT31 didn't work out for you.  The Acer Aspire 1410 comes with an Intel processor I presume?  Probably the reason everything works out of the box.  I'm an AMD fan so sticking with it for now.  I just hope that Gateway (Acer) comes out with a BIOS update or the power mgmt. gets supported down the road so this manual tweaking is not required.  But I'm very glad you took the time to figure it out in the mean time!

Thanks again!

---

### Post by npath on 2009-09-01
I just registered to thank Prikolchik and Krists Krilovs for your excellent work on getting power management set up on the LT3103u.  This is a great little computer, and now is much better with CPU scaling.  I am getting a solid 4-5 hours with active use, which is much better than before.  I only hope these changes get incorporated officially into the kernel just in case you guys aren't available to help with the next Ubuntu update.  I may have to figure out how to do this myself.  Thanks again!

---

### Post by omniuni on 2009-09-01
Hi!

I tried recompiling my own kernel with the patch, and that did not go very well. I'm trying to download the kernel parts now. Rapidshare is quite annoying. I'm going to post links to the kernel on my own server. It's just a box sitting in my room, but the university has a rather epic Internet, so speed should be much better than Rapidshare. That said, perhaps we could find some better options for hosting these files, like Box? There's no guarantee that my server will always be up, although I do the best I can.

---

### Post by omniuni on 2009-09-02
Wonderful!

CPU Frequency Scaling is working.

It doesn't really like changing frequencies, and occasionally freezes the machine if it enters the wrong mode, but generally, it is working quite well. Powertop is giving me 3.7-4.1 hours of estimated battery life, without any additional optimizations.

Dimming my screen a bit improves this quite a bit more. I'm now up to 4.3 hours.

[COLOR="Red"]Dynamic (Conservative) seems to be the problematic mode.[/COLOR] I'll get the .deb's on my server ASAP, so they'll be easier to download.

Correction. I think the instability I have with the kernel is due to my graphics driver. I am using the *radeon* driver from xorg-edgers to keep 3D working. I do not think the patch is actually at fault for the freezes I was having, rather, something in the kernel was conflicting with the drivers.


[ATTACH]127126[/ATTACH]

---

### Post by gtwy on 2009-09-03
Hey thanks. I will give this a shot.

In the meanwhile, does "**Hibernate**" work on the LT3103 for any of you?  :confused: On Ubuntu 9.04 I try setting mine to hibernate but it returns back to the desktop after blanking out for a couple of seconds. 

For now, I set the lid close action to "**Standby**" as a resort ... until I figure out why hibernation doesn't work correctly. Any ideas?

---

### Post by wermerskoch on 2009-09-03
Thanks for this!  I am having the same issue as omniuni -- it seems to freeze every now and then.
omniuni:  which graphics driver did you end up using to remedy this?

---

### Post by omniuni on 2009-09-03
wermerskoch, I'm glad to hear I'm not the only one. Unfortunately, I have not been able to remedy it yet. I think that disabling hardware acceleration would do it, because disabling desktop effects causes the crash to happen much more rarely. I was figuring it was due to my using xorg-edgers repository (which fixes the graphics bugs when enabling KWin effects).

What video driver are you using? Do you think it's a bug with the 2.6.30 kernel, or with the patch? Currently, I'm leaning towards the kernel being the problem, because the frequency scaling, after observing half a dozen crashes, seems to work fine, and NOT be related to when the interface freezes. Also, no blinking caps-lock seems to indicate that it is NOT a kernel panic, and yet Magic keys don't work either!

Perhaps we could convince Prikolchik to try compiling against the 2.6.30-10.12 sources as used in the xorg-edgers repository? I had good luck with this kernel (though, of course, it lacked frequency scaling).

---

### Post by Prikolchik on 2009-09-03
> **wermerskoch said:**
> Thanks for this!  I am having the same issue as omniuni -- it seems to freeze every now and then.
Hmm, I did not have absolutely any freezes. I used the stock driver, i.e. whatever came with Ubuntu installation. Also, I was using Compiz (with custom CCSM settings to disable some animations) for desktop effects.

> **omniuni said:**
> Perhaps we could convince Prikolchik to try compiling against the 2.6.30-10.12 sources as used in the xorg-edgers repository? I had good luck with this kernel (though, of course, it lacked frequency scaling).
Well, since I no longer have my Gateway compiling would be a little problematic. If you really want, you can compile it yourself. Here is what you need:
[Compiling kernel instructions]("http://easylinuxcds.com/blog/?p=3244"). The only thing you change there is you dont need to install linux-sources (you download them from wherever). And you dont need to copy .config files. Also you may want to avoid turning off/enabling options in kernel config if you don't know what you are doing.

[Get .diff file here]("http://forum.notebookreview.com/showpost.php?p=5238903&postcount=217")
[dsdt.hex]("http://www.pow.za.net/dsdt.hex.txt") here

Apply .diff file by [FONT="Courier New"]cd[/FONT]'ing to linux kernel source dir and typing ```
sudo patch -p0 < powernow-k8.diff
``` 
Instructions for [incorporating your new DSDT into the kernel]("http://www.gentoo-wiki.info/ACPI/Fix_common_problems#3._Build-in_Options_for_Kernel_2.6.9_and_Later")

That is all I used to compile my kernels. Should take you less than 30mins to figure it all out! Cheers!

---

### Post by wermerskoch on 2009-09-03
Well I'm not so convinced it's the graphics driver now...  I tried updating to the 9.4 ati drivers that were released recently (the ones that are supposedly compatible with Ubuntu 9.04).  I had issues, and wound up removing and purging all ATI drivers of any sort.  Booting up in pure software rendering with the new kernel still produced the freezing.  But it doesn't seem to freeze if you manually set the CPU frequency -- only if you have it set to some auto-switching mode.  

  Could someone who doesn't have any freezing issues post what version their bios is?  I know with the newer models (or rather more recently manufactured) that have a more recent bios version (which I have) have some acpi issues with 9.04.  I wasn't able to boot into the install disc at all, and had to install 8.10 and do a dist-upgrade to 9.04.  I wonder if these are two symptoms of the same issue...

---

### Post by omniuni on 2009-09-03
Ah,

First, the latest ATI drivers don't support the card. The open source radeon driver works very well, though. To get full 3D support, enable the xorg-edgers PPA:

[https://launchpad.net/~xorg-edgers](https://launchpad.net/~xorg-edgers)

(Oddly enough, this works extremely well.)


So if it works to manually set the clock speed, why is it not able to have a program set it? Seems odd to me.

Anyway, should be fine once it gets into the kernel. Oh, and in response to the question about hibernation, I just tested it, and it seems to work just fine for me.

---

### Post by coverYourTracks on 2009-09-03
a

---

### Post by npath on 2009-09-04
My system also kept freezing with the patched kernel.  I am glad to know that it is not only me.  I was actually blaming Skype until I rechecked this thread.  Hopefully we can figure out how to make this stable.  I was getting around 30-45 minutes more on battery life with CPU scaling.  Had to go back to the original kernel for now.

---

### Post by AutoStatic on 2009-09-12
Hello, I just got myself a Packard Bell dot 202 and apparently it's the same machine as the Gateway LT3103u. I've compiled a new kernel with the patch and the DSDT file. It should be identical to Prikolchik's version. You can find it here: [http://linux.autostatic.com/ubuntu/](http://linux.autostatic.com/ubuntu/)
I've also made a checkinstall package of cpupowerd, it's in the same directory.
Any questions, don't hesitate to ask, and I'm keeping this netbook, don't plan on returning it.

Jeremy

Edit Sep 24 2009: compiled kernel 2.6.30.6 with powernow-k8 patch and DSDT file. Also stripped the kernel config specifically for the Gateway LT3103u/Packard Bell dot m/a.NL/202. Use at your own risk and please let me know if you experience any lockups or if you need extra modules/functionality.

---

### Post by malevolentjelly on 2009-09-25
AutoStatic: The kernel works fine for the power management and such on my Gateway LT3103u, but I couldn't help but notice my webcam no longer works. Did you not include the drivers for webcams in your kernel?

---

### Post by AutoStatic on 2009-09-26
Good point! I'll check it this weekend and recompile. I don't use the webcam myself so I probably omitted the needed modules.
I'd like to point out though that the lt3103u does not really like frequency scaling, I've compiled several kernels but the little fellow keeps locking up every now and then when frequency scaling is enabled.
With cpupowerd I do manage to get as low as 0.6625 V. Saves a few tenths of Watts.

PS, I'm going to do it tomorrow, I'm in the middle of a renovation and all...

Edit: compiled two new kernels with webcam support (hopefully I picked the right drivers), 2.6.30.6 and 2.6.31, and moved the debs to a faster server.

Edit II: webcam works, tested it with cheese. Also no lock ups until now with the 2.6.31 kernel.

---

### Post by Turmlos on 2009-09-29
> **AutoStatic said:**
> I'd like to point out though that the lt3103u does not really like frequency scaling, I've compiled several kernels but the little fellow keeps locking up every now and then when frequency scaling is enabled.
Regarding the lockups, you might want to see my last two posts here:

[http://forum.notebookreview.com/showthread.php?t=393200&page=24](http://forum.notebookreview.com/showthread.php?t=393200&page=24)

---

### Post by AutoStatic on 2009-09-30
Hello Turmlos, I will check what clock generator is inside my Packard Bell. It will probably be the SLG84605. But then I'll have to install Windows first and run SetFSB then. Or maybe it will run with Windows PE (BartPE).
But does frequency scaling work well with this clock generator under Windows? Or does it lock up too?

---

### Post by Turmlos on 2009-09-30
> **AutoStatic said:**
> But does frequency scaling work well with this clock generator under Windows? Or does it lock up too?
Unfortunately, no.  It locks up under Windows as well, regardless of the method used (DSDT override or RMClock).

---

### Post by AutoStatic on 2009-10-01
I've checked the clock generator and it is indeed the "wrong" one. I'm going to contact Packard Bell to find out if they could replace my notebook. I'd like to get the most out of it without lock ups.

---

### Post by malevolentjelly on 2009-10-06
I am not sure what the nature of patching we're doing on the kernel is here, but is there are any plans for these DSDT hacks to be merged into the mainline kernel? Doesn't the linux kernel carry around a big bag of ACPI hacks? When will our ACPI hacks be included?

---

### Post by Footer on 2009-10-06
I agree.  I want to go to 9.10 as soon as it comes out but I still want the power management to work.  Will it?

Thanks.

---

### Post by diffy on 2009-10-06
I'veI just installed the 9.10 Beta and by default the power management dosen't work

Diffy

---

### Post by malevolentjelly on 2009-10-06
Also: Is there a kernel independent way of solving this issue, like injecting DSDT tables at boot or something?-- or does it go beyond that?

If this solution isn't going into the mainline kernel, we'll eventually need to figure out a solution that allows us to use the mainstream ubuntu kernel.

Also: is there any reason the kernel provided here wouldn't work in Karmic?

---

### Post by AutoStatic on 2009-10-06
Karmic has a 2.6.30 kernel right? This kernel does not allow to add custom DSDT's to your initramfs. But it does allow to add a custom DSDT to your kernel config. That's what I've been doing all the way. And together with the powernow-k8 patch this allows for CPU scaling on the lt3103u. And where it is heading, well part of the powernow-k8 patch has been added to the 2.6.31 branch but not all (that's where the powernow-k8-git patch is for, used that one for my 2.6.31 kernel), but when it comes to adding custom DSDT's, only OpenSuSE still allows for adding them to your initramfs, with all other distro's you have to compile a kernel yourself. The kernel devs are apparently going to work around all those buggy DSDT tables.
I haven't tested my kernels on Karmic, I don't use Karmic as long as it's not officially released. You could try though, but chances are things won't work (different libc version etc.). As soon as Karmic is officially released and a [debootstrap deb]("http://archive.ubuntu.com/ubuntu/pool/main/d/debootstrap/") for Karmic is available I will compile a Karmic specific kernel.

---

### Post by spaceballl on 2009-11-12
It has been about a month since the last post on this thread. Just got a great deal on one of these from Woot... I really would love to run Karmic on it. Does Karmic fix any of the problems that people with 9.04 had?

---

### Post by omniuni on 2009-11-12
Hi,

I left the Gateway for an MSI Wind, but based on what Karmic has, the default install will work very well with the hardware, including wireless, but without CPU frequency scaling, taking your battery life to under 3 hours.

If you want frequency scaling, you'll need to try some of the experimental kernels or patches posted here.

---

### Post by spaceballl on 2009-11-12
> **omniuni said:**
> Hi,

I left the Gateway for an MSI Wind, but based on what Karmic has, the default install will work very well with the hardware, including wireless, but without CPU frequency scaling, taking your battery life to under 3 hours.

If you want frequency scaling, you'll need to try some of the experimental kernels or patches posted here.
Okay cool - but if that doesn't bother me, and I just want a computer working with wifi out of the box, Karmic will get the job done? Thanks!

---

### Post by omniuni on 2009-11-13
Correct.

The ATi Video card is supported well by the open source driver (I ran desktop cube just fine), the sound, webcam, etc. all work. The wireless simply needed the backported drivers from Karmic to work on Jaunty, so I have every reason to expect that they should work out of the box with the Karmic final release. It's a good computer, really, I just needed something with a bit more battery life, and I did not like the idea of a buggy BIOS. Construction is good, speakers perform well for a machine that size, and with the 6-cell battery, you'll still get good enough battery life for it to not be too bad. The AMD processor, of course, makes it feel more like a laptop than a netbook in terms of performance, and you can even run a virtual machine pretty well.

Good luck, and enjoy the computer!

---

### Post by spaceballl on 2009-11-13
> **omniuni said:**
> Correct.

The ATi Video card is supported well by the open source driver (I ran desktop cube just fine), the sound, webcam, etc. all work. The wireless simply needed the backported drivers from Karmic to work on Jaunty, so I have every reason to expect that they should work out of the box with the Karmic final release. It's a good computer, really, I just needed something with a bit more battery life, and I did not like the idea of a buggy BIOS. Construction is good, speakers perform well for a machine that size, and with the 6-cell battery, you'll still get good enough battery life for it to not be too bad. The AMD processor, of course, makes it feel more like a laptop than a netbook in terms of performance, and you can even run a virtual machine pretty well.

Good luck, and enjoy the computer!
Great! Thanks so much for the response. Maybe by the time my brother gets the computer at the end of December, the CPU scaling will be supported out of the box. Thanks!

---

### Post by cyberey66 on 2009-11-19
If anyone can upload the kernel to a server, I would appreciate it.  Rapidshare is annoying.  

I can also stick the kernel on my server for a while if anyone else needs it after me.

---

### Post by spaceballl on 2009-11-19
Is it possible that the power management modifications will get merged back into the kernel? I'm hoping that the next kernel might natively support this. Would be easier for everyone.

---

### Post by Turmlos on 2009-11-19
> **spaceballl said:**
> Is it possible that the power management modifications will get merged back into the kernel? I'm hoping that the next kernel might natively support this. Would be easier for everyone.
No.  DSDT tables overrides are not supported by the kernel developers, and actually taint the kernel.  Their view is "DSDT modification is for debugging and development only. Supported systems should run ONLY the DSDT supplied by the platform vendor."  This is for good reason.  Changing the system configuration (adding more RAM) and/or modifying certain BIOS settings can affect the stock DSDT table.  If one fails to update the DSDT used in the override accordingly, the result can be an unusable system.

---

### Post by cyberey66 on 2009-11-20
Thanks for posting your compiled kernel.  My netbook is working very well now!  Everything on it works, including the mic and frequency scaling.

If anyone is having trouble downloading from rapidshare, shoot me a pm and I might be able to put up the kernel for you to download.

---

### Post by antonikus on 2009-11-22
> **omniuni said:**
> Wonderful!

CPU Frequency Scaling is working.

It doesn't really like changing frequencies, and occasionally freezes the machine if it enters the wrong mode, but generally, it is working quite well. Powertop is giving me 3.7-4.1 hours of estimated battery life, without any additional optimizations.

Dimming my screen a bit improves this quite a bit more. I'm now up to 4.3 hours.

[COLOR=Red]Dynamic (Conservative) seems to be the problematic mode.[/COLOR] I'll get the .deb's on my server ASAP, so they'll be easier to download.

Correction. I think the instability I have with the kernel is due to my graphics driver. I am using the *radeon* driver from xorg-edgers to keep 3D working. I do not think the patch is actually at fault for the freezes I was having, rather, something in the kernel was conflicting with the drivers.


[ATTACH]127126[/ATTACH]
Same here, it freezes over like hell.
It is not a graphics driver problem, for me it happens when no x is running.

---

### Post by antonikus on 2009-11-22
I "fixed" it by using the userspace governor and chacking the frequency myself with simple echo "1200000" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_setspeed 

still dissapointed it doesnt work out of the box. 
Compiz fusion works good thou, just need to disable kms by passing radeon.modeset=0 on bootline.

note: this is the same laptop as packard bell dot m nc900. (which is actually an acer)

---

### Post by cyberey66 on 2009-11-23
Has anyone tried recompiling the karmic kernel?  Can we use a custom DSDT?  Some people say we can't and some say we can.

---

### Post by cyberey66 on 2009-11-26
From what I understand the patch does not work with 2.6.31.  The only distribution working on a patch for 2.6.31 is suse.  Hopefully a patch will be made for 2.6.31 and all of us that need to use a fixed DSDT file can upgrade.

---

### Post by cyberey66 on 2009-11-29
Well I went ahead and compiled the 2.6.31 kernel from the Karmic repositories and included the corrected DSDT file.  So far, it works great.  If you just install the kernel source from the Karmic repositories and run xconfig or menuconfig, you can point it to the correct DSDT file in the ACPI section.

It's a shame there is no patch to dynamically load the DSDT in the 2.6.31 kernel, but the static method still works and is easy with xconfig.

If there is any need for it, I can make a step-by-step how to for all of us with buggy DSDTs that want to run Karmic with the DSDT override.

---

### Post by spaceballl on 2009-11-29
> **cyberey66 said:**
> If there is any need for it, I can make a step-by-step how to for all of us with buggy DSDTs that want to run Karmic with the DSDT override.
I would love that. So to be clear, a default Karmic install will work like a charm with this laptop, minus the power configuration stuff. That requires a custom kernel compile.

Would be nice if we could write a script to do this. Maybe your step-by-step will help. I assume as new kernels are released, the old ones will no longer be in use, and thus no more power management.

---

### Post by cyberey66 on 2009-11-29
> **spaceballl said:**
> I would love that. So to be clear, a default Karmic install will work like a charm with this laptop, minus the power configuration stuff. That requires a custom kernel compile.

Would be nice if we could write a script to do this. Maybe your step-by-step will help. I assume as new kernels are released, the old ones will no longer be in use, and thus no more power management.

Yes, but for each new kernel you should be able to update the source package and compile the new one using the same exact steps.  It might seem tedious to have to compile each new kernel, but its not too bad.  In reality it comes down to just copy and pasting a few lines in the terminal.

I'll go ahead and write a step by step when I have the free time.

---

### Post by Footer on 2009-11-29
> I'll go ahead and write a step by step when I have the free time.

I'd like to cast my vote for this too.  I'm itching to upgrade my LT31 to 9.10 but don't want to lose the power management.

Thanks!

---

### Post by cyberey66 on 2009-11-29
I posted a general thread on how to use a custom DSDT here:

[http://ubuntuforums.org/showthread.php?p=8411199](http://ubuntuforums.org/showthread.php?p=8411199)

Note that for the LT31 your must apply the powernow patch!   I will post the patch I used for the 2.6.31-15.50 kernel:

Use this kernel:
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-source-2.6.31_2.6.31-15.50_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-source-2.6.31_2.6.31-15.50_all.deb)

and use this patch:
[http://people.virginia.edu/~mc8qr/powernow-k8.diff](http://people.virginia.edu/~mc8qr/powernow-k8.diff)

When you follow my guide copy powernow-k8.diff to the ~/src/linux-source-2.6.31/ directory.

If there are problems, let me know.  I am running karmic after following those steps.  I wrote them afterwards though, so if I missed something, please let me know.

---

### Post by ssorgatem on 2009-12-13
Friday I bought a Packard-bell dot mr/a.sp/134, wich seems to be the same machine. The dsdt was slightly different from the Gateway's one, but it could be because it came with bluetooth and 2Gb of ram.

I applied the changes to the dsdt, compiled it, and then compiled a custom kernel 2.6.32 with it and... it works! I haven't experiencied any freezes so far... 

Now I would like an explained way to undervolt it, or a recommended cpupowerd configuration :)

---

### Post by Turmlos on 2009-12-14
> **ssorgatem said:**
> Now I would like an explained way to undervolt it, or a recommended cpupowerd configuration :)
The cpupowerd README file is very helpful, you may want to take a look at that. ;)

You could also try the [linux-phc phc-k8 module](http://linux-phc.org/forum/viewtopic.php?f=13&t=2).  This is what I've been using.

---

### Post by AutoStatic on 2010-01-08
> **AutoStatic said:**
> Good point! I'll check it this weekend and recompile. I don't use the webcam myself so I probably omitted the needed modules.
I'd like to point out though that the lt3103u does not really like frequency scaling, I've compiled several kernels but the little fellow keeps locking up every now and then when frequency scaling is enabled.
With cpupowerd I do manage to get as low as 0.6625 V. Saves a few tenths of Watts.

PS, I'm going to do it tomorrow, I'm in the middle of a renovation and all...

Edit: compiled two new kernels with webcam support (hopefully I picked the right drivers), 2.6.30.6 and 2.6.31, and moved the debs to a faster server.

Edit II: webcam works, tested it with cheese. Also no lock ups until now with the 2.6.31 kernel.

I've compiled a new kernel for Jaunty 9.04 64bits:
[http://linux.autostatic.com/ubuntu/linux-image-2.6.31-acpifix2_amd64.deb](http://linux.autostatic.com/ubuntu/linux-image-2.6.31-acpifix2_amd64.deb)
[http://linux.autostatic.com/ubuntu/linux-headers-2.6.31-acpifix2_amd64.deb](http://linux.autostatic.com/ubuntu/linux-headers-2.6.31-acpifix2_amd64.deb)

This kernel is not stripped down like my previous one so everything should work.

Best,

Jeremy

---

### Post by Footer on 2010-01-09
> **AutoStatic said:**
> I've compiled a new kernel for Jaunty 9.04 64bits:
[http://linux.autostatic.com/ubuntu/linux-image-2.6.31-acpifix2_amd64.deb](http://linux.autostatic.com/ubuntu/linux-image-2.6.31-acpifix2_amd64.deb)
[http://linux.autostatic.com/ubuntu/linux-headers-2.6.31-acpifix2_amd64.deb](http://linux.autostatic.com/ubuntu/linux-headers-2.6.31-acpifix2_amd64.deb)

This kernel is not stripped down like my previous one so everything should work.

Best,

Jeremy

Thanks Jeremy.  I just updated my LT31 using your kernel files and it works perfectly.  I've been toying with the idea of going to 9.10 but so far, it seems like too much trouble. 

Also, I've been running 9.10 on my desktop since it was officially released and I'm less than thrilled with the new grub.  So I'm not so sure I really want to go to 9.10 on the LT31!

Thanks again for your kernel files.

:)

---

### Post by Footer on 2010-01-10
> **Footer said:**
> Thanks Jeremy.  I just updated my LT31 using your kernel files and it works perfectly.

Well, I think I spoke too soon!  After working with the new kernel a bit, my wireless gets dropped.  It worked perfectly under the previous kernel (2.6.30.5-acpifx.1) which the OP provides instructions for installing in this thread.

I installed that back in late August and didn't experience any wireless drops.  So the new kernel is the only update I've done since then.

Is wireless working for you with the new kernel?

Thanks!

---

### Post by Footer on 2010-04-07
Anyone tried Kubuntu 10.04 on their LT31 yet?  I see it's coming with the 2.6.32 kernel ... So I wonder if power management and WiFi will work 'out of the box'?  The netbook remix screenshot looks pretty sweet:

[https://wiki.kubuntu.org/LucidLynx/Beta1/Kubuntu#Official%20Kubuntu%20Netbook%20release](https://wiki.kubuntu.org/LucidLynx/Beta1/Kubuntu#Official%20Kubuntu%20Netbook%20release)

I'm thinking about giving this a try sooner than later.  If so, I'll report back here with my results.  Don't know if I can wait for the final in a few weeks or not!

Thanks.

---

### Post by Footer on 2010-04-11
I've got Kubuntu 10.04 Beta 2 (64-bit PC AMD64 desktop version) running on my LT31.  Just one tweak to get the video working correctly.  Had to add radeon.modeset=0 to the grub parameters.  Otherwise the video was very flaky.  Thanks to the forums here for solving that problem!

I'm not sure if power management is working but I've had it running for about an hour and still have 64% battery life.  The wireless seems to be working fine so far.

I tried the netbook edition but it's only for x86 and I wanted to go 64-bit so decided against it.  10.04 seems much more polished at this point.  And KDE4 is maturing as well, lots of widgets to explore!

I'd say go for it if you're thinking about going to 10.04 on your LT31!

:)

---

### Post by s.mulleady1122 on 2010-05-13
I compiled a new kernel based on the latest ubuntu source files using cyberey66's guide! 

[http://www.zshare.net/download/76287458e51a5c06/](http://www.zshare.net/download/76287458e51a5c06/)

I'm using 10.04 and all is well. Here are the files and some instructions

If using Ubuntu 10.04 then you have to copy these files as the script isn't automatically run anymore

```
sudo cp /usr/share/doc/kernel-package/examples/etc/kernel/postinst.d/initramfs /etc/kernel/postinst.d/initramfs
sudo cp /usr/share/doc/kernel-package/examples/etc/kernel/postrm.d/initramfs /etc/kernel/postrm.d/initramfs
```

(If you get an error, than make the directories)

Delete the nvidia-common file located in /etc/kernel/postinst.d

If using 9.10 start here

Go do the directory of the deb files and install
```
sudo dpkg -i linux-image-2.6.32.11_2.6.32.11-10.00.Custom_i386.deb
sudo dpkg -i linux-headers-2.6.32.11_2.6.32.11-10.00.Custom_i386.deb
```

install Powernowd (The best daemon to use, sets it to on demand at the lowest freq and dynamically sets it up)

```
sudo apt-get install powernowd
```

Restart

Enjoy Frequency scaling on Ubuntu 10.04 and 9.10!

---

### Post by Footer on 2010-05-25
Any chance you're going to build a custom kernel to support frequency scaling and power mgmt for the x86_64 architecture?  I'm currently running this kernel:

2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

and it doesn't support scaling natively.

Thanks!

---

### Post by s.mulleady1122 on 2010-05-26
> **Footer said:**
> Any chance you're going to build a custom kernel to support frequency scaling and power mgmt for the x86_64 architecture?  I'm currently running this kernel:

2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

and it doesn't support scaling natively.

Thanks!
Probably not, I'd recommend sticking with 32 bit, or either compiling the kernel yourself. (Its very simple, it just takes a hour or so)

---

### Post by s.mulleady1122 on 2010-05-26
Compiled a new one on the 2.6.34 sources. I've had multiple problems with screen tearing with compositing. The latest DRM in this kernel works wonders with the x1270 in the Gateway. Plus I get less wireless drops.


[2.6.34]("http://www.zshare.net/download/76557182277d798f/")

---

### Post by ssorgatem on 2010-06-12
I've managed to modify the BIOS and put in it the fixed dsdt table, so no more custom kernels are needed!

My model is a Packard-Bell dot m/a, the BIOS version I hacked is 1.3302.

With this BIOS mod, cpu freq scaling works in ***any*** OS 

If you're interested in testing my modified BIOS in your Gateways/P-Bs, send me an email to ssorgatem at gmail

---

### Post by gtwy on 2010-06-14
> **ssorgatem said:**
> I've managed to modify the BIOS and put in it the fixed dsdt table, so no more custom kernels are needed!

My model is a Packard-Bell dot m/a, the BIOS version I hacked is 1.3302.

With this BIOS mod, cpu freq scaling works in ***any*** OS 

If you're interested in testing my modified BIOS in your Gateways/P-Bs, send me an email to ssorgatem at gmail

Can you please describe or post the instructions somewhere, about how you modified the BIOS. I have a similar model - Gateway LT 3103u. Thanks in advance.

---

### Post by cyberey66 on 2010-06-15
> **ssorgatem said:**
> I've managed to modify the BIOS and put in it the fixed dsdt table, so no more custom kernels are needed!

My model is a Packard-Bell dot m/a, the BIOS version I hacked is 1.3302.

With this BIOS mod, cpu freq scaling works in ***any*** OS 

If you're interested in testing my modified BIOS in your Gateways/P-Bs, send me an email to ssorgatem at gmail

I flashed my gateway LT3103u bios with your hacked version.  It still does not allow CPU scaling using the stock 2.6.31 ubuntu kernel.

The DSDT dumped from the BIOS gives an error when trying to compile,

> 1: ACPITB)
Error    4095 -              ^ syntax error, unexpected PARSEOP_NAMESEG, expecting PARSEOP_DEFINITIONBLOCKIf you can give some insight as to how you hacked the BIOS, it would be of much help.

---

### Post by ssorgatem on 2010-06-15
In order to mod the BIOS you need:

0- The desired DSDT.dsl file, formatted with DOS line endings (CR-LF)

1- The original BIOS file (probably BIOS1.WPH)

2- Phoenix BIOS editor Pro 2.1 or higher (a.k.a. Intel BIOS Logo editor, downloadable free of charge from intel)

3- Microsoft's ASL compiler version 3 (downloadable from microsoft)

4- Visual Basic 6 runtime (if you're running them in wine; "winetricks vb6run" will do the job if you have winetricks installed).

Steps:

1- Install the BIOS editor and (if necessary) visual basic 6 runtime.

2- Install MS ASL compiler.

3- Copy asl.exe to the BIOS editor program folder, that is, in the same folder as BIOSEDIT.EXE

4- Open the BIOS editor, open your BIOS1.WPH file, and then open the ACPI editor. The DSDT of the BIOS will show up. Select all and erase it all.

5- Open in notepad your custom DSDT.DSL file, select all, copy and then paste into the ACPI editor

6- Build your BIOS and then save it to somewhere.

7- Flash your newly created BIOS, from windows using WinPhlash, or from FreeDOS using PHLASH16.EXE.




People have reported success and working CPU scaling on LT31's with the dot MA BIOS. It's strange it's not your case... Are you sure that you correctly flashed the BIOS?

In the BIOS editor other thingss can be edited: default settings (only the already visible), menu strings and splashscreen images.

---

### Post by cyberey66 on 2010-06-15
> **ssorgatem said:**
> In order to mod the BIOS you need:

0- The desired DSDT.dsl file, formatted with DOS line endings (CR-LF)

1- The original BIOS file (probably BIOS1.WPH)

2- Phoenix BIOS editor Pro 2.1 or higher (a.k.a. Intel BIOS Logo editor, downloadable free of charge from intel)

3- Microsoft's ASL compiler version 3 (downloadable from microsoft)

4- Visual Basic 6 runtime (if you're running them in wine; "winetricks vb6run" will do the job if you have winetricks installed).

Steps:

1- Install the BIOS editor and (if necessary) visual basic 6 runtime.

2- Install MS ASL compiler.

3- Copy asl.exe to the BIOS editor program folder, that is, in the same folder as BIOSEDIT.EXE

4- Open the BIOS editor, open your BIOS1.WPH file, and then open the ACPI editor. The DSDT of the BIOS will show up. Select all and erase it all.

5- Open in notepad your custom DSDT.DSL file, select all, copy and then paste into the ACPI editor

6- Build your BIOS and then save it to somewhere.

7- Flash your newly created BIOS, from windows using WinPhlash, or from FreeDOS using PHLASH16.EXE.




People have reported success and working CPU scaling on LT31's with the dot MA BIOS. It's strange it's not your case... Are you sure that you correctly flashed the BIOS?

In the BIOS editor other thingss can be edited: default settings (only the already visible), menu strings and splashscreen images.

Thank you very much!  If I have time this week, I will try this with the modified DSDT I am currently using.

---

### Post by Turmlos on 2010-06-15
CPU scaling will not work on this processor under Linux without modifying the powernow-k8 code.  The kernel developers are actually doing 'the right thing' here and following official documentation.  As with the DSDT override method, you still need to either patch powernow-k8 or compile/install the phc-k8 module and load it with the direct_transitions parameter.

---

### Post by ssorgatem on 2010-06-15
> **Turmlos said:**
> CPU scaling will not work on this processor under Linux without modifying the powernow-k8 code.  The kernel developers are actually doing 'the right thing' here and following official documentation.  As with the DSDT override method, you still need to either patch powernow-k8 or compile/install the phc-k8 module and load it with the direct_transitions parameter.

True, I didn't remember that...

But 2.6.31 i pretty old now. which kernel verion uses lucid?

I didn't have to patch 2.6.33 or 2.6.34 in order to get cpu scaling -- I'm not sure about 2.6.32 though. 

It seems that the patches for powernow-k8 were merged mainstream semewhere between 2.6.32 and 2.6.33.

---

### Post by spaceballl on 2010-06-16
> **ssorgatem said:**
> True, I didn't remember that...

But 2.6.31 i pretty old now. which kernel verion uses lucid?

I didn't have to patch 2.6.33 or 2.6.34 in order to get cpu scaling -- I'm not sure about 2.6.32 though. 

It seems that the patches for powernow-k8 were merged mainstream semewhere between 2.6.32 and 2.6.33.
Is this true?? Will the most recent version of ubuntu w/ the most recent kernel "just work" with this AMD cpu!?

---

### Post by ssorgatem on 2010-06-16
> **spaceballl said:**
> Is this true?? Will the most recent version of ubuntu w/ the most recent kernel "just work" with this AMD cpu!?

If you use a fixed BIOS, yes

---

### Post by gtwy on 2010-06-18
> **ssorgatem said:**
> In order to mod the BIOS you need:

0- The desired DSDT.dsl file, formatted with DOS line endings (CR-LF)

1- The original BIOS file (probably BIOS1.WPH)

2- Phoenix BIOS editor Pro 2.1 or higher (a.k.a. Intel BIOS Logo editor, downloadable free of charge from intel)

3- Microsoft's ASL compiler version 3 (downloadable from microsoft)

4- Visual Basic 6 runtime (if you're running them in wine; "winetricks vb6run" will do the job if you have winetricks installed).

Steps:

1- Install the BIOS editor and (if necessary) visual basic 6 runtime.

2- Install MS ASL compiler.

3- Copy asl.exe to the BIOS editor program folder, that is, in the same folder as BIOSEDIT.EXE

4- Open the BIOS editor, open your BIOS1.WPH file, and then open the ACPI editor. The DSDT of the BIOS will show up. Select all and erase it all.

5- Open in notepad your custom DSDT.DSL file, select all, copy and then paste into the ACPI editor

6- Build your BIOS and then save it to somewhere.

7- Flash your newly created BIOS, from windows using WinPhlash, or from FreeDOS using PHLASH16.EXE.

Thank you very much for posting this information. Every CPU has different tolerance levels when undervolted but I have been using the following settings successfully for almost a year now on my Gateway LT3103u.

Can you please confirm the voltages you have compiled into your BIOS DSDT? These are what I use in RMClock: 

[[IMG]http://img714.imageshack.us/img714/766/gatewaylt3103ucpuprofil.png[/IMG]](http://img714.imageshack.us/i/gatewaylt3103ucpuprofil.png/)

If no, I may have to tread the dangerous path myself. I have flashed before but never actually modified a BIOS like this. Any precautions I should take or is flashing with WinPhlash relatively fail safe? I do not want to brick it. Thanks!

---

### Post by ssorgatem on 2010-06-18
Also check out this:[ http://forum.notebookreview.com/acer/480992-acer-laptop-phoenix-bios-bios-mod-request-20.html#post6368072]("http://forum.notebookreview.com/acer/480992-acer-laptop-phoenix-bios-bios-mod-request-20.html#post6368072")


Also, I got from a guy an original BIOS supposedly by gateway, enabling AMD-V on the LT31. It's version 3.303. I'll upload it somewhere

---

### Post by spaceballl on 2010-06-19
> **ssorgatem said:**
> Also check out this:[ http://forum.notebookreview.com/acer/480992-acer-laptop-phoenix-bios-bios-mod-request-20.html#post6368072]("http://forum.notebookreview.com/acer/480992-acer-laptop-phoenix-bios-bios-mod-request-20.html#post6368072")


Also, I got from a guy an original BIOS supposedly by gateway, enabling AMD-V on the LT31. It's version 3.303. I'll upload it somewhere

That would be great. I would love it if you could post the modified BIOS. So if I grab your modified BIOS, flash it to my brother's netbook, and then put a fresh install of Ubuntu on his netbook with the most recent software updates, all should work just fine?

---

### Post by cyberey66 on 2010-07-09
> **ssorgatem said:**
> In order to mod the BIOS you need:

0- The desired DSDT.dsl file, formatted with DOS line endings (CR-LF)

1- The original BIOS file (probably BIOS1.WPH)

2- Phoenix BIOS editor Pro 2.1 or higher (a.k.a. Intel BIOS Logo editor, downloadable free of charge from intel)

3- Microsoft's ASL compiler version 3 (downloadable from microsoft)

4- Visual Basic 6 runtime (if you're running them in wine; "winetricks vb6run" will do the job if you have winetricks installed).

Steps:

1- Install the BIOS editor and (if necessary) visual basic 6 runtime.

2- Install MS ASL compiler.

3- Copy asl.exe to the BIOS editor program folder, that is, in the same folder as BIOSEDIT.EXE

4- Open the BIOS editor, open your BIOS1.WPH file, and then open the ACPI editor. The DSDT of the BIOS will show up. Select all and erase it all.

5- Open in notepad your custom DSDT.DSL file, select all, copy and then paste into the ACPI editor

6- Build your BIOS and then save it to somewhere.

7- Flash your newly created BIOS, from windows using WinPhlash, or from FreeDOS using PHLASH16.EXE.




People have reported success and working CPU scaling on LT31's with the dot MA BIOS. It's strange it's not your case... Are you sure that you correctly flashed the BIOS?

In the BIOS editor other thingss can be edited: default settings (only the already visible), menu strings and splashscreen images.

Thanks for the help.  I tried this and used the DSDT file provided on the first post of this thread.  I booted up the 2.6.34 kernel and power management did not work.  I then recompiled the kernel only adding to the config the lines necessary to load the custom DSDT.  After this, power management is working.  I used the same DSDT in both cases, so I am confused.

If anyone else has success in adding the corrected DSDT to their bios, please post here.  Maybe it is because this method uses the microsoft compiler?

It's a bummer that this is one of the few netbooks with a usable screen and has a buggy BIOS.  I'm on the verge of selling this if I can find a buyer locally.

---

### Post by ssorgatem on 2010-07-09
Are you sure you replaced the BIOS correctly?

Can you dump your dsdt, dissamble it and then compare it to see if it has been effectively replaced?

---

### Post by cyberey66 on 2010-07-09
> **ssorgatem said:**
> Are you sure you replaced the BIOS correctly?

Can you dump your dsdt, dissamble it and then compare it to see if it has been effectively replaced?

I just dumped the DSDT from the bios, it does not have the added p-states from the modifed dsdt.  I guess it didn't flash correctly.  I used winphlash,  I don't have windows installed anymore, so I'll try another method.

---

### Post by ssorgatem on 2010-07-09
> **cyberey66 said:**
> I just dumped the DSDT from the bios, it does not have the added p-states from the modifed dsdt.  I guess it didn't flash correctly.  I used winphlash,  I don't have windows installed anymore, so I'll try another method.

You can also try PHLASH16.EXE from within a live FreeDOS usb stick.

---

### Post by cyberey66 on 2010-07-12
@ssorgatem, THANK YOU!!!!

I was able to modify my bios and replace it with a corrected DSDT.  For flashing, at least with my LT31, the version of the flashing software seemed to be critical.  All the windows and DOS utilities I found on the web did not seem to work.

To find a correct version, I downloaded the bios update program for the DOT M-A from [http://www.packardbell.co.uk](http://www.packardbell.co.uk).

To extract the files, i ran the program on a windows virtual machine, (it automatically flashes the bios when you run it, so a virtual machine allows us to run the program without flashing).  I then copied the winphlash files from the temp directory on the windows machine.

So far power management works using the stock 2.6.32-5 kernel from Debian testing!  This is a great alternative to recompiling each new kernel.  Although it requires windows, any computer with a buggy DSDT most likely came with a windows license.

Thanks again!

Can anyone tell me the stock voltages of the L110 chip?

---

### Post by s.mulleady1122 on 2010-07-13
I did the same thing as cyberey66. Extracted the temp files used in the flasher from packard bells website. And flashed the fixed bios image to my Gateway LT31. Scaling works in Ubuntu 10.04 off the liveCD, and works in Windows 7 too.

Here are the files I extracted, with the fixed Bios image in there (Named BIOS1)

Finally no more recompiling kernels :D

[http://www.mediafire.com/?ilnqvfyojtn](http://www.mediafire.com/?ilnqvfyojtn)

---

### Post by cubicsilver on 2010-07-14
I have been watching this for awhile, and have tested quite a few bios's out.  This bios works awesome.  Even has vt enabled in bios.  

Tested with 9.10 and 10.04, confirmed, stepping works.  After adding nolapic to the startup of 10.04, I now get nearly the same battery life as windows 7. 

Thanks for posting the fixed bios.  Good job!

---

### Post by spaceballl on 2010-07-15
> **s.mulleady1122 said:**
> Here are the files I extracted, with the fixed Bios image in there (Named BIOS1)

Okay cool. I just downloaded this big zip file. So if I just re-flash my BIOS with the BIOS1 file in your zip package, all will "just work" out of the box, and there will be no need for custom kernels or anything like that? Say it ain't so!

Can I flash the BIOS from windows using winphlash? Is that the best method? I don't have windows installed on the netbook. Right now I have Linux Mint, but it's ready for a reinstall... should my process be...
- Install windows and overwrite linux mint
- flash the BIOS with the file you've attached and the utility you've attached
- re-install the newest version of ubuntu
- install all package updates

have power scaling working perfectly?

---

### Post by cyberey66 on 2010-07-15
> **spaceballl said:**
> Okay cool. I just downloaded this big zip file. So if I just re-flash my BIOS with the BIOS1 file in your zip package, all will "just work" out of the box, and there will be no need for custom kernels or anything like that? Say it ain't so!

Can I flash the BIOS from windows using winphlash? Is that the best method? I don't have windows installed on the netbook. Right now I have Linux Mint, but it's ready for a reinstall... should my process be...
- Install windows and overwrite linux mint
- flash the BIOS with the file you've attached and the utility you've attached
- re-install the newest version of ubuntu
- install all package updates

have power scaling working perfectly?

You can install windows in a second partition, use winplash and flash the bios.  You can recover grub with a live CD, [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows). 

 I haven't been able to find a DOS flash utility that works, so installing windows seems to be the only option, but the time it takes to install windows and flash the bios is comparable to the time it takes to compile a new kernel on this particular computer.

---

### Post by spaceballl on 2010-07-15
> **cyberey66 said:**
> You can install windows in a second partition, use winplash and flash the bios.  You can recover grub with a live CD, [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows). 

 I haven't been able to find a DOS flash utility that works, so installing windows seems to be the only option, but the time it takes to install windows and flash the bios is comparable to the time it takes to compile a new kernel on this particular computer.

Right... there are other options other than the specific method I mentioned, but the short story is that if I flash the BIOS, then I'll just be able to be a happy Ubuntu user and never worry about this again! Right?

---

### Post by cyberey66 on 2010-07-15
> **spaceballl said:**
> Right... there are other options other than the specific method I mentioned, but the short story is that if I flash the BIOS, then I'll just be able to be a happy Ubuntu user and never worry about this again! Right?

 yes

---

### Post by s.mulleady1122 on 2010-07-17
> **spaceballl said:**
> Right... there are other options other than the specific method I mentioned, but the short story is that if I flash the BIOS, then I'll just be able to be a happy Ubuntu user and never worry about this again! Right?

Yes, I use arch linux on my netbook now and scaling works without recompiling, I just use the stock kernel

The Winphlash files are included in my ZIP, just run the EXE

Also I only recommend you use my ZIP file with Windows 7 32 bit, other versions of windows might possibly be incompatible.

---

### Post by spaceballl on 2010-07-22
Alrighty!

I used winphlash - SUCCESS. Thanks so much for attaching the files. The computer restarted without issue. I'm actually going to keep the default Vista partition on there (tiz a SMALL partition...) in case I need to do something similar in the future.

Decided to give the newest run of Linux Mint a shot. Shouldn't be too far off from Ubuntu.

How do I verify that power management is working?

---

### Post by s.mulleady1122 on 2010-07-22
> **spaceballl said:**
> Alrighty!

I used winphlash - SUCCESS. Thanks so much for attaching the files. The computer restarted without issue. I'm actually going to keep the default Vista partition on there (tiz a SMALL partition...) in case I need to do something similar in the future.

Decided to give the newest run of Linux Mint a shot. Shouldn't be too far off from Ubuntu.

How do I verify that power management is working?

Add the CPU freq applet to Gnome-panel.

---

### Post by spaceballl on 2010-07-22
> **s.mulleady1122 said:**
> Add the CPU freq applet to Gnome-panel.
Awesome - i see it moving up from 800mhz to 1.2ghz as needed - very nice. My notebook has become that much more likable now that i've got power management working!

---

### Post by s.mulleady1122 on 2010-07-22
Cheers!

---

### Post by cyberey66 on 2010-07-22
> **spaceballl said:**
> Awesome - i see it moving up from 800mhz to 1.2ghz as needed - very nice. My notebook has become that much more likable now that i've got power management working!

Right on!  This gets my vote as one of the best laptops with the corrected bios.  The screen res is as high as the 21-22in monitors you get nowadays!

Does anyone know the stock voltages for this chip?  I would like to use a DSDT with the stock voltages, I believe the one Krists Krilovs made has lower voltages for power saving.

---

### Post by spaceballl on 2010-07-22
Yeah it really is a great little notebook. Seems much speedier than the Atom alternatives. I'm interested in trying out the newest version of Suse linux w/ Meego on it, but for now, i think i'll stick w/ Mint.

---

### Post by s.mulleady1122 on 2010-07-24
Bad news! The screen on my Gateway LT31 has failed! Literally one day after the warranty expired. Ugh, I'm disappointed in Acer/Gateway

---

### Post by AutoStatic on 2010-09-15
Upgraded my BIOS using a BartPE Windows XP CD and s.mulleady1122's ZIP file. Worked flawlessly and I can now scale my CPU without compiling a custom kernel myself. So many thanks!
Stock voltages: 
800Mhz  0.7000
900Mhz  0.7500
1000Mhz 0.8000
1100Mhz 0.8500
1200Mhz 0.9000

With the cpupowerd package from my PPA you can easily underclock/undervolt the L110 CPU since it's  a AMD K8 CPU and the 2.6.32 kernel supports it (older kernels needed a patch for the powernow-k8 module).

[http://ppa.launchpad.net/autostatic/ppa/ubuntu/pool/main/c/cpupowerd/](http://ppa.launchpad.net/autostatic/ppa/ubuntu/pool/main/c/cpupowerd/)

---

### Post by naujokas on 2010-09-29
got no acpi bios after upgrade cant boot in graphic mode :( can' reinstall ubuntu from usb flash or cd LT3103U now i do have bios version 1.3302 can boot in recovery mode, but if try startx end of story only power button can help

in windows blue screen: the BIOS in this system is not fully ACPI compliant. contact vendor for updated BIOS :( and reformated flash with bios backup i do can boot BartPE

---

### Post by ssorgatem on 2010-09-30
> **naujokas said:**
> got no acpi bios after upgrade cant boot in graphic mode :( can' reinstall ubuntu from usb flash or cd LT3103U now i do have bios version 1.3302 can boot in recovery mode, but if try startx end of story only power button can help

in windows blue screen: the BIOS in this system is not fully ACPI compliant. contact vendor for updated BIOS :( and reformated flash with bios backup i do can boot BartPE

Weird, but don't panick. Are you sure you flashed the correct file? Maybe the update went wrong. Anyway, if you can boot BartPE, you can try to reformaat BIOS with another file (non-Backup, maybe the backup is also flawed...).

Also, booting ubuntu with the option noacpi could help.

---

### Post by naujokas on 2010-09-30
i did tried to boot with no acpi with no luck, where can i get new file of bios, gateway does not provide it :( i did flashed bios1 from the zip file with flasher from zip
if i try to reflash the same BIOS image from BartPE  it comes to the point of writing new bios and then i get blue screen and reboot also BartPE boots in noacpi mode only.
can somebody help me with correct bios image.

---

### Post by ssorgatem on 2010-09-30
[try here]("http://global-download.packardbell.com/GDFiles/BIOS/BIOS/BIOS_PackardBell_3302_A_A.zip?acerid=634026559063479574&Step1=Netbook&Step2=dot&Step3=dot%20m%20-%20a&OS=V10&LC=es&BC=Packard%20Bell&SC=EMEA_11P")

---

### Post by naujokas on 2010-09-30
> **ssorgatem said:**
> [try here]("http://global-download.packardbell.com/GDFiles/BIOS/BIOS/BIOS_PackardBell_3302_A_A.zip?acerid=634026559063479574&Step1=Netbook&Step2=dot&Step3=dot%20m%20-%20a&OS=V10&LC=es&BC=Packard%20Bell&SC=EMEA_11P")
thanks for the link, couldn't upgrade from bartPE, got blue screen and reboot.
i have tried to flash using yours updated bios from notebookreview.com forum using bartPE and flasher from the zip file of this thread, and got bluescreen just before start of writing new bios.


FIXED it, made win98 usb key disk booted in dos an flashed in dos from link above thanks again for the link :)

---

### Post by hans12345 on 2010-10-27
If this was called: How-to: Getting power management to work on ACER L110 I would be so happy.

Is the Gateway LT31 the same as the ACER L110?

Are the procedures explained above OK for the ACER?

---

### Post by ssorgatem on 2010-10-27
> **hans12345 said:**
> If this was called: How-to: Getting power management to work on ACER L110 I would be so happy.

Is the Gateway LT31 the same as the ACER L110?

Are the procedures explained above OK for the ACER?

If it has the same hardware, it may well be a different-branded clone of the Gateway Lt31/packard-bell dot m/a (both those brands belong to acer).

Does it have an ati radeon integrated GPU? An a l110 processor? and a Phoenix BIOS? then you're likely lucky. Just try it and tell us about your succes.

---

### Post by Vervol on 2010-11-16
ppl can u help me.
i have Packard bell dot ma. Can someone give me correct bios to enable scale cpu speed and etc?:) 
Also can someone tell me can i firmware this bios in this topic: [http://forum.notebookreview.com/acer/480992-acer-laptop-phoenix-bios-bios-mod-request-20.html#post6368072](http://forum.notebookreview.com/acer/480992-acer-laptop-phoenix-bios-bios-mod-request-20.html#post6368072) from [SIZE=1]**[COLOR=Red]UPDATE (17 October 2010) [/COLOR]**[COLOR=Black]o can some on mod it for pacard bell? coze when i frimware it in ubuntu  i get white screen and lines etc artifacts can't see nothing :\ and when a wanna boot windows it says that can't coze some problem with acpi

Sry for my eng)
[/COLOR][/SIZE]

---

### Post by ssorgatem on 2010-11-16
> **Vervol said:**
> ppl can u help me.
i have Packard bell dot ma. Can someone give me correct bios to enable scale cpu speed and etc?:) 
Also can someone tell me can i firmware this bios in this topic: [http://forum.notebookreview.com/acer/480992-acer-laptop-phoenix-bios-bios-mod-request-20.html#post6368072](http://forum.notebookreview.com/acer/480992-acer-laptop-phoenix-bios-bios-mod-request-20.html#post6368072) from [SIZE=1]**[COLOR=Red]UPDATE (17 October 2010) [/COLOR]**[COLOR=Black]o can some on mod it for pacard bell? coze when i frimware it in ubuntu  i get white screen and lines etc artifacts can't see nothing :\ and when a wanna boot windows it says that can't coze some problem with acpi

Sry for my eng)
[/COLOR][/SIZE]

You could at least try to write proper *eng)*. It would probably make it easier for people to read your post and therefore try to help you...

I didn't know about that update, it might give it a try. If you have problems with that BIOS file, I think the best place to ask for help about it is not here, but the place where you got it (the post you link to).

Also, sending PM just asking people to reply to posts isn't the most polite way to address to someone. You've been lucky I was in a good mood.

---

### Post by omniuni on 2010-11-16
Hi ssorgatem,

Although what little research I was able to do indicates that the laptops have a lot in common, I would recommend against trying this procedure on your computer. When I tried it on the Gateway it was less than stable, and the problem is buried within the BIOS. It may NOT hurt the computer, but it also MIGHT cause problems. I would recommend that if you need extra battery life, use Intel Powertop instead, and hope for the best. (Yes, it works fine with AMD laptops)

Down the line, look for a netbook with the AMD Athlon Neo, AMD's actual netbook processor. One example of such a netbook is the MSI Wind U210: [http://www.amazon.com/MSI-U210-008US-12-1-Inch-Black-Netbook/dp/B002LZUHNW]("http://www.amazon.com/MSI-U210-008US-12-1-Inch-Black-Netbook/dp/B002LZUHNW")

-OmniUni

---

### Post by Rogue007 on 2010-11-19
Hello ssorgatem,

I currently have two Gateway LT31 netbooks; an LT3103u with an upgraded L310 cpu and bios v1.3302 running Windows 7 32-bit, and an LT3119u which came with an L310 cpu and bios v1.3307 and is running Windows 7 64-bit.  Both computers appear to have identical hardware with the exception of touch pads (one Synaptics, the other ALPS). 

I've tried moving all of my computers to Windows 64-bit but the LT3103u sleep and/or hibernate does not work under 64-bit.  I've tried every "fix" I could find on the web and installed a couple MS hotfixes that dealt with similar problems, but nothing worked.  If the computer tries to enter sleep or hibernate, it simply freezes and requires the power to be cycled.  It works perfectly under Windows 7 32-bit and Vista 32-bit.  None of these problems exist on the LT3119u and I'm assuming that is because it has bios v1.3307.

I'm now considering copying bios v1.3307 from the LT3119u to the LT3103u if I can find a fairly safe way to do so (I have flashed bioses before but I'm definitely no expert...though I do understand the risks).  Is it possible to even use the bios backup from one computer to flash the other???  If so, I am willing to make a copy of bios v1.3307 and send it to you if you you're interested in it.  I only ask that you instruct me on how to do so and check the integrity of the backup before I flash it to the LT3103u.  The only obvious difference I see in the v1.3307 bios menus is that it has a Processor Assisted Virtualization (enable/disable) option.) 

Please let me know if you're interested.

Thanks!

R

---

### Post by Turmlos on 2010-11-22
Hello Rogue007,

This is kind of off-topic, but would you mind telling me the specifications of the AC adapter that came with your LT3119u?  I replaced the processor in my LT3103u with a 1.6GHz Athlon 64 X2 TK-42 a while back, but the supplied 30W adapter doesn't seem like it can handle anything above 1.2GHz for very long.  I'm guessing that they bumped the wattage on it due to the LT3119u's L310.  I wonder if the motherboard design changed at all...

---

### Post by spaceballl on 2010-11-22
> **Turmlos said:**
> Hello Rogue007,

This is kind of off-topic, but would you mind telling me the specifications of the AC adapter that came with your LT3119u?  I replaced the processor in my LT3103u with a 1.6GHz Athlon 64 X2 TK-42 a while back, but the supplied 30W adapter doesn't seem like it can handle anything above 1.2GHz for very long.  I'm guessing that they bumped the wattage on it due to the LT3119u's L310.  I wonder if the motherboard design changed at all...
Woah you can upgrade the CPU?? Will you send me a link to compatible CPUs / instructions??

---

### Post by Rogue007 on 2010-11-22
Turmlos,

The power block specs for my LT3119u are:   Make: Lite-On; Model: PA-1300-04; Input: 100-120V, 50-60 Hz; Output: 19V, 1.58A; bottom right corner has Rev:A06 stamp.

It appears to be identical to the LT3103u block (both 30W) except for the Rev (revision??) number.  My LT3103u block is Rev: A03.

I can run the L310 (in my LT3103u) overclocked to 1.44 GHz all day without issue, though it does get a little toasty if I do that.  It&#8217;ll run in the upper 60&#8217;s C when taxed and has broke 70 a few times, though the CPU is supposedly rated at 95 C according to CPU-World.com.  The L310 is listed as having a TDP of 13W (same as the L110, which I do find hard to believe).  SANDRA also reported the same motherboard model number for both of my LT31s.

Spaceballl,

This netbook has an AMD socket S1.  You can just drop in an L310 without any problems at all (SEE: [http://www.cpu-world.com/CPUs/K8/AMD-Athlon%20X2%20Dual-Core%20Mobile%20L310%20-%20AMML310HAX5DM.html]("http://www.cpu-world.com/CPUs/K8/AMD-Athlon%20X2%20Dual-Core%20Mobile%20L310%20-%20AMML310HAX5DM.html")).   I found one on ebay several months ago and snagged it for $60 (steep, but these were rare at the time&#8230;and still may be).  Some others have successfully installed more powerful CPUs (like Turmlos), but there may be some power and heat issues that you may need to overcome if you do that.

As far as instructions to install it? I never found any, but did find some photos of the internals here:   [http://forum.notebookreview.com/notebook-news-reviews/393200-gateway-intros-its-first-11-6-netbook-17.html](http://forum.notebookreview.com/notebook-news-reviews/393200-gateway-intros-its-first-11-6-netbook-17.html)

As far as disassembling the computer, I winged it.  Here&#8217;s what I did:

Flip the computer upside down.  Remove battery, doors, hard drive, memory module, and pcie card.  Remove all screws on the bottom around the perimeter.  Flip the computer right side up.  Depress the four little tabs at the top of the keyboard (between esc&F1, F5&F6, F10&F11, and Ins&Del keys) and tip the keyboard up.  Lift the lock for the keyboard ribbon cable to detach the keyboard. Lift the lock for the touch pad ribbon cable and detach.  Remove all screws that were exposed by removing the keyboard. Remove the little hinge covers at the inboard sides of the LCD hinges (this may take a bit of wiggling and getting the LCD in &#8220;just the right spot&#8221;). The upper and lower halves of the body should now be able to be pulled apart (this is a bit unnerving and possibly easy to break, be gentle).  Carefully detach the audio cables, WiFi cables, and LCD cables and remove the motherboard.  Detach the fan plug and remove the heat sink.  Unlock the CPU, swap in the new one, and relock.  (NOTE:  You&#8217;ll need new thermal grease for the CPU and may need a new thermal gap-pad for the GPU if you damage the original pad (I ordered a 0.5 mm thick pad from ebay and it worked.  I also found some better ones at FrozenCPU.com&#8230;make sure it does fill the gap between the GPU and the heat sink).  Reassemble in reverse order.

If you do this, be patient and careful.  I could have easily missed a few steps here since this is mostly out of my memory.  I take no responsibility for any damage that results.;)

Now, about that bios......

---

### Post by Footer on 2010-12-07
Has anyone gotten 10.10 to work on their LT31?  I tried upgrading from 10.04 but that didn't work.  So I tried installing 10.10 (Kubuntu amd64) but after installing, it kept freezing to the point it was not useable.  So I went and tried the Netbook version and got that installed but only saw a purple screen!  I could mouse around and see things occasionally but still unuseable.

So back to Kubuntu 10.04 (amd64) I go and it's fine so far.  I'm not even going to mess with power management, it sucks the battery life pretty fast but that's more trouble than it's worth ... which drew me to this thread in the first place!

So anyway, sorry to bring this a bit off topic but I'm just curious about 10.10.

Thanks!

Here's my current kernel parameters:

footer@netbook:~$ uname -a
Linux netbook 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 10:14:11 UTC 2010 x86_64 GNU/Linux

---

### Post by gberliner on 2010-12-30
Here's an odd curveball for you all:

Following the guidance I've read here and on notebookreview.com, I successfully flashed my LT31's bios with the modded bios offered by kiswan over at notebookreview.

With this, frequency scaling now works out of the box in the latest ubuntu/linuxmint. Very curious and annoying issues remain, though, some of them evidently related to a wonky clockgen chipset on the more recent incarnations of this gateway machine (including mine, unfortunately). 

One curiosity I have observed is that, if I wake the machine up from suspend, WITH THE POWER CORD UNPLUGGED, the wifi becomes unusable. Sometimes I can rmmod/modprobe and get it working again, but it will then start dropping more than half of the packets sent through it.

However, if I wake it from suspend WITH THE POWER CORD PLUGGED IN, no problem with the wifi ensues.

I have tried various settings for frequency scaling, ondemand, performance, userspace, but this outcome remains consistent: waking from suspend WITH the cord plugged in, the wifi works, waking UNPLUGGED the wifi is always hosed!

---

### Post by cyberey66 on 2010-12-30
> **gberliner said:**
> Here's an odd curveball for you all:

Following the guidance I've read here and on notebookreview.com, I successfully flashed my LT31's bios with the modded bios offered by kiswan over at notebookreview.

With this, frequency scaling now works out of the box in the latest ubuntu/linuxmint. Very curious and annoying issues remain, though, some of them evidently related to a wonky clockgen chipset on the more recent incarnations of this gateway machine (including mine, unfortunately). 

One curiosity I have observed is that, if I wake the machine up from suspend, WITH THE POWER CORD UNPLUGGED, the wifi becomes unusable. Sometimes I can rmmod/modprobe and get it working again, but it will then start dropping more than half of the packets sent through it.

However, if I wake it from suspend WITH THE POWER CORD PLUGGED IN, no problem with the wifi ensues.

I have tried various settings for frequency scaling, ondemand, performance, userspace, but this outcome remains consistent: waking from suspend WITH the cord plugged in, the wifi works, waking UNPLUGGED the wifi is always hosed!

I would like to add, I notice that with the WiFi as well.  If I try to bring the card back up I get an error, saying "no such device"

I also notice this weird bug, if I am plugged in and have freqency scaling enabled, my laptop will eventually lockup.  If when I plug in my laptop, I set the power management to keep the CPU at maximum speed, I do not experience lockups.  There is still a lot of buggy stuff here but it's still the cheapest 1366x768 11" laptop one can buy.  Once support for the M11X is up to par, I may have to upgrade to that.

---

### Post by fenofonts on 2011-03-18
> **cyberey66 said:**
> I would like to add, I notice that with the WiFi as well.  If I try to bring the card back up I get an error, saying "no such device"

I also notice this weird bug, if I am plugged in and have freqency scaling enabled, my laptop will eventually lockup.  If when I plug in my laptop, I set the power management to keep the CPU at maximum speed, I do not experience lockups.  There is still a lot of buggy stuff here but it's still the cheapest 1366x768 11" laptop one can buy.  Once support for the M11X is up to par, I may have to upgrade to that.

Cyberey66, are you still getting lockups? I'm interested in this because just as I thought my machine was running perfectly, I started getting lockups (most of the time with a completely blank screen. Is this what you're getting? I am using the MOD BIOS from notebookreview.

---

### Post by cyberey66 on 2011-03-18
> **fenofonts said:**
> Cyberey66, are you still getting lockups? I'm interested in this because just as I thought my machine was running perfectly, I started getting lockups (most of the time with a completely blank screen. Is this what you're getting? I am using the MOD BIOS from notebookreview.

When frequency scaling was enabled, I noticed two problems that occurred seemingly randomly, but not often.  1:  The WiFi would randomly cutoff.  If I tried ifconfig up/down, it would give an error.  I would have to reboot to use WiFi.  2:  Sometimes the computer would randomly lockup.  The screen would remain on, but the mouse/keyboard etc had no effect.  I noticed through my own experience, that it seemed to happen when frequency scaling was enabled and it was plugged in.

I ended up selling this laptop and made sure my next laptop was compatible before purchase, so I stopped playing around with it.

*edit*  I was using a mod BIOS as well, I saw no difference between modded BIOS with DSDT or modded kernel with DSDT.

---

### Post by SlickSSDNetbook on 2012-08-01
> **cyberey66 said:**
> When frequency scaling was enabled, I noticed two problems that occurred seemingly randomly, but not often.  1:  The WiFi would randomly cutoff.  If I tried ifconfig up/down, it would give an error.  I would have to reboot to use WiFi.  2:  Sometimes the computer would randomly lockup.  The screen would remain on, but the mouse/keyboard etc had no effect.  I noticed through my own experience, that it seemed to happen when frequency scaling was enabled and it was plugged in.

I ended up selling this laptop and made sure my next laptop was compatible before purchase, so I stopped playing around with it.

*edit*  I was using a mod BIOS as well, I saw no difference between modded BIOS with DSDT or modded kernel with DSDT.

I know this is an older thread, but It helped me a lot in getting my lt31 Netbook up and running, so i wanted to help anyone who got stuck with the above issues of hanging on A/C Power with Cpu scaling turned on. I shoudd say the modded bios made all the difference except for the above 2 issues.  i simply turned off wifi powersave feature and then did the following.  

A very simple fix I found to this is to  use laptop-mode-tools available through the usual repositories. After install  Edit the laptop-mode.conf file (/etc/laptop-mode/laptop-mode.conf)to allow it to function on battery and A/C.  Then go into the conf.d folder in the same directory and edit the cpufreq.conf to look like so: 

```
#
# Configuration file for Laptop Mode Tools module cpufreq.
#
# For more information, consult the laptop-mode.conf(8) manual page.
#

###############################################################################
# CPU frequency scaling and throttling
# ------------------------------------
#
# Laptop mode tools can automatically adjust your kernel CPU frequency
# settings. This includes upper and lower limits and scaling governors.
# There is also support for CPU throttling, on systems that don't support
# frequency scaling.
#
# This feature only works on 2.6 kernels.
#
#
# IMPORTANT: In versions 1.36 and earlier, these settings were included in the
# main laptop-mode.conf configuration file. If they are still present, they
# overrule the settings in this file. To fix this, simply delete the settings
# from the main config file.
#
###############################################################################

# Enable debug mode for this module
# Set to 1 if you want to debug this module
DEBUG=0

#
# Should laptop mode tools control the CPU frequency settings?
#
# Set to 0 to disable
CONTROL_CPU_FREQUENCY=[COLOR="Red"]1[/COLOR]


#
# Legal values are "slowest" for the slowest speed that your
# CPU is able to operate at, "fastest" for the fastest speed,
# "medium" for some value in the middle, or any value listed in
# /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies.
# The "governor" can be any governor installed on your system, this usually
# includes "ondemand", "conservative", and "performance". The
# "IGNORE_NICE_LOAD" setting specifies that background programs that have
# a low priority ("nice level") should not cause the CPU frequency to
# be increased. (You generally want this to be enabled in battery mode.)
#[COLOR="Red"]
BATT_CPU_MAXFREQ=fastest
BATT_CPU_MINFREQ=slowest
BATT_CPU_GOVERNOR=powersave
BATT_CPU_IGNORE_NICE_LOAD=1
LM_AC_CPU_MAXFREQ=fastest
LM_AC_CPU_MINFREQ=fastest
LM_AC_CPU_GOVERNOR=performance
LM_AC_CPU_IGNORE_NICE_LOAD=1
NOLM_AC_CPU_MAXFREQ=fastest
NOLM_AC_CPU_MINFREQ=fastest
NOLM_AC_CPU_GOVERNOR=performance
NOLM_AC_CPU_IGNORE_NICE_LOAD=1[/COLOR]


#
# Should laptop mode tools control the CPU throttling? This is only useful
# on processors that don't have frequency scaling.
# (Only works when you have /proc/acpi/processor/CPU*/throttling.)
# 
# This is only useful on older P4 processors that do not support frequency
# scaling. On such processors, this is the only way to reduce power consumption
# but at the cost of higher performance penalty.
#
# Enable this only if you have a processor that does not support frequency scaling
# On most new processors, you might want to disable it.
#
# Set to 0 to disable.
CONTROL_CPU_THROTTLING=0


#
# Legal values are "maximum" for the maximum (slowest) throttling level,
# "minimum" for minimum (fastest) throttling level, "medium" for a value
# somewhere in the middle (this is usually 50% for P4s), or any value listed
# in /proc/acpi/processor/CPU*/throttling. Be careful when using "maximum":
# this may be _very_ slow (in fact, with P4s it slows down the processor
# by a factor 8).
#
BATT_CPU_THROTTLING=medium
LM_AC_CPU_THROTTLING=medium
NOLM_AC_CPU_THROTTLING=minimum

```

What this does is tell laptop mode to automatically set the cpu to performance and to not scale on A/C power.  its not an ideal solution but solves my crashes and allows me to run in powersave automatically when unplugged.  

[COLOR="Blue"]The only other issue I rant into, and I'm not sure if it is a lubuntu only thing as I am a bit of a novice is that I had to go in and modify the file ondemand in /init.d to turn on the performance governor instead of the ondemand or when I booted in A/C mode it would default to ondemand after 60 seconds and hang my computer.[/COLOR]  

Since the above mods no more freezing, wifi works like a charm, 
I can suspend without issues.. etc.. Thank you for all the info I've gotten from this forum

Mods if I screwed anything up here please let me know.. first time on the forums.

---

