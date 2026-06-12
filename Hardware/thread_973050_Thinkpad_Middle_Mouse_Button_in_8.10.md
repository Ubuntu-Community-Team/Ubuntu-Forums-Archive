---
title: "Thinkpad Middle Mouse Button in 8.10"
date: 2008-11-06
forum: Hardware
---

### Post by Skywing on 2008-11-06
Does anyone here know how to configure the middle mouse button on a thinkpad to scroll instead of act as mouse button 3? Right now if I press it it acts as a middle mouse click, I would like to use it to scroll as it does it Windows. Thanks.

---

### Post by ssully on 2009-01-02
This has been answered elsewhere, and from what I've read may depend on the type of thinkpad you're using.  Any any rate, you can try the following (I think this is attributable to a howto on [www.thinkwiki.org)](www.thinkwiki.org)).

As root, create the file /etc/hal/fdi/policy/mouse-wheel.fdi

```
sudo gedit /etc/hal/fdi/policy/mouse-wheel.fdi
```

and enter as contents

```
<match key="info.product" string="TPPS/2 IBM TrackPoint">
  <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
  <merge key="input.x11_options.EmulateWheelButton" type="string">2</merge>
  <merge key="input.x11_options.ZAxsisMapping" type="string">4 5</merge>
  <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
</match>
```

Save the file, restart X and see if it worked.

---

### Post by arist0tle on 2009-01-30
Cool thanks. Also, if you have a trackpoint AND a trackpad (say an R500), read this ( [http://web.archive.org/web/20061010223935/http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-51536](http://web.archive.org/web/20061010223935/http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-51536) ). That worked for me on my R500

---

