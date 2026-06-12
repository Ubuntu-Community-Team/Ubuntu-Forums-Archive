---
title: "Disabling the touchpad when a mouse is plugged in (SO CLOSE!)."
date: 2009-04-12
forum: Hardware
---

### Post by cfogelberg on 2009-04-12
Hi all,

I've been tweaking my touchpad's behaviour. Right now I'm trying to have it disable itself when my USB mouse (logitech wireless) is plugged in. It nearly works, but I there are two problems with it so far, and any help would be much appreciated.

I'm not going to explain in gory detail what I've done in this post, and will leave that for a how to later. Here I'm just going to summarise the details.

* I have written a udev rule that should call a script whenever the wireless receiver is plugged in/unplugged. "udevadm test" shows that this script is called whenever the rule matches. I'm running the Jaunty beta on my Dell XPS M1330 and AFAICT the synaptics touch pad drivers are all present and working.

* However, the rule only matches/the script only fires when the mouse receiver is plugged in. I know that this is the case despite the second problem (details of that soon) because I also create a directory when the script is run, and that directory is only created when the mouse is plugged in. E.g. if I delete the directory before unplugging the mouse receiver it isn't recreated. This is the first problem, some information that might help debug what's going on:

Example dmesg output as I plug in:
```
[19136.768109] usb 5-1: new low speed USB device using uhci_hcd and address 21
[19136.943832] usb 5-1: configuration #1 chosen from 1 choice
[19136.974978] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input48
[19136.996331] generic-usb 0003:046D:C518.0027: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1/input0
[19137.025669] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.1/input/input49
[19137.048546] generic-usb 0003:046D:C518.0028: input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1/input1
```

And unplug the wireless usb receiver key thing:
```
[19143.272146] usb 5-1: USB disconnect, address 21
```

I don't know why udev isn't firing an event when the mouse receiver is unplugged, it seems to be being detected. Would it have a different pattern? The rules that I've written are:
```
# Touchpad off when logitech mouse is plugged in:
ACTION=="add", ATTR{phys}=="usb-0000:00:1d.0-1/input1", ATTR{name}=="Logitech USB Receiver", RUN+="/home/christo/bin/touchpad-onoff.sh add"

# Touchpad on when logitech mouse is unplugged:
ACTION=="remove", ATTR{phys}=="usb-0000:00:1d.0-1/input1", ATTR{name}=="Logitech USB Receiver", RUN+="/home/christo/bin/touchpad-onoff.sh remove"
```

* The second problem is that the script doesn't disable the touch pad! The script is as follows:
```
#!/bin/bash

# This script turns the touchpad on if the variable ACTION="remove", and off if ACTION="add"

#mkdir /home/christo/MOUSE

ACTION=add

if [ "$1" ]; then
    ACTION=$1
fi

mkdir /home/christo/MOUSE$ACTION

if [ $ACTION = "add" ]; then
    echo Turning touchpad off
    synclient touchpadoff=1
else
    echo Turning touchpad on
    synclient touchpadoff=0
fi
```

When I run the script or either of these commands from the terminal myself it works as expected. And I know that it is being run (at least when the mouse receive is plugged in) because the directory ~/MOUSEadd gets created.

Other things I've tried have been sudo -u christo "synclient touchpadoff=1" and "sudo synclient touchpadoff=1" but those are just random shots in the dark and didn't work.

Summary:
* The udev rule only matches when the device is added/plugged in, and not when it is removed/unplugged.
* Whatever way udev is running the script means that "synclient touchpadoff=1" and "synclient touchpadoff=0" just fail silently.

Any help much appreciated, I'm keen to write this up as my first stab at a how-to for other people to use. Getting just the syndaemon stuff and other things working took quite a lot of hacking around and reading, and it would be nice to be able to synthesise an updated version of the old how-tos.

Thanks,
Christo

---

### Post by Scotty Bones on 2009-05-05
This is something that I am interested in being able to do. I don't have the knowledge to be of much help, but if you need a tester, I would be more than happy.

I'll continue to watch with interest.

---

### Post by cfogelberg on 2009-05-06
> **Scotty Bones said:**
> This is something that I am interested in being able to do. I don't have the knowledge to be of much help, but if you need a tester, I would be more than happy.

I'll continue to watch with interest.

Yep, I'll definitely be in touch - I've shelved this a bit for the time being due to work pressure, but it's near the top of the todo list so hopefully I'll get onto it soon-ish :)

---

### Post by xMarine73 on 2009-05-14
Interesting.  I've got a script that runs and polls x for input devices every couple of seconds to detect a change in my mouse connection.  I've wanted to tap into the event side of things but didn't know where to turn even after exhaustive googling (is that a word? lol).

Here's my script in hopes it might help you, though I doubt it as it doesn't really deal with the event issues you're experiencing.

```

#!/bin/bash
#
# Toggle touchpad on and off
#
# For startup wait for desktop to load first.

while true
do
	if ps -A | grep gnome-panel > /dev/null; 
	then
		echo 'X loaded'
		break; 
	else
		echo 'X not loaded, waiting...'
		sleep 5
	fi
done

while true
do
	# 'xinput list' will list all input devices x detects
	# I could reference my usb mouse by ID but I'm afraid that if I plug
	# another device in before my mouse, it might not have the same ID each
	# time.  So using the device name makes it relatively fail-safe.

	if xinput list 'Microsoft Microsoft? 2.4GHz Transceiver v5.0';
	then


		# Found my usb wireless mouse
		# Disable everything on the Touchpad and turn it off

		synclient TouchpadOff=1 MaxTapTime=0 ClickFinger1=0 ClickFinger2=0 ClickFinger3=0;
 


		# End all syndaemon capturing which may have been used to monitor the touchpad/keyboard activity

		killall syndaemon

	else
		# My usb wireless mouse isn't present we need the touchpad
		# Reenable Touchpad and configure pad-clicks
		# RTCornerButton is the Right Top Corner on the touchpad
		# 	The value 3 maps it as the right click button
		# RBCornerButton is the Right Bottom Corner on the touchpad
		#	The value 2 maps it as the middle click button

		synclient TouchpadOff=0 MaxTapTime=150 ClickFinger1=1 ClickFinger2=2 ClickFinger3=3 RTCornerButton=3 RBCornerButton=2;


		# Force break of touchpad functions while typing if the touchpad is enabled.
		# Add a 3 second interval following keyboard use which helps to prevent the
		# mouse from jumping while typing & resting hands on restpad or the touchpad

		syndaemon -i 3 -d;
	fi
	
	# wait 2 seconds and poll the mouse state again
	sleep 2
done


```

I'm subscribing to this thread to keep tabs on any progress made.

---

### Post by Pitt Stains on 2009-06-07
@cfogelberg: I don't think this will work.  I've been hacking at a similar problem for a few hours, and as I was going over the udev documentation ([http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)), I came across this:

> udev does not run these programs on any active terminal, and it does not execute them under the context of a shell. Be sure to ensure your program is marked executable, if it is a shell script ensure it starts with an appropriate shebang (e.g. #!/bin/sh), and do not expect any standard output to appear on your terminal.

As I understand this, the script you designate is essentially run in a different environment than yours.  So changes to the filesystem will "take," but echoing output or playing audio, for instance, will not.

Maybe this is a good way to think about it: Imagine you've walked up to a server and logged in.  Then you SSH into the server from your laptop as the same user.  If you change or delete a file from the session you started on your laptop, you will see the same changes to the filesystem from the terminal.  However, if you display a file's contents using cat, only your laptop will display the file contents, even though you are logged in as the same user on the server.

I'm not an expert, but this is how I read the situation.  I'd love to hear someone else's thoughts... or better yet, a workaround!

---

### Post by Setheus on 2009-11-09
> **Scotty Bones said:**
> This is something that I am interested in being able to do. I don't have the knowledge to be of much help, but if you need a tester, I would be more than happy.

I'll continue to watch with interest.

Im on the same position: interest but no knowledge to help. Like Scotty I would love to be a tester. ;)

---

