---
title: "Successful Install on Lenovo 3000 N 100"
date: 2006-08-08
forum: Hardware &amp; Laptops
---

### Post by rajeshrs on 2006-08-08
Hi all,

Just installed Ubuntu 6.06 Dapper Drake on my Lenovo 3000 N100. Here is a summary of what went right and what did not. Hope this helps others make a laptop decision, since the laptop is real value for money.

1. My laptop has an Intel GMA 950 and a WXGA LCD, so Xorg wasnt configured by default for 1280 X 800. Had to use the package 915resolution using "sudo apt-get install 915resolution" and then change the i810 settings using this. I guess there is already an article on this. Xorg gave me some problems when switching resolutions before, but when I used the 915resolution program it was a snap!

2. Sound was enabled by doing the snd-intel-hda thing. It wasn't enabled by default too. MP3 playback was also not ready by default. I installed XMMS and the Enlightened Sound Daemon plugin for that...available at xmms.org I guess.

3. Synaptic Touchpad and my USB wheelmouse (optical) both got detected properly with no issues. There was a problem with getting the USB web camera built into the laptop to work. I still don't have the drivers which get it to work. Can anyone help me out? There was no driver available for the fingerprint reader (and it didnt get detected in Ubuntu as well...got detected in Mandriva 2006 though).

4. The function keys work and so do the special volume buttons. No problems there but for the Lenovo help center button which gets activated through a software present in Windows XP (comes installed). I dont think there is a suitable driver for this in Linux.

4. Ubuntu seems to have detected processor 0 (the Lenovo 3000 has an Intel Centrino Core Duo, mine is the T2300 version with 1.6 GHz) but doesnt seem to indicate processor 1. Correct me if I am wrong though. I had installed Mandriva 2006 (from the DVD) before Dapper, but that detected that it was a "dual processor" machine. The machine runs cool for desktop applications, but when I installed Nexius (a first person shooter based on the old Quake engine) and fired it up, the framerates were on the lower end. And this is a machine which (on windows xp) runs Unreal 2 and Quake 4 (both top game engines) at acceptable framerates (30 something) in 800 X 600. Can anyone help me out on this? Also, does the i810 driver for Intel 945GM on linux support hardware acceleration?

5. I am disappointed that ICEWM, Enlightenment and Windowmaker do not bundle with Ubuntu. IMO these are the most elegant window managers in Linux for some time now. KDE and Gnome offer a lot of functionality though and are quite user friendly. Had to do an apt-get for them again.

Apart from these glitches on my Lenovo (which may not be there on desktops or more conventional laptops), Ubuntu is a truly world class OS and I am thoroughly enjoying working with it.

Cheers!

---

### Post by TheMono on 2006-08-08
Thankyou for the report and some intelligent questions!

The i810 driver does support hardware acceleration, but I couldn't tell you how it works with your specific chip unfortunately. I'm using one of the 82855GM chips and works fine for me...

[EDIT:
Sorry, I tell a lie, I was wrong with what I originally had here. Just upgrade to the 686 kernel which contains SMP support by default now. Ubuntu ships with the 386 which doesn't.

Install linux-image-2.6.15-26-686

---

### Post by rajeshrs on 2006-08-08
TheMono,

Thanks for the image specification. Shall install and let you know if SMP support works. Should upgrade to the 686 version f the kernel I guess, since even the older Mandriva 2006 came with a 686 version.

Meanwhile, anyone has any idea on how to activate the webcam built into the Lenovo 3000? Any ideas about enabling the fingerprint reader? (I gather quite a few linux users use thinkpads, a fair share of which have these fingerprint readers.)

Two things I found strange about Ubuntu was the root account (there was none...just sudo) and the absence of a compiler! I mean, how is one expected to compile tarballs without gcc? But you have to congratulate them on sudo as well as apt-get. Its fairly simple once you have your network setup and the universe and multiverse packages selected in that conf file.

I am looking for an IDE for linux which has the functionality of MS Visual Studio on Windows. Had checked out KDevelop once before but it seems a heavy download (or atleast a long one). Anyone have any recommendations for the IDE? Or does this Q belong in another forums here?

Thanks,
Rajesh

---

### Post by sfabel on 2006-08-10
I'm not sure what type of N100 you guys have, but I have nothing but trouble with mine:

- CD-ROM / DVD / DVD DL burning doesn't work. I'm using Kubuntu 6.06 and k3b, and it *always* fails no matter what I try (or so it seems). My physical CD/DVD burner gets detected as two different devices: /dev/scd0 and /dev/sg1. I don't know why or if this has anything to do with it. I also opened up another thread [here]("http://www.ubuntuforums.org/showthread.php?t=233125").

- fingerprint reader doesn't work.

- webcam doesn't work

- neither suspend to RAM nor disk works.

- no volume button has *any* effect on anything. It doesn't matter whether I try the extra volume button or the FN+F1/F2 combination.

Does anyone have any idea what I could do? I'm using an the linux-686 package, so it is SMP enabled (and I see both cpus).

---

### Post by renaissance on 2008-01-16
Hello, i have questoion. what kind wifi card and chipset are used in Lenovo 3000 n 100

---

### Post by starryeyedboy on 2008-03-06
> **renaissance said:**
> Hello, i have questoion. what kind wifi card and chipset are used in Lenovo 3000 n 100

it is a broadcom 43xx card. most likely 4328, but that's not really an issue. to install it, u can do the below:

install ndiswrapper:
> sudo aptitude install ndiswrapper-utils-1.9

install wifi card driver, n enable it:
> wget [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE)
mkdir driver
unzip -a R151517.EXE -d driver/
cd driver/DRIVER/
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l
sudo ndiswrapper -m

best done on a clean install, without previous versions of ndiswrapper!

credited to Micah Carrick, [http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes.html](http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes.html)

whose solution works like a charm every single time =)

---

