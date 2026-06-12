---
title: "Can't get Elantech Touchpad to work - Asus A42F"
date: 2010-07-21
forum: Hardware
---

### Post by transmition on 2010-07-21
I have been unable to configure my Touchpad on my Asus A42F. When I first installed Arch two days ago, after running Xorg -configure, the touchpad worked with two finger scrolling, multi-touch clicking, etc. However, I was unable to run anything like gsynaptics, or change any settings in /etc/X11/xorg.conf.d/ to change things like clicking behavior or disabling the touchpad while typing.

Under xinput list, my pointing device was listed as a Logitech Wheel Mouse, instead of some sort of trackpad.

Upon researching the issue, I discovered that this behavior was due to a problem with a kernel driver, but had been fixed in the 2.6.34 kernel. So I went ahead and upgraded, hopefully to allow myself to be able to start configuring the touchpad.

I have attached my current xorg.0.log, xorg.conf, and xinput list output. So far, my touchpad does absolutely nothing (I don't believe it is even being loaded).

Can anyone help me get this thing going?

EDIT: I managed to solve my issue by running the following commands:
```

echo "options psmouse force_elantech=1" | sudo tee -a /etc/modprobe.d/psmouse.conf
sudo rmmod psmouse && sudo modprobe psmouse

```

My touchpad now works perfectly, and xinput list shows the following:
> **xinput]
&#9121 said:**
> 
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynapticsTouchpad                           id=6    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad


---

### Post by verminform on 2010-07-24
Asus ePC 1015PE - Lucid

Thank you for this.  As strange as it may sound, I had the same problem as you did, but I was trying to turn the touchpad off; not on.  :D  

```
echo "options psmouse force_elantech=1" | sudo tee -a /etc/modprobe.d/psmouse.conf
```

Drove me to the brink of madness trying to simply turn the thing off; would have thought they would hardwire such an obvious feature, but that is just me.

At least I can turn it off.  Now to make these function keys useful...

---

### Post by iamroddo on 2010-08-25
I'm also trying to work out a way of turning off the touchpad on my 1015PE but I want to be able to do it either dynamically, when typing or manually, with FN-F3.

Adding the above options turned off the touchpad completely, I needed to remove the options and restart to turn it back on. Is there any way of marrying this with either detecting typing or with a function key?

---

### Post by s00n on 2011-04-27
thank you. it worked like a charm ;)

---

### Post by anarcho1188 on 2011-11-07
i tried this code

echo "options psmouse force_elantech=1" | sudo tee -a /etc/modprobe.d/psmouse.conf
sudo rmmod psmouse && sudo modprobe psmouse

but then instead my touchpad stopped working
before i could still use it but when i input the code it is disabled

any help?

---

### Post by evengrift on 2011-12-20
This 'fix' is probably obsolete as newer Kernels are unlikely to know the 'force_elantech' parameter.

If this borks your Trackbad you can remove the line from /etc/modprobe.d/psmouse.conf:
> sudo vi /etc/modprobe.d/psmouse.conf

Then reload the module
> sudo modprobe psmouse

---

