---
title: "VSync within X?"
date: 2008-07-12
forum: General Help
---

### Post by chazdraves on 2008-07-12
Hi, all!

I like the new(-ish) desktop effects, but I'm wondering if there's a way to enable vsync on the desktop as most all of the effects cause a terrible amount of tearing which really ruins most of the fun. I'm using a 9600GT.

Thanks!
- Chaz

---

### Post by chazdraves on 2008-07-13
Nobody, eh?

- Chaz

---

### Post by eugustine on 2008-10-16
I'm also looking for this answer. HALP! The Desktop Settings in the advanced compiz settings manager doesn't help either.

---

### Post by loomsen on 2008-10-17
Alright.

post content of your xorg here by doing this:
```

cat /etc/X11/xorg.conf

```

Then maybe someone will start taking care.

Further read your X.log files.

---

### Post by krU6)#43 on 2008-12-21
Hi all

I too suffer from this. I'm on a macbook pro using the open source ati driver and desktop effects are turned off. Using dual monitor i.e. latop screen + external. Is there some option I can add to my xorg.conf?

My xorg file is as follows:
```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	3120 1050
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```

Many thanks

---

### Post by rossmoore on 2008-12-22
Isn't there a setting in compiz config, under the General section, for setting VBlank? I think you should be able to set it there.
Oh, and there's a Sync to VBlank for Nvidia cards in nvidia-settings (provided you've got the restricted driver installed).

There are quite a few different places where you can set "sync to VBlank", and I'm afraid I don't know the details of exactly what each setting does that's different from the others (I tend to switch it on if I can find the option, provided it doesn't break anything else...)

---

### Post by .arean on 2008-12-22
I get tearing with compiz on or off no matter what vblank settings I enable. It's just another one of linux's little quirks I've learned to live with.

---

### Post by krU6)#43 on 2008-12-22
Well I was hoping that since I have desktop effects turned off I could find a way of getting vsync working without having to twiddle with compiz (which is disabled), or nvidia (for which I don't have an nvidia driver), or the ATI drivers (which are completely useless).

---

### Post by Usufruct on 2008-12-22
> **.arean said:**
> I get tearing with compiz on or off no matter what vblank settings I enable. It's just another one of linux's little quirks I've learned to live with.

Have you tried enabling Xinerama?  That has solved the issue for some people.

I have never had a tearing issue with compiz.

---

### Post by krU6)#43 on 2008-12-23
thanks, i'll give xinerama whirl!

---

