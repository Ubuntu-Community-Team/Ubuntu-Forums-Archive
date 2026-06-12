---
title: "GeForce 1440x900 resolution, virtual terminals and wide usplash-theme-ubuntu [gutsy]"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by SirYes on 2007-11-24
Edit: I recently added the instructions to use an Ubuntu *or* Kubuntu usplash theme. I hope some of you may like it better. :)

Hello all,

[B]Here you can find instructions how to change the usplash theme to support 1440x900 native resolution. At least that worked for me, so maybe you can be lucky as well.
[/B]
First, the hardware:[LIST]
[*]ASUS F3S notebook
[*]1440x900 LCD
[*]nVIDIA GeForce 8400M[/LIST]Second, the system:[LIST]
[*]Ubuntu 7.10 Gutsy Gibbon, desktop-i386
[*]Kernel: Linux 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux[/LIST]Third, the goals:[LIST]
[*]Enable framebuffer on vt1-vt6 using the native 1440x900 resolution (see [bug #129910]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910"))
[*]Change the usplash theme to look good on 1440x900 display (see [bug #64147]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/64147"))[/LIST]Overview of steps required:[LIST=1]
[*]Set a nice font for virtual terminals
[*]Enable the vesafb module
[*]Modify kernel boot parameters
[*]Change usplash configuration
[*]Reboot
[*]Install some development packages
[*]Patch the source of usplash theme
[*]Compile and install updated usplash theme
[*]Reboot and enjoy[/LIST][COLOR=Blue][SIZE=4]1. Set a nice font for virtual terminals[/SIZE][/COLOR]

In Ubuntu Gutsy virtual terminals work only using the low-resolution text mode by default. The reason is that the framebuffer modules are generally disabled (blacklisted) in the modules configuration. I suspect that's because this part of kernel code is not 100% up to date, doesn't work for everybody and is designed to work best on x86/amd64 systems.

It is possible, however, to enable at least the **vesafb** module and try to use a higher resolution for virtual terminals. See [bug #129910]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910") for a long list of success and failure reports.

So, get your hands dirty and open the terminal first. Remember to [COLOR=Green]**type only the green text**[/COLOR], also omit all comment lines that start with '#':
```
[COLOR=Green]sudo dpkg-reconfigure console-setup[/COLOR]
```Select the keyboard options, keep the UTF-8 settings on the console and *finally* select the "Fixed" font (which supports a wide variety of UTF-8 characters), or any other font you like/prefer.

[COLOR=Blue][SIZE=4]2. Enable the vesafb module[/SIZE][/COLOR]

This is somewhat longer. First enable autoloading of selected modules at boot time:
```
[COLOR=Green]sudo nano /etc/initramfs-tools/modules[/COLOR]
```At the end of file add **fbcon** and **vesafb** modules:
```
# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod

[COLOR=Green]fbcon
vesafb[/COLOR]
```Also remove the modules from blacklist:
```
[COLOR=Green]sudo nano /etc/modprobe.d/blacklist-framebuffer[/COLOR]
```Comment out the blacklisting of **vesafb** module, by changing corresponding "**blacklist vesafb**" line to "**# blacklist vesafb**":
```
# Framebuffer drivers are generally buggy and poorly-supported, and cause
# suspend failures, kernel panics and general mayhem.  For this reason we
# never load them automatically.
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist cyblafb
blacklist gx1fb
blacklist hgafb
blacklist i810fb
blacklist intelfb
blacklist kyrofb
blacklist matroxfb_base
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist rivafb
blacklist s1d13xxxfb
blacklist savagefb
blacklist sisfb
blacklist sstfb
blacklist tdfxfb
blacklist tridentfb
[COLOR=Green]# blacklist vesafb[/COLOR]
blacklist vfb
blacklist vga16fb
```Note that **fbcon** module is *NOT* blacklisted, so it's not necessary to un-blacklist it.

Finally generate modules.dep and map files:
```
[COLOR=Green]sudo depmod -a[/COLOR]
```[COLOR=Blue][SIZE=4]3. Modify kernel boot parameters[/SIZE][/COLOR]

Because the **fbcon** and **vesafb** modules will be loaded automatically only at the boot time, right now load them manually:
```
[COLOR=Green]sudo modprobe fbcon[/COLOR]
[COLOR=Green]sudo modprobe vesafb[/COLOR]
```Make sure your card supports the resolution you'd like to use. So install and invoke the **hwinfo** program:
```
[COLOR=Green]sudo apt-get install hwinfo[/COLOR]
[COLOR=Green]sudo hwinfo --framebuffer[/COLOR]
```Below is the output of **hwinfo** on my computer. I marked in red the graphics mode I'm using right now, 1440x900 @ 24bpp (you may have to scroll a bit the following text area to see it):
```
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.447]
  Unique ID: rdCR.04O_qA0Mq31
  Hardware Class: framebuffer
  Model: "NVIDIA G86 Board - e416h01 "
  Vendor: "NVIDIA Corporation"
  Device: "G86 Board - e416h01 "
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 14 MB
  Memory Range: 0xfb000000-0xfbdfffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0349: 1400x1050 (+5600), 24 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Mode 0x0362: 768x480 (+768), 8 bits
  Mode 0x0364: 1440x900 (+1440), 8 bits
  [COLOR=Red]Mode 0x0365: 1440x900 (+5760), 24 bits[/COLOR]
  Mode 0x0368: 1680x1050 (+1680), 8 bits
  Mode 0x0369: 1680x1050 (+6720), 24 bits
  Mode 0x037c: 1920x1200 (+1920), 8 bits
  Mode 0x037d: 1920x1200 (+7680), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```Since the number of desired graphics mode is known (0x365), the kernel parameters can be now updated:
```
[COLOR=Green]sudo nano /boot/grub/menu.lst[/COLOR]
```Scroll down the text in editor until you find the following section:
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash locale=pl_PL
```You may also search (press Ctrl+W) for the word "**defoptions**" to speed up the process.

Add the "**vga=0x365**" option (the locale setting will probably be different in your case, don't change it!):
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=[COLOR=Green]vga=0x365[/COLOR] quiet splash locale=pl_PL
```Some people report that "**vga=0x0365**" also works for them. You might want to use that, but I suggest to use the shorter version (it works for me at least).

Make sure the changes are applied:
```
[COLOR=Green]sudo update-grub[/COLOR]
```[COLOR=Blue][SIZE=4]4. Change usplash configuration[/SIZE][/COLOR]

This one is easy but important:
```
[COLOR=Green]sudo nano /etc/usplash.conf[/COLOR]
```Change the:
```
xres=
yres=
```To:
```
xres=[COLOR=Green]1440[/COLOR]
yres=[COLOR=Green]900[/COLOR]
```Reconfigure the usplash package. What's important is that during reconfiguration the initrd will be regenerated (initrd is an initial ramdisk that contains minimal file system and scripts used by the boot process). This will copy files modified as above, including modules configuration (autoloading and blacklisting) and usplash settings, into the initrd. So, apply all changes in one go:
```
[COLOR=Green]sudo dpkg-reconfigure usplash[/COLOR]
```[COLOR=Blue][SIZE=4]5. Reboot[/SIZE][/COLOR]

Now restart the system and check if all went correctly. Don't worry yet about strange usplash picture proportions, we'll take care of that in a moment. Check this:[LIST]
[*]whether the virtual terminals use the selected resolution - just press Ctlr+Alt+F1 to switch to virtual terminal vt1 (also check vt2-vt6 by using Ctrl+Alt+F2 ... Ctrl+Alt+F6)
[*]if there is a proper font on the virtual terminals (I typically log in at the terminal and use **aptitude** for making sure the national characters and lines/boxes are displayed correctly)
[*]whether you can switch back to graphical screen, which resides on vt7 (press Ctrl+Alt+F7 and try to log in)[/LIST]Now is time for modifying the usplash theme to support 1440x900 resolution.

[COLOR=Blue][SIZE=4]6. Install some development packages[/SIZE][/COLOR]

You will soon need to recompile the **usplash-theme-ubuntu** package, but to do so you need some tools and libraries. Install these packages:
```
[COLOR=Green]sudo apt-get install build-essential libusplash-dev[/COLOR]
```Also create the temporary directory:
```
[COLOR=Green]mkdir ~/work[/COLOR]
```Now follow a selected part of the instructions below:[LIST]
[*][COLOR=Blue][SIZE=3]**6.1. Ubuntu splash**[/SIZE][/COLOR]

Download the attached file, "**usplash-theme-ubuntu-mod.tar.gz**", and put it in the **~/work** directory. Here's the file:
[ATTACH]51230[/ATTACH]

Extract two files from the archive, "**usplash-theme-ubuntu-mod.diff**" and "**usplash_1440_900.png**":
```
[COLOR=Green]cd ~/work[/COLOR]
[COLOR=Green]tar xvzf usplash-theme-ubuntu-mod.tar.gz[/COLOR]
```**Note**
By default usplash tries to make a best match from available pictures to the resolution specified in its configuration file. Unluckily, in the current version the usplash's best picture seems to be "usplash_1365_768_scaled.png", which contains a horizontally squeezed Ubuntu logo. As you may have noticed, it looks wrong on the 1440x900 display. So I created a new "usplash_1440_900.png" file which is based on original "usplash_1365_768.png" image. I opened it in GIMP, changed the size of the image and centered it, then I filled the resulting "empty" border with black color and saved the image under a new name. And there you have it.
[*][COLOR=Blue][SIZE=3]**6.2. Kubuntu splash**[/SIZE][/COLOR]

Download the attached file, "**usplash-theme-kubuntu-mod.tar.gz**", and put it in the **~/work** directory. Here's the file:
[ATTACH]54487[/ATTACH]

Extract two files from the archive, "**usplash-theme-kubuntu-mod.diff**" and "**kubuntu_1440_900.png**":
```
[COLOR=Green]cd ~/work[/COLOR]
[COLOR=Green]tar xvzf usplash-theme-kubuntu-mod.tar.gz[/COLOR]
```[/LIST][COLOR=Blue][SIZE=4]7. Patch the source of usplash theme[/SIZE][/COLOR]

Note that I've made the patches against the 0.17 version of usplash-theme-ubuntu and 7.10 version of kubuntu-default-settings packages. The "*.diff" files will work for these versions correctly. Whether they will work against any other version I have no idea (probably not). You have been warned. :neutral:[LIST]
[*][COLOR=Blue][SIZE=3]**7.1. Ubuntu splash**[/SIZE][/COLOR]

Get the source code of the package:
```
[COLOR=Green]apt-get source usplash-theme-ubuntu[/COLOR]

# look for the following line:
[COLOR=Blue]dpkg-source: extracting usplash-theme-ubuntu in usplash-theme-ubuntu-0.17[/COLOR]
# if you can see it all should be fine
```Copy the additional "usplash_1440_900.png" file:
```
[COLOR=Green]cd ~/work/usplash-theme-ubuntu-0.17[/COLOR]
[COLOR=Green]cp ../usplash_1440_900.png .[/COLOR]
[COLOR=Green]patch -p0 < ../usplash-theme-ubuntu-mod.diff[/COLOR]
```
[*][COLOR=Blue][SIZE=3]**7.2. Kubuntu splash**[/SIZE][/COLOR]

Get the source code of the package:
```
[COLOR=Green]apt-get source kubuntu-artwork-usplash[/COLOR]

# look for the following line:
[COLOR=Blue]dpkg-source: extracting kubuntu-default-settings in kubuntu-default-settings-7.10[/COLOR]
# if you can see it all should be fine
```Copy the additional "kubuntu_1440_900.png" file:
```
[COLOR=Green]cd ~/work/kubuntu-default-settings-7.10/usplash/[/COLOR]
[COLOR=Green]cp ../../kubuntu_1440_900.png .[/COLOR]
[COLOR=Green]patch -p0 < ../../usplash-theme-kubuntu-mod.diff[/COLOR]
```[/LIST][COLOR=Blue][SIZE=4]8. Compile and install updated usplash theme[/SIZE][/COLOR]

Since the source is patched and the tools should be in place you can now compile the code:
```
[COLOR=Green]make[/COLOR]
```[LIST]
[*]If all went fine, you can use the preferred method, the "alternatives system", to install the resulting "**usplash-theme-*.so**" file. You can find a reference in the [USplashCustomizationHowto]("https://help.ubuntu.com/community/USplashCustomizationHowto") topic in the Community Ubuntu Documentation. Here are the commands:[LIST]
[*][COLOR=Blue][SIZE=3]**8.1. Ubuntu splash**[/SIZE][/COLOR]
```
[COLOR=Green]sudo mkdir -p /usr/local/lib/usplash/[/COLOR]
[COLOR=Green]sudo cp usplash-theme-ubuntu.so /usr/local/lib/usplash/usplash-theme-ubuntu-mod.so[/COLOR]
[COLOR=Green]sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/local/lib/usplash/usplash-theme-ubuntu-mod.so 55[/COLOR]
[COLOR=Green]sudo update-alternatives --set usplash-artwork.so /usr/local/lib/usplash/usplash-theme-ubuntu-mod.so[/COLOR]
```
[*][COLOR=Blue][SIZE=3]**8.2. Kubuntu splash**[/SIZE][/COLOR]
```
[COLOR=Green]sudo mkdir -p /usr/local/lib/usplash/[/COLOR]
[COLOR=Green]sudo cp usplash-theme-kubuntu.so /usr/local/lib/usplash/usplash-theme-kubuntu-mod.so[/COLOR]
[COLOR=Green]sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/local/lib/usplash/usplash-theme-kubuntu-mod.so 55[/COLOR]
[COLOR=Green]sudo update-alternatives --set usplash-artwork.so /usr/local/lib/usplash/usplash-theme-kubuntu-mod.so[/COLOR]
```[/LIST]If you later change your mind you can select which alternative should be used for "usplash-artwork.so" file:
```
[COLOR=Green]sudo update-alternatives --config usplash-artwork.so[/COLOR]
```In fact you can even install *BOTH* Ubuntu and Kubuntu splashes and switch between them using the above command.
[*]You can also install the "**usplash-theme-*.so**" file using **make install**. That's the simplest method and it overwrites the original "**/usr/lib/usplash/usplash-theme-*.so**". However, a latter system update may overwrite it back, so be warned:
```
[COLOR=Green]sudo make install[/COLOR]
```[/LIST]Finally reconfigure the usplash package and you should be all set. Always do this after selecting the alternative for "usplash-artwork.so" in order to regenerate the initrd (so both boot-splash and shutdown-splash will be the same):
```
[COLOR=Green]sudo dpkg-reconfigure usplash[/COLOR]
```[COLOR=Blue][SIZE=4]9. Reboot and enjoy[/SIZE][/COLOR]

Nothing more to add. :mrgreen:

---

### Post by uqbar on 2007-11-29
Wonderful!
This guide applied seamlessly to my Asus G1S!
Just a typo to be fixed at step #6: "build-essential" and not "build-essentials".

Thank you SirYes and give my regards to Poland!

---

### Post by SirYes on 2007-11-30
> **uqbar said:**
> Wonderful!
This guide applied seamlessly to my Asus G1S!
Great! So the result is repeatable, that's really good news. Although I'd wish it was completely unnecessary and more or less supported upstream.

I'm glad you were able to make all the steps. :) I really wondered if I have forgotten something or not.

> Just a typo to be fixed at step #6: "build-essential" and not "build-essentials".Corrected. An obvious error, but it slipped through. Thanks!

> Thank you SirYes and give my regards to Poland!Thank you for your kind words.
Have a nice... hi-res! :D

---

### Post by jaz013 on 2007-12-05
Excellent post SirYes!  I've been trying to find info on how to get this working on my Asus G1S notebook for a week now and yours is the first to help me get it working!

Running Kubuntu 7.10 and the only differences I had were i had to run 1680x1050 (yeah, damn :) ) and I didn't have to do the last bit with rebuilding usplash because it looks fine!

Thanks again!  You rock!

---

### Post by gman16000 on 2007-12-18
I'm on an Asus G1S and I've been booting with a black screen until I saw this post.  Everything worked flawlessly!!  Perfect instructions.  Now I can show off Ubuntu while I'm booting!!

---

### Post by Zorael on 2007-12-25
I'd love this, but I'm running Kubuntu. Is there any chance I might be able to persuade you into posting instructions for that splash? :)

---

### Post by ronb94 on 2007-12-25
hello
After grub i am getiing this messege:
starting-up
you passed an undefined mode number
press [return] to see video modes avaible [space] to continue
what did i wrong?
thank you

---

### Post by Zorael on 2007-12-25
> Below is the output of hwinfo on my computer. I marked in red the graphics mode I'm using right now, 1440x900 @ 24bpp (you may have to scroll a bit the following text area to see it):

Chances are your videocard doesn't support the 0x365 mode, in that case. Try replacing that with something else that's listed when you run hwinfo. :>

---

### Post by ronb94 on 2007-12-25
i have 8600gts and when i run [HTML]sudo hwinfo --framebuffer[/HTML] its showing that my card  supports look:
[IMG]http://img89.imageshack.us/img89/9151/screenshotronronvj6.png[/IMG]

---

### Post by Zorael on 2007-12-25
Hmm.

> Some people report that "vga=0x0365" also works for them. You might want to use that, but I suggest to use the shorter version (it works for me at least).

Did you try that?

---

### Post by ronb94 on 2007-12-25
yes tried nothing changed

---

### Post by Zorael on 2007-12-25
Well then, if you're sure you set it up to properly load vesafb and fbcon (removing vesafb from the blacklist), and did everything else by the book, I've no idea what could cause it.

Perhaps someone else knows.

---

### Post by derekaug on 2007-12-25
Going to reboot now, I have a feeling all will be well on my Latitude D630 now, thanks a bunch!

---

### Post by SirYes on 2007-12-28
> **Zorael said:**
> I'd love this, but I'm running Kubuntu. Is there any chance I might be able to persuade you into posting instructions for that splash? :)

You asked and now you have it. :D
Maybe a little bit late for a Christmas present, but anyway...

Remember, you can install *BOTH* splashes (not only one), then select one of the alternatives and update initrd.
Have fun!

---

### Post by gustavoavellar on 2008-01-20
[FONT=Tahoma][SIZE=1][COLOR=black]Hello,
Thank you for th[/COLOR][/SIZE][/FONT][FONT=Tahoma][SIZE=1][COLOR=black]is howto! It worked for me, eve[/COLOR][/SIZE][/FONT][FONT=Tahoma][COLOR=black][SIZE=1]n with my 1280x800 resolution. I had to make some modifications:[/SIZE]

[/COLOR][/FONT][SIZE=4][FONT=Arial Black][COLOR=black][COLOR=Blue]Step 3:[/COLOR]
[/COLOR][SIZE=1][COLOR=black][FONT=Tahoma]This is the output of hwinfo on my computer:
[/FONT][/COLOR][/SIZE][/FONT][/SIZE]```
gustavo@notebook:~$ sudo hwinfo --framebuffer
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.447]
  Unique ID: rdCR.5WU5JOR4rxD
  Hardware Class: framebuffer
  Model: "Intel(r)915GM/910ML/915MS Graphics Chip Accelerated VGA BIOS Intel(r)915GM/910ML/915MS Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(r)915GM/910ML/915MS Graphics Controller"
  SubVendor: "Intel(r)915GM/910ML/915MS Graphics Chip Accelerated VGA BIOS"
  SubDevice: 
  Revision: "Hardware Version 0.0"
  Memory Size: 12 MB
  Memory Range: 0xc0000000-0xc0bfffff (rw)
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+2560), 16 bits
  [COLOR=Red]Mode 0x0362: 1280x800 (+5120), 24 bits[/COLOR]
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```[FONT=Tahoma][SIZE=1]So, I used 0x362 in /boot/grub/menu.lst instead of 0x365:[/SIZE][/FONT]
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash [COLOR=Green]vga=0x362[/COLOR]

```[FONT=Arial Black][SIZE=4][COLOR=Blue]Step 4:
[FONT=Tahoma][SIZE=1][COLOR=Black]I changed the file /etc/usplash.conf to my resolution
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]```
xres=[COLOR=Green]1280[/COLOR]
yres=[COLOR=Green]800[/COLOR]

```[FONT=Arial Black][SIZE=4][COLOR=Blue]Step6:[/COLOR][/SIZE][/FONT]
[FONT=Tahoma][SIZE=1][COLOR=Black] The rest is the same but you have to use this file instead of the one provided by SirYes:
[/COLOR][/SIZE][/FONT][SIZE=1][COLOR=Black][FONT=Tahoma] [ATTACH]57076[/ATTACH][/FONT]

[/COLOR][/SIZE]

---

### Post by _Stevie_ on 2008-02-06
hmm, when i do a hwinfo the max resolution i get is 1024*768.
is that normal? using a notebook with a geforce 7600 go and a 1440*900 display.

---

### Post by SirYes on 2008-02-18
> **_Stevie_ said:**
> hmm, when i do a hwinfo the max resolution i get is 1024*768.
is that normal? using a notebook with a geforce 7600 go and a 1440*900 display.

Alas, it seems like some video cards have limited VBE (VESA BIOS Extension) support. At least that has been my experience with two my computers, a laptop with GeForce 8400M (good!) and a desktop with GeForce 7600GS AGP card (unsatisfactory wrt. VBE). :?

You may try using different modes for vga= parameter, but probably this will not work. IIRC I was forced to stay with 1024x768. :(
But anyway it was better than plain 80x25 text mode! :)

---

### Post by _Stevie_ on 2008-02-18
hey SirYes,

yep, seems so. thats pretty poor from the hardware manufacturers though :(
gotta live with 1024, heh.

best,

stevie

---

### Post by marvinlee on 2008-02-29
I have a Dell Inspiron 1720, GT8600M @ 1440*900, and this worked perfectly for me with a slight modification, thanks to Caravel, here:
[COLOR="DarkGreen"]
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910/](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910/)[/COLOR]

Briefly, in SirYes's [COLOR="Navy"]step 2[/COLOR]:

A. Added ** nvidiafb**  in ** /etc/initramfs-tools/modules**
B. When editing ** /etc/modprobe.d/blacklist-framebuffer**, also commented out:
[B]blacklist vga16fb
blacklist nvidiafb[/B]

In [COLOR="Navy"]step 3[/COLOR]:

A. Also modprobe'd the **nvidiafb**
B. I used **vga=0x365** in** /boot/grub/menu.lst**

...and everything worked perfectly. If anything here seems unnecessary or redundant lemme know, as I'm not always sure why I'm doing something.

Huge thanks to SirYes!

---

### Post by _Stevie_ on 2008-02-29
hi marvinlee!

did hwinfo --framebuffer give you 1440x900?

---

### Post by marvinlee on 2008-03-01
Hey Stevie, here's what hwinfo gave me:

02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.447]
  Unique ID: rdCR.RenlEygV6o6
  Hardware Class: framebuffer
  Model: "NVIDIA G84 Board - p410h1  "
  Vendor: "NVIDIA Corporation"
  Device: "G84 Board - p410h1  "
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 14 MB
  Memory Range: 0xfb000000-0xfbdfffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0349: 1400x1050 (+5600), 24 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Mode 0x0362: 768x480 (+768), 8 bits
[COLOR="Red"]  Mode 0x0364: 1440x900 (+1440), 8 bits
  Mode 0x0365: 1440x900 (+5760), 24 bits[/COLOR]
  Mode 0x0368: 1680x1050 (+1680), 8 bits
  Mode 0x0369: 1680x1050 (+6720), 24 bits
  Mode 0x037c: 1920x1200 (+1920), 8 bits
  Mode 0x037d: 1920x1200 (+7680), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

---

### Post by _Stevie_ on 2008-03-01
hi marvinlee!

thanks!

doh, i got much less entries. it must be my gfx-card then.

```
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.447]
  Unique ID: rdCR.4plRuPgVLX4
  Hardware Class: framebuffer
  Model: "NVIDIA G73 Board - fscxtb70"
  Vendor: "NVIDIA Corporation"
  Device: "G73 Board - fscxtb70"
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 256 MB
  Memory Range: 0xd0000000-0xdfffffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

---

### Post by pelle.k on 2008-03-04
Never did step 5 and onwards. I just configured grub for 1650x1080 and put;
```
xres=1650
yres=1280
```
in usplash.conf. Looks great without patching usplash. yres=1080 did *not* look that good though...
Thanks for the great howto! :)

---

### Post by damvcoool on 2008-03-28
After i reboot i get 

starting-up
you passed an undefined mode number
press [return] to see video modes avaible [space] to continue

I did everything by the book i even tried enabling nvidiafb

---

### Post by zilo on 2008-03-29
Wow. This is great! Thanx.

---

### Post by johnconnor on 2008-05-18
Hi SirYes your tutorial worked great on my Sony VAIO VGN-AR41L (GeForce 8400M GT) :KS
Thanks a lot!

---

### Post by dontcopymusic on 2008-05-28
Hi SirYes

Just to let you know your howto worked perfectly on my Sony Vaio FS315B with Ubuntu Hardy Heron 8.04 and usplash-theme-ubuntu 0.18 (!).
Also, I never did steps 1 and 2. My resolution is 1280 by 800 pixels, so I used the tar-gz file *gustavoavellar* attached to his post on page 2.

Thanks! It look so much better :)

---

### Post by BilliShere on 2008-06-17
my graphic card is messed up. I am currently using 1680*1050 resolution flawlessly on my gnome desktop (hardy heron). yet there is no such thing in the hwinfo --framebuffer. its really annoying. why cant i find a mode for that?



02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.447]
  Unique ID: you dont need to know. lol.
  Hardware Class: framebuffer
  Model: "Intel(r) 82945G Chipset Family Graphics Chip Accelerated VGA BIOS Intel(r) 82945G Chipset Family Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(r) 82945G Chipset Family Graphics Controller"
  SubVendor: "Intel(r) 82945G Chipset Family Graphics Chip Accelerated VGA BIOS"
  SubDevice: 
  Revision: "Hardware Version 0.0"
  Memory Size: 7 MB + 704 kB
  Memory Range: 0xe0000000-0xe07affff (rw)
  Mode 0x033c: 1920x1440 (+1920), 8 bits
  Mode 0x034d: 1920x1440 (+3840), 16 bits
  Mode 0x033a: 1600x1200 (+1600), 8 bits
  Mode 0x034b: 1600x1200 (+3200), 16 bits
  Mode 0x035a: 1600x1200 (+6400), 24 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown



any help?

---

### Post by SirYes on 2008-06-18
> **BilliShere said:**
> my graphic card is messed up. I am currently using 1680*1050 resolution flawlessly on my gnome desktop (hardy heron). yet there is no such thing in the hwinfo --framebuffer. its really annoying. why cant i find a mode for that?
...
Model: "Intel(r) 82945G Chipset Family Graphics Chip Accelerated VGA BIOS Intel(r) 82945G Chipset Family Graphics Controller"
...
any help?
Looks like your graphics card has no support for the VESA mode you're looking for. VESA support in the form of VBE (VESA BIOS Extension) varies between manufacturers and even between card models from the same manufacturer. Support for the "normal" operations like you described is different, since X drivers do not use the VESA BIOS at all (it would be dog slow in such case).

I'm afraid I can't help you much here. And I really don't have access to any Intel-based graphics card, so I can't test whether it would work or not. I suggest you to choose a mode that best matches physical reslution of your LCD and live with it. At least that would be a bit (a lot?) better than ordinary 80x25 text mode...

---

### Post by screaminj3sus on 2008-07-18
I'm running 1440x900, but this doesn't work for me, when I boot up it says video mode not supported.

  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0349: 1400x1050 (+5600), 24 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Mode 0x0362: 768x480 (+768), 8 bits
  Mode 0x0364: 1440x900 (+1440), 8 bits
  Mode 0x0365: 1440x900 (+5760), 24 bits
  Mode 0x0368: 1680x1050 (+1680), 8 bits
  Mode 0x0369: 1680x1050 (+6720), 24 bits
  Mode 0x037b: 1280x720 (+5120), 24 bits
  Mode 0x037c: 1920x1200 (+1920), 8 bits
  Mode 0x037d: 1920x1200 (+7680), 24 bits
This says 1440x900 is supported fine though. I unblacklisted the vesa framebuffer and even tried unblackisting the nvidia buffer but to no avail.

---

### Post by SirYes on 2008-07-22
1. And how does your menu.lst look like? Maybe you could post it here?
2. Have you tried any other mode from the list above? Did it work?

Honestly, I never touched 9600GT so far. But from the list it really looks like the procedure should work.
That's strange indeed. :-k

---

