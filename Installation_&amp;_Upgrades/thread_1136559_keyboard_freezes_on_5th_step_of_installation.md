---
title: "keyboard freezes on 5th step of installation"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by bluearth on 2009-04-25
Hi,

I've just grabbed xubuntu jaunty and planning to wipe the entire ntfs partition on my old PC sporting 600Mhz/128MB/10GB primary HD/20GB 2nd-ary HD. Ive been abusing this box for experimenting with various linux distros, and now I decided to try xubuntu.

Here's what I did: 
- Burned the image, pop the CD, and reboot. 
- Few first steps went well (albeit slow, gee i figured xubuntu installer should consume less resources), my keyboard was detected during the 3rd step, typed some letters to test it, got echoes in the textbox, hit next.
- The next step was partitioning, this too went well. Choose to use the entire disk. This step completed without whining. Move on the next step, entering 1st time username/password.

- Wham! I could not type anything in any of the textboxes. Tried the tab key, but nothing happend. Strange, knowing that keyboard as fine during keyboard layout selection before. All keys are suddenly dead. Num/Caps lock key gave response so it's not freezing. Mouse still working, I could still hit next, but of course the installer validates the textboxes and brought me back.

Any others experiencing the same problem? Has this got to do with this [bug]("https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54836") ?

---

### Post by PapaWiskas on 2009-09-29
Anyone else experience this?

---

### Post by rreese6 on 2009-09-29
Let's take a shot at this one.
Is you Keyboard USB?
DO you have the "USB Legacy" enabled in BIOS?
if so turn it off, if not turn it on.
Also Check to see if the BIOS uses the BIOS to send info or is it relies on the OS (Basically Plug and Play Option) This should be off.

If none of that helps. Did you try unplugging the keyboard for 10 seconds and plug it back in on that screen? (Man am I ever shooting in the dark here)

---

