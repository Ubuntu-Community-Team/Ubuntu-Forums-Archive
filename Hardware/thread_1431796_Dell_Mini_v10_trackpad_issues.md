---
title: "Dell Mini v10 trackpad issues"
date: 2010-03-17
forum: Hardware
---

### Post by JayUK20 on 2010-03-17
I've got some trackpad issues where by i cannot left click and highlight or scroll as the cursor goes mental. 


I've done the "synclient bottomedge 4000" thing in terminal but it didnt have any effect.

I have read this thread [http://ubuntuforums.org/showthread.php?t=1213114&highlight=dell+mini+trackpad](http://ubuntuforums.org/showthread.php?t=1213114&highlight=dell+mini+trackpad) about using patched drivers but the patch URL which is added to package manager gives me an error about it no longer being available 


EDIT: Works fine in Windows.

---

### Post by JayUK20 on 2010-03-18
Anyone have any ideas? It seemed to work on Karmic but after an update it went wrong again.

---

### Post by jrssystemsnet on 2010-03-18
See here: [http://ubuntuwiki.net/index.php/Dell_Mini_10v](http://ubuntuwiki.net/index.php/Dell_Mini_10v)

---

### Post by JayUK20 on 2010-03-20
Thanks for your reply.

The deadening of the buttons areas interested me and I added the code the url you said to look at showed me but the button area is still active, I assume I have entered it correctly,

> You will probably want to disable cursor movement when touching the button-click area; enable vertical edge scrolling; and disable horizontal edge scrolling. Set the following inside the <match> area of /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi :

> <?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
<merge key="input.x11_options.HorizEdgeScroll" type="string">false</merge>
<merge key="input.x11_options.VertEdgeScroll" type="string">true</merge>
<merge key="input.x11_options.MovementBottomEdge" type="string">4000</merge>
        <merge key="input.x11_driver" type="string">synaptics</merge>
        </match>
  </device>
</deviceinfo>

---

### Post by jrssystemsnet on 2010-03-20
If you didn't enable shared memory as shown at that article first, then neither synclient nor the .fdi will actually do anything.

Note that the .fdi does not take effect until you reboot.  Neither does the SHMConfig (shared memory config).

---

### Post by JayUK20 on 2010-03-20
This is a little odd as I seem to have already enabled SHMConfig, here it is.

> <?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">on</merge>
    </match>
  </device>
</deviceinfo>

---

### Post by jrssystemsnet on 2010-03-20
> **JayUK20 said:**
> This is a little odd as I seem to have already enabled SHMConfig, here it is.```
<merge key="input.x11_options.SHMConfig" type="string">on</merge>
```In my (working) UNR Karmic Dell Mini 10v machines, that line sets to **True**, not to **on** as you have it there.

---

