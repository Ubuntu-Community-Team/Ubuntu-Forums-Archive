---
title: "How to enable hardware acceleration with the Radeon HD 7870?"
date: 2013-07-16
forum: Hardware
---

### Post by scaru on 2013-07-16
[COLOR=#333333][FONT=UbuntuRegular]Any idea on how to do this? The open source driver does not do this, and the 2 propriety drivers (fglrx and fglrx-updates) both cause my computer to refuse to boot up.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]The output of /usr/lib/nux/unity_support_test -p is:[/FONT][/COLOR]

Not software rendered: noNot blacklisted: yesGLX fbconfig: yesGLX texture from pixmap: yesGL npot or rect textures: yesGL vertex program: yesGL fragment program: yesGL vertex buffer object: yesGL framebuffer object: yesGL version is 1.4+: yesUnity 3D supported: no[COLOR=#333333][FONT=UbuntuRegular]The lack of hardware acceleration has made my computer pretty much unusable, it runs minecraft at 6 fps... I'm currently on Ubuntu 13.04 if it matters. [/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Thanks in advance for the help![/FONT][/COLOR]

---

### Post by papibe on 2013-07-16
Hi scaru.

The problem with the proprietary driver may be a kernel compatibility problem. I would try to boot using the **nomodeset** option. Check the section 'How to temporarily set kernel boot options on an installed OS' in this [thread]("http://ubuntuforums.org/showthread.php?t=1613132") for details.

If that works, follow the steps on the next section (How to permanently set kernel boot options on an installed OS) in order to set the option for every subsequent boot.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by scaru on 2013-07-17
> **papibe said:**
> Hi scaru.

The problem with the proprietary driver may be a kernel compatibility problem. I would try to boot using the **nomodeset** option. Check the section 'How to temporarily set kernel boot options on an installed OS' in this [thread]("http://ubuntuforums.org/showthread.php?t=1613132") for details.

If that works, follow the steps on the next section (How to permanently set kernel boot options on an installed OS) in order to set the option for every subsequent boot.

Hope it helps. Let us know how it goes.
Regards.

Just tried that and still no hardware acceleration.

---

### Post by Yellow Pasque on 2013-07-17
I would try installing Catalyst 13-4 manually: [http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

---

### Post by QIII on 2013-07-17
In my testing, a manual installation does not allow setting up hardware acceleration.

When you used the nomodeset option, could you boot with fglrx-updates?

If you can, I think we can get what little hardware acceleration ATI offers for Linux enabled.

---

### Post by Yellow Pasque on 2013-07-17
> **QIII said:**
> In my testing, a manual installation does not allow setting up hardware acceleration

Huh? Do you mean with this specific card?

> If you can, I think we can get what little hardware acceleration ATI offers for Linux enabled. 
Catalyst offers full 3D accel for this card (open-source is still under development). Again, I'm not sure what you mean.

---

### Post by QIII on 2013-07-17
Ah, crud.  Red-faced.  He did say **3D**.  Video, no.  3D, yes.

I will now go hide in a corner and come out when I am ready to pay closer attention.

---

### Post by scaru on 2013-07-17
> **Temüjin said:**
> I would try installing Catalyst 13-4 manually: [http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

Just tried that and the same thing as before happened, everything worked fine, I reboot, and then it blackscreens shortly after the Ubuntu loading screen appears. Any ideas?

---

### Post by scaru on 2013-07-17
> **QIII said:**
> When you used the nomodeset option, could you boot with fglrx-updates?

If you can, I think we can get what little hardware acceleration ATI offers for Linux enabled.

Nope, just tried that and same thing (black screen on boot up). Any other ideas?

---

### Post by Yellow Pasque on 2013-07-19
When the system "blackscreens", can you get to a terminal by pressing Ctrl+Alt+F1 ?

---

