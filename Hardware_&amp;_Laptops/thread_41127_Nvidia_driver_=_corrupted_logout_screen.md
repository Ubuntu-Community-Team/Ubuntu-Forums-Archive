---
title: "Nvidia driver = corrupted logout screen"
date: 2005-06-12
forum: Hardware &amp; Laptops
---

### Post by tristan on 2005-06-12
Hi all.

I'm using an Nvidia FX5900XT, with the latest 7664 drivers (although I've seen the following problem with earlier drivers too).

Here's a slightly annoying (but harmless) thing I've noticed: when I logout from gnome (or xfce or whatever), the screen initially goes black, and then pops up the desktop background I'd had, with a box of corrupted gfx in the top left. Eventually after 2-3 seconds the screen goes black again and the gdm greeter starts up.

If I switch my xorg.conf file to use the nv or vesa driver rather than the nvidia, then after logout the screen goes black, and stays that way until gdm. This looks a bit "neater".

I'm wondering if anyone else is seeing this, and if there is a setting in the xorg.conf file I can use to prevent it.

Thanks in advance for any info.

---

### Post by Xian on 2005-06-12
I've seen it but haven't found a fix. On my box it only happens when logging out of Kubuntu. It's interesting that you have it happen as well in Gnome. If I find anything I'll post back but as of now it has me stumped.

---

### Post by Snipersnest on 2005-06-12
I was going to make a new thread but I saw yours up, hope you don't mind.  

But I really need to install the 7664 drivers but don't know how to get my kernel headers and stuff so I can compile them.  Can somebody help me out?

I wanna upgrade my kernel, but I don't know how to do that either.... I know how to do a lot of stuff...just nothing with the kernels.

---

### Post by skoal on 2005-06-12
Yes, I've seen that little blue twisted looking bar in the upper left hand corner too since using Ubuntu, while logging back to GDM.  I've never used a Graphical Login manager before until using Ubuntu, so I have no point of reference to say I have (or have not) seen it before.  Maybe GDM is just cycling through resolutions via XRandR extensions and not doing so very cleanly.

\\//_

---

### Post by Xian on 2005-06-12
[QUOTE=Snipersnest]I was going to make a new thread but I saw yours up, hope you don't mind.  

But I really need to install the 7664 drivers but don't know how to get my kernel headers and stuff so I can compile them.  Can somebody help me out?

I wanna upgrade my kernel, but I don't know how to do that either.... I know how to do a lot of stuff...just nothing with the kernels.[/QUOTE]
You do really need to just start a new thread. 
It would help you more I think.

---

### Post by Snipersnest on 2005-06-12
[QUOTE=Xian]You do really need to just start a new thread. 
It would help you more I think.[/QUOTE]
 I did already after realizing you guys didn't reply directly to me....Thanks

---

### Post by tristan on 2005-06-12
Thanks Xian and Skoal. 

Like I said it's harmless, so it's not a high priority, but it'd be nice to know why.

---

### Post by Xian on 2005-06-12
I know that it didn't happen to me with Warty so that eliminates alot.

---

### Post by tristan on 2005-06-14
I've found a workaround of sorts...

Edit  /etc/gdm/PostSession/Default
, and add xsetroot -solid "black"


Last few lines....
```

SESSREG=`gdmwhich sessreg`
if [ "x$SESSREG" != "x" ] ; then
	"$SESSREG" -d -w /var/log/wtmp -u /var/run/utmp -x "$X_SERVERS" -h "$REMOTE_HOST" -l "$DISPLAY" "$USER"
fi
xsetroot -solid "black"
exit 0
```

There's still the little bit of corrupted gfx in the top left of screen, but since it's black, you won't see it.

---

### Post by Xian on 2005-06-14
[QUOTE=tristan]There's still the little bit of corrupted gfx in the top left of screen, but since it's black, you won't see it.[/QUOTE]
If you then immediately start another X session does the corrupted gfx also carry over to your desktop. That's what I've been seeing as well when this happens to occur.

---

### Post by tristan on 2005-06-14
> If you then immediately start another X session does the corrupted gfx also carry over to your desktop.

Not for me, if I log back in using gdm, the next desktop background will be fine.

---

### Post by Xian on 2005-06-14
Hmmm. This just keeps getting weirder. 
I still don't even notice it save that I log out of KDE.

I'm totally stumped.

---

### Post by tristan on 2005-06-14
No biggie xian, thanks for your input anyway!

---

