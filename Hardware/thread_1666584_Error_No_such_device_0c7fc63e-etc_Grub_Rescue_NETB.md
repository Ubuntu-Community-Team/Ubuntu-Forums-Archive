---
title: "Error: No such device: 0c7fc63e-etc Grub Rescue NETBOOK (no CD)"
date: 2011-01-13
forum: Hardware
---

### Post by Macintuss on 2011-01-13
Hi, I know this is a common problem, but I've spent the last hour searching the web and haven't come across a solution yet.

I just installed Wubi, the ubuntu alongside windows partition, I devoted all of C: drive to windows, and all (30 GB out of 150....) of D drive to Ubuntu.  After it installed everything ran fine, started to update all my synaptic stuff and I'm pretty sure grub wanted to update, so I did and then I rebooted and im stuck in grub rescue>.  

Typically id pop in the Windows 7 CD and be done with it (boot fix), however im kinda screwed because 1)  I dont have a windows 7 CD, Netbooks dont come with one.  2) The reason they dont come with one is because they dont have a CD drive.

The only thing i can do is press the power button.  The computer turns off.  I press the power button again and instantly back in grub rescue, no options before that.

So, i honestly don't even know what to do.  Some help please?

---

### Post by Rubi1200 on 2011-01-14
Hi and welcome to the forums :)

If you are unable to boot Windows, then it sounds as if GRUB was erroneously installed to the MBR.

You can create a LiveUSB to boot the computer and repair things.

Here is what you need to do:

1. read the first section of the Wubi Megathread, especially problem #1

2. post the results of the boot info script (also mentioned near the top of the thread)

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

If you need more help, let me know.

---

### Post by Macintuss on 2011-01-14
sorry

---

### Post by Macintuss on 2011-01-14
i dont know if its your server or my internet, but i just replicated itself like 200 times, sorry, ignore them and erase them because i cant and this site is too slow.

---

### Post by Macintuss on 2011-01-14
dp

---

### Post by Macintuss on 2011-01-14
dp

---

### Post by Macintuss on 2011-01-14
Thanks for the reply, thats a good link.  

My issue was that I  didnt think i had a chance to boot from the USB, it would go straight  into that grub recovery, the way i fixed it was by MASHING all the F1-12  buttons haha, then it just popped up bios, and from that moment on  every time it restarted i would see the default bios screen before the  error.  

I used your method of lilo to fix the mbr, worked like a  charm, now im again given the option on which OS to boot.  Ill apply  your permanent fix located at the bottom of that link in a min here,  first just wanted to say thanks.


-Macintuss

---

### Post by Macintuss on 2011-01-14
Thanks for the reply, thats a good link.  

My issue was that I  didnt think i had a chance to boot from the USB, it would go straight  into that grub recovery, the way i fixed it was by MASHING all the F1-12  buttons haha, then it just popped up bios, and from that moment on  every time it restarted i would see the default bios screen before the  error.  

I used your method of lilo to fix the mbr, worked like a  charm, now im again given the option on which OS to boot.  Ill apply  your permanent fix located at the bottom of that link in a min here,  first just wanted to say thanks.


-Macintuss

---

### Post by Macintuss on 2011-01-14
Thanks for the reply, thats a good link.  

My issue was that I  didnt think i had a chance to boot from the USB, it would go straight  into that grub recovery, the way i fixed it was by MASHING all the F1-12  buttons haha, then it just popped up bios, and from that moment on  every time it restarted i would see the default bios screen before the  error.  

I used your method of lilo to fix the mbr, worked like a  charm, now im again given the option on which OS to boot.  Ill apply  your permanent fix located at the bottom of that link in a min here,  first just wanted to say thanks.


-Macintuss

---

### Post by Macintuss on 2011-01-14
Thank you, the link worked like a charm, just had to mash buttons to get into to bios menu.

---

### Post by Macintuss on 2011-01-14
[edit]

---

### Post by Macintuss on 2011-01-14
Thanks for the reply, thats a good link.  

My issue was that I  didnt think i had a chance to boot from the USB, it would go straight  into that grub recovery, the way i fixed it was by MASHING all the F1-12  buttons haha, then it just popped up bios, and from that moment on  every time it restarted i would see the default bios screen before the  error.  

I used your method of lilo to fix the mbr, worked like a  charm, now im again given the option on which OS to boot.  Ill apply  your permanent fix located at the bottom of that link in a min here,  first just wanted to say thanks.


-Macintuss

---

### Post by Rubi1200 on 2011-01-15
You are more than welcome :)

Glad you got it sorted out (despite all the double posts ;))

---

