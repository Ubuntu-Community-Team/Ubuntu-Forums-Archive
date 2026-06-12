---
title: "disable cursor movement when touching the button-click area"
date: 2010-12-03
forum: Hardware
---

### Post by JayUK20 on 2010-12-03
I followed the guide at [http://ubuntuwiki.net/index.php/Dell_Mini_10v](http://ubuntuwiki.net/index.php/Dell_Mini_10v) to disable cursor movement when touching the button-click area this has not worked

I had no SHMConfig file so I made one up and added this

> <?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">True</merge>
  </match>
 </device>
</deviceinfo>


I also added > <merge key="input.x11_options.HorizEdgeScroll" type="string">false</merge>
<merge key="input.x11_options.VertEdgeScroll" type="string">true</merge>
<merge key="input.x11_options.AreaBottomEdge" type="string">4000</merge>


To 11-x11-synaptics.fdi but the click button area is still active, any suggestions?

---

