---
title: "Logitech MX700 mouse MX5000 keyboard"
date: 2006-06-07
forum: Hardware &amp; Laptops
---

### Post by roderikk on 2006-06-07
Hi,

Just recently I received a Logitech MX700 and MX5000 which connect using a Bluetooth USB dongle. And the standard 2 mouse buttons and keyboard functioned out of the box in Dapper.

Today I also became frustrated that I have 7 buttons on my mouse and only 2 + scrollwheel would work. So I did some searching and this 'solution' helped me to use the back/forward button in the browser: [here]("http://linux.wordpress.com/2006/06/06/tip-my-logitech-mx700-mouse-with-linux-and-firefox/").

Just a recap:

```
sudo gedit /etc/X11/xorg.conf
```

And add to your 'mouse' section the last two lines (buttons and buttonmapping). It should look something like follows:

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option	   "Buttons" "7"
    Option	   "ButtonMapping" "1 2 3 6 7"
EndSection
```

I don't know whether this is a really good solution or just a workaround, but it works in my dapper with XGL/compiz on so I hope it helps someone.
In the first period when I started using this mouse it was really slow very often. I heard from someone that Logitech apparently released this type of mouse with some sort of faulty drivers so I had to actually plug the dongle into a windows computer, install all the logitech software and do a full update on the drivers. Now I do have a thermometer on my keyboard and my mouse is almost never sluggish again.

On the keyboard side however, I can use it to enter the BIOS straight after starting the computer, but I can't switch between options in GRUB. Also when I do a fresh install from either the liveCD or the advanced CD I cannot use the bluetooth keyboard to choose an option. Letting the counter go to 0 in grub puts me through and I can login using the MX5000 again. Is this a bug?

Besides it will also quite often after a period of inactivity, when I start typing again, print the first character twice, making me ssudo quite a lot. I don't know whether this has something to do again with ubuntu suspending (or something) the usb bluetooth dongle or with the keyboard itself.

Should I file a bug on these last two items?

---

### Post by ampes on 2006-06-09
coool....now my mx700(ps/2) mouse can browse happily again...ive read all HOWTO in this forum just to make my thumbbtn works but none works until i read your post..so the hint just number of buttons and btn map.thanx..plus,i dont need logitech-applet etc..just need simple easy usage..

anyway,does someone with MX700 Dou keyboard able to ctrl volume(master volume) with vol controller on this keyboard?

---

### Post by roderikk on 2006-06-09
Hi,

I am glad this helped you. My volume control seems to be working with my mx5000 keyboard. However, now that I've installed XGL/compiz none of my multimedia keys work (not even my Super/windows key) no matter what keyboard layout I set.

You might want to check out [Lineak]("http://lineak.sourceforge.net/"), even though I don't recall your keyboard being recognized you can try to get it recognized yourself.

---

### Post by ampes on 2006-06-09
[QUOTE=roderikk]
I am glad this helped you. My volume control seems to be working with my mx5000 keyboard. However, now that I've installed XGL/compiz none of my multimedia keys work (not even my Super/windows key) no matter what keyboard layout I set.
[/QUOTE]

Hmm strange kb problem...thats why i dont want to try xgl/compiz yet until stable release is out..BTW yesterday i managed to ctrl master volume through volume button on my keyboard and played with it quite a lot(glad it works\\:D/ )
dont remember what ive done(nothing been edited and it works suddenly) and today when i turn on my pc,the function gone:cry:.. then i tried to config Lineak but failed..got this message after run ./configure...

```
yus@yus-linux:~/Desktop/lineakd-0.8.4$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking whether g++ supports -Wmissing-format-attribute... no
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... no
checking whether g++ supports -Wno-long-long... no
checking whether g++ supports -Wnon-virtual-dtor... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
yus@yus-linux:~/Desktop/lineakd-0.8.4$ make
make: *** No targets specified and no makefile found.  Stop.

```

---

### Post by roderikk on 2006-06-10
First of all, I believe Lineak is in the repos, so you could just install from there.
Secondly, recently I had my first shot at installing something from source and figured out you need a lot of stuff to do that. You can find my progress in [this thread]("http://ubuntuforums.org/showthread.php?t=191522"). I don't know whether you ever compiled before, but if not some of the stuff in that thread might be useful. I don't know a tutorial/step by step guide that walks you through a first compile from source...

Good luck, and let me know how you are proceeding!

---

### Post by ampes on 2006-06-12
well now I am able to use my multimedia buttons on the keyboard..Set them from System>Preferences>Keyboard Shortcuts and alot of keys can be applied to various controls...About the volume controller,I have to disable manually from BIOS my onboard sound device so my SBA2 ZS is selected as default..Now my input devices and controls completed...

---

### Post by SpiritIsReality on 2007-05-04
howdy all!
just one bit that I found to enter bios.
the wxp install cd has a manual, start>allprograms>logitech>mouseandkeyboard>help.
it said that to make the f keys perform standard actions, to press the fmode key so that 
an f symbol shows in the keyboard display. 
once that was done and the computer recycled, typed f2 key to enter setup, bios,
for the d915pbl motherboard.
hope this helps somebody.
glad you are all here, this forum has been a great help.
happy trails all!

---

