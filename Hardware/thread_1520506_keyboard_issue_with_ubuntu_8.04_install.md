---
title: "keyboard issue with ubuntu 8.04 install"
date: 2010-06-29
forum: Hardware
---

### Post by disparais on 2010-06-29
My parents had a strange computer problem come up, and they asked me to fix it. That said, I'm a little sketch on what happened immediately preceding it (I no longer live with them), but here are the main pars of their story:
-my sister switched out her Logitech keyboard for the family keyboard
-my mother complained that the computer was running much more slowly; she tried to run MSE, but something went wrong, and she restarted
-she tried to do system recovery through the BIOS, but it was ended abruptly somehow (summer storms or maybe her impatience, iono)
-the computer no longer load

In loading the computer, the keyboard doesn't register until after you can no longer do anything with it. This is an issue across the three keyboards I used, as well as any of the open USB ports. The mouse starts up as normal, however. It has been impossible so far to load system recovery or bring up the BIOS options.

The keyboard would register at this point (would require being removed and plugged back in), but not earlier!, with an error message on the screen before the operating system loaded:

"Windows couold not start because the following file is missing or corrupt:
<Windows root>\system32\ntoskrnl.exe.
Please re-insta;; a copy of the above file."

The recovery disk we owned didn't register, and at this point, my mother was willing to give Ubuntu a try.

Their specs are:
-512 GB RAM
-original OS was Windows XP
-160 GB HD space
-3400+ AMD processor
-the comp itself is a Compaq
-purchased in 2006

I wrote two discs:
-a DVD copy of 10.04
-a DVD copy of 08.04

The 10.04 disc didn't load at all. It paused on the BIOS screen in the very, very beginning where white text registers the CD in the drive that it's about to load from. The longest I waited was 15 minutes, and nothing happened. Reboots yielded similar results. I booted the CD on my own desktop, and I didn't have any of these problems. It occured to me the recommended specs for Ubuntu 10.04 were higher than what my parents had, so I wrote the older disk instead. I didn't take the advice of the Ubuntu main website to use a different distro, because I honestly don't think my family would adapt.

8.04 was little better. 8.04 did get past that screen and offered me a screen where I could choose the language. This is the point at which the keyboard would light up and register, but I couldn't hit enter for the selected "English option." At that point, I'd be at an impasse and could do  little more than turn the computer off. Again, I'd like to stress that the mouse registers, the speakers register, and the DVD drive all register. The only external hardware issue is the keyboard.

Sorry for the tl;dr type post, but I was concerned any information I had might be useful in figuring this one out. I only barely know enough about hardware and software to troubleshoot my own problems.

What can I do to force the computer to read and write the disk?

Thanks a lot for anything you can offer.

anni

---

### Post by nixscripter on 2010-06-29
Does the BIOS have a "USB legary keyboard" mode? That can cause all sorts of strange problems.

---

### Post by disparais on 2010-06-30
Nope. ):

---

### Post by nixscripter on 2010-06-30
Well, that was fast.

One thing you might try doing is burning a [Knoppix]("http://www.knoppix.net/") CD and see how far it gets. It will explain what it is doing during boot, and may report and error or other problem that Ubuntu would suppress.

Ubuntu has debugging options, but I don't know if the LiveCD uses them or not.

---

