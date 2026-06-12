---
title: "[SOLVED] How to throttle down nvidia card?"
date: 2008-07-14
forum: Hardware
---

### Post by kpkeerthi on 2008-07-14
I want my nvidia GPU to run at lower clock speed. How do I do that without having to flash its BIOS. Is it possible (with a command or something) ?

---

### Post by sdennie on 2008-07-14
To some extent you can underclock your nvidia card.  Edit /etc/X11/xorg.conf and, in the section where it describes your nvidia card, add:

```

Option "CoolBits" "1"

```

Once you restart the X server, you'll have an option in nvidia-settings called Clock Freqencies.  You can also set the clock speeds via the command line with:

```

nvidia-settings -a GPUOverclockingState=1
nvidia-settings -a GPU3DClockFreqs=400,600

```

If your graphics card has PowerMizer, the under/over clocking only seems to effect the highest PowerMizer state.

---

### Post by kpkeerthi on 2008-07-14
Thanks. I forgot to mention that this is on a Dell XPS Gen 2 laptop. I reckon that coolbits is locked in the BIOS. Anyway, I'll give this a try when I get back home.

---

### Post by sdennie on 2008-07-14
I'm using CoolBits on an XPS m1330 without any problems.  As long as you don't need the legacy nvidia drivers, it should be supported.  For laptops I believe the driver only lets you underclock.

---

### Post by damis648 on 2008-07-14
Is there any way at all to change the lowest powermizer state?

---

### Post by sdennie on 2008-07-14
> **damis648 said:**
> Is there any way at all to change the lowest powermizer state?

Not that I'm aware of.  It's possible to underclock the 2D power state to something below default (which is usually the same as lowest the 3D state) but, in talking to someone who has done this, it caused stability problems.

---

### Post by kpkeerthi on 2008-07-14
> **vor said:**
> I'm using CoolBits on an XPS m1330 without any problems.  As long as you don't need the legacy nvidia drivers, it should be supported.  For laptops I believe the driver only lets you underclock.

Great. Thats a relief. Also, I noticed that the GPU automatically throttles down when run with battery power. So I guess there is some hope. Can't wait to check this out. Thanks again.

---

### Post by kpkeerthi on 2008-07-14
Perfect. Worked flawlessly.

---

### Post by Lego Dragon Rider on 2009-09-28
> **sdennie said:**
> I'm using CoolBits on an XPS m1330 without any problems.  As long as you don't need the legacy nvidia drivers, it should be supported.  For laptops I believe the driver only lets you underclock.
On my 9-month-old Compaq CQ50 with Nvidia 8200M G, the only option I see is a checkbox labeled "Enable Overclocking", and a bunch of controls that are faded out.

 Do I have to enable overclocking, then reduce the frequencies? Or should there be a separate option labeled "underclocking"?

---

