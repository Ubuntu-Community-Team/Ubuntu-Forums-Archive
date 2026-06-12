---
title: "Ibex on Flybook"
date: 2008-11-01
forum: Hardware
---

### Post by toastball on 2008-11-01
Hi!

I own one of the original Dialogue Flybook laptops, which I recently upgraded from Ubuntu 8.04 to 8.10.  The most immediate problem seems to be that the mouse cursor moves backwards.  (I'm using the little blue pencil eraser thing to move the mouse cursor -- getting the touchscreen working would be nice too, but first things first!)

In my old xorg.conf, I had manually added lines like

  Option "InvX" "True"
  Option "InvY" "True"

to the InputDevice section corresponding to the mouse.  I see that the upgrade has commented out most of the file and added a vague note about using HAL.  Subsequent research has led me to believe that the preferred way to fix this problem involves adding an FDI file to /etc/hal/fdi/policy/.  I haven't been able to find a whole lot of documentation for either HAL or these FDI mysterious files, but I cribbed something together that seemed reasonable to me based on something someone else had posted elsewhere.  (In a moment, I'll see if I can't post the contents of that file from the laptop itself.)  I saved the file and rebooted the laptop.  Naturally, the mouse is still backwards, or I probably wouldn't be posting this.

/var/log/Xorg.0.log shows HAL detecting a "TPPS/2 IBM TrackPoint" which I'm pretty sure is the mouse in question.  No sign of my InvX/InvY nonsense in there.

I'm at a bit of a loss.  How do I get HAL to tel me what it's up to?  I've been grovelling around in /var/log/ but haven't had much luck thus far.

---

### Post by toastball on 2008-11-02
<?xml version="1.0" encoding="utf-8"?>
<deviceinfo version="0.2">
<device>
<match key="info.capabilities" contains="input.mouse">
<merge key="input.x11_options.InvX" type="bool">True</merge>
<merge key="input.x11_options.InvY" type="bool">True</merge>
</match>
</device>
</deviceinfo>

---

### Post by toastball on 2008-11-02
This does the trick:

<?xml version="1.0" encoding="utf-8"?>
<deviceinfo version="0.2">
<device>
<match key="info.product" string="TPPS/2 IBM TrackPoint">
<merge key="input.x11_driver" type="string">mouse</merge>
<merge key="input.x11_options.Protocol" type="string">auto</merge>
<merge key="input.x11_options.Device" type="string">/dev/input/mice</merge>
<merge key="input.x11_options.InvX" type="string">True</merge>
<merge key="input.x11_options.InvY" type="string">True</merge>
</match>
</device>
</deviceinfo>

I still don't know how to get diagnostics from HAL, but I eventually hit upon the above after doing some more reading (e.g. [http://cgit.freedesktop.org/xorg/xserver/tree/config/x11-input.fdi](http://cgit.freedesktop.org/xorg/xserver/tree/config/x11-input.fdi)) and a lot of trial and error.  Xorg.0.log is reasonably helpful.  I think the key point is that the new evdev driver doesn't seem to support InvX/InvY and friends, so it's necessary to coddle the old mouse driver into working.

---

