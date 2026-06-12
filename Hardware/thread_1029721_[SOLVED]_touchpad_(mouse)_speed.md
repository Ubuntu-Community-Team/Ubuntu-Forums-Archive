---
title: "[SOLVED] touchpad (mouse) speed"
date: 2009-01-03
forum: Hardware
---

### Post by rgrig on 2009-01-03
I used to set MinSpeed and MaxSpeed in xorg.conf so that the mouse moves faster. After upgrading to 8.10 the section for the touchpad was "commented out because hal is used." How can I achieve the same effect now?

System->Preferences->Mouse already is set to maximum speed but that's too slow for me.

---

### Post by Ruyuk on 2009-01-03
What are you talking about? Which OS?

---

### Post by Paul Miller on 2009-01-03
Doesn't System -> Preferences -> Mouse work for you?

---

### Post by rgrig on 2009-01-03
I'm talking about ubuntu.

The GUI thing works but, as I said, it's too slow for me. In 8.04 I could make the mouse faster by editing xorg.conf. Unfortunatelly the relevant section has been commented out by dist-upgrade.

---

### Post by kerry_s on 2009-01-03
> **rgrig said:**
> I used to set MinSpeed and MaxSpeed in xorg.conf so that the mouse moves faster. After upgrading to 8.10 the section for the touchpad was "commented out because hal is used." How can I achieve the same effect now?

System->Preferences->Mouse already is set to maximum speed but that's too slow for me.

you can still add it to xorg.conf.

```

Section "ServerLayout"

	InputDevice    "Touchpad"

```

```

Section "InputDevice"
        Identifier "Touchpad"
	 Driver      "synaptics"
        Option      "AccelFactor" "0.05"
EndSection

```

play with the number.

---

### Post by rgrig on 2009-01-03
Thanks. It works.
Is there any chance this will interact badly with hal?

---

### Post by kerry_s on 2009-01-03
> **rgrig said:**
> Thanks. It works.
Is there any chance this will interact badly with hal?

none that i know of. hal is suppose to give up to xorg.conf, so your settings are used.

---

