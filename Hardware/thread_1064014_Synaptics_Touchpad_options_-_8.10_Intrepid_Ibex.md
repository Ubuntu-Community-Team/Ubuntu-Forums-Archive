---
title: "Synaptics Touchpad options - 8.10 Intrepid Ibex"
date: 2009-02-08
forum: Hardware
---

### Post by taylork on 2009-02-08
I upgraded one of my laptops to 8.10 from 7.04 and noticed that the touchpad option "continue scrolling on edge" no longer worked. By modifying the edge numbers to be what they were in 7.04, it started working perfectly again.

This is what I did to get that feature working again mostly relying upon a wiki at [http://wiki.archlinux.org/index.php/Touchpad_Synaptics](http://wiki.archlinux.org/index.php/Touchpad_Synaptics).

sudo gedit /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi

Then changed the touchpad section to this (an HP NC4010):


      <match key="info.product" contains="Synaptics TouchPad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
	<!-- Arbitrary options can be passed to the driver using 
	     the input.x11_options property since xorg-server-1.5. -->
	<merge key="input.x11_options.SHMConfig" type="string">On</merge>
        <merge key="input.x11_options.LeftEdge" type="string">1872</merge>
        <merge key="input.x11_options.RightEdge" type="string">5072</merge>
        <merge key="input.x11_options.TopEdge" type="string">1712</merge>
        <merge key="input.x11_options.BottomEdge" type="string">4144</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">false</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">true</merge>
	<!-- EXAMPLE:
	<merge key="input.x11_options.LeftEdge" type="string">120</merge>
	-->
      </match>

If you haven't already upgraded. I would add the SHMConfig option to xorg.conf, run synclient -l and store the results in a file to compare against when upgrading to 8.10.

---

