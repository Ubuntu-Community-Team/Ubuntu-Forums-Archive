---
title: "Sound, but only in some apps"
date: 2005-03-24
forum: Hardware &amp; Laptops
---

### Post by rickwood on 2005-03-24
I recently installed some applications that use sound in Hoary.  I have system sounds, and Rhythmbox sound is ok.  However, when I install and run mplayer, I get no sound.  Also, when I install kde apps like juk, it tells me that the mixer device is busy and I get no sound from it.  If I turn off the ESD sound server, sometimes I get sound from these apps, but not consistently (it seems like the first time I run them I get sound, but not afterwards).  Also, if I turn off the ESD sound server, Rhythmbox no longer produces sound.

I have an older pci soundblaster 128 card in my machine.  Anyone have suggestions for me on how to get sound consistently from my applications and also keep the system sounds?  Is this specific to my setup, or is it simply a bug that hasn't been worked out of Hoary yet?

P.S. I dual boot with Mandrake.  In Mandrake I exclusively use kde.  But after experiencing this problem I booted Mandrake and ran gnome just to check out sound there.  Everything worked fine (i.e., system sounds, rhythmbox, juk, mplayer), so I'm assuming this is something unique to Ubuntu and not gnome.  Of course I could be wrong, Mandrake 10.1 is using an aniquated version of gnome.

---

### Post by Firetech on 2005-03-24
I had similar problems when I was doing some work on my kernel.
There are three systems (at least, thats whats in the kernel) for sound, ESD, OSS and ALSA. When I had my problems, I got the sount telling me to login, but not the sound after I logged in, and XMMS only worked with ESD and ALSA. (OSS was badly configured)
Your problem might also be a kernel issue. Try downloading a new kernel and see if that helps.

To download a new kernel, fire up a terminal and run "apt-cache search linux-image", find the newest one for your computer. (386,586,k7,etc... If you are unsure, run "uname -a" to check which one you are running now.) Then use "sudo apt-get install linux-image-x.y.z-a-b" (replacing x.y.z-a-b with the correct version).

The reason it works in Mandrake is probably because Mandrake is running another kernel.

---

### Post by rickwood on 2005-03-24
Thanks for the help.

I looked and found that I have the most recent kernel already, so I kept searching the forums for answers.  Then I found the answer -- I had to tell ESD to give up the sound card when it was idle.  This was listed as item 3 in the restricted formats howto:

[http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats)

Now Juk and other non-gnome sound apps seem to work just fine.

---

