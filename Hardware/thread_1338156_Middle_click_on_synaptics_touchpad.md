---
title: "Middle click on synaptics touchpad"
date: 2009-11-26
forum: Hardware
---

### Post by Iesos on 2009-11-26
Hi,

I have just installed 9.10 on a tablet and noticed that when i 2-finger click my touchpad, I get a left-click. Now I do not see the use for this, the excellent use for the two-finger click is to be able to copy and paste. Hence I wanted to reactivate that feature.

I know that hal is the way to do things in this era, so I try to do it the hal-way. In /usr/share/hal/fdi/policy/20thirdparty/ there is an example fdi and in the man pages for synaptics it says how I should activate this.

My fdi file is (/etc/hal/fdi/policy/11-x11-synaptics.fdi)
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <merge key="input.x11_options.TapButton2" type="string">3</merge>
    </match>
  </device>
</deviceinfo>
```

my guess was that 3 is the middle button, however according to the man pages, 0 disables 2-finger tap, but still using two fingers gives me a left click.

So, what is wrong with the fdi file? Can anyone help me on this?

P.S.
Just a side question. Restart hal is all I need to do when I edit an fdi right (# restart hal)? I have rebooted to make sure, but I would like to know if this is enough.

---

### Post by Iesos on 2009-11-26
Ok, this I could figure out for myself:

The fdi-file works. Looking in lshal, I can see the change (my side question is also answered (in the positive)). However the feature is not activated. Two possibilities:

1 - Something overrides the hal settings. I guess this is not the case, since why then would you be using hal?

2 - I have misunderstood the synaptics man pages. Can someone decipher which option I am to set to get a 2-finger click on the touchpad to act as a middle mouse button?

---

### Post by Iesos on 2009-11-26
ok, can someone please just their lshal or fdi for their synaptics if you have one working? I'll figure it out by myself if I just get some example files that have this feature activated.

---

### Post by bornagainpenguin on 2009-12-01
/BUMPing because I too would like to revert this back to the previously default behavior...

--bornagainpenguin

---

### Post by sgosnell on 2009-12-01
Two fingers gives me the middle click, three is right-click. Plus, a single tap in the top right corner gives a middle click, and bottom right corner gives a right click.  I don't have the files you cited.

---

### Post by bornagainpenguin on 2009-12-03
> **sgosnell said:**
> Two fingers gives me the middle click, three is right-click. Plus, a single tap in the top right corner gives a middle click, and bottom right corner gives a right click.  I don't have the files you cited.

This is a Karmic issue apparently relating to the mouse driver.  Someone in the Italian eeepc forums posted a recompiled module that works under Karmic and fixes the behavior back to the default you mention for Jaunty and earlier--it doesn't work that way under Karmic.

--bornagainpenguin

---

### Post by STuPiDiCuS on 2009-12-08
This worked for me, HP DV5T, 9.10 32 bit. 

[http://ubuntuforums.org/showpost.php?p=8323401&postcount=6](http://ubuntuforums.org/showpost.php?p=8323401&postcount=6)

Now to get it applied on startup.

---

### Post by bornagainpenguin on 2010-01-07
The eeeuser.com fix I mentioned can be found here: [http://forum.eeeuser.com/viewtopic.php?id=79225](http://forum.eeeuser.com/viewtopic.php?id=79225)

Scroll down to message #10, which has the Italian link with the fix.

--bornagainpenguin

---

