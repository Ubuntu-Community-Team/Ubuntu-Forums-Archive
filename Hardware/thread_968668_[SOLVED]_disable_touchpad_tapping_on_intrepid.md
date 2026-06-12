---
title: "[SOLVED] disable touchpad tapping on intrepid"
date: 2008-11-02
forum: Hardware
---

### Post by leptogenesis on 2008-11-02
In the past, I've used the MaxTapTime attribute in /etc/X11/xorg.conf to disable touchpad tapping.  However, on my fresh install of Kubuntu intrepid, the xorg.conf doesn't even have a section for the synaptics touchpad.  I'm assuming that this means kubuntu is configuring the touchpad in some other way.  

So, what's the best way to disable touchpad tapping kubuntu?

System information: Dell e1505 laptop, fresh install of kubuntu intrepid ibex i386.

---

### Post by berman56 on 2008-11-02
Yeah, this is really annoying.  Intrepid uses HAL instead of xorg.  To allow the use of the touchpad app in system-preferences, you need a shmconfig.fdi file in:

/etc/hal/fdi/policy/

I've attached my file which should do the trick.  Extract the file in the policy folder, reboot, and you should be able to launch your touchpad control in system-preferences.

Cheers.

---

### Post by berman56 on 2008-11-02
Just to make sure the shmconfig.fdi loads, properly, double check to make sure it reads:

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">True</merge>
  </match>
 </device>
</deviceinfo>

---

### Post by leptogenesis on 2008-11-02
Ah, thank you; It works now.  Although...kubuntu doesn't seem to have any touchpad preferences in system-preferences.  I had to install gsynaptics, and invoke it from a terminal.  Of course, gsynaptics only worked once I had copied your file as you said.

---

### Post by leptogenesis on 2008-11-04
Hmm...I just rebooted, and realized that the using gsynaptics to disable the touchpad isn't permanent.  It would be very annoying to have to do this every time I reboot--do you have any suggestions on making the setting permanent?

---

### Post by leptogenesis on 2008-11-04
Nevermind--I figured it out.  Rather than configuring using a gui, you can just disable it directly from /etc/hal/fdi/policy/shmconfig.fdi by making it look like this:

```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.MaxTapTime" type="string">0</merge>
  </match>
 </device>
</deviceinfo>

```

So really, these options work just like the familiar xorg.conf, except using xml :-)

---

### Post by jonsson on 2008-11-16
Thanks, this made things much better. :-) Do you know of a list of options that can be set in this way?

In previous versions I used to disable the touchpad completely (I have a pointing stick and prefer to use that). But it would be nice to be able to use the pad just for scrolling for example.

---

