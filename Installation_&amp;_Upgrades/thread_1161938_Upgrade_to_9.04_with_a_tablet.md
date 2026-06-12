---
title: "Upgrade to 9.04 with a tablet"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by tatewaki on 2009-05-17
Hey, i was wondering if anybody had tried upgrading from 8.10 to 9.04 on a tablet? I was able to get automatic rotation with the screen an touch working, so i am a bit scared of upgrading if it should brake it all.

I'm using a Lenovo x61 tablet, but as i know, a tablet uses the same drivers and scripts to rotate the screen.

---

### Post by tatewaki on 2009-06-01
Nobody?

---

### Post by tatewaki on 2009-08-14
Well for anybody interrested, i got it to work with 9.04 by the old X way. But in 9.10 i got i to work with hal so i will be posting a howto soon

---

### Post by Mark Phelps on 2009-08-14
I have a tablet PC(Fujitsu) and a trial upgrade to 9.04 broke nearly everything.  I had a highly customized xorg.conf which, as you know, is nearly useless in 9.04.  So, I reverted back.

Will be very interested in your how-to.

Thanks

---

### Post by melon2006 on 2009-08-17
I've managed to set up graphic tablet Trust TB-6300 under 64-bit 9.04 (dual monitor with Nvidia)

I requires installing wizardpen drivers (v0.7-alpha2). Compilation&installation is pretty straightforward but hopefully some day wizardpen drivers would be in repositories.

Pressure sensitivity works in all graphics applications that I use: Gimp, Inkscape and Blender (i.e. sculpting).

HAL instant plug-in works OK, it requires file
/etc/hal/fdi/policy/99-x11-wizardpen.fdi that contains following text:

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<deviceinfo version="0.2">
<device>
<!-- This MUST match with the name of your tablet -->
<match key="info.product" contains="UC-LOGIC Tablet WP8060U">
<merge key="input.x11_driver" type="string">wizardpen</merge>
<merge key="info.product" type="string">stylus</merge>
<merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
<merge key="input.x11_options.TopX" type="string">0</merge>
<merge key="input.x11_options.TopY" type="string">234</merge>
<merge key="input.x11_options.BottomX" type="string">32747</merge>
<merge key="input.x11_options.BottomY" type="string">32726</merge>
<merge key="input.x11_options.MaxX" type="string">32747</merge>
<merge key="input.x11_options.MaxY" type="string">32726</merge>
<merge key="input.x11_options.TopZ" type="string">1</merge>
<merge key="input.x11_options.BottomZ" type="string">512</merge>
<merge key="input.x11_options.MaxZ" type="string">512</merge>
</match>
</device>
</deviceinfo>

```

Note: "stylus" key makes pressure sensitivity works in Blender (it's my everyday work app, so it's crucial to have 100% functional graphics tablet).

---

### Post by Favux on 2009-08-17
Hi melon2006,

Congratulations on setting up your WizardPen tablet!

DoctorMO does have a ppa (with deb.s) for the wizardpen driver.  It's here:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen](https://launchpad.net/~doctormo/+archive/xorg-wizardpen)

He's hoping people test it out and report any bugs here:  [https://bugs.launchpad.net/wizardpen](https://bugs.launchpad.net/wizardpen)  If he can get enough feedback he'd like to add it to the wiki.

---

### Post by melon2006 on 2009-08-21
hi Favux,

Thanks for information. I've succesfuly installed deb packages from DoctorMO's repository (64-bit 9.04). So far everything is working fine.

---

### Post by Favux on 2009-08-21
Hi melon2006,

Good deal!  Like I said, he would appreciate feedback.

---

### Post by trevjs on 2009-09-10
This thread was helpful in that I wouldn't have found the packages, but now I'm wondering how to use these packages with the howto.  How would I run the calibration tool in order to see what it outputs?  I have a brand new g-pen M-609 that I'm trying to get setup for dual monitors, but I can't figure out how to set it to use only one monitor.

---

### Post by Favux on 2009-09-10
Hi trevjs,

Partly that depends on what video card you have.  ATI and nVidia have proprietary solutions and don't use Xrandr.  So if you're using their proprietary drivers you have to use their solutions.

---

