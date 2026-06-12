---
title: "thinkpad T60 cannot run ubuntu10.10?? Ask for help~~"
date: 2010-11-13
forum: Hardware
---

### Post by farmerking on 2010-11-13
Hi guys,

I have a thinkpad T60 with intel T2400 and ati x1300.  However I failed to get it running the latest ubuntu 10.10. The screen just go  black when I boot the system and even under the safety graphic mode.  Would anyone please suggest a way to help me figure this out since I am a  freshman in ubuntu. Thanks

---

### Post by farmerking on 2010-11-14
Can someone help me with this?

Thanks~

---

### Post by sikander3786 on 2010-11-14
Hi.

If you are booting from Live CD, did you try using **nomodeset** parameter?

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

Or if it is installed, press and hold Shift key at the Bios screen until you see the Grub menu. Press 'e' to edit the first entry. Navigate to "quiet & splash". Delete them and type "radeon.modeset=0" in their place. Press Ctrl + X to continue boot and see if desktop shows up this time.

I think X1300 is not supported by the new verions of fglrx in Ubuntu but you could still use the open source ATI drivers??? Somebody needs to confirm this. However that blank screen problem should go away by following the steps mentioned above.

---

### Post by farmerking on 2010-11-14
Thank you! I have successfully boot the system. However I got problems that my fan is always running at high speed. Do you know any solution to this?
Many Thanks~~

---

### Post by sikander3786 on 2010-11-14
> **farmerking said:**
> Thank you! I have successfully boot the system. However I got problems that my fan is always running at high speed. Do you know any solution to this?
Many Thanks~~
Glad it worked for you.

Not many ideas here for that fan problem. I never got that :-) Wait and some-one else might soon jump in and help you on that.

Or better start a new thead with fan speed titles to catch attention.

---

### Post by farmerking on 2010-11-14
OK! Thanks a lot! :)

---

### Post by farmerking on 2010-11-14
> **sikander3786 said:**
> Glad it worked for you.

Not many ideas here for that fan problem. I never got that :-) Wait and some-one else might soon jump in and help you on that.

Or better start a new thead with fan speed titles to catch attention.

I have a new problem. I have already install the open-source-driver for the x1300. However I still have to use the method you told me to boot the system. If I boot the system directly, the screen just go black again...Do you know why?

Thanks~

---

### Post by sikander3786 on 2010-11-15
You need to edit /etc/default/grub,

```
gksudo gedit /etc/default/grub
```

And put "radeon.modeset=0" replacing "quiet & splash" in this line.

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Now update Grub by,

```
sudo update-grub
```

The changes would become permanent.

Infact I have never use ATI cards on Linux and have no idea about if you later can install the proprietary drivers for X1300 on Meerkat. If you get those drivers sometime later, change that line back to "quiet & splash".

---

### Post by farmerking on 2010-11-15
> **sikander3786 said:**
> You need to edit /etc/default/grub,

```
gksudo gedit /etc/default/grub
```And put "radeon.modeset=0" replacing "quiet & splash" in this line.

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```Now update Grub by,

```
sudo update-grub
```The changes would become permanent.

Infact I have never use ATI cards on Linux and have no idea about if you later can install the proprietary drivers for X1300 on Meerkat. If you get those drivers sometime later, change that line back to "quiet & splash".


Thank you a lot~

---

