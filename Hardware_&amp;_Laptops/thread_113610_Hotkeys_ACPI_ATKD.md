---
title: "Hotkeys ACPI ATKD"
date: 2006-01-06
forum: Hardware &amp; Laptops
---

### Post by Teddy-O on 2006-01-06
I have two hotkeys on my Compaq Presario 2100US Laptop that don't work, and I want to hook them up. One has a magnifying glass logo on it and the other a question mark. I'm assuming they are meant to hookup to a search engine and a help source of some sort.

Here's what I know: acpid monitors events. Events and their handler scripts are listed in etc/acpi and etc/acpi/events folders. Actual keys are mapped to a key combination or  hex number (listed in System>Preferences>Keyboard Shortcuts).

As an example, my internet browser hotkey is mapped to 0xbb ( =decimal [COLOR="Red"]178[/COLOR] ). That key press seems to be recognized by acpid as the /etc/acpi/events/asus-internet file which passes it on to webbtn.sh for handling, as shown below. I can see how the handler recognizes the button mapping as [COLOR="Red"]178[/COLOR], but my question is where is the [COLOR="Red"]ATKD 00000051[/COLOR] number mapped to the hotkey? Is it in a config file someplace? Where? And what does ATKD stand for anyway?

In short: I need to find the ATKD number for the two buttons.

Here's the contents of the event and event handler files:

EVENT:

# /etc/acpi/events/asus-internet
# This is called when the user presses the internet button and calls
# /etc/acpi/hotkey.sh for further processing.

event=hotkey [COLOR="Red"]ATKD 00000051[/COLOR]
action=/etc/acpi/webbtn.sh


EVENT HANDLER:

#!/bin/bash

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs

getXconsole
if [ x"$XAUTHORITY" != x"" ]; then
    acpi_fakekey [COLOR="Red"]178[/COLOR]
fi

Thanks.

--Teddy-O

---

