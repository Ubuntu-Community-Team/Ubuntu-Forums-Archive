---
title: "Interlink VersaPad driver/problems"
date: 2011-10-07
forum: Hardware
---

### Post by summersab on 2011-10-07
All,

I have a Toughbook CF-31 that comes with a Interlink VersaPad. Out of the box with Windows 7, it works fine. In Ubuntu, it is completely unresponsive. However, I emailed the manufacturer and got a lot of good information. Since I'm not a driver dev and he's not an Ubuntu dev, we're at a bit of a roadblock. Below is our correspondence if anyone has some tech-guru insight.

> Hi Andrew,

The touchpad is actually a PS2 device, not a USB or PCI device.  We have dug into this issue and have found a an anomoly in the communication from Ubuntu to our VersaPad, and an error in the way our device handles the anomoly.
 
Please refer to the attached excel file which details the communication from Ubuntu to first a generic Microsoft PS2 wheel mouse, and then to our VersaPad.  This is not on a Toughbook, since that machine does not have an external PS2 port.  However the results should be very similar to what happens in the Toughbook.
 
I have highlighted the problem areas in yellow; scroll down to find them.   You will see in both cases that Ubuntu tries to set the mouse sampling rate to some disallowed and unusual values.  The allowed values, per the PS2 spec , are hex values of 0x0A, 0x14, 0x28, 0x3C, 0x50, 0x64, and 0xC8.  Ubuntu is trying to set the sampling rate to 0x66 and 0x88.   This may be part of some "magic knock" where certain devices might recognize these codes and respond by going into a special mode.   We are not familiar with this particular magic knock if that is really what it is.
 
Unfortunately, our device does not handle this anomoly in the correct manner.   I note also that the Microsoft mouse also fails to follow the spec, but it is apparently close enough.  What should happen is that when the host first sends the unrecognized value of 0x66, the device should respond with a request for resend (0xFE).  Then the host will resend the most recently sent byte.  If the device still does not recognize or like the value, it should respond with an error (0xFC).  The VersaPad fails to respond in this way, and then has a bug where it is forever stuck in an error mode.  
 
I have already verified that adding 0x66 and 0x88 to the list of allowed sample rates does indeed let the VersaPad work on Ubuntu.  Of course we will also be improving the error handling to be more robust.
 
However the Toughbook firmware is not field upgradeable, so our bugfix would not help you with your existing Toughbooks, or any new Toughbooks until a Panasonic engineering refresh allows a firmware change.  This is unfortunate, and I apologize for any disappointment or frustration that this may cause.
 
If you have some expertise at the PS2 protocol and how it works in Ubuntu, you may be able to modify the communication to the VersaPad.   Removing the attempt to set the sampling rate to unorthodox values will most likely allow the VersaPad to function.   
 
Best regards,
 
Jeff


> Jeff,

Since this isn’t my technical area of expertise, I do have one question. Where did you edit these hex values in Ubuntu to get the VersaPad to work, and why wouldn’t this work in the case of the Toughbooks? I’m confused if you modified the firmware at a hardware level or a settings file at the OS level. If the latter, then that should work just fine since we will be using Ubuntu and Ubuntu-derived systems.

Thanks again for all your support!

Andrew


> Hi Andrew,

I modified the firmware in a lab version of our VersaPad, which was then connected to the external PS2 port of a generic PC.  We are unable to modify the firmware of a closed Toughbook without complete disassembly and painstaking desoldering and resoldering.  I was not modifying the firmware inside a PC or a BIOS or anything like that.

You would be free to post our discussion as you like, but please do me the favor of an email if you ever come to an understanding of  the following questions:

[B]-why does Ubuntu try to set the sample rate to 0x66 and then 0x88?
-how do you modify that behavior?[/B]

Also, if you ever encounter a fix, such as for example a driver patch or something like that, I would be happy to document the communication stream between the OS and the VersaPad.  And I would love a copy.  

Thanks,

Jeff


---

### Post by summersab on 2011-10-10
As a bump and new info, it seems that FreeBSD supports some basic VersaPad input - any thoughts on this, and is it possible to merge it?

[http://www.unix.com/man-page/FreeBSD/8/moused/](http://www.unix.com/man-page/FreeBSD/8/moused/)

---

### Post by sjuranic on 2011-11-03
I'm experiencing these problems as well.  I'm not really a kernel dev either, but I'll take a look at it and see what I can figure out.

Are you having any trouble with the ethernet port?  I'm having trouble where the device isn't even present when I do an 'ifconfig -a'.  I should see an eth0, but there's nothing there.  Have you seen anything like this?

---

### Post by Jws0001 on 2011-11-07
Bump.  I also am having this issue.  And I also am missing an ethernet adapter in 10.04, although it seems to be fine in 11.10.  Doesn't matter what version of Ubuntu I use, the touchpad is useless.  There has to be a way to change the PS/2 polling rate...

---

### Post by summersab on 2011-11-07
Okay, so I know that Ubuntu and Linux in general have pulled some code from FreeBSD from time to time, but I'm not sure how this would work. It LOOKS like FreeBSD's moused(8) has VersaPad support:

[http://ftp2.pl.freebsd.org/pub/FreeBSD/current/src/usr.sbin/moused/](http://ftp2.pl.freebsd.org/pub/FreeBSD/current/src/usr.sbin/moused/)

However, moused doesn't seem to be supported in Ubuntu since I'm not finding a single man page in 11.10, but I could be wrong. Is this a lead?

---

### Post by Jws0001 on 2011-11-08
I'm not sure if or how we could use this.  I've looked at the source for the psmouse module and I don't see any references to sampling rate being set to 0x66 or 0x88.

Edit:

The sentelic.c file in kernel source (linux-2.6.32/drivers/input/mouse) has ps2_sendbyte commands in it that attempt to send the sequences described as problematic above, 0x66 and 0x88.  I'm still digging...

> static int fsp_reg_read(struct psmouse *psmouse, int reg_addr, int *reg_val)
{
	struct ps2dev *ps2dev = &psmouse->ps2dev;
	unsigned char param[3];
	unsigned char addr;
	int rc = -1;

	/*
	 * We need to shut off the device and switch it into command
	 * mode so we don't confuse our protocol handler. We don't need
	 * to do that for writes because sysfs set helper does this for
	 * us.
	 */
	ps2_command(ps2dev, NULL, PSMOUSE_CMD_DISABLE);
	psmouse_set_state(psmouse, PSMOUSE_CMD_MODE);

	ps2_begin_command(ps2dev);

	if (ps2_sendbyte(ps2dev, 0xf3, FSP_CMD_TIMEOUT) < 0)
		goto out;

	[B]/* should return 0xfe(request for resending) */
	ps2_sendbyte(ps2dev, 0x66, FSP_CMD_TIMEOUT2);
	/* should return 0xfc(failed) */
	ps2_sendbyte(ps2dev, 0x88, FSP_CMD_TIMEOUT2);
[/B]
	if (ps2_sendbyte(ps2dev, 0xf3, FSP_CMD_TIMEOUT) < 0)
		goto out;

	if ((addr = fsp_test_invert_cmd(reg_addr)) != reg_addr) {
		ps2_sendbyte(ps2dev, 0x68, FSP_CMD_TIMEOUT2);
	} else if ((addr = fsp_test_swap_cmd(reg_addr)) != reg_addr) {
		/* swapping is required */
		ps2_sendbyte(ps2dev, 0xcc, FSP_CMD_TIMEOUT2);
		/* expect 0xfe */
	} else {
		/* swapping isn't necessary */
		ps2_sendbyte(ps2dev, 0x66, FSP_CMD_TIMEOUT2);
		/* expect 0xfe */
	}
	/* should return 0xfc(failed) */
	ps2_sendbyte(ps2dev, addr, FSP_CMD_TIMEOUT);

	if (__ps2_command(ps2dev, param, PSMOUSE_CMD_GETINFO) < 0)
		goto out;

	*reg_val = param[2];
	rc = 0;

 out:
	ps2_end_command(ps2dev);
	ps2_command(ps2dev, NULL, PSMOUSE_CMD_ENABLE);
	psmouse_set_state(psmouse, PSMOUSE_ACTIVATED);
	dev_dbg(&ps2dev->serio->dev, "READ REG: 0x%02x is 0x%02x (rc = %d)\n",
		reg_addr, *reg_val, rc);
	return rc;
}

---

### Post by Jws0001 on 2011-11-08
Ok, here is the function call in psmouse-base.c that probes the device for its capabilities.  I've highlighted the section that calls fsp_detect(), which in turn calls fsp_reg_read().  From my previous post, fsp_reg_read() is the function that appears to contain the hex sequences that are invalid for the Interlink VersaPad.  My thought it that if I comment out all of the probe section listed below except for base and recompile, it should skip that bad piece of code and possibly work.

> /*
 * psmouse_extensions() probes for any extensions to the basic PS/2 protocol
 * the mouse may have.
 */

static int psmouse_extensions(struct psmouse *psmouse,
			      unsigned int max_proto, bool set_properties)
{
	bool synaptics_hardware = false;

/*
 * We always check for lifebook because it does not disturb mouse
 * (it only checks DMI information).
 */
	if (lifebook_detect(psmouse, set_properties) == 0) {
		if (max_proto > PSMOUSE_IMEX) {
			if (!set_properties || lifebook_init(psmouse) == 0)
				return PSMOUSE_LIFEBOOK;
		}
	}

.
.
.

[B]/*
 * Try Finger Sensing Pad. We do it here because its probe [COLOR="Red"]upsets
 * Trackpoint devices[/COLOR] (causing TP_READ_ID command to time out).
 */
	if (max_proto > PSMOUSE_IMEX) {
		if (fsp_detect(psmouse, set_properties) == 0) {
			if (!set_properties || fsp_init(psmouse) == 0)
				return PSMOUSE_FSP;
/*
 * Init failed, try basic relative protocols
 */
			max_proto = PSMOUSE_IMEX;
		}
	}
[/B]
/*
 * Reset to defaults in case the device got confused by extended
 * protocol probes. Note that we follow up with full reset because
 * some mice put themselves to sleep when they see PSMOUSE_RESET_DIS.
 */
	ps2_command(&psmouse->ps2dev, NULL, PSMOUSE_CMD_RESET_DIS);
	psmouse_reset(psmouse);

	if (max_proto >= PSMOUSE_IMEX && im_explorer_detect(psmouse, set_properties) == 0)
		return PSMOUSE_IMEX;

	if (max_proto >= PSMOUSE_IMPS && intellimouse_detect(psmouse, set_properties) == 0)
		return PSMOUSE_IMPS;

[B]/*
 * Okay, all failed, we have a standard mouse here. The number of the buttons
 * is still a question, though. We assume 3.
 */
	ps2bare_detect(psmouse, set_properties);
[/B]
	if (synaptics_hardware) {
/*
 * We detected Synaptics hardware but it did not respond to IMPS/2 probes.
 * We need to reset the touchpad because if there is a track point on the
 * pass through port it could get disabled while probing for protocol
 * extensions.
 */
		psmouse_reset(psmouse);
	}

	return PSMOUSE_PS2;
}

---

### Post by jllink on 2011-11-11
Did it work?  Let us know.

Thanks.

---

### Post by Jws0001 on 2011-11-14
Nope... doesn't seem to have any effect.  I think I'm stuck at this point.  I stuck some print statements in the psmouse-base.c code to see what it was doing and I get this from dmesg:

init() (module loads into the kernel)

psmouse_connect()
psmouse_set_state()
psmouse_probe()
psmouse_interrupt()

psmouse_connect()
psmouse_set_state()
psmouse_probe()
psmouse_interrupt()
psmouse_interrupt()

psmouse_connect()
psmouse_set_state()
psmouse_probe()
psmouse_interrupt()

psmouse_connect()
psmouse_set_state()
psmouse_probe()
psmouse_interrupt()

It stops looping through those functions at this point.  probe() always seems to return -1.  *shrug*

> **jllink said:**
> Did it work?  Let us know.

Thanks.

---

### Post by benmesander on 2012-01-17
If you supply the argument:

proto=base

To the psmouse driver module, the CF-31 versapad will operate correctly.

Please note if it has locked up prior to you doing this, the computer will require a power cycle before it will operate normally.

---

