---
title: "Which video driver does Ubuntu use by default?"
date: 2009-02-12
forum: Hardware
---

### Post by luvr on 2009-02-12
I'm running Ubuntu 8.10 on a system with a Gigabyte **GA-MA78G-DS3H** motherboard, which has an integrated **ATI Radeon HD 3200** graphics adapter.

If I connect the system to a **Sony SDM-X82** LCD screen, which has a native resolution of **1280x1024,** then Ubuntu gets the display configuration wrong: It sets the display to ***1152x864,*** and the *Monitor Resolution Settings* utility shows the following options for the resolution: 1360x768, 1152x864, 1024x768, 800x600, 640x480, and "Off"--The correct resolution of 1280x1024 is even missing from the list!

After some experimentation, I learned that the problem disappears if I simply add the line
```
   Driver   "vesa"
```to the *"Device"* section in my *xorg.conf* file.

That made me wonder what driver Ubuntu uses by default? Must be something different from VESA, mustn't it?

Also, how can I find out which driver is being used by a running Ubuntu system? I tried *lsmod* and *lshw,* but these commands don't show the video driver. Is there any other command that does show the video driver?

Finally, I don't want to install the proprietary AMD/ATI driver, because I find it rather troublesome. Is there an easy way to install the open-source driver that is, apparently, becoming available these days? Even though it's probably an unfinished work, I would like to try and see how well or how poorly it performs.

---

### Post by luvr on 2009-02-13
I have just found documentation about the open-source ATI driver over at the Ubuntu Community Documentation pages: [RadeonDriver.]("https://help.ubuntu.com/community/RadeonDriver") Will give it a try.

That still leaves my two other questions:
[LIST]
[*]Which display driver does Ubuntu use by default?
*(The xorg.conf file, by default, doesn't specify a driver.)*
[*]How can I query the name of the display driver in use on a running system?
*(Particularly when the xorg.conf file doesn't specify a driver.)*
[/LIST]

---

### Post by markbuntu on 2009-02-13
/var/log/Xorg.0.log will show you more than you need to know about what x is doing when it starts up, including which driver it is using.

---

### Post by luvr on 2009-02-13
> **markbuntu said:**
> /var/log/Xorg.0.log will show you more than you need to know about what x is doing when it starts up, including which driver it is using.
Many thanks! Should have remembered to look there first...

I'm running the ati radeon driver now, but the screen image is positioned a little bit too high: Approximately the top half of the top panel bar is off-screen, and at the bottom of the screen there's a black border. *(In fact, it seems to me that this ati radeon driver is the default, since I get the exact same behaviour by default.)*

I tried *xvidtune,* but that doesn't do anything useful; even if I immediately hit *"Test,"* without modifying any values, I get an *"Invalid Mode requested"* message, telling me:
> Sorry: You have requested a mode-line
That is not possible, or not supported by your
hardware configuration

The *Xorg.0.log* file does seem to report two possible modes for the 1280x1024 resolution, so perhaps I should try and use the other reported modeline values, and see if that helps any?

That'll be for tomorrow, however. It's getting late, I'm getting tired, and I need my sleep... :shock:

---

### Post by luvr on 2009-02-15
Been playing with the ati radeon driver, but I cannot get it to display the screen image in the correct position when I'm running at 1280x1024. The image is displayed a little too high, no matter what I do.

I have now even copied the mode lines (as I find them in my Xorg.0.log) into the xorg.conf file, but that doesn't help: Nothing changes.

I cannot, for the life of me, understand where the driver gets the idea that it should run at a resolution of 1152x864?!? There's nothing in the Xorg.0.log file that gives even the slightest hint that there even exists anything like this resolution on my hardware...

There seem to be quite a few similar reports about this type of problem, and there doesn't seem to be anything that can be done about it for now. I think I'll leave it at that, and see if Ubuntu 9.04 (the Jaunty Jackalope) fixes this; I'm currently running the alpha4 LiveCD--which boots up at 1024x768, and the *"Screen Resolution"* utility crashes when I attempt to start it, so I wouldn't know if I could set the resolution any higher. At least it doesn't do something as absurd as 1152x864... which just *might* be a good sign...

---

### Post by luvr on 2009-02-28
I'm running the Ubuntu 9.04 alpha5 LiveCD now, and that starts up with the correct resolution of 1280x1024, **and** it displays the screen image at the perfectly correct position!

Furthermore, the *"Screen Resolution"* utility no longer crashes, and it lists only those resolutions that the monitor supports (and that are listed in the Xorg.0.log file).

Looks like 9.04 will get rid of the most irritating display problems for me. Great news!

Of course, that still leaves the issue of properly supported full-featured drivers for ATI graphics adapters--but whether we'll ever see those is for ATI to decide.

---

