---
title: "No input at all"
date: 2008-11-18
forum: General Help
---

### Post by RXRob on 2008-11-18
Hi everyone. First time Linux user having got sick of Windows security issues, and about to go back anyway I think.

I've installed ubuntu 8.10 alongside XP SP2, on an unmodified one of these [IMEDIA 1403]("http://support.packardbell.com/uk/item/?m=home&sn=041103420144")

I have a USB mouse and a P/S2 Keyboard, and I can't recieve input from either of them.

Now I've already searched the forums, and from the console accessed by hitting ctrl+alt+f2 I have so far tried:
> sudo apt-get install xserver-xorg-input-all

> sudo dpkg-reconfigure xserver-xorg

> sudo dpkg -reconfigure -phigh xserver-xorg

> sudo apt-get dist-upgrade

On top of this, I have to tap ctrl+alt+backspace when I boot up before I can even see the login screen that I can't use.

Am I really doomed to spend my life fighting off every little thing that decides it wants to muscle in onto my Windows PC?

---

### Post by RXRob on 2008-11-19
I guess that's a no then

---

### Post by tseligkas on 2008-11-19
Sorry,

I don't understand your problem. You say you don't receive input from either mouse or keyboard. How did you manage to type keys for ctrl+alt+f2 and ctrl+alt+backspace?

If the mouse only is not working, you may have to get into your PC's BIOS and enable USB mouse/keyboard support.

If the keyboard works with key combinations but you cannot type text on a gnome editor for example (which I think unlikely) you may have to check your keyboard layout.

---

### Post by RXRob on 2008-11-19
On the actual login screen the only thing I can enter is the key combinations mentioned earlier. In the console my keyboard works fine. When I installed I set up my keyboard for UK, and it worked fine during installation.

At the login screen I can see the cursor flashing in the box, so I know that IF I could type, it should appear in said box.

---

### Post by tseligkas on 2008-11-19
In that case I can only think of the following:

- Hardware problem. Keyboard keys stuck (like Alt+Shift or Ctrl+Shift) -> Replace/fix keyboard.
- Software problem. Configuration or system conflict -> Try booting with LiveCD and if mouse/keyboard work there try copying your xorg.conf to your installed linux environment.

---

### Post by RXRob on 2008-11-19
> **tseligkas said:**
> In that case I can only think of the following:

- Hardware problem. Keyboard keys stuck (like Alt+Shift or Ctrl+Shift) -> Replace/fix keyboard.
- Software problem. Configuration or system conflict -> Try booting with LiveCD and if mouse/keyboard work there try copying your xorg.conf to your installed linux environment.

It isn't hardware because everything is as fine as can be expected in XP.

Keyboard and Mouse work perfectly on LiveCD. So how do I find xorg.conf and where do I have to copy it to?

Edit: I've just discovered that my keyboard is set to US when I use LiveCD. I don't know if that makes any difference

---

### Post by RXRob on 2008-11-19
Right I found the files, but I couldn't overwrite xorg.conf from LiveCD due to not having the correct permissions.

I have a copy of the file from LiveCD on a USB stick, just waiting to stick on my hard drive, but being a first time Linux user I don't know how.

Help?

---

### Post by tseligkas on 2008-11-19
OK, so you found a working xorg.conf from your LiveCD environment. When booting from LiveCD your hard drives/partitions (any OS) are automounted, I think in /media/hda1, hda5 etc. (you may have something different than hda). If you don't see anything in /media directory try the /mnt dir.

You should now find one of the drives containing your linux installation. You will recognise it by its structure (containing folders /etc, /root, /var etc.). So go to the etc/X11/ directory of your linux installation from a terminal (be careful not to go to the LiveCD's one) and type the following (this is an example; you may need to change the last part of the command depending on the drive):
```
sudo cp /etc/xorg.conf /media/hda5/etc/xorg.conf
```If it asks for a password, it is the one you created for your user.

After doing that open the new xorg.conf to verify that it has been overwritten and if it's ok reboot without the LiveCD.

Hope that helds. If not, I'd suggest reinstalling your ubuntu (I assume you won't lose much data) with whatever configuration works from the LiveCD and then do your modifications within the installed system.

---

### Post by RXRob on 2008-11-19
> **tseligkas said:**
> So go to the etc/X11/ directory of your linux installation from a terminal 

I understood all of that post except for this bit. How to I access it from a terminal?

I apologise, I had never touched Linux before I installed this last night.

---

### Post by RXRob on 2008-11-20
Bump. So close, yet so far

---

### Post by RXRob on 2008-11-22
Sod it, I'm gonna delete the Ubunutu partition and stick with my spyware, I mean Windows. At least I can use my mouse and keyboard on that.

---

### Post by tseligkas on 2008-11-25
RXBob, sorry for the late reply. I was busy. I think that replying to your last question doesn't mean much now.

However, for the record (other visitors) I meant your hard-drive installed Linux, not your LiveCD session. So if the root drive of your Linux installation is in /media/hda5/, then your faulty xorg.conf should be in /media/hda5/etc/X11/. If you look closely at the command I posted it will make sense.

If all this seems too complicated try re-install or go to your windows installation and insert the Ubuntu CD. From there it is possible to install Ubuntu in Windows. If you don't like it you can just go to Add/Remove Programs and uninstall it! If you want to see how it works, check [COLOR=Sienna]**[this]("http://wubi-installer.org/")**[/COLOR].

As far as this
> Sod it, I'm gonna delete the Ubunutu partition and stick with my spyware, I mean Windows. At least I can use my mouse and keyboard on that.is concerned, generally speaking, do not despair of Linux. Sometimes even Windows present issues upon installation. But with Linux you have many alternatives. Ultimately, you can always try a different distribution. You can check Fedora Core, OpenSuSE, PCLinuxOS, [COLOR=Sienna]**[you name it]("http://distrowatch.com/")**[/COLOR]!

---

### Post by JiltedCitizen on 2008-12-04
I kind of have the same problem.  My mouse and keyboard work for a bit, then decide to lock up.  Not even ctrl+alt+backspace works.

---

