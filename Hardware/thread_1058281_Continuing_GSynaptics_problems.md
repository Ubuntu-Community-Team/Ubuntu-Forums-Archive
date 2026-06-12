---
title: "Continuing GSynaptics problems"
date: 2009-02-02
forum: Hardware
---

### Post by muppetjones on 2009-02-02
System: I am running Ubuntu 8.10 with the eee kernel by Adam McDaniel.
Problem: GSynaptics requires SHMconfig to be enabled.

I have followed the instructions to enable SHMconfig found [here]("https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig"), which leads to the following in my shmconfig.fdi file.

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">True</merge>
  </match>
 </device>
</deviceinfo>

```

In addition, I also applied the changes found [here]("http://blog.hyperandy.com/2008/11/02/using-gsynaptics-with-ubuntu-810/") to my 11-x11-synaptics.fdi  file.

```
	<merge key="input.x11_options.SHMConfig" type="string">On</merge>

```

in 

```
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="Synaptics TouchPad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
	<!-- Arbitrary options can be passed to the driver using 
	     the input.x11_options property since xorg-server-1.5. -->
	<!-- EXAMPLE:
	<merge key="input.x11_options.LeftEdge" type="string">120</merge>
	-->
	<merge key="input.x11_options.SHMConfig" type="string">On</merge>
      </match>
...

```

Unfortunately, neither solution worked. I have not found another solution (since xorg.conf is non-viable in 8.10). I would really appreciate some help getting gsynaptics working, or maybe suggestions for other modules to perform the same tasks.

Thanks!!

---

