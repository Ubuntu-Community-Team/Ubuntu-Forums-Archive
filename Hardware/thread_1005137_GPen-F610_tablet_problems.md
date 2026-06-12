---
title: "GPen-F610 tablet problems"
date: 2008-12-07
forum: Hardware
---

### Post by scardario on 2008-12-07
Hi

excuse me if there's already the solution to this problem anywhere in the forums, I searched and I didn't find something close to what I need

I have installed Ubuntu 8.10, it's already upgraded

The problem is: When I connect my tablet it works until I clic (touch the tablet with the pencil), when I do that the cursor freeze and the tablet stops working. I disconnect the tablet and connect it again and the same thing happens, it works until I clic.

The tablet model is Genius G-Pen F610 and it works correctly in windows

I tried to look into the xorg.conf file but I didn't find some tablet configuration, in fact, I didn't find any hardware configuration, I don't know where the rest of the X system configuration is


Thanks

---

### Post by Amazona aestiva on 2008-12-30
Hello,

I have a Genius G-Pen F610 Slim graphic tablet too and it works perfectly for me. I followed the "Option 2" in [this]("http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html") how to.

In the 4. part of the configuring, you'll have to replace a few numbers, because those are for another tablet.
```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<deviceinfo version="0.2">
<device>
<!-- This MUST match with the name of your tablet -->
<match key="info.product" contains="[COLOR="Red"]**NAME OF YOUR TABLE OBTAINED FROM STEP THREE**[/COLOR]">
<merge key="input.x11_driver" type="string">wizardpen</merge>
<merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
<merge key="input.x11_options.TopX" type="string">200</merge>
<merge key="input.x11_options.TopY" type="string">200</merge>
<merge key="input.x11_options.BottomX" type="string">18800</merge>
<merge key="input.x11_options.BottomY" type="string">12000</merge>
<merge key="input.x11_options.MaxX" type="string">18800</merge>
<merge key="input.x11_options.MaxY" type="string">12000</merge>
</match>
</device>
</deviceinfo>
```
These numbers are not exact for the tablet but almost fit.(I think they are only good if your screen resolution is 1280x1024)

It is perfect with [Inkscape]("apt://inkscape"), but the pressure sensitivy doesn't work in Gimp yet.

At the bottom of this [older how to]("https://help.ubuntu.com/community/TabletSetupWizardpen"), you can find some information to configure the buttons on the pen and maybe on the tablet.(I've not tried that yet)

Regards,

---

