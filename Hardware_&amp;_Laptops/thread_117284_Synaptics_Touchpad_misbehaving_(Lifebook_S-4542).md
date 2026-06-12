---
title: "Synaptics Touchpad misbehaving (Lifebook S-4542)"
date: 2006-01-14
forum: Hardware &amp; Laptops
---

### Post by fiestaforever on 2006-01-14
Hi, 

after Installation of Ubuntu 5.10 (Lifebook S-4542 which I got used), I am having problems with my touchpad (probably a Synaptics model, as I read on some sites, I can't get precise information from Fujitsu). 
The touchpad is "tappable" (clickable), so you can tap on the touchpad to "click". Unfortunately, it seems to send random clicks all the time, so you keep activating/dragging objects etc. all the time unwillingly. Pretty annoying. 
This seems to be either a defect of the touchpad or a misfunction due to unappropriate drivers. The touchpad shows the same annoying behaviour in Windows, too (which doesn't have a specific driver and treats the touchpad as a PS/2 mouse). But it's even more recognizable in Ubuntu.

The question is: 
(a) Is there a specific driver to correct this or 
(b) is there a way to disable the "tappability"?

TIA

**Edited 2006.01.20: Update** - I found out that it is not a Synaptics touchpad. It is an **Alps Glidepoint** touchpad. See below.

---

### Post by Sef on 2006-01-20
> (b) is there a way to disable the "tappability"?

Yes can go into your BIOS and shut the touchpad off and just have only a mouse work.  (USB is better than PS/2 - sometimes ps/2 mice do not work without tweaking.)  

Note: my touchpad/mouse is listed under pointer device in the BIOS.

---

### Post by Khaine on 2006-01-20
It a common complaint, their are several fixes (from some website about Linux on a Toshiba M30) :

Another option would be to patch the kernel, as described in a mail I got from Simon Effenberg, who found the reason for the bug in the kernel 2.6-sources to show up again, specifically in "./drivers/input/mouse/psmouse-base.c" of the PS/2-driver, which causes the keyboard-bouncing to show up again with SuSE 9.1 and which can be fixed with a small patch. The original looks like this

/*
 * Try Synaptics TouchPad
 */
      if (psmouse_max_proto > PSMOUSE_PS2 && synaptics_detect(psmouse)) {
                synaptics_hardware = 1;
                psmouse->vendor = "Synaptics";
                psmouse->name = "TouchPad";

                if (psmouse_max_proto > PSMOUSE_IMEX) {
                        if (synaptics_init(psmouse) == 0)
                                return PSMOUSE_SYNAPTICS;

/*
 * Some Synaptics touchpads can emulate extended protocols (like IMPS/2).
 * Unfortunately Logitech/Genius probes confuse some firmware versions so
 * we'll have to skip them.
 */
                      psmouse_max_proto = PSMOUSE_IMEX;
                }
        }
and has to be changed to

/*
 * Try Synaptics TouchPad
 */
/*      if (psmouse_max_proto > PSMOUSE_PS2 && synaptics_detect(psmouse)) {
                synaptics_hardware = 1;
                psmouse->vendor = "Synaptics";
                psmouse->name = "TouchPad";

                if (psmouse_max_proto > PSMOUSE_IMEX) {
                        if (synaptics_init(psmouse) == 0)
                                return PSMOUSE_SYNAPTICS;
*/
/*
 * Some Synaptics touchpads can emulate extended protocols (like IMPS/2).
 * Unfortunately Logitech/Genius probes confuse some firmware versions so
 * we'll have to skip them.
 */
/*                      psmouse_max_proto = PSMOUSE_IMEX;
                }
        }
*/


Synaptics bug solution
Thanks to David Flogeras for his effort contacting the people who helped out: 
I contacted the Synaptics kernel guys, and they told me to try passing rate=40 to the psmouse module. Either as a module:

modprobe psmouse rate=40

or if compiled into the kernel, pass the kernel:

psmouse.rate=40 
David thanks Peter and Dmitry (synaptics kernel hackers) for the tip.

---

### Post by yves on 2006-01-20
Hi,

I have the same problem on a BM Thinkpad T42.  I just found this that I beleive will do the trick, but did not tried it yet :  [http://web.telia.com/~u89404340/touchpad](http://web.telia.com/~u89404340/touchpad)

---

### Post by fiestaforever on 2006-01-20
**Update:** I haven't tried anything new in Ubuntu yet, but I have found out now that it is **not a Synaptics ** touchpad, **but an Alps Glidepoint** touchpad. Sorry for misleading everyone, but this is rather hard to find out. 
I found a driver for Windows from Fujitsu (which is btw **really** hard to find, as they have lots of missing files and lots of incorrect information on their various sites in different countries), now it works perfectly (taps, scrolls etc.) under Windows. 
Under Linux, I haven't found anything specific yet to enable (sic!) those functions. In fact, the identification as Synaptics I read on a Linux site. It seem to work with the Synaptics driver, but barely. The "jumping" bug, however, seems to be specific for real Synaptics touchpads and has nothing to do with my case. I never had "jumping" or "bouncing", but random clicks all the time.

---

### Post by fiestaforever on 2006-12-31
Another Update (in case anyone is interested): 
I don't use that machine regularly any more, but temporarily installed Xubuntu 6.10 Edgy on it and now the touchpad seems to behave better (even the vertical scroll works). And I have come across a description of settings to make the Alps touchpad work correctly with the Synaptics driver. Unfortunately, I can't remember where, and I haven't tried it.

EDIT: Nope, the same old "sticky click" problem (inadvertedly doing click-and-drag with touchpad). Still have to find a way to disable tappability.

---

