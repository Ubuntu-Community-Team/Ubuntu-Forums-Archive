---
title: "Pen buttons on Compaq TC1100"
date: 2007-10-12
forum: Hardware &amp; Laptops
---

### Post by robnz on 2007-10-12
I have Kubuntu 7.04 running on my Compaq TC1100 tablet. The wacom pen works great except for the three pen buttons on the left of the screen (in XP these are mapped to rotate screen, journal and keyboard). After a long Internet trawl I decided that only practical way to crack it was to modify the wacom driver myself.

I've done this and now 'xidump stylus' reports button events for each pen button. Strangely xev doesn't report the button press/release. If I use xsetwacom to map the buttons to key sequences they work partially. By partially I mean that I still have some work to do around the logic of the button press and the flags that the driver sets. What I'd really like to do is map these to XF86 events but so far I've come up short.

What I'm looking for is someone else with a TC1100 and more (or different) development experience than I have to assist.

For those interested the changes are as follows. 

First you'll need the source package and to set up an xorg build environment. Get the wacom sources from [http://linuxwacom.sourceforge.net/index.php/dl]("http://linuxwacom.sourceforge.net/index.php/dl"). I'm using linuxwacom-0.7.8-3.tar.bz2.

Modify isdv4Parse in src/xdrv/wcmISDV4.c according to the instructions in [this thread.]("http://sourceforge.net/mailarchive/message.php?msg_id=cab1bdbb05072112587e43d20b%40mail.gmail.com")

Modify xf86WcmSendButtons in src/xdrv/wcmCommon.c as follows (one change in blue)
```
/*****************************************************************************
 * xf86WcmSendButtons --
 *   Send button events by comparing the current button mask with the
 *   previous one.
 ****************************************************************************/

static void xf86WcmSendButtons(LocalDevicePtr local, int buttons, int rx, int ry, 
		int rz, int v3, int v4, int v5)
{
	int button, mask, bsent = 0;
	WacomDevicePtr priv = (WacomDevicePtr) local->private;
	WacomCommonPtr common = priv->common;
	DBG(6, priv->debugLevel, ErrorF("xf86WcmSendButtons "
		"buttons=%d for %s\n", buttons, local->name));

	/* Tablet PC buttons. */
	if ( common->wcmTPCButton && !IsCursor(priv) && !IsPad(priv) && !IsEraser(priv) )
	{
		[color=blue]if ( buttons & 57 )[/color]
		{
			if ( !(priv->flags & TPCBUTTONS_FLAG) )
			{
				priv->flags |= TPCBUTTONS_FLAG;
```

Do a make wacom_drv.so and copy the new driver to /usr/lib/xorg/modules/input/wacom_drv.so. Restart X and start playing.

---

### Post by phenest on 2007-10-30
This is great news! I was going to sell mine 'cos too much didn't work (pcmcia, sd card reader, etc). I have no development experience in Linux, but I am an experienced programmer in C++ (Windows to date) and would like to assist you. I'm not new to Linux as I've using it for about a year now.

I'm getting my TC1100 back out of the cupboard, and install 7.10.

Please let me know what I can do, and I'll gladly help.

---

### Post by phenest on 2007-10-30
Hmmm. I'm not getting any results here. Could you paste that code from the link here, please. I think that code shows some formatting codes (3D) and I'm not sure I've done it right.

---

### Post by phenest on 2007-10-30
I got it working. Spent all day on this. Please let me know if this works for you.

Everything is the the same with 1 addition to the code in src/xdrv/wcmISDV4.c
```
/* Coordinate data bit check */
if (data[0] & 0x40)
{
if ((int)data[0] == 0xc1)
{
if (data[1] & 0x07)
{
ds = &common->wcmChannel[0].work;
/* Now fool it into thiking it's in proximity */
ds->proximity = 1;
ds->buttons = ((data[1] & 0x07) << 3);
xf86WcmEvent(common,0,ds);
}
}
return common->wcmPktLength;
}
```

Now map the new buttons to keys. Add these lines to .profile in your home folder:
```

# enable buttons on HP TC1100
xsetwacom set stylus Button4 "core key shift F1"
xsetwacom set stylus Button5 "core key shift F2"
xsetwacom set stylus Button6 "core key shift F3"
```

Open the Configuration Editor and browse to apps/metacity/global_keybindings
run_command1[INDENT]<Shift>F1[/INDENT]
run_command2[INDENT]<Shift>F2[/INDENT]
run_command3[INDENT]<Shift>F3[/INDENT]
...then browse to apps/metacity/keybinding_commands...
command_1[INDENT]sh /usr/bin/rotate.sh[/INDENT]
command_2[INDENT]xournal[/INDENT]
command_3[INDENT]cellwriter[/INDENT]
Obviously, you need a rotate script, xournal, and cellwriter (or whatever you want). And the keys don't have to be shift F1, etc.

---

### Post by robnz on 2007-10-30
Awesome! It was the logic around proximity that I was referring to before. I simply didn't have more time to spend on it with two children under two and a house under renovation. I may not get the chance to try this right away but am expecting it will work. Next step will be to contribute this to the wacom project team for incorporation. It will be interesting to know whether this fix for the TC1100 breaks other tablets. There may need to be a TC1100 specific driver.

Thanks for picking up the baton. Rob

---

### Post by phenest on 2007-11-01
If you submit this to the Wacom Project, it needs to be noted that what we have done is a workaround. They may have a much better way of doing it and maybe able to generate key codes (same ones as XP?) instead of button presses.

I have noticed that if you wish to press a button twice, you need to move the stylus away from the button (out of proximity) for the 2nd press to work. As I said, they may have a better way of doing it.

---

### Post by robnz on 2007-11-01
Tested this last night in KDE and it doesn't work. There are a number of issues in Gutsy concerning xorg interacting with kwin so I suspect this may be related. Next chance I get I'll install Gnome and see how much my milage varies.

Your points regading submission are good. As I said earlier, this workaround may in fact break other Wacom based tablets. I wonder if *any* Wacom tablet PC using the standard driver reports Button4 and above. Perhaps this part of the tpc driver was simply never implemented. Could be worth checking the other driver modes to see how their button presses are managed. Whatever approach is used would likely port well into the tpc driver.

---

### Post by WolfpacKxx86 on 2007-11-02
Hey, i was wondering if you guys could help me out a bit here. I just finish fixing everything on my tc1100 after installing gutsy :) , but the only thing am stuck at is getting the 3 pen buttons to work. I was reading through your post and got stuck on how to make the wacom_drv.so file. If you can explain that step in a little more detail, that would be greatly appreciated. Thank you.

---

### Post by phenest on 2007-11-02
After downloading  the source code and making the alterations as stated in previous posts, you need to compile it. Open a terminal window and cd to the main directory containing the source. Type:
```
./configure
```
(no need for sudo). It may complain about not finding things. Simply install those packages from Synaptic. Keep trying until you get no errors. Then:
```
sudo make
```
You need to copy the newly compiled driver over (wacom_drv.so) as described in post #1. I did this without GDM running. Logout and press Ctrl/Alt/F2. Type:
```
sudo /etc/init.d/gdm stop
```
then copy wacom_drv.so to the specified folder and then reboot.

That's the gist. Reply if you need more details and one of us will help.

You mention everything else works, 'cos it don't on mine. Check the link in my signature and if there is anything you can help me with, post it there. Thanks.

---

### Post by robnz on 2007-11-02
Only one thing I'd add. If you're not used to compiling drivers then you might get confused trying to install missing items identified by ./configure. If it asks for **XYZ** and according to synaptic **XYZ** is already installed then look for **XYZ-dev** and install that also. The -dev packages contain header files that are needed for compiling.

Good luck,
Rob

---

### Post by mimatsu on 2007-11-05
hello i'm very interesting about this work, i make the driver with your specifications but in my tc110 do not work.
i have used xev and it had copied the event pen-on-botton but i did not set button with shift+f1.
Do you hel me?
thanks

---

### Post by phenest on 2007-11-06
> **mimatsu said:**
> i have used xev and it had copied the event pen-on-botton but i did not set button with shift+f1.

I suggest you follow all the information above exactly as it is to check it will work. If it works, you can change the <Shift>F1 afterward.

I assure you, the above method works in Gnome for both Feisty and Gutsy. It has not been tested in KDE yet.

---

### Post by rreynolds on 2007-11-18
Thank you!!!

This has been bugging the crap out of me since I got my tablet. Plus, I'm now marginally less afraid of real programming languages (I'm from a VBA background...)

---

### Post by phenest on 2007-11-19
> **rreynolds said:**
>  (I'm from a VBA background...)

Slightly off-topic I know, but take up a 'real' language like C. That's good for a lot of things and many different OS's too, not to mention web-sites.

It will also help you fix drivers like the example in this thread.

I never looked back after learning it.

---

### Post by rreynolds on 2007-11-19
To promote the continuation off topic:

I've always intended to move to an actual programming language from V BA but my problem has always been implementation.  My clients (both of them) have asked, "how do I get MS Word to do this..., or how do I get MS Excel to to that..." which, I have to think, does take logic (considering how much I charge them)... just maybe not to the same depth as C or C++.

My passion would be programming for laboratory equipment (i.e., device interfaces for pressure, flowmeter, maybe pH, UV, seriall 4-20ma devices)  But, so far, I'm more advanced than "hello world" and not advanced enough for GUI's and device drivers.  So I get frustrated quickly with the beginning and overwhelmed with the intermediate.

Any advice on a starting point?  Because, I would love to advance my programming (C, C++. python, java, something useful to multiple (i.e., linux ) platforms) but I really don't know where to start.

I think the programming thing is covered elsewhere, but I don't recall seeing anything for the lower intermediate programmer that was hoping to automate data collection for something along the lines of a UF/DF skid...  though, that may have been a bit specific to hope for...

FYI-- in case it didn't make it through before-- THANK YOU!!  beyond getting my tablet working right,  this thread really has gotten me looking more at how C code is written.. Thanks so much to Phenest and Robnz.

PS- did either of you get the SD/PCMCIA working?  I've only used a MoGo mouse (which charges regardless of the data transfer)  but don't have SD support on Feisty?

---

### Post by popch on 2007-11-20
I'm frightfully sorry. I copied the following text exactly into the file, replacing everything from '/*' up to (inluding) the brace after the last return statement:

[quote=phenest;3672701]
```
/* Coordinate data bit check */
if (data[0] & 0x40)
{
if ((int)data[0] == 0xc1)
{
if (data[1] & 0x07)
{
ds = &common->wcmChannel[0].work;
/* Now fool it into thiking it's in proximity */
ds->proximity = 1;
ds->buttons = ((data[1] & 0x07) << 3);
xf86WcmEvent(common,0,ds);
}
}
return common->wcmPktLength;
}
```

However, this will not compile. I seem to get no errors from ./configure, but make yields:

./wcmISDV4.c:331: Fehler: expected declaration or statement at end of input

I presume that I missed some end of statement delimiter or some curly brace or something. Since I can not even 'read' c, I am at a loss here.

Can I bother you to help me?

---

### Post by phenest on 2007-11-20
Ok. Here is the wcmISDV4.c file with changes:
```
/*
 * Copyright 1995-2002 by Frederic Lepied, France. <Lepied@XFree86.org>
 * Copyright 2002-2007 by Ping Cheng, Wacom Technology. <pingc@wacom.com>		
 * 
 * This program is free software; you can redistribute it and/or
 * modify it under the terms of the GNU General Public License
 * as published by the Free Software Foundation; either version 2
 * of the License, or (at your option) any later version.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU Lesser General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software 
 * Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA.
 */

#include "xf86Wacom.h"
#include "wcmSerial.h"
#include "wcmFilter.h"

static Bool isdv4Detect(LocalDevicePtr);
static Bool isdv4Init(LocalDevicePtr);
static void isdv4InitISDV4(WacomCommonPtr, const char* id, float version);
static int isdv4GetRanges(LocalDevicePtr);
static int isdv4StartTablet(LocalDevicePtr);
static int isdv4Parse(LocalDevicePtr, const unsigned char* data);

	WacomDeviceClass gWacomISDV4Device =
	{
		isdv4Detect,
		isdv4Init,
		xf86WcmReadPacket,
	};

	static WacomModel isdv4General =
	{
		"General ISDV4",
		isdv4InitISDV4,
		NULL,                 /* resolution not queried */
		isdv4GetRanges,       /* query ranges */
		NULL,                 /* reset not supported */
		NULL,                 /* tilt automatically enabled */
		NULL,                 /* suppress implemented in software */
		NULL,                 /* link speed unsupported */
		isdv4StartTablet,     /* start tablet */
		isdv4Parse,
	};

/*****************************************************************************
 * isdv4Detect -- Test if the attached device is ISDV4.
 ****************************************************************************/

static Bool isdv4Detect(LocalDevicePtr local)
{
	WacomDevicePtr priv = (WacomDevicePtr) local->private;
	WacomCommonPtr common = priv->common;
	return (common->wcmForceDevice == DEVICE_ISDV4) ? 1 : 0;
}

/*****************************************************************************
 * isdv4Init --
 ****************************************************************************/

static Bool isdv4Init(LocalDevicePtr local)
{
	int err;
	WacomDevicePtr priv = (WacomDevicePtr)local->private;
	WacomCommonPtr common = priv->common;

	DBG(1, priv->debugLevel, ErrorF("initializing ISDV4 tablet\n"));    

	/* Try 19200 first */
	if (xf86WcmSetSerialSpeed(local->fd, common->wcmISDV4Speed) < 0)
		return !Success;
   
	/* Send stop command to the tablet */
	err = xf86WcmWrite(local->fd, WC_ISDV4_STOP, strlen(WC_ISDV4_STOP));
	if (err == -1)
	{
		ErrorF("Wacom xf86WcmWrite error : %s\n", strerror(errno));
		return !Success;
	}

	/* Wait 250 mSecs */
	if (xf86WcmWait(250))
		return !Success;

	return xf86WcmInitTablet(local,&isdv4General,"ISDV4", common->wcmVersion);
}

/*****************************************************************************
 * isdv4InitISDV4 -- Setup the device
 ****************************************************************************/

static void isdv4InitISDV4(WacomCommonPtr common, const char* id, float version)
{  
	/* set parameters */
	common->wcmProtocolLevel = 4;
	common->wcmPktLength = 5;       /* length of a packet 
					 * device packets are 9 bytes long,
					 * multitouch are only 5 */
	common->wcmResolX = 2540; 	/* tablet X resolution in points/inch */
	common->wcmResolY = 2540; 	/* tablet Y resolution in points/inch */
	common->wcmTPCButton = 1;	/* Tablet PC buttons on by default */
	common->wcmTPCButtonDefault = 1;
	common->tablet_id = 0x90;
}
static int isdv4GetRanges(LocalDevicePtr local)
{
	char data[BUFFER_SIZE];
	WacomDevicePtr priv = (WacomDevicePtr)local->private;
	int maxtry = MAXTRY, nr;
	WacomCommonPtr common =	priv->common;

	DBG(2, priv->debugLevel, ErrorF("getting ISDV4 Ranges\n"));
	/* Send query command to the tablet */
	do
	{
		nr = xf86WcmWrite(local->fd, WC_ISDV4_QUERY, strlen(WC_ISDV4_QUERY));
		if ((nr == -1) && (errno != EAGAIN))
		{
			ErrorF("Wacom xf86WcmWrite error : %s", strerror(errno));
			return !Success;
		}
		maxtry--;
	} while ((nr == -1) && maxtry);

	if (maxtry == 0)
	{
		ErrorF("Wacom unable to xf86WcmWrite request query command "
				"after %d tries\n", MAXTRY);
		return !Success;
	}

	/* Read the control data */
	maxtry = MAXTRY;
	do
	{
		if ((nr = xf86WcmWaitForTablet(local->fd)) > 0)
		{
			nr = xf86WcmRead(local->fd, data, 11);
			if ((nr == -1) && (errno != EAGAIN))
			{
				ErrorF("Wacom xf86WcmRead error : %s\n", strerror(errno));
				return !Success;
			}
		}
		maxtry--;  
	} while ( nr <= 0 && maxtry );

	if (maxtry == 0 && nr <= 0 )
	{
		ErrorF("Wacom unable to read ISDV4 control data "
				"after %d tries\n", MAXTRY);
		return !Success;
	}

	/* Control data bit check */
	if ( !(data[0] & 0x40) )
	{
		/* Try 38400 now */
		if (common->wcmISDV4Speed != 38400)
		{
			common->wcmISDV4Speed = 38400;
			return isdv4Init(local);
		}
		else
		{
			ErrorF("Wacom Query ISDV4 error magic error \n");
			return !Success;
		}
	}
	
	common->wcmMaxZ = ( data[5] | ((data[6] & 0x07) << 7) );
	common->wcmMaxX = ( (data[1] << 9) | (data[2] << 2) 
				| ( (data[6] & 0x60) >> 5) );      
	common->wcmMaxY = ( (data[3] << 9) | (data[4] << 2 ) 
				| ( (data[6] & 0x18) >> 3) );
	common->wcmVersion = ( data[10] | (data[9] << 7) );

	return Success;
}

static int isdv4StartTablet(LocalDevicePtr local)
{
	int err;

	/* Tell the tablet to start sending coordinates */
	err = xf86WcmWrite(local->fd, WC_ISDV4_SAMPLING, (strlen(WC_ISDV4_SAMPLING)));

	if (err == -1)
	{
		ErrorF("Wacom xf86WcmWrite error : %s\n", strerror(errno));
		return !Success;
	}

	return Success;
}

static int isdv4Parse(LocalDevicePtr local, const unsigned char* data)
{
	WacomDevicePtr priv = (WacomDevicePtr)local->private;
	WacomCommonPtr common = priv->common;
	WacomDeviceState* last = &common->wcmChannel[0].valid.state;
	WacomDeviceState* ds;
	int n, cur_type, ismt = 0;
	static int lastismt = 0;

	DBG(10, common->debugLevel, ErrorF("isdv4Parse \n"));

	/* determine the type of message */
	if (data[0] & 0x10)
	{
		ismt = 1;
		common->wcmPktLength = 5;
	}
	else
	{
		common->wcmPktLength = 9;
		if (common->buffer + common->bufpos - data < common->wcmPktLength)
		{
			/* we can't handle this yet */
			return 0;
		}
	}

	if ((n = xf86WcmSerialValidate(common,data)) > 0)
		return n;
	else
	{
		/* Coordinate data bit check */
		if (data[0] & 0x40)
		{
			if ((int)data[0] == 0xc1)
			{
				if (data[1] & 0x07)
				{
					ds = &common->wcmChannel[0].work;
					/* Now fool it into thiking it's in proximity */
					ds->proximity = 1;
					ds->buttons = ((data[1] & 0x07) << 3);
					xf86WcmEvent(common,0,ds);
				}
			}
			return common->wcmPktLength;
		}
	}
	/* pick up where we left off, minus relative values */
	ds = &common->wcmChannel[0].work;
	RESET_RELATIVE(*ds);

	if (ismt)
	{
		if (!lastismt && last->pressure)
		{
			/* pen sends both pen and MultiTouch input, 
			 * since pressing it creates pressure. 
			 * We only want the pen input though.
			 */
			return common->wcmPktLength;
		}
		lastismt = ismt;

		/* MultiTouch input is comparably simple */
		ds->proximity = 0;
		ds->x = (((((int)data[1]) << 7) | ((int)data[2])) - 18) * common->wcmMaxX / 926;
		ds->y = (((((int)data[3]) << 7) | ((int)data[4])) - 51) * common->wcmMaxY / 934;
		ds->pressure = (data[0] & 0x01) * common->wcmMaxZ;
		ds->buttons = 1;
		ds->device_id = STYLUS_DEVICE_ID;
		ds->device_type = 0;
		DBG(8, priv->debugLevel, ErrorF("isdv4Parse MultiTouch\n"));
	}
	else
	{
		ds->proximity = (data[0] & 0x20);

		/* x and y in "normal" orientetion (wide length is X) */
		ds->x = (((int)data[6] & 0x60) >> 5) | ((int)data[2] << 2) |
			((int)data[1] << 9);
		ds->y = (((int)data[6] & 0x18) >> 3) | ((int)data[4] << 2) |
			((int)data[3] << 9);

		/* pressure */
		ds->pressure = (((data[6] & 0x07) << 7) | data[5] );

		/* buttons */
		ds->buttons = (data[0] & 0x07);

		/* check which device we have */
		cur_type = (ds->buttons & 4) ? ERASER_ID : STYLUS_ID;

		/* first time into prox */
		if (!last->proximity && ds->proximity) 
			ds->device_type = cur_type;
		/* check on previous proximity */
		else if (cur_type == STYLUS_ID && ds->proximity)
		{
			/* we were fooled by tip and second
			 * sideswitch when it came into prox */
			if ((ds->device_type != cur_type) &&
				(ds->device_type == ERASER_ID))
			{
				/* send a prox-out for old device */
				WacomDeviceState out = { 0 };
				xf86WcmEvent(common, 0, &out);
				ds->device_type = cur_type;
			}
		}

		ds->device_id = (ds->device_type == CURSOR_ID) ? 
			CURSOR_DEVICE_ID : STYLUS_DEVICE_ID;

		/* don't send button 3 event for eraser 
		 * button 1 event will be sent by testing presure level
		 */
		if (ds->device_type == ERASER_ID && ds->buttons&4)
		{
			ds->buttons = 0;
			ds->device_id = ERASER_DEVICE_ID;
		}

		DBG(8, priv->debugLevel, ErrorF("isdv4Parse %s\n",
			ds->device_type == ERASER_ID ? "ERASER " :
			ds->device_type == STYLUS_ID ? "STYLUS" : "NONE"));
	}
	xf86WcmEvent(common,0,ds);
	return common->wcmPktLength;
}

```

---

### Post by popch on 2007-11-21
On ubuntu 7.10, every single step of your procedure now works. Still no joy.

The wacom driver now compiles and works. xidump reports events when tapping the pen on the pen buttons.

The entries in .profile work. If present, 'xidump stylus' reports buttons 190-192 being pressed and released. If absent, other button numbers are shown (4-6, I believe)

The entries in Configuration Editor/..Metacity are correct. Pressing shift+f1, shift+2 and shift+f3 on the keyboard rotate the screen, open Xournal and open cellwriter, respectively.

Where did I miss out? how and where does the code 'Button 190' converted into shift+f1? (or 191, 192 and so forth)

BTW, there's a typo in the entries which go into .profile:

# enable buttons on HP TC1100
xsetwacom set stylus Button4 "core key shif1 F1"
xsetwacom set stylus Button5 "core key shift F2"
xsetwacom set stylus Button6 "core key shift F3"There's a digit '1' (one) after 'shift', before 'F1'

---

### Post by phenest on 2007-11-21
> **popch said:**
> On ubuntu 7.10, every single step of your procedure now works. Still no joy.

The wacom driver now compiles and works. xidump reports events when tapping the pen on the pen buttons.

The entries in .profile work. If present, 'xidump stylus' reports buttons 190-192 being pressed and released. If absent, other button numbers are shown (4-6, I believe)

The entries in Configuration Editor/..Metacity are correct. Pressing shift+f1, shift+2 and shift+f3 on the keyboard rotate the screen, open Xournal and open cellwriter, respectively.

Where did I miss out? how and where does the code 'Button 190' converted into shift+f1? (or 191, 192 and so forth)

BTW, there's a typo in the entries which go into .profile:

# enable buttons on HP TC1100
xsetwacom set stylus Button4 "core key shif1 F1"
xsetwacom set stylus Button5 "core key shift F2"
xsetwacom set stylus Button6 "core key shift F3"There's a digit '1' (one) after 'shift', before 'F1'

You say it works but no joy. Do you mean you followed the procedure fine, but the buttons do nothing?

Do not concern yourself with the strange codes reported by xidump. If you run xev, it should report the correct key codes for Shift and F1,F2, and F3.

I noticed the typo too. I will edit that.


If xev reports the correct key codes, then try using different key combinations (I'm now using <Control><Shift>F1 etc). If you're using Compiz, have a look at my tutorial for this tablet. I have added a bit regarding the buttons not working using Compiz and how to fix it.

---

### Post by popch on 2007-11-23
> **phenest said:**
> If xev reports the correct key codes

It took a while for me to realize that xev only reports the events I was interested in when the mouse cursor was placed within xev's window.

Now I have found that out, I can state positively that xev detects my touching those areas beside the screen with the pen. 

The events are
[LIST]
[*]ButtonPress
[*]EnterNotify
[*]KeymapNotify
[*]LeaveNotify
[*]ButtonRelease
[*]LeaveNotify[/LIST]The ID (numer) of the button varies. Before ***xsetwacom set stylus Button4 "core key Shift F1"*** the button is reported as #4, after as #190. 

This appears to be my remaining problem: The stylus reports those areas as buttons, and metacity does not expect button presses but key presses on the keyboard. The xsetwacom command mentioned above makes all appearances of translating a button press into a key press but does not actually do that thing.

What step did I miss?

---

### Post by shadowstar on 2008-01-02
Took me a while, but it worked. Some notes:

All I needed to install was xorg-dev to solve all dependencies compiling the wacom driver:
```
 sudo apt-get install xorg-dev 
```

Also, you'll find wacom_drv.so located in "<wacom source folder>/src/xdrv/". This took me a long time to find...

After a reboot, I decided to use xbindkeys instead of the Gnome Configuration Editor. That way, I can stick with the same configuration regardless of what environment you use. :KS
For those that don't know, run this:

```
 sudo apt-get install xbindkeys xbindkeys-config 
```

Then, you can extract the example .xbindkeysrc in the attachment in your home folder. Or, you can run this command to start making your own .xbindkeys config:

```
 xbindkeys --defaults > ~/.xbindkeysrc 
```
(It's an adaptation of the command given when xbindkeys is run for the first time).

Then play with the file by using xbindkeys-config (or with a text editor :KS). Then all you have to do is run xbindkeys everytime you start your session. Besides Ubuntu, I've played with (K/X/Flux)buntu, but I don't remember exactly how you start a program automatically with those window managers :(

robnz & phenest - good look! I've been sticking with Edgy Eft b/c it was the last Ubuntu version to work with the buttons until now... I wish I had the time/skill to delve into C-based drivers like that...

---

### Post by kanatejr on 2008-04-05
Biggest problem I have... The pen doesnt work... As in the cursor won't move around when I drag the pen on the screen.

Thought it was a driver problem but did all the things you guys mentioned here but still no avail. HELP!

---

### Post by romana on 2008-06-09
> **kanatejr said:**
> Biggest problem I have... The pen doesnt work... As in the cursor won't move around when I drag the pen on the screen.

Thought it was a driver problem but did all the things you guys mentioned here but still no avail. HELP!

try this thread : [http://ubuntuforums.org/showthread.php?t=563736](http://ubuntuforums.org/showthread.php?t=563736)

---

