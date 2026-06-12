---
title: "wlan led on ASUS laptop"
date: 2007-08-17
forum: Hardware &amp; Laptops
---

### Post by fvds on 2007-08-17
I managed to get the wlan led on my ASUS notebook working.
This is how I did it:

My ASUS is a Z9200 / Z92U, having a BCM4306 wlan onboard. I use the NetworkManager to start the wlan adapter. Ubuntu 7.04 is the OS level. Gnome as desktop.

The wlan led is controlled by the asus acpi, which installed during software installation. The way to lightup the led is quite simple:
```
echo "1" > /proc/acpi/asus/wled
```
Turning it off is done with:
```
echo "0" > /proc/acpi/asus/wled
```

Try this from the commandline:
```
sudo echo "1" > /proc/acpi/asus/wled
```
If the result is a burning led, you are almost there! 

Next comes the NetworkManager (dispatcher). This tool executes in  alphabetical order the scripts in  ```
/etc/NetworkManager/dispatcher.d
```
There is one script there named 01ifupdown.
We are going to create a new script there, and we call it 02lights:```
sudo gedit /etc/NetworkManager/dispatcher.d/02lights
```
Copy and past this code: ```
#!/bin/sh -e
# Script to dispatch NetworkManager events
#

if [ -z "$1" ]; then
    echo "$0: called with no interface" 1>&2
    exit 1;
fi

# Fake ifupdown environment
export IFACE="$1"
export LOGICAL="$1"
export ADDRFAM="NetworkManager"
export METHOD="NetworkManager"
export VERBOSITY="0"

# Run the right scripts
case "$2" in
    up)
	export MODE="start"
	export PHASE="up"
        echo "1" > /proc/acpi/asus/wled
	;;
    down)
	export MODE="stop"
	export PHASE="down"
        echo "0" > /proc/acpi/asus/wled
	;;
    pre-up)
	export MODE="start"
	export PHASE="pre-up"
#        echo "1" > /proc/acpi/asus/wled
	;;
    post-down)
	export MODE="stop"
	export PHASE="post-down"
#        echo "0" > /proc/acpi/asus/wled
	;;
    *)
	echo "$0: called with unknown action \`$2'" 1>&2
	exit 1
	;;
esac
```

Save and exit gedit. Now only thing left is set the rights for the new script ```
sudo chmod 755 02lights
```to make it executable.

Thats all......

---

