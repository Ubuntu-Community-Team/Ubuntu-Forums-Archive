---
title: "sixaxis cursor speed, help?"
date: 2009-06-03
forum: Hardware
---

### Post by Teutorix on 2009-06-03
How do i increase the speed my cursor moves at using my sixaxis.

heres the code
```
&#8722;
<deviceinfo version="0.2">
&#8722;
<device>
&#8722;
<match key="info.capabilities" contains="input">
<!-- Match on anything you like from lshal -->
&#8722;
<match key="input.product" string_outof="Sony Computer Entertainment Wireless Controller;Sony PLAYSTATION(R)3 Controller">
&#8722;
<!--
 xorg-server<1.5 will only hotplug devices where these two capatilities
             are set. This hack can confuse other hal clients. 
-->
&#8722;
<!--

        <append key="info.capabilities" type="strlist">input.keys</append>
        <append key="info.capabilities" type="strlist">input.mouse</append>
        
-->
<merge key="input.x11_driver" type="string">joystick</merge>
&#8722;
<!--
 Arbitrary options can be passed to the driver using 
             the input.x11_options property since xorg-server-1.5. 
-->
&#8722;
<!--
 DEFAULT CONFIGURATION 
             Change this to override the default settings of the input driver.
        
-->
<merge key="input.x11_options.MapButton10" type="string">button=1</merge>
<merge key="input.x11_options.MapButton9" type="string">button=2</merge>
<merge key="input.x11_options.MapButton11" type="string">button=3</merge>
<merge key="input.x11_options.MapAxis1" type="string">mode=relative axis=+1x deadzone=5000</merge>
<merge key="input.x11_options.MapAxis2" type="string">mode=relative axis=+1y deadzone=5000</merge>
<merge key="input.x11_options.MapAxis3" type="string">mode=relative axis=+1zx deadzone=5000</merge>
<merge key="input.x11_options.MapAxis4" type="string">mode=relative axis=+1zy deadzone=5000</merge>
<merge key="input.x11_options.MapAxis5" type="string">mode=accelerated axis=+1x deadzone=5000</merge>
<merge key="input.x11_options.MapAxis6" type="string">mode=accelerated axis=+1y deadzone=5000</merge>
&#8722;
<!--
 EXAMPLES
        <merge key="input.x11_options.DebugLevel" type="string">5</merge>
        <merge key="input.x11_options.AutoRepeat" type="string">500 4</merge>
        <merge key="input.x11_options.MapButton4" type="string">key=Alt_L+Tab</merge>
        <merge key="input.x11_options.MapButton8" type="string">amplify=0.3</merge>
        <merge key="input.x11_options.MapButton9" type="string">disable-mouse</merge>
        <merge key="input.x11_options.MapButton10" type="string">key=space</merge>

        <merge key="input.x11_options.MapAxis1" type="string">mode=accelerated keylow=Left keyhigh=Right</merge>
        <merge key="input.x11_options.MapAxis2" type="string">mode=accelerated keylow=Up keyhigh=Down</merge>
        
-->
</match>
</match>
</device>
</deviceinfo>
```

---

### Post by Teutorix on 2009-06-03
Any ideas? even point out the code that deals with the cursor movement and i can try myself...

---

### Post by falkTX on 2009-06-22
> **Teutorix said:**
> Any ideas? even point out the code that deals with the cursor movement and i can try myself...

On the fdi file change:
```
... axis=+1x ...
```
to something like:
```
... axis=+3x ...
```
(this make the sixaxis cursor goes 3x faster than usual)

---

### Post by Teutorix on 2009-06-24
Sweet, thanks alot

---

### Post by falkTX on 2009-06-24
> **Teutorix said:**
> Sweet, thanks alot

If you're using Sixaxis, you'll probably want to check out this:
[http://ubuntuforums.org/showthread.php?t=1190061](http://ubuntuforums.org/showthread.php?t=1190061)

It's a program I made to connect the Sixaxis to the PC (in linux), in bluetooth (wireless) mode

---

### Post by Teutorix on 2009-06-25
I dont have a bluetooth card :P

It took me much longer to get a guide for a wired connection actually lol.

---

