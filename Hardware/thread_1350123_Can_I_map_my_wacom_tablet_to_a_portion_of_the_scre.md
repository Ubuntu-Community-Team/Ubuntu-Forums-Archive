---
title: "Can I map my wacom tablet to a portion of the screen?"
date: 2009-12-09
forum: Hardware
---

### Post by KikutaKnight on 2009-12-09
Ubuntu Studio 9.10
Dell Optiplex GX620
Wacom Intuos 2 6x8
2 17" monitors 1280x1024

Hi, my wacom tablet is working fine with pressure sensitivity and painting in GIMP, but I'm using a dual monitor setup. I've been searching for answers and I can't find any documentation about mapping to a portion of the screen.

I don't want my 6x8 tablet mapped all the way across my dual-monitor display, but rather would like it mapped to one monitor.

Does anyone know how to configure this?

(I also installed tablet-apps, which is very nice...but not helpful for this)

---

### Post by KikutaKnight on 2009-12-09
Ok, it took me a while to understand it...but eventually i found the options i was looking for on this page:

[http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev)

and then i used the instructions on this page:

[https://help.ubuntu.com/community/Wacom.fdi](https://help.ubuntu.com/community/Wacom.fdi)

and created this file to solve my problem:

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">

  <device>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="stylus">
        <merge key="input.x11_options.Twinview" type="string">horizontal</merge>
        <merge key="input.x11_options.ScreenNo" type="string">1</merge>
      </match>
    </match>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="eraser">
        <merge key="input.x11_options.Twinview" type="string">horizontal</merge>
        <merge key="input.x11_options.ScreenNo" type="string">1</merge>
      </match>
    </match>
  </device>

</deviceinfo>
```

now the tablet is mapped to just my right monitor.

---

### Post by RenderRob on 2010-06-04
What is the name of your file? Where did you put the file? What do you have to do to reload the tablet driver and see the effect?

---

