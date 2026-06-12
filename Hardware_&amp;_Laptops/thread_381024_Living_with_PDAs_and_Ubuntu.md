---
title: "Living with PDAs and Ubuntu"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by Catsworth on 2007-03-10
Ok, so.....

I got myself a Palm T|X, it seems like living with this beautiful piece of technology is going to be as frustrating as living with Ubuntu, mainly because (having specifically chosen a non MS PDA) I'm finding that there seems to be a lot you can't do unless you are using a MS operating system.

I've managed to install some software on it for reading native format PDF files, but that's about the face of it - that was more problematic than it needed to be because the Palm desktop software only comes in Mac or Windows flavours.

If any Palm/Ubuntu users could give me some hints on how they've accomplished the following I would really appreciate it.

1.  I can't get the Palm to sync wirelessly with Ubuntu.  It connects fine to my wireless network, as does Ubuntu, but the sync software just doesn't seem to want to play ball.  I've got jpilot installed, but other than that I'm stabbing in the dark.

2.  Is there any software I can use in Ubuntu in place of Adobe's software, to convert native PDF files into a format that the Adobe reader for Palm can read?  Alternatively, is there some software that I can install that will allow me to read PDF files without crashing all the time?

3.  (Not strictly a Ubuntu thing but.....) what document reading/manipulation software are you using on your Palm?  I only have the Office to Go application that came with it and that only reads Excel, Word and PowerPoint files.  I need to read .rtf and .txt files as well as the standard Office formats.  The only thing I can think of doing at the moment is to use OOo to convert everything to PDF format, but then I still have the same problems as in 2 above.

Te frustrating thing is that all of the above would probably be really simple if I was using Windows, but I don't want to do that - I love my Ubuntu install (sort of) and I don't want to go back to the dark side.

I'd really appreciate any help anybody can give.

Thanks.

---

### Post by Catsworth on 2007-03-11
Ok, making some progress.

The T|X now sync's with the laptop, and backs up _from_ PDA to laptop quite nicely.

What I can't figure is how to get it to do it in the other direction.  I want to be able to create entries on either device and have them updated on the other - is that possible?

---

### Post by megamania on 2007-03-11
> **Catsworth said:**
> Ok, making some progress.

The T|X now sync's with the laptop, and backs up _from_ PDA to laptop quite nicely.

What I can't figure is how to get it to do it in the other direction.  I want to be able to create entries on either device and have them updated on the other - is that possible?
I'm not sure what problem you're experiencing. If you're using Jpilot, it basically works like Palm Desktop.

If you update your data on the computer then sync the palm, changes will be updated to the palm.
To make sure it works, just try this:
-make a hotsync (to be sure you have two identical copies of your data)
-add a new contact in Jpilot (i.e. mark shuttleworth and his phone number)
-hotsync
-check if the new contact is on the Palm

Let me know if it works!

---

### Post by Catsworth on 2007-03-11
The problem is that I just can't get JPilot to sync at all, I'm syncing using gnome-pilot which is the only way I can get any sort of connection/exchange of data to work at all at the moment.

I'm really enjoying my new toy though, this is one cool piece of kit :)

---

### Post by megamania on 2007-03-12
> **Catsworth said:**
> The problem is that I just can't get JPilot to sync at all, I'm syncing using gnome-pilot which is the only way I can get any sort of connection/exchange of data to work at all at the moment.

I'm really enjoying my new toy though, this is one cool piece of kit :)
Are you trying wireless sync or usb sync with jpilot?

---

### Post by Catsworth on 2007-03-12
USB sync with Jpilot won't even connect, wireless sync connects but I get the problems I've described above.

---

### Post by megamania on 2007-03-15
> **Catsworth said:**
> USB sync with Jpilot won't even connect, wireless sync connects but I get the problems I've described above.
I'm not sure I understand what problems you're having wireless syncing with jpilot...

Since you say it connects, does it stop in the middle of the syncing activity? I remember of a bug with long files, but I thought it had been fixed.

---

### Post by Catsworth on 2007-03-15
I have gnome-pilot running.  When I hot-sync wirelessly it works fine.

If I uninstall that and install Jpilot it can't even connect to the palm.

---

### Post by Lilithd on 2008-07-04
> **Catsworth said:**
> I have gnome-pilot running.  When I hot-sync wirelessly it works fine.

If I uninstall that and install Jpilot it can't even connect to the palm.



If you are using JPilot to sync with wire or base (not wirelessly)... 

File:Preferences:Settings:"Serial Port(/dev/ttyS0, /dev/pilot) 
Make sure this says "**USB:**" not "/dev/pilot"

With my Tungsten E2, Jpilot was the only one that worked, but it took a small bit of tweaking. Try that, if it doesn't work let me know.

---

