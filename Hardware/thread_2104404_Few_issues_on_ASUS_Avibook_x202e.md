---
title: "Few issues on ASUS Avibook x202e"
date: 2013-01-13
forum: Hardware
---

### Post by Arjunanda on 2013-01-13
I have a few issues on my othervise fantastic ASUS Avibook X202E / F202E:

1. The touchpad has a "swing-button", thus to simulate 3rd mouse button (i.e. to paste text) by clicking both buttons is not possible. Any other way to simulate 3rd button? Some mouse gesture?
2. Touchpad is too sensitive, and the cursor jumps easily away while typing.
3. The screen brightness keys are not working. All other fn+F keys are working, in cluding blank screen, volume etc. (external screen key not tested)
4. Wired network connection (RJ-45 connector) not working - no link led.
5. Auto-hide of unity dock not working

---

### Post by Arjunanda on 2013-03-13
Anyone?

---

### Post by tux-gamer on 2013-03-15
1. I f you using KDE Desktop , you can set it under "System Settings" -> "Hardware" -> "Input Device" -> "Touch Pad" -> "Tapping" --> "Tapping with three fingers" = "middle mouse button"
Or you can read here [http://www.linlap.com/asus_x201e](http://www.linlap.com/asus_x201e) ( i write this ), go to section "Notes" and read "improved clickpad"

2. i don't have that kind of issue, looklike you need to get used to it.

3. You need to manual set it up, read here again [http://www.linlap.com/asus_x201e](http://www.linlap.com/asus_x201e) ,  go to section "Notes" and read "How to have brightness control :"

4. hmm, i don't understand this question.
i have X201E ( an X202E without touchscreen display ) and i can connect it to my desktop pc (use PClinuxOS distro ), i connect it to transfer my anime collection to my laptop, i can get 8MBps speed.

5. i don't know, i don't like Unity dock, i use KDE Desktop , i love KDE Desktop since i use Mandrake 8.0

---

### Post by Arjunanda on 2013-03-16
1. Yes, I installed also kubuntu desktop and found that option, but felt too much out of my comfort zone with the kubuntu behaviour, could not find my config options, felt weird with the 1-click stuff etc, so I shifted back to Unity. Is there not similar thing in Unity desktop?
2. Well, cannot get used to it, as it detects my finger even from distance when not touching the pad. It is hypersensitive, and as such quite irritating.
3. Will do the manual setup, thanks :)
4. The physical ethernet port is not working. When I try to plug a LAN cable (RJ-45), even the link LED on the laptop or the router remains blank. Perhaps no driver for this chipset. 
5. The auto-hide started working after last upgrade.

---

### Post by Arjunanda on 2013-03-21
3. Latest update fixed the problem before i was able to use your script. This is great :)

---

### Post by Arjunanda on 2013-03-22
Dirver problems solved with this:

```

sudo apt-get update; sudo apt-get upgrade; sudo apt-get install linux-headers-generic build-essential
wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1-snpc.tar.bz2
tar -xf compat-wireless-3.5.1-1-snpc.tar.bz2
cd compat-wireless-3.5.1-1-snpc
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx

```

---

