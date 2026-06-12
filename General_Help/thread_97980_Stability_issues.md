---
title: "Stability issues?"
date: 2005-12-02
forum: General Help
---

### Post by excelsior on 2005-12-02
Anyone else finding breezy to be more unstable than hoary?
I mean, in the week since i upgraded it crashed about 5 times (this almost never happened when i used hoary and warty). I can't keep my laptop on throughout the night anymore as it will certainly crash in the morning; this is something I always did with hoary.

---

### Post by Pablo_Escobar on 2005-12-02
For me Breezy is very stable. Hoary was stable and Breezy is also stable as rock.

---

### Post by kirmonkey on 2005-12-02
Hi,

I find individual packages wobbly sometimes. Especially amarok and open office impress. Oh yes and skype. Ah and evolution. And realplayer. And k3b. And the USB automounting system.

We do have a lot of power cuts here though, that can't help......


Apart from that 


Rock solid.......

---

### Post by nocturn on 2005-12-02
I had some problems with Breezy RC, but it has been stable for me.

Only crashes are related to changing networks with ndiswrapper (requires rmmod) and running konqueror in Gnomer freezes the machine.

---

### Post by 23meg on 2005-12-02
[QUOTE=excelsior]I can't keep my laptop on throughout the night anymore as it will certainly crash in the morning; this is something I always did with hoary.[/QUOTE]Is it a hard crash? See if it's a framebuffer-related problem; can you get back to x when you hit ctrl+alt+f1 and then ctrl+alt+f7? If this is the case, see if temporarily disabling splashy brings an improvement.

Also try disabling display power management in System / Preferences / Screensaver / Advanced and turning off DPMS by commenting it out in your xorg.conf file.

---

### Post by lerrup on 2005-12-02
Yes, I am.

What will happen is that everything freezes for no apparent reason at all.  The keyboard and trackpad stop working and nothing changes on the display at all.

I suspect that beneath the X server things are ticking on fine, but with no way of finding out this is just a guess.

---

### Post by excelsior on 2005-12-02
[QUOTE=23meg]Is it a hard crash? See if it's a framebuffer-related problem; can you get back to x when you hit ctrl+alt+f1 and then ctrl+alt+f7? If this is the case, see if temporarily disabling splashy brings an improvement.

Also try disabling display power management in System / Preferences / Screensaver / Advanced and turning off DPMS by commenting it out in your xorg.conf file.[/QUOTE]

no, ctrl+alt +whatever doesn't work
And it crashed again today- seriously contemplating going back to hoary

---

### Post by excelsior on 2005-12-06
[QUOTE=23meg]I
Also try disabling display power management in System / Preferences / Screensaver / Advanced and turning off DPMS by commenting it out in your xorg.conf file.[/QUOTE]

I tried this and it worked perfectly. Thanks!
But is there any way I can make it work and still save DPMS?

---

