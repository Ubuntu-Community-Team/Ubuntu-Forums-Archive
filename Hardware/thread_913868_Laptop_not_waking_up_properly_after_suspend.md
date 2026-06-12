---
title: "Laptop not waking up properly after suspend"
date: 2008-09-08
forum: Hardware
---

### Post by Jorge_C on 2008-09-08
Hi,

My laptop suspends fine, but when it wakes up the keyboard/touchpad are unresponsive and the screen shows kind of vertical bars of different colours. Then, I have to hard power it off holding the power button.
It's an HP Pavilion dv7-1080es with an nVidia 9600M GT running Hardy 64 bits.

Any ideas on how to make it wake up properly? Thanks in advance

---

### Post by tazblbl on 2008-10-18
Hi,
I have the same kind of problem on a VAIO PCG-GRT915M with GeForce Fx Go5600 graphic card . But waking up leads to a black screen. The only way to escape is to hard power off the computer.I think it's because when I installed the driver nvidia it was not activated in the waking up sequence as in the normal boot sequence. If somebody know how to insert it ?

---

### Post by whichpaul on 2008-11-06
I have a HP Pavilion dv5-1075er and it also does not wake up properly from suspend. It will give me the "unlock" screen, but after I enter my password I'm simply left with a blank screen and a mouse cursor. Hibernate, however, does seem to work properly, albeit a few spurious looking error messages that wizz by in the process.

HP Pavilion dv5-1075er: Intel Core 2 Duo 2.4Ghz / 3GB RAM / Nvidia 9600M GT 512MB / 320GB HDD / Plus all the other toys...

---

### Post by Jorge_C on 2008-11-08
Now I'm using Intrepid, and the laptop still goes to suspend fine but it won't wake up properly.

With Intrepid I am left with a black screen and a cursor I can move, but I can't do anything at all. I can switch to the terminals, but I can't even login since some error messages start appearing. I can also kill x with ctr+alt+backspace: my wallpaper will flash for a split of a second, and I will get to a terminal that throws more errors but doesn't let me write any commands. Fortunately enough, the keyboard works and I can use sys req + REISUB to reboot more safely.

---

### Post by salsa95 on 2008-11-09
I'm having similar problems with my HP Pavillion DV5000.  Upon waking from suspend or hibernate, I get no screen display at all, and no cursor.  I'll have to try the REISUB trick to see what happens the next time.  Sure would be nice to have the power management working though!

---

### Post by stitchmysmile93 on 2008-11-09
I have the same problem with hp pavilion dv2000...

---

### Post by s60mjk23 on 2008-11-09
i am also having the same problem with my hp pavilion dv5 1000. i am dual booting vista and ubuntu 8.10, and when i wake up from suspend it goes to a black screen and i have to hold the power to turn off. 

i posted a thread about this like 5min ago, then i saw this post. if i find out anything i will let you guys know. it is a really irritating problem.

---

### Post by whichpaul on 2008-11-10
I took a few moments to run the scenario over again and observe some error messages. The results were not very helpful for my level of knowledge but I was able to track down a recently closed bug in the Linux kernel that appears to be getting some sort of current scrutiny. While I can't be 100% that it is the exact bug that I'm suffering from it does seem uncannily similar. (Hint: you need to take time to view the various links and attachments in the bug report to be sure this is relevant to you).

[http://bugzilla.kernel.org/show_bug.cgi?id=11845]("http://bugzilla.kernel.org/show_bug.cgi?id=11845")

It appears that the patch is in line for the next release of the kernel ( 2.6.28 ). I think I might wait for that if it doesn't take too long, I have other things to do besides recompiling kernels all weekend.

---

### Post by calibre97 on 2008-11-11
HP dv5035nr with 1.5GB RAM and 2.5GB swap. I can suspend to RAM just fine, and in fact just woke it up after leaving it suspended overnight...BUT...wireless is kaput. I have to configure it to wake locked because for now it just pops back into the screen I left it at. I can't connect to my network and if I take out the PC Card and pop it back in, wireless is completely gone. I'll have to try just restarting networking after waking it up.

---

### Post by Jorge_C on 2008-11-11
When trying to resume from suspend, I get some errors about ata5 irq_stat status changed and ata1 except Emask...Where are those things logged? I'd like to read them and do some more research.

The last thing that appears after resuming which isn't an error yet is about not starting k desktop manager because it is not the default one (I have kubuntu-desktop installed). So I tried suspending from a kde4 session, and instead of getting a black screen with a cursor I got back to the desktop, but it was unusable, the icons disappeared (and didn't come back) after hovering the mouse on them, I couldn't launch any apps...

Any way, I'll probably reinstall soon and see what happens in a clean install.

---

### Post by crysys on 2008-11-11
Same problem here using Acer Extensa 4420.  No keyboard, no trackpad, no usb mouse after waking up.  I can put it to sleep by closing the lid and on waking they all work; sometimes.  If I choose any options from the logout menu everything locks up.  I'm using the ATI binary driver.

---

### Post by SpoonerPS3 on 2008-11-11
I have an HP dv2600(nvidia 8400gs) and suspend didn't worked when I first installed Ubuntu 8.04 on it. On one of the Kernel updates, it finally worked, kind of. It would resume 5-6 times, but then would hang. On 8.10, it hasn't failed me once. You guys might also want to try suspend from the keyboard(fn + suspend key) and clicking suspend on the desktop. I have a friend with an Inspiron 1520, and suspend works  and resumes when you do it with the mouse, but with the keyboard, it woudn't resume back. He just gets weird colors and stuff.

---

### Post by Huss on 2008-11-13
Similar problem here

NEC Versa P8100 laptop. Sometimes suspend works beautifully, other times it will wake up but with a blank screen. I've tried restarting X with ctrl alt backspace - it logs out but stays blank

Any clues?

---

### Post by phoogkamer on 2008-11-17
I have the same problem on a Acer Aspire 5051AWXMi. Suspend works ok, but after resume I can go to a console and have command-line, but console 7 (X-server) gives me a black screen and is unresponsive. Xorg log gives me errors regarding to fglrx, but I don't know if the are relevant. I also get a fail message when restarting GDM.

---

### Post by heidricha on 2008-11-17
HP/Compaq 6715B does the same. Goes down to suspend fine, but sometimes can recover, sometimes not. 
It is upgraded from Hardy, the same problem had existed when upgraded to Hardy as well, but after a while it had disappeared.
CPU scaling does work. I suspected powernowd, but deselectin/stopping this did not make any difference.

---

### Post by Huss on 2008-11-19
I've upgraded to 8.10 and the bug seems to have been fixed.

---

### Post by duffrecords on 2008-12-05
If you're using an AGP card, make sure the correct AGP module is being loaded.  For example, my laptop has an NVIDIA GeForce4 440 Go and suspend/hibernate will not work with the agpgart module.  Each time I upgrade to a new version of Ubuntu I have to remember to edit /etc/X11/xorg.conf and modify this line in the "Device" section:```
Option     "NvAGP"     "1"
```so that it's forced to use the nvidia module.

---

### Post by Jorge_C on 2008-12-05
Thank you duffrecords, but the graphic card in my laptop (nVidia 9600M GT) is using PCI-Express.

---

### Post by miaviator278 on 2008-12-12
The keyboard and touchpad problem seems prevalent even with all of the Ibex updates to date.  

Try plugging in a usb mouse and keyboard to ensure that this is the same problem.  

Then try switching to a terminal 
```
sudo -s
echo 8 > /proc/sys/kernel/printk
pm-suspend
```

and see if says anything use full.

Anyone know why my Quickplay button says it is the "v" key?

---

### Post by Jorge_C on 2008-12-12
Wow, when reading your post I remembered I hadn't tried suspending with a mouse attached (why should it make a difference?) but I gave it a try, and it worked! Now my laptop wakes up fine from suspended.

Then, I tried without the usb mouse attached, with the generic kernel instead of the custom one I usually use, and everything went well!

So, maybe a software update solved my issues? I haven't got a clue. Doing a clean install and applying all updates would show if that was the case, but I just can't do it.

miaviator278, your laptop recognizes the quickplay button, doesn't it? Mine isn't recognized, and I can't set it to launch a media player or something. Despite this, the rest of the touch buttons do work...

---

### Post by miaviator278 on 2008-12-12
> Wow, when reading your post I remembered I hadn't tried suspending with a mouse attached (why should it make a difference?) but I gave it a try, and it worked! Now my laptop wakes up fine from suspended.

Glad I could inspire you!

Here is my list of issues and hardware:
HP DV7-1135nr  ATI 3200HD graphics AMD turion RM-70 CPU

Sound: product: RS780 Azalia controller Driver: snd_hda_intel
Problem: headphone jack doesn't work

WiFi: product: AR242x 802.11abg Wireless PCI Express Adapter driver=ath5k
Problem ATH drivers are SLOW Ndiswrapper doesn't work I've tried 4 sets of drivers so far.

My quickplay buttons are all recognized but the actual quickplay button is recognized as the V key so I can't bind it to anything.

Suspend/Resume looses mouse and keyboard (I am using intrepid proposed) I will be custom compiling a kernel to find out if it helps this issue.

---

### Post by miaviator278 on 2008-12-12
> your laptop recognizes the quickplay button, doesn't it? Mine isn't recognized, and I can't set it to launch a media player or something. Despite this, the rest of the touch buttons do work...

If you run ```
xev
``` and press the quickplay button does it give you a keycode or nothing?

---

### Post by Jorge_C on 2008-12-13
Unfortunately, xev gives me nothing when I touch the quickplay button.

Regarding your problems, I'm sorry I can't really help you, but this [opensuse thread]("http://forums.opensuse.org/applications/multimedia/401150-no-sound-rs780-azalia-controller-sbx00-azalia-intel-hda.html") might have some interesting info, although you may have already read it. 

Wifi...I've quite some problems with it...I can connect to unencrypted networks fine, but wpa ones are no go. First I had problems with the default key ring, which wouldn't unlock, but I managed to solve them deleting some files and creating them again. Right now, if I try to connect to a wpa network, it will keep asking me the network password, though it's well-written, and never connect. It's an intel wifi link 5100 agn, by the way.

---

### Post by Jorge_C on 2008-12-13
Finally, I found out why my laptop wakes up properly after suspend: I had updated the BIOS to version F21 a few days ago! So if you have a hp dv7 try upgrading it and see if it works for you.

---

### Post by esmurdo on 2008-12-13
Jorge_C, I have a dv9910, which should be the same bios. how did you update yours? I'm lost on the steps.

---

### Post by Jorge_C on 2008-12-14
In order to update the bios, you'll need to boot into windows.

Download the appropriate bios update from hp's website. For instance, [here is the site]("http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?lc=en&dlc=es&cc=es&lang=es&product=3740565&") for the dv9910us, if this isn't yours, just search it. Then, somewhere you'll find "drivers and updates" or something similar. Just makes sure you get the update for your windows OS.

The actual update is really easy, in fact the file you download is an .exe. Remember to run the updater with the laptop plugged into the current and the battery charged, since a power loss while doing this can cause lots of problems.

---

### Post by esmurdo on 2008-12-14
Is Window$ the only way to update the BIOS? Does anyone know of an opensource program that can do the job as well?

---

