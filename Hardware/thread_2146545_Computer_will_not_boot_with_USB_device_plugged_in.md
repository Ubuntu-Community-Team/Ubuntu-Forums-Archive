---
title: "Computer will not boot with USB device plugged in"
date: 2013-05-18
forum: Hardware
---

### Post by ICouldBeAnyone on 2013-05-18
I turned on my computer this morning and found that all I saw was the bios splash screen. The BIOS had hung, there where no boot options displayed (normaly it says "F9 Boot Menu  F10 Setup" etc).

I have had this problam before when one of my hard drives died, so I tried unplugging my main HD and my CD drive, still wouldn't boot. So I unplugged all the USB devices connected to the computer (after plugging the HD and CD drive back in), and the computer booted. Now there is another issue, I have a power on password, so I need the keyboard plugged in. I tried plugging in the keyboard when it asks me for the password (and not when I press the power button) but the BIOS then hangs at that screen!

I am unable to find a BIOS or CMOS reset pin on my motherboard so I don't know how to take the password off without using the keyboard, I tried taking the BIOS battery out for 5 mins but that did not reset the password. After doing the battery thing, the BIOS stopped hanging, but the keyboard still does not work - and I tried two keyboards!

The computer case, motherboard and processer are from an HP Compaq dx7300 Microtower, and I have changed the CD and HD drive out of it, as well as adding a 2GB ram chip. It was working last night but not this morining!!!

I am verry annoyed :mad: -- Not at you (why would I be annoyed at you, you are trying to help me :)) but at the computer!!!

Thanks in advance!

---

### Post by 2F4U on 2013-05-19
I would think that the keyboard has to be plugged-in from the beginning (power-on) to be functional. I guess you already tried different USB ports? Is the keyboard connected directly to the PC or through a USB hub? If you are using a USB hub try if it works when its directly connected.

---

### Post by stylintile on 2013-05-19
Hi,
     I had a similar problem once before.  I had to unplug the usb keyboard and plug in an old PS2 keyboard that I had laying around.

---

### Post by ICouldBeAnyone on 2013-05-20
> **2F4U said:**
> I would think that the keyboard has to be plugged-in from the beginning (power-on) to be functional. I guess you already tried different USB ports? Is the keyboard connected directly to the PC or through a USB hub? If you are using a USB hub try if it works when its directly connected.

Sorry for the late reply, I don't think my BIOS checks for a keyboard on startup, I do know of some that do.

---

### Post by ICouldBeAnyone on 2013-05-20
> **2F4U said:**
> I would think that the keyboard has to be plugged-in from the beginning (power-on) to be functional. I guess you already tried different USB ports? Is the keyboard connected directly to the PC or through a USB hub? If you are using a USB hub try if it works when its directly connected.

I have borrowed an old PS/2 keyboard from a friend, I haven't tried it yet. But I need the USB devices plugged in to be able to print, use my externel HDD, use the internet (wifi) and use my Ubuntu mouse (It lights up orange :)).

I will try this PS/2 mouse, but it could be new computer time.

Any more help would be appreciated!
Thanks!

---

### Post by ICouldBeAnyone on 2013-05-20
> **stylintile said:**
> Hi,
     I had a similar problem once before.  I had to unplug the usb keyboard and plug in an old PS2 keyboard that I had laying around.

(Sorry for re-posting, I used the wrong quote)

I have borrowed an old PS/2 keyboard from a friend, I haven't tried it  yet. But I need the USB devices plugged in to be able to print, use my  externel HDD, use the internet (wifi) and use my Ubuntu mouse (It lights  up orange :smile:).

I will try this PS/2 mouse, but it could be new computer time.

Any more help would be appreciated!
Thanks!

---

### Post by stylintile on 2013-05-20
Hello again,
     If I remember right (it's been awhile since I did this), I used the PS2 keyboard to get into bios, then disabled usb legacy support, then I could use the usb keyboard.
This may or may not be what you need to do.  I had to do it because it was searching for an OS in my printer.  If you do this, usb devices will not be recognized until after startup, so you'll need to keep a PS2 keyboard around in case you need to get into bios.

Hope this helps.

---

### Post by ICouldBeAnyone on 2013-05-22
Thanks for your help everyone, I have used a PS/2 keyboard to turn off the power on password. I can now use the computer with usb devices - I just cannot use the bios without a PS/2 keyboard, but that's fine!

Thanks everyone! :)

---

