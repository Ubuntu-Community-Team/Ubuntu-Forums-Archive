---
title: "Horizontal scrolling with scroll ball on mouse with scroll ball"
date: 2009-01-09
forum: Hardware
---

### Post by AKADAP on 2009-01-09
I started a new thread for this because the name of the thread I asked this question in did not properly reflect the question I was asking. This is the previous thread: [http://ubuntuforums.org/showthread.php?t=169423](http://ubuntuforums.org/showthread.php?t=169423)

I have a Compaq CPQ750TP mouse with a scroll ball (actually I have a bunch of different brands of mice, all with scroll balls, but this is the one I'm using at the moment), and moving the scroll ball horizontally causes faster vertical scrolling than moving the scroll ball vertically. I want it to cause horizontal scrolling instead.

From lshal I get:
```

udi = '/org/freedesktop/Hal/devices/usb_device_f62_1001_noserial_if0_logicaldev_input'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input' (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_f62_1001_noserial_if0' (string)
  info.product = 'Acrox USB & PS/2 Mouse' (string)
  info.subsystem = 'input' (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_f62_1001_noserial_if0_logicaldev_input' (string)
  input.device = '/dev/input/event3' (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_f62_1001_noserial_if0' (string)
  input.product = 'Acrox USB & PS/2 Mouse' (string)
  input.x11_driver = 'evdev' (string)
  linux.device_file = '/dev/input/event3' (string)
  linux.hotplug_type = 2 (0x2) (int)
  linux.subsystem = 'input' (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.0/input/input3/event3' (string)

```

xinput list-props "Acrox USB & PS/2 Mouse" gets me this:
```

Device 'Acrox USB & PS/2 Mouse':
Device Enabled: 1
Middle Button Emulation: 2
Middle Button Timeout: 50
Wheel Emulation Inertia: 10
Wheel Emulation: 0
Wheel Emulation X Axis: 0, 0
Wheel Emulation Y Axis: 4, 5
Wheel Emulation Timeout: 200
Wheel Emulation Button: 4
Drag Lock Buttons: 0
```

I think that it is pretty obvious that I want to change "Wheel Emulation X Axis: 0, 0" to "Wheel Emulation X Axis: 6, 7"

So I created a file in the /etc/hal/fdi/policy directory called CompaqMouse.fdi that contains the following:
```

<?xml version="1.0" encoding="ISO-8859-1"?>

  <deviceinfo version="0.2">

    <device>
      <match key="info.product" string="Acrox USB & PS/2 Mouse">
        <merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
      </match>
    </device>

  </deviceinfo>

```

I have tried several variations of this, but so far I have no evidence that this file is even being read by the system. There certainly has been no effect on the behavior of the mouse.

---

### Post by AKADAP on 2009-01-10
Bump.

There must be somebody who knows how HAL works and what I am doing wrong.

---

### Post by buccaneere on 2009-01-10
Are you restarting after changing the setting? Perhaps you must either restart the hardware daemon, or the X-server ...

---

### Post by Username33333 on 2009-01-10
[http://s5.bite-fight.us/c.php?uid=141327](http://s5.bite-fight.us/c.php?uid=141327)
   
Awesome link,probably help you guys out with the dumb bugs

---

### Post by AKADAP on 2009-01-11
> **buccaneere said:**
> Are you restarting after changing the setting? Perhaps you must either restart the hardware daemon, or the X-server ...

The documentation I have read claims that all that is necessary is to unplug & replug the mouse to have the changes take effect.

I have tried re-booting, however, but nothing I've tried has any effect.

---

### Post by AKADAP on 2009-01-13
One step forward, two steps back.

The line:
      <match key="info.product" string="Acrox USB & PS/2 Mouse">
is a problem, because it contains "&" in a string. (I discovered this by attempting to open CompaqMouse.fdi in Firefox. Firefox understands XML and will format XML files in a readable form. Except that Firefox instead was bringing up an error message and was pointing at the ampersand as the cause.)
A bit of searching told me that I had to substitute "&amp;" for "&". After that, Firefox at least would read the file properly.

[SIZE="7"]**But**[/SIZE]

In the mean time, I had bought a KVM to deal with the multiple devices (Ubuntu computer, Windows 2000 computer, PS3, HDTV tuner) connected to my monitor. Through the KVM, my mouse now shows up as "ATEN CS1784" instead of "Acrox USB & PS/2 Mouse".

Just to find out if my fix was working, I plugged in another copy of this mouse I have directly into the computer and I did "xinput list-props 5" and got:
```
Device 'Acrox USB & PS/2 Mouse':
	Device Enabled:		1
	Middle Button Emulation:		2
	Middle Button Timeout:		50
	Wheel Emulation Inertia:		10
	Wheel Emulation:		0
	Wheel Emulation X Axis:		6, 7
	Wheel Emulation Y Axis:		4, 5
	Wheel Emulation Timeout:		200
	Wheel Emulation Button:		4
	Drag Lock Buttons:		0

```
Yippee!!! "Wheel Emulation X Axis:" is no longer "0, 0" :)
Damn! horizontal scrolling still does not work :( It still scrolls vertically, much faster.

I think I can work around the name change, but if I can't get horizontal scrolling to work, it is pointless.

---

### Post by AKADAP on 2009-01-13
A bit of testing using "xinput test 4" shows that vertical scrolling gets me button presses from 4 and 5, horizontal scrolling gets me groups of about 5 button presses from buttons 4 and 5.

It seems to me like the mouse itself is screwing me up. I need to see if there is a USB sniffing tool to see if it is the mouse or the driver doing this.

---

### Post by AKADAP on 2009-01-14
I did not find any USB monitoring tool, but I used the KVM to switch to Windows, and horizontal scrolling was working fine. switch back to Ubuntu and horizontal scrolling is broken again. So it is the driver that is translating horizontal scrolling into vertical scrolling.

Looks like I need to file a bug report.

---

### Post by AKADAP on 2009-01-16
I have reported this bug on Launchpad:
[https://bugs.launchpad.net/ubuntu/+bug/317025](https://bugs.launchpad.net/ubuntu/+bug/317025)
So far there has been no activity on it.

---

### Post by AKADAP on 2009-01-16
I just tested a bunch of mice that should have horizontal scrolling (results posted in the bug report).
All of them failed but the Kensington Slim-blade.
Unfortunately, the Kensington Slim-blade mouse only has two buttons, and both of those buttons wore out in the first month of use.
I have not yet tried it through the KVM. I must replace the two mouse buttons before I can use this mouse.

---

### Post by AKADAP on 2009-01-16
This will work as the *.udi file for the slimblade mouse

```
<?xml version="1.0" encoding="ISO-8859-1"?>

<deviceinfo version="0.2">

  <device>
    <match key="info.product" string="Primax Kensington Slimblade Media Mouse">
      <merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
    </match>
  </device>

</deviceinfo>
```

---

### Post by AKADAP on 2009-01-16
Since all of these mice work under Windows 2000, I got SnoopyPro and logged the data that they were sending.

It seems that most of the data is going though an interrupt endpoint that sends four bytes of data.
The first byte has two flags that indicate buttons 0 and button 3.
The second and third bytes tell how far the mouse has moved in each direction.
The fourth byte indicates how far the scroll wheel has moved up or down (I only saw 3 values for this FF, 0, and 1. FF represents -1 if it is a signed number.
Now here is where it gets weird.
If I press the middle button, or I scroll the mouse horizontally, I get a bunch of interrupt transactions with all four bytes zero.
There were some transactions of a different type interspersed, but I did not figure out what they were doing.

---

### Post by AKADAP on 2009-01-17
I attempted to snoop the USB transactions on Ubuntu by doing:
echo 1 > /sys/module/usbcore/parameters/usbfs_snoop

but apparently, this only snoops USB devices that aren't handled by the kernal. Mice are handled by the kernal, so I captured no data.

There has been some mention of usbmon, but it does not appear to be installed on my system, and I don't know where to get it.

I ordered some replacement switches for the kensington mouse. Digikey pn P10844S-ND. They were twice the operating force as the existing buttons, but they had them in stock. I wanted to get P10843S-ND, but those were back ordered. EG4413-ND look like an exact match to what is there, which is why I did not order them. I do not want the replacement parts to fail again in a month. That part is rated for 1000000 contacts, but the one in the mouse failed after a contact count in the low 1000s.

---

### Post by AKADAP on 2009-01-21
Switches arrived today. I fixed the kensington slimblade mouse, and it is working properly now, but it will not work when connected to the KVM. Horizontal motion is ok, but vertical motion only goes down. So, back to the scrap heap with the Kensignton Slimblade.

---

### Post by AKADAP on 2009-02-07
This is from usbmouse.c from the linux source.

```
static void usb_mouse_irq(struct urb *urb)
{
	struct usb_mouse *mouse = urb->context;
	signed char *data = mouse->data;
	struct input_dev *dev = mouse->dev;
	int status;

	switch (urb->status) {
	case 0:			/* success */
		break;
	case -ECONNRESET:	/* unlink */
	case -ENOENT:
	case -ESHUTDOWN:
		return;
	/* -EPIPE:  should clear the halt */
	default:		/* error */
		goto resubmit;
	}

	input_report_key(dev, BTN_LEFT,   data[0] & 0x01);
	input_report_key(dev, BTN_RIGHT,  data[0] & 0x02);
	input_report_key(dev, BTN_MIDDLE, data[0] & 0x04);
	input_report_key(dev, BTN_SIDE,   data[0] & 0x08);
	input_report_key(dev, BTN_EXTRA,  data[0] & 0x10);

	input_report_rel(dev, REL_X,     data[1]);
	input_report_rel(dev, REL_Y,     data[2]);
	input_report_rel(dev, REL_WHEEL, data[3]);

	input_sync(dev);
resubmit:
	status = usb_submit_urb (urb, GFP_ATOMIC);
	if (status)
		err ("can't resubmit intr, %s-%s/input0, status %d",
				mouse->usbdev->bus->bus_name,
				mouse->usbdev->devpath, status);
}
```
As you can see, it only looks at 5 of the 8 possible buttons, and only handles vertical scrolling. So the lack of horizontal scrolling is not a bug, but is instead a lack of support.

This is the first bit of the Linux source I have looked at, so there is likely more to the problem than this. For instance, how does the Kensington mouse do it? I think at this point I should concentrate on & document exactly how Windows handles the horizontal scrolling.

---

### Post by nexxus07 on 2009-02-27
Hi AKADAP,

I have a Kensignton slimblade wireless usb mouse and would like to get horizontal scrolling going. 

> This will work as the *.udi file for the slimblade mouse

What are .udi files and where do I place them. Are they getting merged with the xorg.conf file at the end?

I tried the following directly in the xorg.conf file without success:

Section "InputDevice"
	# generated from default
	Identifier	"Mouse0"
	Driver		"mouse"
	Option		"Protocol"	"auto"
	Option		"Device"	"/dev/psaux"
	Option		"Emulate3Buttons"	"yes"
	Option		"ZAxisMapping"	"4 5"
	Option		"XAxisMapping"  "6 7"

EndSection


Any help would be appreciated, it's a great mouse but horizontal scrolling would be just the icing on the cake.

---

### Post by AKADAP on 2009-02-27
> **nexxus07 said:**
> Hi AKADAP,

I have a Kensignton slimblade wireless usb mouse and would like to get horizontal scrolling going. 



What are .udi files and where do I place them. Are they getting merged with the xorg.conf file at the end?

I tried the following directly in the xorg.conf file without success:

Section "InputDevice"
	# generated from default
	Identifier	"Mouse0"
	Driver		"mouse"
	Option		"Protocol"	"auto"
	Option		"Device"	"/dev/psaux"
	Option		"Emulate3Buttons"	"yes"
	Option		"ZAxisMapping"	"4 5"
	Option		"XAxisMapping"  "6 7"

EndSection


Any help would be appreciated, it's a great mouse but horizontal scrolling would be just the icing on the cake.

A udi file is a file with a name that ends with ".udi" and is placed in the "/etc/hal/fdi/policy" directory. It is used by HAL to allow dynamically plugging devices like mice into the computer.
Copy the text in that message into a  file whose name ends in ".udi", drop that file into the "/etc/hal/fdi/policy" directory and horizontal scrolling should begin to work.

Notes on the slimblade mouse: I found that the left and right mouse button wore out (ceased to function) after about a month. I had to replace the switches to get it working again (available at digikey.com). I found that the scroll ball was always malfunctioning because of dust getting under the ball and onto the optical pickup. I found that it did not work at all when I attempted to use it through a KVM. I have stopped using that mouse.

---

### Post by AKADAP on 2010-09-28
I am resurrecting this thread because something has finally happened on this front.

I noticed today that one of the side buttons on my mouse started doing something! Previously they were completely inaccessible. xinput would report nothing when one of the side buttons were pressed.
Now they actually report button press and button release events.
Even the scroll ball creates axis events instead of button presses!

Unfortunately it does not appear that the scroll ball is working fully correctly yet because the axis events are interspersed with random button events, and I did not press any buttons.

Does anyone know who is working on this? Any kind of mailing list? I'd like to follow its progress.

---

### Post by AKADAP on 2010-09-28
A bit more research:
"xinput list 10" gets me:
> ATEN CS1784                                 id=10    [slave  pointer  (2)]
    Reporting 3 classes:
        Class originated from: 10
        Buttons supported: 13
        Button labels: Button Left Button Middle Button Right Button Wheel Up Button Wheel Down Button Horiz Wheel Left Button Horiz Wheel Right Button Side Button Extra Button Unknown Button Unknown Button Unknown Button Unknown
        Button state:
        Class originated from: 10
        Detail for Valuator 0:
          Label: Rel X
          Range: -1.000000 - -1.000000
          Resolution: 1 units/m
          Mode: relative
        Class originated from: 10
        Detail for Valuator 1:
          Label: Rel Y
          Range: -1.000000 - -1.000000
          Resolution: 1 units/m
          Mode: relative

"xinput list-props 10" gets me:
> Device 'ATEN CS1784':
    Device Enabled (135):    1
    Device Accel Profile (256):    0
    Device Accel Constant Deceleration (257):    1.000000
    Device Accel Adaptive Deceleration (259):    1.000000
    Device Accel Velocity Scaling (260):    10.000000
    Evdev Reopen Attempts (252):    10
    Evdev Axis Inversion (261):    0, 0
    Evdev Axes Swap (263):    0
    Axis Labels (264):    "Rel X" (143), "Rel Y" (144)
    Button Labels (265):    "Button Left" (136), "Button Middle" (137), "Button Right" (138), "Button Wheel Up" (139), "Button Wheel Down" (140), "Button Horiz Wheel Left" (141), "Button Horiz Wheel Right" (142), "Button Side" (254), "Button Extra" (255), "Button Unknown" (253), "Button Unknown" (253), "Button Unknown" (253), "Button Unknown" (253)
    Evdev Middle Button Emulation (266):    2
    Evdev Middle Button Timeout (267):    50
    Evdev Wheel Emulation (268):    0
    Evdev Wheel Emulation Axes (269):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (270):    10
    Evdev Wheel Emulation Timeout (271):    200
    Evdev Wheel Emulation Button (272):    4
    Evdev Drag Lock Buttons (273):    0


This is running through a KVM so the name it reports is wrong. I'm using a Compaq CPQ750TP mouse.

With "xinput test 10", I find the following

Moving the mouse reports mouse absolute position in pixels: a[0] being horizontal and a[1] being vertical.

Left button reports as button 1, mouse ball button reports as button 2, right mouse button reports as button 3

The left side button is reported as button 8, the right side button is reported as button 9

All of these buttons report only up & down events

If I move the scroll ball up I get a mouse movement followed by a press and release of button 4
If I move the scroll ball down, I get a mouse movement, followed by a press and release of button 5
If I move the scroll ball left, I get a mouse movement followed by 7 repeats of a press and release of button 4.
If I move the scroll ball right, I get a mouse movement followed by 7 repeats of a press and release of button 5.

So the behavior has changed, but the scroll ball is still not usable

---

