---
title: "Aiptek 6000U tablet?"
date: 2010-08-06
forum: Hardware
---

### Post by knurledflanges on 2010-08-06
Hi everyone, I want to do some graphic stuff. I have an old (bought it probably 10 years ago) Aiptek T-6000U tablet. It's always worked well, money is tight and I don't really want to replace it. I had it working under Zenwalk several years ago; can't remember what hoops I had to jump through, maybe used a Windows driver? My machine has Ubuntu 9.10 on it now. Normally I use xfce, if that matters.

First I tried installing xserver-xorg-input-aiptek and making the /usr/share/hal/fdi/policy/10-linuxaiptek.fdi file with the following contents, as described in the community documentation guide:
```
<deviceinfo version="0.2">
&#8722;
<device>
&#8722;
<match key="info.product" contains="Aiptek">
<merge key="input.x11_driver" type="string">aiptek</merge>
<merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
<merge key="input.x11_options.USB" type="string">On</merge>
<merge key="input.x11_options.Type" type="string">stylus</merge>
<merge key="input.x11_options.Mode" type="string">absolute</merge>
<merge key="input.x11_options.zMin" type="string">0</merge>
<merge key="input.x11_options.zMax" type="string">511</merge>
</match>
</device>
</deviceinfo>
``` 

Then I follow the procedure described [here]("http://ubuntuforums.org/showthread.php?t=1248550&highlight=6000u") and do 
sudo echo absolute > ./coordinate_mode &&  sudo echo anything > ./executea bunch of times, and then the tablet will start controlling the cursor with the stylus held down but not while "hovering", and I can't get it to "click" anything, ie no input other than position. It's also not going to the correct onscreen position relative to wear on the tablet the stylus is being pushed. So basically it's useless. I've tried re-installing xserver-xorg-input-aiptek several times; I believe one time I had it so it was moving the cursor while "hovering" the stylus.

While seeing if I could get the tablet to work in GIMP, I encountered a situation where in addition to not registering pressure/clicks from the tablet, holding the normal mouse button wouldn't activate the brush, pencil, etc tools when selected.

The community documentation page says that some Aiptek tablets use the Wacom driver. I tried removing the aiptek package and the file I created and trying that. I installed wacom-tools and found that xserver-xorg-input-wacom was already installed (it's still there, and I haven't tried removing it). This caused the tablet to not do anything at all.

I should also mention that I'm not 100% sure of what "normal" behavior for the tablet is under Ubuntu, ie whether by default you can use the stylus for pointing and clicking like the mouse, as is the default behavior in Windows.

Thanks!

---

