---
title: "Configure mouse with HAL in 8.10"
date: 2008-11-22
forum: Hardware
---

### Post by svivian on 2008-11-22
I've just upgraded to Ubuntu 8.10, and my back/forward buttons on my mouse aren't working any more. Previously I edited my xorg.conf to add them in, but now parts are commented out, and it says, "commented out by update-manager, HAL is now used"

I've done some searching but can't find anything about using HAL to configure my mouse. Is there an app I need to install or something?

---

### Post by kostkon on 2008-11-22
> **svivian said:**
> I've just upgraded to Ubuntu 8.10, and my back/forward buttons on my mouse aren't working any more. Previously I edited my xorg.conf to add them in, but now parts are commented out, and it says, "commented out by update-manager, HAL is now used"

I've done some searching but can't find anything about using HAL to configure my mouse. Is there an app I need to install or something?
You have to make your own .fdi file. Give [this thread]("http://ubuntuforums.org/showthread.php?t=948154") a read, for a start.

---

### Post by svivian on 2008-11-22
I tried this as my /etc/hal/fdi/policy/mouse.fdi but it's not working. I basically took the values from my xorg.conf. Is this the right way to do it? Can you spot any mistakes?

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<device>
	<match key="info.capabilities" contains="input.mouse">
		<merge key="input.x11_options.Emulate3Buttons" type="string">false</merge>
		<merge key="input.x11_options.Buttons" type="string">7</merge>
		<merge key="input.x11_options.ZAxisMapping" type="string">4 5</merge>
		<merge key="input.x11_options.ButtonMapping" type="string">1 2 3 6 7 4 5</merge>
	</match>
</device>
</deviceinfo>

```

---

### Post by svivian on 2008-11-22
UPDATE: this appears to be working in Firefox, but not in Opera or Nautilus.

8 and 9 were the numbers that came up from running xev. My current fdi file is as follows:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<device>
<match key="info.capabilities" contains="input.mouse">
<merge key="input.x11_options.Device" type="string">/dev/input/mice</merge>
<merge key="input.x11_options.Protocol" type="string">ExplorerPS/2</merge>
<merge key="input.x11_options.Emulate3Buttons" type="string">false</merge>
<merge key="input.x11_options.Buttons" type="string">7</merge>
<merge key="input.x11_options.ZAxisMapping" type="string">4 5</merge>
<merge key="input.x11_options.ButtonMapping" type="string">1 2 3 8 9 4 5</merge>
</match>
</device>
</deviceinfo>
```

Any ideas?

---

### Post by svivian on 2008-11-22
Well I got it working in Opera, but now it doesn't work in Firefox! Aargh!

As recommended by this article... [http://mesanna.wordpress.com/2008/11/02/ubuntu-810-intrepid-ibex-mouse-configuration/](http://mesanna.wordpress.com/2008/11/02/ubuntu-810-intrepid-ibex-mouse-configuration/)
...I added a file ".xmodmap" to my home directory. Finally got the right order for Opera and it must be different for Firefox.

See, this is why people hate linux. Ah, screw it...

---

### Post by visitor u on 2008-12-21
> **svivian said:**
> 
See, this is why people hate linux. Ah, screw it...

i will just not use, mouse does not work, sound does not work, it is a piece of joke not os

---

