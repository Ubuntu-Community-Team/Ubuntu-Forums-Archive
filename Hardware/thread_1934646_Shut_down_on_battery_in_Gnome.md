---
title: "Shut down on battery in Gnome"
date: 2012-03-02
forum: Hardware
---

### Post by Retor on 2012-03-02
I have a laptop that I used to be connected to the network by wire. It booted down when I yanked to power supply. I achieved this by making 
/etc/acpi/events/battery
call the ../powerbtn.sh script in stead of ../power.sh

([See this post]("http://ubuntuforums.org/showthread.php?t=1850513"))

But I had to drop the cord any switch to wifi. Easiest way to automate wifi connection on boot was to set the laptop to automatically log into Gnome. 

Since then the laptop hasn't shutdown when I pull the power cord. I think it is because acpi gives over power control to pm(?) when the user is logged into Gnome.

I couldn't find out much about PM, and the folders in /etc/pm/ were empty.

For now I've set it to shutdown when power is critically low though the GUI. But that means that it'll run for two hours before it shuts down.

Any ideas on how to change it so that it again will shut down when I pull the power cord - even though it is logged into Gnome?

---

